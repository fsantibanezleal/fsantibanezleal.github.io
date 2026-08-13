---
title: 'FragmentIQ: 116 recovered against 70 true, and the number stays on the page'
date: 2026-08-07
permalink: /rollings/2026/08/fragmentiq-the-bias-is-in-the-artifact/
tags:
  - computer-vision
  - mining
  - benchmarks
  - honesty
---

FragmentIQ: 116 recovered against 70 true, and the number stays on the page
======

![FragmentIQ: a muckpile photo turned into a mass-weighted particle-size distribution](/images/projects/fragmentiq_app.png)

[FragmentIQ](https://fragmentiq.fasl-work.com) turns a muckpile photograph into a mass-weighted particle-size distribution: Otsu, distance transform, marker non-maximum suppression, watershed, connected components, then a mass weighting by diameter cubed, a Rosin-Rammler least-squares fit and P10/P50/P80, live in the browser.

Delineating touching rock fragments is a problem where a method can look excellent and be wrong, so the failure is shipped in the artifact rather than described in prose:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">On the R-COARSE case: 116 fragments recovered against 70 true.</strong><br/>
Over-segmentation, visible in the case, not buried in a caveat.<br/>
<span style="color:#5a9ac0;font-size:13px;">The synthetic cases are scored against per-pixel generator truth, which is the only place an exact fragment count exists at all.</span>
</div>

The learned layer is reported at the strength the sample size allows. A boundary CNN cuts P50 error from 27.2 percent to 23.8 percent with hyperparameters selected on a **disjoint** tune bank and reported on a **disjoint** test bank, and at n=8 that is labelled indicative rather than significant, because eight cases cannot carry a stronger word.

The real photographs get the same treatment. Five post-blast images from the Gole-Gohar iron-ore mine (CC BY 4.0) are marked **RELATIVE** in English and Spanish: the scale is unset and there is no sieve ground truth, so every real number is pixel-relative and none of them is a millimetre claim. Kuz-Ram, Swebrec and SAM are cited in the literature and explicitly not implemented, rather than name-dropped as if they were. [Live](https://fragmentiq.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_FragmentIQ).
