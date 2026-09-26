---
title: 'Aerovia: a rejected first version, replaced rather than patched, and now the airflow moves'
date: 2026-09-12
permalink: /rollings/2026/09/aerovia-a-rejected-version-replaced-not-patched/
tags:
  - aerovia
  - mining
  - ventilation
  - engineering
---

Aerovia: a rejected first version, replaced rather than patched, and now the airflow moves
======

![Aerovia, design, solve, trace and screen, all local in the browser](/images/projects/aerovia_pipeline.svg)

Aerovia 0.02.001 is on main today. The first version of this underground-ventilation workbench did not reach the bar and I rejected it; the rebuild started again from the product template on the shared shell, and the rejected version is recorded as such rather than quietly overwritten. The release receipt ties source promotion, the executed pipelines, the public runtime verification and the downloadable artifacts to exact commits.

The whole loop runs in the browser. Draw the network in 3D (draw, connect, move, split; boundaries and fans; mapped node and airway CSV import; undo and recovery; portable projects). Solve it: flow, pressure, paths, recirculation, fan duty, sensitivity, energy and baseline comparisons. Release a conservative passive tracer with pulse or continuous sources, scheduled changes, timeline playback and a complete mass ledger. Screen designs with MLP and graph models that ship as 24 ONNX exports, each with its held-out approximation limit, so a learned answer is labelled by how far it may be from the solver and the planner knows when to fall back to it.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">What 0.02.001 adds is the thing I most wanted to see: the solved airflow field animated.</strong><br/>
Tracer particles move along the signed transport field, colour follows concentration, the fan rotors turn, a live-airflow marker sits on the instrument, and the animation pauses while the architecture dialog is open.<br/>
<span style="color:#5a9ac0;font-size:13px;">Twelve authored networks, 33,792 learned dataset states and the 216-cell benchmark are reproducible from the public scripts; the public site passed 34 Chromium journeys without retries, five direct-route refreshes and all 24 inference checks.</span>
</div>

What is not claimed, in the product's own words: the networks are planning inputs, not measured operational mines; user acceptance, industrial savings, field calibration and adoption are not inferred. Apache-2.0 for the code and the authored networks.

[Live](https://aerovia.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_Aerovia)
