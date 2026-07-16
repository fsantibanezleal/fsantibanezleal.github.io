---
title: "TailWatch — InSAR Ground-Deformation Studio for Tailings Dams & Slopes"
date: 2026-07-15
excerpt: "An in-browser InSAR ground-deformation studio for tailings dams and slopes: a multi-temporal line-of-sight displacement cube (velocity, coherence, cumulative series) with classical inverse-velocity failure forecasting plus two small neural nets. Five cases are physics-simulated from a forward model, one is a real Sentinel-1 sample. Honest by design: on the held-out benchmark the classical velocity map (AUC 0.968) beats the learned anomaly autoencoder (AUC 0.898), and the app says so.<br/><img src='/images/projects/tailwatch_app.png'>"
collection: portfolio
tags: [geotechnical, insar, ground-deformation, tailings-dam, slope-stability, inverse-velocity, forecasting, conformal-prediction, onnx, sentinel-1, mining]
---

TailWatch is an in-browser **InSAR ground-deformation studio** for tailings dams and slopes. It renders a multi-temporal line-of-sight displacement cube (velocity, coherence, cumulative series) and runs classical failure forecasting plus two small neural nets over it. Live at [tailwatch.fasl-work.com](https://tailwatch.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) mining-analytics hub.

![TailWatch — an InSAR displacement cube with inverse-velocity forecasting and two ONNX models, in the browser](/images/projects/tailwatch_app.png)

## What runs on the selected case

- **Classical tier** (training-free): per-pixel OLS velocity with a slope t-statistic significance test, two-geometry LOS decomposition into Up and East, and a Fukuzono inverse-velocity time-of-failure forecaster (EWMA velocity, onset-of-acceleration detection, r-squared gate). A split-conformal interval (Vovk) wraps the failure time, calibrated per lead-time bucket and validated on a disjoint held-out set.
- **Learned tier** (ONNX, in-browser): a 1-D CNN six-class time-series classifier runs live on every clicked pixel, and a denoising conv-autoencoder trained on normal-only patches produces an unsupervised anomaly map.

## The data, stated plainly

Five of six cases are simulated from a physically-grounded forward model: true 3-D motion projected on real Sentinel-1 look geometry, plus stratified and turbulent atmosphere, DEM-error, orbital ramp and coherence-driven decorrelation. Every error term is a real InSAR error source, but the dam, the pit and the collapse are invented. One case is real: a COMET LiCSAR / LiCSBAS Sentinel-1 clip over the Campi Flegrei caldera. That is a volcano, not a tailings dam, used as a domain-transfer probe, and the repo says so.

## The honest limit

On a held-out split the classical velocity map beats the learned anomaly detector: |v| AUC 0.968 versus the AE anomaly AUC 0.898, and the Benchmark page reports it rather than hiding it. The inverse-velocity forecaster reaches 5.7% median time-of-failure error with 0 false alarms over 60 control scenes, and the split-conformal interval reaches 0.892 empirical coverage against a 0.900 nominal. TailWatch is not calibrated to any real dam, not a real-time ingest system, and makes no full SBAS network-inversion or map-fused-alarm claim.

[Live demo](https://tailwatch.fasl-work.com) · [Source on GitHub](https://github.com/fsantibanezleal/CAOS_TailWatch)
