---
title: 'Two Tools That Show Their Working'
date: 2026-06-19
permalink: /rollings/2026/06/simlab-rotorvitals-open/
tags:
  - Simulation
  - DSP
  - PredictiveMaintenance
  - OpenSource
---

Two Tools That Show Their Working
======

Two new things are live, both open, both running entirely in your browser, and both built around the same conviction: a tool you can't see inside is a tool you have to take on faith. I have spent enough time on the receiving end of black-box "it's fine, trust me" software to want the opposite.

The first is **[CAOS SimLab](https://simlab.fasl-work.com)** — a didactic lab for Discrete-Event Simulation and Agent-Based Modeling. Most simulation tutorials stop at a toy script; most simulation tools hide the model behind a GUI. SimLab refuses both: you land in a running simulation, move the sliders, and watch the dynamics change, with the real engine (SimPy, Mesa, OR-Tools) underneath. The design decision I'm happiest with is that a run is a *pure function of (params, seed)* → a compact trace, and the front end only animates the trace. So "replay is truth", and a measured 3-gate rule decides honestly whether a scenario is light enough to run live in the browser (via Pyodide) or must be precomputed.

![CAOS SimLab — one engine, two lanes, one render path](/images/projects/simlab_architecture.svg)

The second is **[RotorVitals](https://rotorvitals.fasl-work.com)** — bearing fault diagnosis by envelope analysis, the field-standard method, done in the open. Bearings are the most common failure point of crushers, conveyors, pumps and fans, and the satisfying thing about this domain is that the physics gives you *exact* numbers to look for:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:'Courier New',monospace;color:#e0e0e0;font-size:13.5px;line-height:1.9;">
<span style="color:#5a9ac0;"># kinematic defect frequencies from bearing geometry + shaft speed</span><br/>
BPFO · BPFI · BSF · FTF<br/>
<span style="color:#5a9ac0;"># a fault rings the resonance; demodulate it and read the spectrum</span><br/>
signal → band-pass → Hilbert envelope → envelope spectrum → score the harmonics
</div>

A developing fault shows up as a line at its exact kinematic frequency, and the diagnosis is just: which fault's first five harmonics carry the most energy above the noise floor. Every number traces back to a computed line — no classifier you have to trust. It's calibrated to the public CWRU bearing benchmark, so the same pipeline that runs the synthetic demos reads real CWRU recordings unchanged. It's part of the [Faena](https://faena.fasl-work.com) mining-analytics hub. Both are MIT-spirited, open, and yours to poke at: [SimLab](https://github.com/fsantibanezleal/CAOS_SIMLAB) · [RotorVitals](https://github.com/fsantibanezleal/CAOS_RotorVitals).
