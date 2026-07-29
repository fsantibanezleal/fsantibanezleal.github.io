---
title: 'Seven more mining tools crossed the bar, each with a negative result on it'
date: 2026-07-08
permalink: /rollings/2026/07/faena-seven-more-at-bar/
tags:
  - mining
  - analytics
  - honesty
  - Faena
---

Seven more mining tools crossed the bar, each with a negative result on it
======

![One of the eleven live Faena tools: DispatchLab, a truck-shovel dispatch bench in the browser](/images/projects/dispatchlab_app.png)

The [Faena](https://faena.fasl-work.com) hub went from three live tools to eleven. The seven that just crossed the bar span most of the value chain: [TailWatch](https://tailwatch.fasl-work.com) (InSAR ground deformation), [DispatchLab](https://dispatchlab.fasl-work.com) (truck-shovel dispatch), [ChancaDEM](https://chancadem.fasl-work.com) (crusher comminution), [CoreLog](https://corelog.fasl-work.com) (drill-core lithology), [PitForge](https://pitforge.fasl-work.com) (ultimate pit limit), [ProspectMap](https://prospectmap.fasl-work.com) (prospectivity) and [FragmentIQ](https://fragmentiq.fasl-work.com) (fragmentation).

What I want to note is not that they are live. It is what each one puts on screen when the learned model does not help:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">One honest result per tool, on the tile:</strong><br/>
TailWatch: the classical velocity map (AUC 0.968) beats the learned anomaly autoencoder (0.898).<br/>
DispatchLab: the Monte-Carlo rollout policy wins 0 of 8 seeds under cycle-time uncertainty.<br/>
PitForge: the grade neural net ties ordinary kriging (0.9613 vs 0.958); it never beats it.<br/>
ProspectMap: on real MVT data, a trivial distance-to-deposit null (0.783) ties the best model.<br/>
<span style="color:#5a9ac0;font-size:13px;">ChancaDEM keeps its name honest too: despite "DEM", the engine is a closed-form population balance, and the 3D chamber is a kinematic animation, not a physics solve.</span>
</div>

Each tool still has its exact or classical core doing the real work (a Dinic min-cut solving PitForge's pit to within 2e-9 of three published MineLib optima; a Whiten population balance calibrated to ten HP500 crusher surveys; a Fukuzono inverse-velocity forecaster with conformal bands). The learned layer sits on top and is measured against that core, in public, including when it loses. That is the whole point of building them this way: a single flattering accuracy would hide exactly the thing an operator needs to know. Eleven live, the rest planned, [honestly counted](https://faena.fasl-work.com).
