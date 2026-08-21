---
title: "ChargeCascade, Tumbling-Mill Charge Motion & Power Studio"
date: 2026-06-26
excerpt: "A live in-browser 3D studio for tumbling-mill (SAG / ball / rod) charge motion and power: critical speed, the cascading → cataracting → centrifuging transition, toe/shoulder, and Hogg-Fuerstenau / Morrell / Bond power, closed-form physics recomputed on every slider, with a trained ONNX power surrogate and an out-of-envelope anomaly guard.<br/><img src='/images/projects/chargecascade_studio.svg'>"
collection: portfolio
tags: [mining, comminution, simulation, 3d-visualization, onnx]
---

A live, in-browser **3D studio for tumbling-mill charge motion and power** (SAG / ball / rod). Move a slider (speed, filling, ball load, mill size) and watch the charge shift between **cascading, cataracting and centrifuging**, with toe/shoulder angles and net power recomputing instantly and the governing equations on screen. Live at [chargecascade.fasl-work.com](https://chargecascade.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) mining-analytics hub.

![ChargeCascade: exact physics, a 3D kinematic view, and a thin learned layer](/images/projects/chargecascade_studio.svg)

## Exact physics as the authority

A dependency-free TypeScript engine implements the published closed-form equations exactly and recomputes on every control change: critical speed `Nc = 42.3/√(D−d)`, the Davis regime bands, toe/shoulder geometry, and net power as the centre-of-mass torque arm (Hogg-Fuerstenau, a Morrell-form, Bond). Two exact analytic controls pass (an empty mill draws 0 kW; at critical speed the charge centrifuges), so the engine is **verified, not asserted**.

## A thin, honest learned layer

Run offline, the exact engine labels a synthetic operating envelope on which two small models are trained (PyTorch → ONNX) and served live via **onnxruntime-web**: a **power surrogate** (~5% error vs the exact engine) for instant envelope sweeps, and an **out-of-distribution autoencoder** (AUC 0.922) that flags off-envelope inputs. The exact engine stays the authority.

## What it is not

The 3D is a **kinematic animation** of the closed-form engine, **not** a DEM / N-body simulation, and there is no population-balance breakage model. All operating points are **synthetic-but-realistic**; the power magnitude is **calibrated** to a ~1.3 MW textbook reference, not validated against a real mill. Honest boundaries are the point: a fast design-intuition studio, not a plant model.

[Live demo](https://chargecascade.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_ChargeCascade)
