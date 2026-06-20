---
title: "RotorVitals — Bearing Fault Diagnosis by Envelope Analysis"
date: 2026-06-19
excerpt: "Open, explainable diagnosis of rolling-element bearing faults from a vibration signal — entirely in the browser, showing its working. Field-standard envelope analysis, calibrated to the public CWRU benchmark.<br/><img src='/images/projects/rotorvitals_pipeline.svg'>"
collection: portfolio
tags: [predictive-maintenance, vibration, dsp, envelope-analysis, bearings, mining]
---

Open, explainable diagnosis of **rolling-element bearing faults** from a vibration signal — running entirely in the browser, showing its working. Bearings are the most common failure point of crushers, conveyors, pumps and fans; RotorVitals computes the bearing's kinematic defect frequencies, demodulates the resonance a defect excites, and reads the **envelope spectrum** for energy at exactly those lines. Live at [rotorvitals.fasl-work.com](https://rotorvitals.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) mining-analytics hub.

![RotorVitals — the envelope-analysis pipeline](/images/projects/rotorvitals_pipeline.svg)

## The pipeline

`signal → band-pass → Hilbert envelope → envelope spectrum → harmonic scoring → diagnosis`

- **Kinematics** — BPFO / BPFI / BSF / FTF from bearing geometry and shaft speed (Randall & Antoni 2011).
- **Envelope analysis** — band-pass around the structural resonance, the analytic signal via the Hilbert transform, magnitude, then its spectrum. A fault appears as a line at its kinematic frequency.
- **Decision** — each fault is scored by summed peak energy at its first 5 harmonics, normalized by the noise floor; the top score wins above a floor gate, else "healthy". Every number traces to a computed line — no black box.

## Honest about data

No dataset is shipped or required: the engine is closed-form DSP and the demo signals are generated on-device from published physics (McFadden & Smith 1984), doubling as a self-validation set — the engine recovers the fault frequency that generated each. The SKF 6205/6203 geometries match the open **CWRU Bearing Data Center** rig, so the same pipeline reads real CWRU recordings unchanged. A single localized defect at steady speed is the easy case; real machines bring variable speed and multiple faults, but the frequency relationships are exact and transfer directly.

[Live demo](https://rotorvitals.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_RotorVitals)
