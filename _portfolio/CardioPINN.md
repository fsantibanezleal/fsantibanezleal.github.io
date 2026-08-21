---
title: "CardioPINN, Physics-Informed Cardiac Inverse-Problem Lab"
date: 2026-07-14
excerpt: "A two-case lab in physics-informed cardiac reconstruction on 100% real measured data, scoped as a complement to classical methods, not a replacement: calibrated per-node uncertainty (2-sigma ~0.90) and a resolved aortic relative-pressure field, outputs the classical estimate cannot give, at point-accuracy parity with Tikhonov (stated in-app).<br/><img src='/images/projects/cardiopinn_app.png'>"
collection: portfolio
tags: [scientific-ml, physics-informed, inverse-problems, ecgi, 4d-flow-mri, uncertainty]
---

A two-case lab in **physics-informed cardiac reconstruction**, run entirely on **real measured data** (EDGAR torso-tank and in-situ ECGi beats; one thoracic-aorta 4D-flow MRI scan), and scoped as a **complement to classical methods, not a replacement**. Live at [cardiopinn.fasl-work.com](https://cardiopinn.fasl-work.com).

![CardioPINN: two offline lanes, Tikhonov+ensemble ECGi and a divergence-free PINN for 4D-flow, baked to JSON and replayed](/images/projects/cardiopinn_app.png)

## The right scorecard

Point accuracy sits at **parity with a well-tuned Tikhonov baseline** on all four beats, and the app states it, by design: replacing classical accuracy was never the goal. What the physics adds is what the deterministic estimate structurally cannot:

- a **calibrated per-node uncertainty** (2-sigma coverage **0.89-0.90** across all four real beats), so you see not just a reconstruction but where to trust it;
- a **resolved relative-pressure field** from a well-posed solve on the 4D-flow side, a different output class than the one-number Bernoulli estimate used clinically.

## Tested advances, published nulls

Candidate advances are validated on known-answer analytic flows (the real data has no invasive gold standard). Two are confirmed and CI-tested: **spatial** analytic-autograd source and flux (pressure-drop error 0.066 vs 4.19 mmHg, 6 of 6, roughly 63x) and **temporal** analytic-autograd dv/dt (scale ~1.0, correlation above 0.99 down to ~6 frames per cycle, where 3-frame finite differences lose amplitude by sinc aliasing). Three nulls are published alongside, including a hard divergence-free construction that was refuted. The ECGi case is honest about its own method: it is regularized least squares plus a graph prior and a deep ensemble, not a PINN; only the 4D-flow case is.
