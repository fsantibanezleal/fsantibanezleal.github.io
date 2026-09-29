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

The cases are authored inside sourced ranges, each range naming its source or labelled as authored, and are not calibrated plants. Two measured lanes, the HZDR particle dataset (RODARE 336) and 52 GeoMet locked-cycle tests (Zenodo 7051975), are kept apart from the engine and never used to calibrate it; the engine is checked against published examples labelled as such. Applying the workbench to a specific plant needs that plant's own metallurgical tests. Version 0.06.000 acted on an audit of its own science. The mineral grindabilities had let a soft bulk mineral override the ore's Bond work index, understating grinding energy up to 1.9 times; every nominal case now grinds at 0.83 to 0.91 of Bond's efficiency, held by a test. Checking every case against its source found seven outside the ranges their sources give, not the three the audit named, and all seven were re-authored inside them; a claims test now holds the manuscript draft to the records. It ships behind 364 Python tests, 174 frontend tests and a 712-check browser gate, with a bake re-run in a sandbox and compared file by file before adoption, every ONNX export bit-identical. Part of the Faena hub; MIT.

[Live](https://oreflow.ml.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_OreFlow)
