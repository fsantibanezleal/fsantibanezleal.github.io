---
title: 'OreFlow: a grinding and separation circuit read as one balance'
date: 2026-09-26
permalink: /rollings/2026/09/oreflow-a-circuit-read-as-one-balance/
tags:
  - oreflow
  - mineral-processing
  - mining
  - faena
---

OreFlow: a grinding and separation circuit read as one balance
======

![OreFlow, an authored case through a closed-circuit engine, a live workbench and baked method records](/images/projects/oreflow_pipeline.svg)

OreFlow 0.05.000 is released today. In a processing plant a change made in one stage, a finer grind or a different classifier cut, changes the results of every stage after it, and each area reports only its own part: grinding answers for throughput and energy per tonne, classification for the load it sends forward, flotation for recovery and concentrate grade. The relations between those stages are documented, energy against particle size, the size split at the classifier, flotation kinetics, the mass balance that closes the circuit. OreFlow links them in one workbench, so a setting changed in one stage is followed through every stage after it, in the units every area reads: tonnes per hour of metal, megawatts, cubic metres of water, kilograms of reagent.

The 0.05.000 engine carries every stream as the mass flow of every mineral in 63 size classes plus water, closes the grinding circuit (an energy-specific population-balance ball mill with Plitt cyclones, the underflow returning to the mill), separates by flotation banks, a gravity bleed, magnetic drums or desliming, and closes every unit within 1e-9. A TypeScript port runs in a Web Worker within 1e-6 of the Python engine on all 72 variants, so the workbench re-solves the circuit on every control change.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The scenarios are authored, not a calibrated plant, and the measured data is kept apart.</strong><br/>
Twelve ores in four circuit families (rougher; gravity plus rougher for free-milling gold; magnetic for fine magnetite; deslime plus rougher for phosphate), six variants each, every variant changing exactly one declared input. The HZDR particle dataset and 52 GeoMet locked-cycle tests are two measured lanes that do not calibrate the circuits.<br/>
<span style="color:#5a9ac0;font-size:13px;">Method records are baked offline: kinetic fits, a constrained optimizer over limits set for every area at once, Latin-hypercube uncertainty, Sobol sensitivity, and five learned surrogates scored by leave one case out with an autoencoder guard. The bake was re-run and reproduced every case number and ONNX export bit for bit.</span>
</div>

341 Python tests, 165 frontend tests and a 684-check browser gate over three viewports, two themes and two languages. Applying the workbench to a specific plant needs that plant's own metallurgical tests; the site says so. It is the processing member of the Faena family and sits beside the single-operation products without duplicating them.

[Live](https://oreflow.ml.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_OreFlow)
