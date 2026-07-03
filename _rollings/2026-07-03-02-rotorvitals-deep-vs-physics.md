---
title: 'When the Deep Model Loses to Physics'
date: 2026-07-03
permalink: /rollings/2026/07/rotorvitals-deep-vs-physics/
tags:
  - PredictiveMaintenance
  - DeepLearning
  - Vibration
  - Honesty
---

When the Deep Model Loses to Physics
======

[RotorVitals](https://rotorvitals.fasl-work.com) has grown well past the "envelope analysis of a bearing" it started as — it now runs a source selector over real measured data (CWRU, Ottawa, MaFaulDa for diagnosis; FEMTO/XJTU/IMS run-to-failure for prognosis), a learned WDCNN classifier and autoencoder, and a four-model remaining-useful-life ladder, all live in the browser. But the result I keep coming back to isn't the deep model winning. It's the deep model losing, in a way worth showing.

I trained a WDCNN on the Case Western (CWRU) bearing rig and then asked it to work on a *different* rig, the MFPT set. It fell apart:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Cross-rig (CWRU → MFPT):</strong><br/>
the CWRU-trained WDCNN scores near chance (~49%), with <strong>0% recall on outer-race faults</strong> — it calls them "normal".<br/>
<span style="color:#5a9ac0;font-size:13px;">The training-free envelope/SES analysis, reading energy at the correct MFPT defect frequencies, transfers <strong>almost perfectly</strong> on the same files.</span>
</div>

![RotorVitals — source selector → classical DSP, learned tier, RUL ladder](/images/projects/rotorvitals_pipeline.svg)

There's a matching story within CWRU: the network trained only on 0.007″ faults nails 0.021″ but collapses on 0.014″ (27.8%) — an atypical signature, not a bug. The lesson I put on screen, rather than assert: **deep learning wins in-distribution, physics wins out-of-distribution.** It's exactly the kind of thing a single flattering accuracy number would hide, and it's the reason I show the SNR-robustness curve and the cross-dataset transfer test instead. The RUL side is a real ladder too — closed-form first-passage, particle filter, Gaussian process, deep-RUL CNN — benchmarked over 36 real run-to-failure trajectories, where the Gaussian process gives the lowest aggregate error and the transparent exponential is a close second. Bearings-first, honestly scoped, [in the browser](https://rotorvitals.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_RotorVitals).
