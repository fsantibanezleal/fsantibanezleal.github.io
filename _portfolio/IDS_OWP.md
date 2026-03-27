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

Given a limited budget of measurements, where should you sample a spatial field to minimize posterior uncertainty about its structure? The framework formalizes this as a submodular optimization problem where greedy entropy maximization achieves a (1 - 1/e) approximation guarantee to the optimal solution. At each step, the algorithm selects the next sampling location that maximally reduces the conditional entropy of the unobserved field, using empirical distributions estimated from an ensemble of training realizations.

Implementation
======

The system implements six sampling strategies for comparison: random, stratified, multiscale, oracle (full-information upper bound), adaptive entropy maximization (AdSEMES), and regular grid. Three reconstruction methods recover the full field from sparse observations: nearest neighbor interpolation, kriging, and entropy-weighted reconstruction. Synthetic field generation covers multiple geological patterns — single channels, branching systems, and multi-channel configurations. Performance is evaluated through SNR, classification accuracy, and resolvability capacity metrics that quantify how well each strategy recovers the true underlying geology.

Origin and modernization
======

This work was developed during 2014-2016 at the IDS Group (Information and Decision Systems), Universidad de Chile, under Fondecyt Grant 1140840 (PI: Prof. Jorge F. Silva). The original MATLAB codebase has been modernized as a Python/FastAPI web application with interactive visualization of the sampling process and reconstruction results.

![Optimal Spatial Sampling](/images/projects/ids_owp.svg)
