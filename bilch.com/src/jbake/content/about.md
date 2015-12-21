title=About BILCH
date=2015-09-25
type=page
tags=benchmarks
status=published
~~~~~~

How can an application use a multiprocessor effectively ?

# OS multiprocessor performance evaluation

Current [operating systems](http://people.freebsd.org/~kris/scaling/dfly.html) can handle multiprocessors well. Performance evaluation is typically done with benchmarks. Because of simplicity Sweep3D will be used. Later it is planned to use some of the  [ASC benchmarks](https://asc.llnl.gov/sequoia/benchmarks/) and other benchmarks.

## Sweep3D

Explicit parallelism is by domain decomposition and message-passing. This version of [Sweep3D](blog/2015/sweep3d-benchmark.html) supports MPI message passing libraries as well as a single processor version. Here is a [description](http://github.com/heinerbilch/sweep3d) Here are [older benchmarks](http://www.cs.rice.edu/~alc/superpages/) where I found the starting point.
![ASC Logo](ASC_co_sm.jpg)

## Benchmarks

[Benchmarks](https://www.epcc.ed.ac.uk/research/computing/performance-characterisation-and-benchmarking/epcc-openmp-micro-benchmark-suite) for OpenMP.
[SNAP](https://www.nersc.gov/users/computational-systems/cori/nersc-8-procurement/trinity-nersc-8-rfp/nersc-8-trinity-benchmarks/snap/) an update of Sweep3D, intended for hybrid computing architectures.

## Tools

[Scalasca 2.x series](http://www.scalasca.org/software/scalasca-2.x/download.html)

## Future work

[Fortran Coarrays](http://opencoarrays.org)

## Applications

Cosmological simulation [GADGET - 2](http://www.mpa-garching.mpg.de/gadget/)

# Flame Graphs

[Flame graphs](http://www.brendangregg.com/flamegraphs.html) are a visualization of profiled software, allowing the most frequent code-paths to be identified quickly and accurately.

![Flame Graph](tcp-conn.svg) 