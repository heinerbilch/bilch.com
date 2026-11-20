title=SeisCNN: Microearthquake Detection with a Compact CNN
date=2026-11-20
type=post
tags=blog
status=published
~~~~~~

When my deep-learning course ended, the final project was supposed to be a modest exercise: train a small convolutional network to tell earthquakes from noise on the STEAD dataset. The finished project is now on Codeberg as [SeisCNN](https://codeberg.org/heiner/seiscnn). Along the way it turned into something more interesting: a model that matches the big two of seismic deep learning on accuracy while running roughly eleven times faster — entirely on a MacBook.

## What SeisCNN does

SeisCNN covers the full picking stack: earthquake detection, P and S arrival picking, and — as a feature neither PhaseNet nor EQTransformer offers — a coda head that estimates coda end. The final detection model, SeisCNN-PSC, has 726k parameters. It was trained on the STEAD dataset (50k earthquake traces from chunk2, 50k noise traces from chunk1) with the usual hygiene: per-trace z-scoring, splits by event ID to prevent leakage, and a channel-order correction for a data problem nobody had documented before (more on that below).

## The numbers

On a stratified benchmark of 2,000 test traces, scored on full 60-second windows:

| Model | Parameters | ROC-AUC | Throughput |
|---|---|---|---|
| SeisCNN-PSC (CoreML, Apple Neural Engine) | 726,039 | 1.0000 | 5,245 traces/s |
| EQTransformer (MPS) | 376,935 | 1.0000 | 461 traces/s |
| PhaseNet (MPS) | 268,443 | 0.9949 | 1,993 traces/s |

SeisCNN-PSC reaches EQTransformer-level detection quality at roughly eleven times its throughput, and it runs via a plain CoreML export on the Apple Neural Engine — on-device seismology, no GPU cluster required. An int8-quantized variant pushes the package size down further for deployment.

## Picking: small, but with fewer outliers

The picking heads are even smaller (about 220k parameters). On the S-picking test set, SeisCNN beats PhaseNet where it matters most: outlier robustness. The median error is 0.07 s versus 0.10 s, but the 99th percentile is 2.1 s versus 15.7 s, and the share of picks off by more than 0.5 s drops from 16.8% to 3.6%. For catalog work, the tail of the error distribution is what ruins location estimates — and that tail is where the compact model wins.

## A real data bug, found and fixed

Running a PhaseNet screener over all 200k chunk2 traces surfaced something odd: a persistent excess of flagged picks among borehole stations of the PB network. The cause turned out to be a channel-mapping inconsistency in those stations' traces. A per-station permutation search found the correct mapping; applying it halved the overall flag rate from 7.1% to 3.6% and cut the 90th-percentile error from 1.75 s to 0.19 s, while the non-PB control group stayed untouched. Sometimes the most valuable output of a deep-learning pipeline is a clean, reproducible diagnosis of the data going into it.

## What "detection is easy" actually means

A common claim in the field is that earthquake detection is a solved, simple problem. The evaluations say: it depends. With a full 60-second window including the coda, detection is close to trivial on this test set — magnitude alone is never the problem, even for microearthquakes below magnitude 1. What actually moves the needle is signal-to-noise ratio: below 10 dB, missed-detection rates rise to 2.3%, and distance beyond 100 km costs another factor. Detection is easy when the signal is there. The interesting frontier is low-SNR, far, small events — exactly where dense local networks and on-device processing matter.

## Try it

Everything is open source under BSD-2-Clause on Codeberg: [codeberg.org/heiner/seiscnn](https://codeberg.org/heiner/seiscnn). The repo contains the full pipeline (preparation, training, benchmarking, CoreML export, reports with plots), pytest coverage, and detailed documentation of each analysis step. Data and model weights stay outside the repo; the reports in the docs directory contain every number cited here.
