---
title: 'FrothSeg: a real model, and the honest fact that the data does not exist'
date: 2026-07-29 18:00:00
permalink: /rollings/2026/07/frothseg-the-data-does-not-exist/
tags:
  - computer-vision
  - flotation
  - negative-results
  - honesty
---

FrothSeg: a real model, and the honest fact that the data does not exist
======

![FrothSeg: seven classical methods vs a learned LamellaStar ensemble, with an honest real-transfer probe](/images/projects/frothseg_app.png)

[FrothSeg](https://frothseg.fasl-work.com) segments flotation froth into individual bubbles, entirely client-side via ONNX, and compares a ladder of seven classical methods against a real published model, LamellaStar (a four-head net shipped as a three-seed logit-mean ensemble, with SAM2 and Cellpose-SAM as offline teachers distilled to a compact browser head).

The honest core is the data situation, and I want it stated plainly rather than hidden behind a synthetic score:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The field's real blocker:</strong><br/>
there is <strong>no public labelled real froth dataset</strong>. The search is recorded as a null (Roboflow dropped).<br/>
<span style="color:#5a9ac0;font-size:13px;">Froth cases are synthetic and labelled as such. BBBC038 (64 real dense-touching images, CC0) is an adjacent-domain transfer probe that does NOT clear the froth blocker, and the transfer study refuted its own hypothesis: the ranking is generator-specific.</span>
</div>

A real model, a real classical ladder, real transfer numbers, and a loudly stated limit. That published null, not a flattering synthetic accuracy, is the deliverable. A research lab, not a plant tool, part of the [Faena](https://faena.fasl-work.com) hub. [Live](https://frothseg.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_FrothSeg).
