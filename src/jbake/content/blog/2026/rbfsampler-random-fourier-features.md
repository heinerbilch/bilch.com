title=RBFSampler: Random Fourier Features on Apple Silicon
date=2026-10-22
type=post
tags=blog
status=published
~~~~~~

Kernel SVMs with a Gaussian kernel are strong learners, but they scale badly: the kernel matrix grows with the square of the training set. In 2007, Rahimi and Recht published an elegant way out: sample random wave vectors, project the data onto them, and train a plain linear model in that space. The result approximates the Gaussian kernel at linear cost. Random Fourier Features.

[RBFSampler](https://github.com/heinerbilch/RBFSampler) is my implementation of the whole pipeline in Swift with [MLX](https://ml-explore.github.io/mlx/) on Apple Silicon: the random feature map, a linear SVM with hinge loss trained by mini-batch SGD, cross-validation, gamma tuning, and a small zoo of visualizations. It started as a learning project and stayed honest about it: Swift was new to me, MLX was new to me, so the code keeps didactic comments and a minimal dependency footprint (mlx-swift, nothing else).

## The pipeline

Draw m wave vectors w ~ N(0, 2*gamma*I), random phases b uniform in [0, 2*pi), and map every point to

```
z(x) = sqrt(2/m) * ( cos(w1*x + b1), ..., cos(wm*x + bm) )
```

An inner product in z-space approximates the Gaussian kernel exp(-gamma*||x-y||^2). A linear SVM is then trained on z(x) with hinge loss and mini-batch SGD; all linear algebra runs on the GPU via MLX.

One small detail with consequences: the mapped features lie on the unit sphere, ||z|| ~ 1, so decision values stay moderate no matter how long you train.

## Gamma is a wavelength

The tuning parameter gamma is best understood as a wavelength. Small gamma draws slow, smooth waves that vary globally; large gamma draws fast waves that look like noise on the data's scale. The cross-validation U-curve is visible in the waves themselves. On 2D blobs (shift 1.2):

* gamma = 0.05: 95.7% accuracy, decision values f in [-2.37, 2.09], a smooth, almost linear boundary
* gamma = 2.0: 94.9% accuracy, f only in [-1.32, 1.22], a jagged boundary

The slow waves stay coherent across the whole extent of a class, so the margin can build up real magnitude. The fast waves average out within a class, and the decision values stay small. Same data, same budget, very different geometry.

## What the epochs actually learn

Tracking the model epoch by epoch shows something instructive: the boundary geometry settles within the first 2 to 4 epochs (with gamma 0.05, accuracy is 92.6% at epoch 2 and 95.3% at epoch 4; everything after that moves accuracy by less than 0.1%). What keeps growing afterwards is almost only the magnitude of f: from [-0.72, 1.04] at epoch 2 to [-2.37, 2.09] at epoch 20, linear in the number of epochs. Training after the first few epochs deepens the margin; it barely moves the boundary. In the ParaView animation of the training epochs, the shell of support-vector-like points (|f| <= 1) visibly thins out over time.

## Real data: Wisconsin breast cancer

The WDBC dataset (569 points, 30 features, malignant vs benign) was the first real-world test, and it delivered two lessons for the price of one.

The first run collapsed. Cross-validation sat flat at 0.637 for every gamma — which is exactly the class prior (357 of 569 points are benign) — and the test score was the prior, too. The model had learned nothing but "predict the majority class". The diagnosis: a pure budget problem. 399 training points with batch size 256 and 20 epochs amount to 40 gradient steps; the raw 30 features can absorb the signal with that, the random Fourier features cannot. The fix was to train 300 epochs with batch size 32, and to hand the same budget to the gamma tuning, because a grid search that trains underfitted models only compares noise.

The second run showed a textbook U-curve: 0.732 at gamma 1e-4, a maximum of 0.977 at gamma 0.01, and 0.611 at gamma 3.0 — on the right flank even below the prior. With the tuned gamma, the RFF model reached 97.1% on the held-out test set, identical to the linear baseline trained with the same budget. The m-sweep over 100 to 1000 features moved results only between 96.5% and 97.6%, saturated from m=100; the differences are one or two test points out of 170.

Three takeaways:

1. A CV curve that sits flat on the class prior across the whole gamma grid is the signature of undertraining, not of a wrong gamma.
2. "The kernel brings nothing" can be undertraining in disguise. Train longer before blaming the features.
3. WDBC is almost linearly separable, so the kernel genuinely buys nothing here. The pipeline lands at the ~97-98% that kernel SVMs report on this dataset in the literature, which is the point: the tool works, the dataset just does not need the trick.

## Seeing all of it

The toolkit renders its own intuitions: 1D waves for small and large gamma, the kernel approximation against the exact Gaussian with a 1/sqrt(m) reference, the drawn wave vectors as a point cloud with the 1-sigma circle at radius sqrt(2*gamma), decision landscapes with the boundary f=0 and the margin |f|=1, a 3D decision surface and the training epochs as VTK time series for ParaView.

For WDBC, 30 features cannot be drawn directly, so the canvas is the PCA plane: PC1 explains 44.3% of the variance, PC2 19.2%, together ~63.5%. The experiment prints the caveat right into its output: points that look misclassified in the plane may be separated in the 28 invisible coordinates. The surface is a slice, not the verdict.

## Determinism

A SeededRNG (SplitMix64) drives the folds and the batch shuffling (seed plus epoch number). The same seeds produce bit-identical models — the epoch snapshots, the 3D surface and the final model agree to the last digit, and a repro test pins that one `fit` equals the sequential `fitEpoch` calls. One measurement note: the first transform compiles the Metal kernels (seconds), everything after is a warm start in milliseconds — only warm runs are worth timing.

## What's next

Ionosphere, a dataset with a genuinely nonlinear boundary, so the features have to beat the linear baseline to justify themselves. Custom Metal kernels for the feature map, and the lambda balance experiment. The repository carries the essay, the experiments and the tests: [github.com/heinerbilch/RBFSampler](https://github.com/heinerbilch/RBFSampler).
