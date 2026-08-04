---
title: 'FrothSeg: run the same list on real images and the order inverts'
date: 2026-07-30
permalink: /rollings/2026/07/frothseg-the-order-inverts/
tags:
  - computer-vision
  - flotation
  - negative-results
  - honesty
---

FrothSeg: run the same list on real images and the order inverts
======

![FrothSeg: the froth ranking against the real-transfer ranking, family by family](/images/projects/frothseg_app.png)

A follow-up finding in [FrothSeg](https://frothseg.fasl-work.com), and the reason its benchmark page carries two rankings instead of one.

On synthetic froth with exact per-bubble ground truth, fifteen methods sit in a certain order: the learned LamellaStar ensemble leads at mean AP 0.5186, just ahead of Cellpose-SAM at 0.5099, with the classical watershed family below. Then I took the same fifteen methods, applied the synthetic-fitted post-processing **unchanged**, and ran them over 64 real photographs of dense touching instances (BBBC038, CC0). Nothing retrained, nothing recalibrated. The numbers measure transfer, not fit.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The order inverts, family by family.</strong><br/>
<span style="color:#5a9ac0;font-size:13px;">Methods trained only on my generator fall the most (mean AP change <strong>-0.243</strong>). Classical methods with no learned prior move up on average (<strong>+0.071</strong>). The one method carrying a large external prior, Cellpose-SAM, rises (<strong>+0.199</strong>), because the adjacent domain plays to its pretraining. LamellaStar drops 0.394.</span>
</div>

The load-bearing caveats stay attached: BBBC038 is an adjacent domain (touching nuclei, not froth), it plays to Cellpose-SAM's cell-microscopy pretraining and says nothing about froth accuracy, and there is still no real froth data, so this cannot clear the release gate. It measures one thing only, whether the ladder generalises off the generator, and the answer for the models that only saw the generator is no. Two classical methods that move against their tier are named rather than averaged away. That is why the page shows both rankings: a method that wins on your own synthetic data can be the one that travels worst. Part of the [Faena](https://faena.fasl-work.com) hub. [Live](https://frothseg.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_FrothSeg).
