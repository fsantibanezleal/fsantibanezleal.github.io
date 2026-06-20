---
title: "CAOS SimLab — A Didactic Lab for Simulation (DES & ABM)"
date: 2026-06-19
excerpt: "Land straight in a running simulation, move the sliders, and watch the dynamics change. An open lab for Discrete-Event Simulation and Agent-Based Modeling — ten worked scenarios, each a pure function of (params, seed) so replay is exact.<br/><img src='/images/projects/simlab_architecture.svg'>"
collection: portfolio
tags: [simulation, des, abm, operations-research, pyodide, education]
---

An **open, didactic lab** for Discrete-Event Simulation (DES) and Agent-Based Modeling (ABM). Instead of a toy script or a GUI that hides the model, you arrive directly in a running simulation, move the sliders, and watch the dynamics change — across ten worked scenarios, with a from-zero curriculum that teaches the real tools (SimPy, Mesa, OR-Tools). Live at [simlab.fasl-work.com](https://simlab.fasl-work.com).

![CAOS SimLab — one engine, two lanes, one render path](/images/projects/simlab_architecture.svg)

## Two lanes, decided by measurement

A run is a pure function of `(params, seed)` that produces a compact **trace**; the front end only animates it, so live and precomputed render through one code path — *replay is truth*. A measured 3-gate rule (pure-Python **and** under 3 s **and** trace under 1 MB) decides the lane:

- **Live** — light scenarios run in your browser via [Pyodide](https://pyodide.org); edit parameters, re-run, watch it animate. No server, nothing to install.
- **Precomputed** — heavy scenarios (native solvers like OR-Tools, large agent counts) are run offline into a seeded trace and replayed with a timeline scrubber under a clear "precomputed due to cost" banner.

## Honest simulation

The lab teaches what most demos skip: a single run is noisy, so results come from **replications + confidence intervals**; steady-state metrics need a **warm-up** cut; the same seed must reproduce the same result; and an animation is a hypothesis generator, not evidence. Each scenario validates against theory or a baseline where one exists — the M/M/c queue against the closed-form Erlang-C.

## Coverage

Ten scenarios across six visualization families (queue · agent-grid · chart · flow · gantt · route): bank/clinic queue, Schelling segregation, SIR epidemic, ED patient flow, the beer game, job-shop scheduling, construction haul routing, vehicle routing, ambulance dispatch, and a Monte-Carlo/CI study.

[Live demo](https://simlab.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_SIMLAB)
