---
title: 'The PINN does not beat Tikhonov, and the app says so'
date: 2026-07-15
permalink: /rollings/2026/07/cardiopinn-loses-to-tikhonov/
tags:
  - physics-informed
  - inverse-problems
  - cardiac
  - honesty
---

The PINN does not beat Tikhonov, and the app says so
======

[CardioPINN](https://cardiopinn.fasl-work.com) recovers cardiac quantities that cannot be measured (heart-surface potentials, aortic relative pressure) from ones that can (body-surface potentials, 4D-flow MRI velocity), on real measured data. I am going to lead with the negative headline, because it is the honest one and the app carries it openly: the physics-informed proposal does not beat a classical baseline on any of the four ECGi beats.

On all four beats, across the human torso-tank and the in-situ dog, a well-tuned zeroth-order Tikhonov regularized least squares is better or equal on relative error, and the graph-Laplacian prior plus deep ensemble trails it. So the ECGi reconstruction numbers on the card are the classical baseline's numbers. A second bit of framing honesty: that ECGi case contains no PINN and no torch at all (it is NumPy and SciPy), so the product name over-promises across half its content. Only the 4D-flow case is a genuine PINN.

The real contribution is narrower and stands up:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">What actually holds:</strong><br/>
calibrated per-node ECGi uncertainty, 2-sigma reliability <strong>0.89 to 0.90</strong> across all 4 beats (a Tikhonov point estimate cannot give this)<br/>
analytic-autograd source and flux vs finite differences: pressure-drop error <strong>0.066 mmHg</strong> vs <strong>4.19 mmHg</strong>, winning 6 of 6 configs<br/>
<span style="color:#5a9ac0;font-size:13px;">The autograd win is a shipped, CI-tested gate, demonstrated on a known-answer analytic flow, not on the real scan. The uncertainty is at parity-to-slightly-worse point accuracy, which is stated in-app.</span>
</div>

Three other candidate advances were run and published as nulls rather than buried: a hard divergence-free curl parameterization made pressure worse (0/6), a differentiable denoiser-solver coupling gave no gain, and a structural-perturbation uncertainty field was calibrated (0.93 coverage) but uninformative on a clean lumen. There is also a recorded round-1 methodological confound that was caught and re-run on the correct path.

It is deliberately narrow: two derived artifacts, four beats, one real 4D-flow scan, and no invasive gold standard for the recovered pressure (which is why the method exists at all). Framed as a validation-discipline and negative-results study, that is a defensible outcome. Framed as a working reconstruction product, it would be selling something the artifacts do not support, so I did not frame it that way. [Live](https://cardiopinn.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_RES_CardioPINN).
