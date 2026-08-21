---
title: "CoreLog Vision, Drill-Core Logging & Lithology Classification Workbench"
date: 2026-07-04
excerpt: "A browser-native drill-core logging workbench: it classifies sliding windows along core-tray channels into six lithologies with a CNN, merges adjacent same-class patches into a depth-stitched strip log with confidence shading, and flags out-of-distribution core with a Mahalanobis detector instead of forcing a class. It runs on procedurally synthetic trays, with a real-photo lane (DCID) used strictly as the out-of-distribution and real-head evaluation set. Honest by design: the CNN accuracy is synthetic-vs-synthetic, a label-permutation control collapses to chance, and the shipped detector is named for what it is.<br/><img src='/images/projects/corelog_app.png'>"
collection: portfolio
tags: [mining-analytics, drill-core, lithology, cnn, computer-vision, out-of-distribution, mahalanobis, onnx, geology, mining]
---

CoreLog Vision is a browser-native **drill-core logging** workbench. It classifies sliding windows along core-tray channels into six lithologies with a CNN, merges adjacent same-class patches into a depth-stitched strip log with confidence shading, and flags out-of-distribution core instead of forcing a class. Live at [corelog.fasl-work.com](https://corelog.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) mining-analytics hub.

![CoreLog Vision, a lithology CNN plus a Mahalanobis out-of-distribution flag, run client-side over core trays](/images/projects/corelog_app.png)

## Three rungs, run live

A classical rung (a colour/texture baseline plus a run-merge segmentation that emerges from the classifier), a learned rung (the 6-class lithology CNN, ONNX, softmax plus a 64-d penultimate feature in one pass), and out-of-distribution flagging via a Mahalanobis detector in that 64-d feature space. Everything runs client-side over onnxruntime-web on the WASM backend, with a graceful fallback to the classical method if a model is absent.

## What it runs on

- **Synthetic trays** (the main lane, and the training data): 8 procedurally generated cases, three lithology suites, three imaging-quality regimes, and two closed-form analytic controls. There is no in-app upload.
- **Real DCID photos** (evaluation only): the Drill Core Image Dataset is loaded as the out-of-distribution and real-head evaluation set, never as training data. 21 verbatim CC BY-NC patches are committed with DOI-level provenance.

## The honest limit

The CNN reaches 0.994 accuracy against a 0.9286 colour baseline on a grouped-by-hole split (14 train / 4 test holes), and this is stated for what it is: synthetic-vs-synthetic, the CNN scored against the generator's own ground truth, not real-core accuracy. A label-permutation null collapses to chance (top-1 0.1387 vs a 0.1429 baseline), the leakage control the grouped split is meant to guarantee. And the shipped OOD detector is named for what it is: a Mahalanobis detector at AUROC 0.9463, which replaced an incumbent pixel-autoencoder that scored 0.3078 (worse than chance); the offline benchmark winner (0.9995) is not the one that ships. The real DCID head reaches top-1 0.9916, but DCID-7 contains no schist and no ore class, so it is an evaluation lane, not a mine-lithology claim.

[Live demo](https://corelog.fasl-work.com) · [Source on GitHub](https://github.com/fsantibanezleal/CAOS_CoreLog)
