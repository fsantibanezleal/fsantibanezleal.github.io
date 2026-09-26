---
title: "Aerovia, an Underground Ventilation Design and Analysis Workbench in the Browser"
date: 2026-09-12
excerpt: "Draw a ventilation network in 3D, solve it for flow, pressure, paths, recirculation, fan duty and energy, release a conservative passive tracer with a complete mass ledger, and screen designs with learned models that ship with their approximation limit stated. Twelve authored networks, 33,792 dataset states, a 216-cell benchmark and 24 ONNX exports, all running in the browser. The networks are planning inputs, not measured mines. A first version was rejected and rebuilt in full.<br/><img src='/images/projects/aerovia_pipeline.svg'>"
collection: portfolio
tags: [mining, ventilation, network-solver, tracer-transport, onnx, three-js, browser-compute]
---

Underground ventilation is a network problem with a spatial body: airways have lengths, grades and resistances, fans have curves, and the questions a planner asks are about paths, recirculation and what happens to a contaminant released at one face over the next hour. **Aerovia** holds the whole loop in the browser, from drawing the network to reading a mass ledger, without a server.

![Aerovia, design, solve, trace and screen, all local](/images/projects/aerovia_pipeline.svg)

## Design, solve, trace

Direct spatial design in the 3D instrument: draw, connect, move and split airways, set boundaries and fans, import mapped node and airway CSV, undo and recover, carry a project as a portable file. The numerical tools link flow, pressure, paths, recirculation, fan duty, sensitivity, energy and baseline comparisons on the same network. Transport is a conservative passive tracer with pulse or continuous sources, scheduled changes, timeline playback and complete mass ledgers; since 0.02.001 the solved airflow field is animated, with tracer particles from the signed transport field, concentration-aware colour and turning fan rotors.

## Learned answers with their limit attached

![Aerovia, the three-level production network with the flow balance solved](/images/projects/aerovia_app_dark.png)

Trained MLP and graph models keep their checkpoints and ship as 24 ONNX exports with **held-out approximation limits**, so a learned answer is labelled by how far it may be from the solver and the planner knows when to fall back to it. Twelve authored network cases, 33,792 learned dataset states and the complete 216-cell benchmark are reproducible from the public scripts; imports, numerical workers and inference run client-side, which is why GitHub Pages is enough.

## What is not claimed, and the version that was rejected

The networks are authored planning inputs, no operational mine was measured, and user acceptance, industrial savings, field calibration and adoption are explicitly not claimed. The first version of this product did not reach the bar and was rejected; v0.02.000 was rebuilt from the product template on the shared shell, with a release receipt tying source promotion, executed pipelines and public runtime verification to exact commits. The public site passed 34 Chromium journeys without retries, five direct-route refresh checks and all 24 model inference checks. Apache-2.0.

[Live](https://aerovia.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_Aerovia)
