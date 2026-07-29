---
title: "SymLab — Symbolic Regression Lab (Accuracy and Recovery, Separately)"
date: 2026-07-16
excerpt: "A public research lab on symbolic regression: recovering a readable closed-form expression from data. Its reason to exist is one honest measurement: accuracy and structural recovery are different claims, and a method can clear R2 above 0.999 while returning the wrong structure. SymLab reports the two separately, on every case, and never averages them into one number.<br/><img src='/images/projects/symlab_app.png'>"
collection: portfolio
tags: [scientific-ml, symbolic-regression, genetic-programming, sparse-regression, interpretability, honesty]
---

A public research lab on **symbolic regression**: recovering an explicit closed-form expression from data, rather than fitting a predictor nobody can read. Live at [symlab.fasl-work.com](https://symlab.fasl-work.com).

![SymLab — genetic programming and sparse regression on known-law cases, accuracy and recovery in two separate columns](/images/projects/symlab_app.png)

## Accuracy and recovery are different claims

A method can fit a curve almost perfectly and hand back an expression that is structurally nothing like the law that generated the data. Reported as one averaged number, that failure is invisible, and "solved" benchmarks routinely reward getting the wrong equation. SymLab reports **accuracy (R2 on test)** and **structural recovery (did it return the true law)** as two separate columns, on every case, never averaged.

## The headline, live

On known-law cases (the Feynman set) recovery is scored exactly by edit distance to the true structure. On the Feynman Gaussian, sparse regression reaches **R2 = 1 - 1.8e-09 in about zero seconds and does not recover the law**, and neither does any genetic-programming configuration (Koza, linear scaling, deduplication). Two search families with nothing in common, one reaching a near-perfect fit in ten milliseconds, and neither finds the equation. Every accuracy-only benchmark scores this as solved; SymLab does not.
