---
title: "OreFlow, a Grinding and Separation Circuit Read as One Balance"
date: 2026-09-26
excerpt: "A change made in one stage of a processing plant moves every stage after it, and each area reports only its own part. OreFlow keeps the circuit as one balance: every stream carries every mineral in 63 size classes plus water, the grinding circuit is closed, and every unit closes within 1e-9. Twelve authored scenarios with 72 variants, re-solved in the browser on every control change; kinetic fits, an optimizer, uncertainty, Sobol sensitivity and five surrogates baked offline. Authored scenarios, not a calibrated plant.<br/><img src='/images/projects/oreflow_pipeline.svg'>"
collection: portfolio
tags: [mineral-processing, grinding, flotation, mass-balance, sobol, surrogates, mining, faena]
---

In a processing plant a change made in one stage, a finer grind or a different classifier cut, changes the results of every stage after it, and each area reports only its own part: grinding answers for throughput and energy per tonne, classification for the load it sends forward, flotation for recovery and concentrate grade. **OreFlow** links the documented relations between those stages into one open workbench, so a setting changed in one stage is followed through every stage after it.

![OreFlow, an authored case through a closed-circuit engine, a live workbench and baked method records](/images/projects/oreflow_pipeline.svg)

## One balance

The engine carries every stream as the mass flow of every mineral in 63 size classes plus water. It solves a Whiten crusher, a closed grinding circuit (an energy-specific population-balance ball mill with Plitt hydrocyclones, the underflow returning to the mill) and separation by flotation banks, a gravity bleed, magnetic drums or desliming, and closes every unit within 1e-9. Twelve authored cases in four circuit families (rougher for copper, zinc, nickel and other ores; gravity plus rougher for free-milling gold; magnetic for fine magnetite; deslime plus rougher for phosphate) carry six variants each, every variant changing exactly one declared input.

## An instrument, not a report

![OreFlow, the workbench: a soft copper porphyry case, its flowsheet with every stream's flow and grade](/images/projects/oreflow_app_dark.png)

A TypeScript port of the engine runs in a Web Worker and is held to the Python engine within 1e-6 on all 72 variants, so the workbench re-solves the circuit on every control change: the flowsheet with every stream's flow and grade, the grinding and separation curves of the current state, response sweeps over any two inputs, and a focus view for one instrument at a time, in the units every area reads: tonnes per hour of metal, megawatts, cubic metres of water, kilograms of reagent. Method records are baked offline: kinetic fits, a constrained optimizer over limits set for every area at once, uncertainty by Latin hypercube, Sobol sensitivity, and five learned surrogates scored by interpolation and by leave one case out with an autoencoder guard.

## The boundary

The cases are authored inside published ranges and are not calibrated plants. Two measured lanes, the HZDR particle dataset (RODARE 336) and 52 GeoMet locked-cycle tests (Zenodo 7051975), are kept apart from the engine and never used to calibrate it; the engine is checked against published examples labelled as such. Applying the workbench to a specific plant needs that plant's own metallurgical tests. 0.05.000 ships behind 341 Python tests, 165 frontend tests and a 684-check browser gate, with a bake that reproduced every case number and ONNX export bit for bit on a re-run. Part of the Faena hub; MIT.

[Live](https://oreflow.ml.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_OreFlow)
