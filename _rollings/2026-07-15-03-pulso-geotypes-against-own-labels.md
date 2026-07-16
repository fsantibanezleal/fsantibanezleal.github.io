---
title: 'A shape catalogue for well tests, honest about what its labels are'
date: 2026-07-15
permalink: /rollings/2026/07/pulso-geotypes-against-own-labels/
tags:
  - reservoir
  - clustering
  - unsupervised
  - honesty
---

A shape catalogue for well tests, honest about what its labels are
======

[Pulso](https://pulso.fasl-work.com) is an unsupervised catalogue of flow-behaviour classes ("GeoTypes") for fractured reservoirs. It takes the diagnostic Bourdet derivative of a pressure-transient response, clusters the curves by shape with DTW k-medoids, and attributes each class to the fracture-network descriptors that control it. The result I want to lead with is not the clustering score. It is the caveat I had to keep attached to the learned tier.

Four neural models (InceptionTime, PatchTST, an autoencoder, an embedding) are exported to ONNX and run in the browser, and they report a good test accuracy: InceptionTime 0.911, PatchTST 0.902. That number is easy to misread. It is measured against the pipeline's own k-medoids cluster labels, not an external ground truth, and the training-set silhouette there is a weak 0.190. So the nets are accurate at reproducing a weakly-separated clustering, not at classifying against reality. That distinction stays on the card.

The clustering itself, though, is real, and the reason I trust it is the control sitting next to it:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Real 4TU curves, silhouette (higher is better):</strong><br/>
low-perm <strong>0.72</strong> · mid-perm <strong>0.86</strong><br/>
single-regime control <strong>0.137</strong> (the null: no structure, so it finds none)<br/>
<span style="color:#5a9ac0;font-size:13px;">A noisy family degrades to 0.172 as it should, and a DARTS analytic gate passes at relative L2 0.0108 against a 0.05 tolerance. The null is what makes the 0.72 mean something.</span>
</div>

The corpus is real and licensed: a 4TU well-test corpus of roughly 4768 dimensionless Bourdet-derivative curves plus about 5000 DFN descriptor rows, vault-only, alongside simulated GeoDFN and open-DARTS ensembles, for 22 baked case studies. It reproduces and extends Kamel Targhi et al. 2026 (Computational Geosciences 30, 57).

Two more limits stay in view. The real low-perm case is k=2 with one rare class (a [174, 26] split), so I describe it as two behaviour classes, one rare, not a rich catalogue. And the transfer to real aquifer pumping tests is a shape-diagnostic proof only: those are a different physical system, transmissivity and storativity are unknown, and where a field site has only eight curves the attribution is skipped outright.

The physics core (Bourdet derivative plus a Warren-Root dual-porosity model via Stehfest inversion) is also the Pyodide live lane, so a pasted curve is classified against the baked medoids in the browser with conformal prediction. [Live](https://pulso.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_RES_Pulso).
