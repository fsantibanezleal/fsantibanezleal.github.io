---
title: 'A Mill''s Power Without a DEM Run'
date: 2026-07-03
permalink: /rollings/2026/07/chargecascade-mill-power/
tags:
  - Mining
  - Comminution
  - Physics
  - Simulation
---

A Mill's Power Without a DEM Run
======

The charge inside a tumbling mill is where a concentrator spends most of its energy, and its behaviour — where the load cascades, where it cataracts onto the toe, when it centrifuges — usually gets studied one of two ways: a static textbook diagram, or a heavyweight discrete-element (DEM) simulation. I wanted the fast, tunable middle, so I built [ChargeCascade](https://chargecascade.fasl-work.com): move a slider and watch the regime and the power move, live in the browser.

The thing I want to be precise about is that the authority is closed-form physics, not a particle solve. The engine implements the published equations exactly and recomputes on every change:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:'Courier New',monospace;color:#e0e0e0;font-size:14px;line-height:1.9;">
<span style="color:#5a9ac0;"># critical speed (rpm)</span><br/>
Nc = 42.3 / √(D − d)<br/>
<span style="color:#5a9ac0;"># Davis departure: cascade → cataract → centrifuge</span><br/>
cos α = φc² · (r / R)<br/>
<span style="color:#5a9ac0;"># net power = centre-of-mass torque arm</span><br/>
P = ω · M · g · arm&nbsp;&nbsp;(Hogg-Fuerstenau · Morrell-form · Bond)
</div>

![ChargeCascade — exact physics, a 3D kinematic view, a thin learned layer](/images/projects/chargecascade_studio.svg)

The 3D is a **kinematic animation** of that engine — I say so plainly, because it is *not* DEM and pretending otherwise would be the whole point missed. Two exact analytic controls keep me honest: an empty mill has to draw 0 kW, and at critical speed the charge has to centrifuge; both pass. On top, a small ONNX layer adds convenience without authority: a power surrogate (about 5% off the exact engine) for instant envelope sweeps, and an out-of-distribution autoencoder that flags when you've dragged the sliders somewhere the training envelope never went. The operating points are synthetic-but-realistic and the power magnitude is calibrated to a ~1.3 MW textbook reference, not to a real mill — it's a design-intuition studio, and it stays inside those lines. Part of the [Faena](https://faena.fasl-work.com) hub · [source](https://github.com/fsantibanezleal/CAOS_ChargeCascade).
