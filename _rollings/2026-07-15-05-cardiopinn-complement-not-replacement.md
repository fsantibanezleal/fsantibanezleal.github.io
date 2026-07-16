---
title: 'CardioPINN: complement, not replacement (and getting my own scorecard right)'
date: 2026-07-15
permalink: /rollings/2026/07/cardiopinn-complement-not-replacement/
tags:
  - physics-informed
  - inverse-problems
  - cardiac
  - uncertainty
---

CardioPINN: complement, not replacement (and getting my own scorecard right)
======

[CardioPINN](https://cardiopinn.fasl-work.com) reconstructs two cardiac quantities that cannot be measured directly, heart-surface potentials (ECGi) and the aortic relative-pressure field (4D-flow MRI), from quantities that can. All of it on real measured data: EDGAR torso-tank and in-situ beats, one thoracic-aorta 4D-flow scan, no synthetic ground truth.

The first framing I gave this work was wrong, and the correction is worth writing down. I initially scored it as "the physics-informed method does not beat a well-tuned Tikhonov baseline on point accuracy", which is true on all four beats and stated in the app. But that is the wrong scorecard: replacing classical accuracy was never the goal. The method is scoped as a complement where information is partial and confidence-per-node is part of the answer.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">What the classical method cannot give, this does:</strong><br/>
calibrated per-node uncertainty, 2-sigma coverage <strong>0.89-0.90</strong> across all four real beats;<br/>
a resolved relative-pressure <strong>field</strong> from a well-posed solve (a different output class than a one-number Bernoulli estimate).<br/>
<span style="color:#5a9ac0;font-size:13px;">Point accuracy sits at parity with Tikhonov, disclosed in-app, by design.</span>
</div>

The methods work underneath is real and tested on known-answer analytic flows: analytic-autograd derivatives beat finite differences twice, spatially (pressure-drop error 0.066 vs 4.19 mmHg, 6 of 6 configurations) and temporally (dv/dt holds scale ~1.0 and correlation above 0.99 down to ~6 frames per cycle, while 3-frame finite differences lose amplitude by the sinc aliasing law: 0.76 at 6 frames, collapsing at 4). Three null results are published alongside, including a hard divergence-free construction that was hypothesized to help pressure and was refuted.

Two lessons in one product, then. The methodological one: physics-informed reconstruction earns its place by adding outputs the classical method cannot produce, not by chasing its accuracy. And the meta one: honesty cuts both ways. Framing parity as a defeat was as inaccurate as framing it as a win would have been. [Live](https://cardiopinn.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_RES_CardioPINN).
