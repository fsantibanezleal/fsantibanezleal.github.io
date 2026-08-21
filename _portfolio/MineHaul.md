---
title: "MineHaul, Mine-Haulage Discrete-Event Simulation"
date: 2026-07-02
excerpt: "An open-source Python package (minehaulsim) for deterministic discrete-event simulation of open-pit and underground mine haulage on constrained road networks, with seeded parametric mine generators. Byte-deterministic, numpy-only, well-tested, the companion generator that feeds structure-real scenarios to DispatchLab.<br/><img src='/images/projects/minehaul_pipeline.svg'>"
collection: portfolio
tags: [simulation, des, mining, haulage, python, open-source]
---

An **open-source Python package** (`minehaulsim`) for deterministic **discrete-event simulation of open-pit and underground mine haulage** on constrained road networks, with seeded parametric mine generators. It is the companion **generator** for DispatchLab, MineHaul builds and simulates the mines, DispatchLab consumes and optimizes them. On [PyPI](https://pypi.org/project/minehaulsim/) (v0.10, Apache-2.0) with a documented API, CLI and docs wiki.

![MineHaul, seed → generator → gates → DES → exports → DispatchLab](/images/projects/minehaul_pipeline.svg)

## Real engine, synthetic mines, said plainly

The discrete-event engine and its physics are genuine and hand-verified: rimpull/retarder speed-by-grade, emergent truck bunching, routing on a constrained network, five dispatch baselines. Every run passes named **validity gates** and is **byte-deterministic** (asserted in CI, 227 tests on Linux + Windows). The mines are **synthetic**, seeded generators produce *realistic structure with fabricated data*, and equipment values use public spec magnitudes with **class-representative, not OEM, curves**.

## Honest scope

It is early (Alpha) and deliberately bounded: it **does not predict or optimize a real operation** (no calibration, that is DispatchLab's role), its physics anchors are qualitative literature orderings used as tests, and its novelty claim keeps its qualifier, the first **open-source** package to do mine haulage on a genuinely constrained road network (commercial closed tools exist).

[GitHub repository](https://github.com/fsantibanezleal/CAOS_MINEHAUL) · [minehaulsim on PyPI](https://pypi.org/project/minehaulsim/)
