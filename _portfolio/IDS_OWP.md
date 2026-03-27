---
title: "Optimal Spatial Sampling via Information Theory"
date: 2016-03-01
excerpt: "Information-theoretic framework for optimal well placement in geological reservoirs using adaptive sequential entropy maximization.<br/><img src='/images/projects/ids_owp.svg'>"
collection: portfolio
tags: [information-theory, entropy, sampling, geostatistics, python, fastapi]
---

This project implements the AdSEMES (Adaptive Sequential Empirical Maximum Entropy Sampling) algorithm for optimal spatial sampling in binary random fields — specifically channelized geological reservoirs. It is the computational companion to my doctoral thesis and published papers in Mathematical Geosciences and Natural Resources Research.

The core problem
======

Given a limited budget of K measurements on a binary random field X of size H x W, where should you sample to minimize posterior uncertainty about the field's structure? The problem is formalized through Shannon entropy: the optimal placement f* = argmax_f H(X_f), which is equivalent to minimizing the posterior uncertainty min_f H(X^f | X_f) since H(X) = H(X_f) + H(X^f | X_f) by the chain rule. The combinatorial search over C(H*W, K) candidate sets is NP-hard, but since entropy is a monotone submodular function, the greedy algorithm (AdSEMES) achieves a (1 - 1/e) ~ 63.2% approximation guarantee to the optimal solution (Nemhauser, Wolsey & Fisher, 1978). At each step, the algorithm selects the next sampling location that maximally reduces the conditional entropy of the unobserved field, estimating conditional probabilities P(X_i = 1 | neighbors) through multi-point pattern matching against training images.

Implementation
======

The system implements six sampling strategies for comparison: random, stratified, multiscale, oracle (full-information upper bound), adaptive entropy maximization (AdSEMES), and regular grid. A Gaussian spatial penalty function H_penalized(i') = H(i') * (1 - alpha * exp(-d^2 / (2*R^2))) prevents the locality trap where greedy selection clusters samples in one region, and a hybrid two-phase approach seeds stratified samples for minimum coverage before running the adaptive phase. Three reconstruction methods recover the full field from sparse observations: nearest neighbor interpolation, indicator kriging (solving the kriging system C*w = c with exponential variogram), and entropy-weighted inverse-distance reconstruction. Synthetic field generation covers multiple geological patterns -- single channels, branching systems, and multi-channel configurations. Performance is evaluated through SNR (dB), classification accuracy, and resolvability capacity C_k = I(f*_k)/H(X) that quantifies the fraction of total field uncertainty resolved after k measurements.

Origin and modernization
======

This work was developed during 2014-2016 at the IDS Group (Information and Decision Systems), Universidad de Chile, under Fondecyt Grant 1140840 (PI: Prof. Jorge F. Silva). The original MATLAB codebase has been modernized as a Python/FastAPI web application with interactive visualization of the sampling process and reconstruction results.

![Optimal Spatial Sampling](/images/projects/ids_owp.svg)

[View on GitHub](https://github.com/fsantibanezleal/IDS_OWP)
