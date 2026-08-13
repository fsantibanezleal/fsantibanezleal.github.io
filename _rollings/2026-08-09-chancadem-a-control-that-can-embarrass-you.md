---
title: 'ChancaDEM: report the control that can embarrass you'
date: 2026-08-09
permalink: /rollings/2026/08/chancadem-a-control-that-can-embarrass-you/
tags:
  - mining
  - simulation
  - benchmarks
  - honesty
---

ChancaDEM: report the control that can embarrass you
======

![ChancaDEM: a closed-form crusher population balance with a kinematic 3D chamber](/images/projects/chancadem_app.png)

[ChancaDEM](https://chancadem.fasl-work.com) models crushing with a closed-form Whiten population balance solved live by LU decomposition over a 28-class root-two sieve grid, with JKMRC t10 breakage, Austin appearance, Evertsson capacity and Bond power. The name says DEM and the app immediately says it is **not** DEM: the 3D chamber is a kinematic animation, and the physics is the closed-form balance. Naming a thing after the method you did not use is the kind of small dishonesty that costs a reader's trust in everything else.

The calibration is against ten published industrial HP500 surveys (Rocha et al., *Minerals* 2024, CC BY, Minas Rio itabirite), transcribed from the paper rather than from a campaign of my own, which the app also states.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Leave-one-out throughput MAPE 12.09%, with both controls beside it.</strong><br/>
<span style="color:#5a9ac0;font-size:13px;">A constant-mean control scores <strong>18.29%</strong> and a label-shuffle control <strong>25.04%</strong>. Ten surveys is a small n, the 80% interval's empirical coverage of 0.90 is labelled coarse, and the numbers are presented at that strength.</span>
</div>

A calibration number without a constant-mean control beside it is close to meaningless: it is the control that tells you whether the model learned the process or just the average. And the scope is bounded honestly at the level of equipment too. Five crusher types are offered, and only the secondary cone has a calibrated lane; the other four are labelled illustrative rather than quietly sharing the calibrated one's credibility.

The ONNX surrogate emulates the engine at R2 0.995 and 0.998, and the autoencoder beside it is a **surrogate-extrapolation guard**, not a plant anomaly detector, which is a distinction worth keeping. [Live](https://chancadem.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_ChancaDEM).
