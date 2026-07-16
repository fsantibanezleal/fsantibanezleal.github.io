---
title: "Pulso — Well-Test Diagnostic-Curve Shape Clustering and Attribution"
date: 2026-07-15
excerpt: "An unsupervised catalogue of flow-behaviour classes (GeoTypes) for fractured reservoirs: it clusters the SHAPE of pressure-transient Bourdet-derivative curves with DTW k-medoids, attributes each class to the fracture-network descriptors that control it (Random Forest + SHAP), and ships a browser workbench that classifies a user curve against the baked medoids with conformal prediction. It reproduces and extends Kamel Targhi et al. 2026 (Comp. Geosciences 30, 57) on a real 4TU corpus (~4768 curves), then transfers the same shape diagnostic to two real aquifer pumping-test sites, with an explicit caveat that the shape transfers but the physics does not.<br/><img src='/images/projects/pulso_app.png'>"
collection: portfolio
tags: [scientific-ml, well-test, pressure-transient, bourdet, warren-root, clustering, dtw, shap, conformal-prediction, onnx, geosciences, reservoir]
---

Pulso is an unsupervised **catalogue of flow-behaviour classes (GeoTypes)** for fractured reservoirs. It takes the diagnostic Bourdet derivative of a pressure-transient (well-test) response, clusters curves by shape with DTW k-medoids, and attributes each behaviour class to the fracture-network descriptors that control it. It reproduces and extends Kamel Targhi et al. 2026 (Computational Geosciences 30, 57). Live at [pulso.fasl-work.com](https://pulso.fasl-work.com). Pulso is a research lab, not part of the Faena hub.

![Pulso — shape clustering of Bourdet-derivative curves with attribution and in-browser conformal classification](/images/projects/pulso_app.png)

## Real curves, a physics core, and a browser lane

The corpus is real and licensed: a 4TU well-test corpus (~4768 dimensionless Bourdet-derivative curves plus ~5000 DFN descriptor rows, GPL-3, vault-only) alongside simulated GeoDFN and open-DARTS ensembles, for 22 baked case studies. The classical physics core (Bourdet derivative plus a Warren-Root dual-porosity model via Stehfest inversion) is also the Pyodide live-lane engine, and four ONNX models (InceptionTime, PatchTST, a curve autoencoder, an embedding model) classify a user-pasted curve against the baked medoids in the browser with conformal prediction.

## The nulls are the point

On the real 4TU curves the clustering is genuinely good: silhouette 0.72 on low-perm and 0.86 on mid-perm. What makes that trustworthy is the control next to it, a single-regime case at 0.137: when there is no structure, the method correctly does not find any, and a noisy family degrades to 0.172 as it should. A DARTS analytic validation gate passes on a homogeneous anchor (relative L2 0.0108 against a 0.05 tolerance), checking the simulation lane against a closed-form answer.

## The honest limit

Two limits stay on the card. First, the aquifer generalization is a shape-diagnostic transfer only: aquifer pumping tests are a different physical system, transmissivity and storativity are unknown, so those curves are clustered by shape, not by a physically referenced response, and where a field site has only eight curves the attribution is skipped (a proof-of-transfer, not a study). Second, the learned models' strong test accuracy (InceptionTime 0.911, PatchTST 0.902) is measured against the pipeline's own k-medoids cluster labels, not an external ground truth, and the training-set silhouette there is a weak 0.190, so those nets reproduce a weakly-separated clustering rather than classify against reality.

[Live demo](https://pulso.fasl-work.com) · [Source on GitHub](https://github.com/fsantibanezleal/CAOS_RES_Pulso)
