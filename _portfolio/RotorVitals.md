---
title: "RotorVitals, Rotating-Machinery Condition Monitoring & Prognostics"
date: 2026-06-28
excerpt: "An in-browser condition-monitoring and prognostics workbench for rotating machinery (bearings-first), on real measured vibration. A source selector switches between a synthetic generator, real diagnosis segments (CWRU / Ottawa order-tracked / MaFaulDa) and real run-to-failure trajectories (FEMTO / XJTU / IMS); classical DSP, a learned WDCNN + autoencoder, and a four-model RUL ladder run live via onnxruntime-web.<br/><img src='/images/projects/rotorvitals_pipeline.svg'>"
collection: portfolio
tags: [predictive-maintenance, condition-monitoring, prognostics, rul, vibration, wdcnn, onnx]
---

An in-browser **condition-monitoring and prognostics** workbench for rotating machinery, **bearings-first**, running on **real measured vibration**. Envelope analysis (the classic bearing-fault method) is now one tier inside it. Live at [rotorvitals.fasl-work.com](https://rotorvitals.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) mining-analytics hub.

![RotorVitals: source selector → classical DSP, learned tier, RUL ladder, live in the browser](/images/projects/rotorvitals_pipeline.svg)

## A source selector drives the whole workbench

- **Synthetic (with controls)**, a physically-grounded generator; fault type, severity, rpm and SNR are live knobs. Severities here are **synthetic and labelled as such**.
- **Real: diagnosis segment**: a measured window from **CWRU** (the classifier's native domain), **Ottawa** (time-varying speed, computed-order-tracked → a real Campbell/order view), or **MaFaulDa**.
- **Real: run-to-failure**, a real trajectory from **FEMTO / XJTU / IMS**; a life slider scrubs measured windows healthy → failure, and RUL projects against the experiment's true failure time.

## Three tiers, run live

A classical DSP chain (envelope/SES, kurtogram, cyclostationary, cepstrum, Campbell/order, ISO zones); a learned tier (a **WDCNN** classifier + a deep-autoencoder health indicator, both ONNX); and a four-model **RUL ladder** (exponential → particle filter → Gaussian process → deep-RUL CNN), benchmarked on **36 real run-to-failure trajectories** (GP gives the lowest aggregate error, ≈1 h MAE, with the transparent exponential a close second).

## Honest about the model's limits

The learned classifier is trained on CWRU and shown **in-domain** there; everywhere else it is **cross-domain-labelled**, with its failures on display: it collapses on an unseen severity (27.8%) and scores near chance cross-rig on MFPT (0% outer-race recall), while the training-free envelope analysis transfers almost perfectly. The honest lesson, shown not claimed: **deep learning wins in-distribution, physics wins out-of-distribution.** Frequency relations are exact; scope is rotating machinery, bearings-first (no gear claim).

[Live demo](https://rotorvitals.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_RotorVitals)
