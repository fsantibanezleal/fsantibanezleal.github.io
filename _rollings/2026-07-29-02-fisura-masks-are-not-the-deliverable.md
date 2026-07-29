---
title: 'Materials-damage vision: the mask is never the deliverable'
date: 2026-07-29 20:00:00
permalink: /rollings/2026/07/fisura-masks-are-not-the-deliverable/
tags:
  - computer-vision
  - crack-detection
  - measurement
  - honesty
---

Materials-damage vision: the mask is never the deliverable
======

![Fisura: a classical-to-foundation method ladder, then measurement turns masks into engineering numbers](/images/projects/fisura_app.png)

[Fisura](https://fisura.fasl-work.com) is a lab on seeing damage in built materials: one image of a concrete wall, a pavement or a facade goes in, and it detects cracks, spalling and surface defects. The thing I care about is what comes after the segmentation. Computer-vision papers stop at a mask and a benchmark score; an inspector needs a number in millimetres, with a stated method.

So masks are only ever the input to measurement: pixel-to-mm calibrated crack width and length, orientation, density, growth between inspection epochs, and vision-based deformation via 2D digital image correlation. And the method families are compared honestly on the same open cases with the same metrics.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The whole ladder, one ruler:</strong><br/>
classical pipelines (ridge filters, morphology, skeleton geometry) · learned SOTA segmentation · promptable foundation models · unsupervised anomaly detection<br/>
<span style="color:#5a9ac0;font-size:13px;">Accuracy and measurement reported separately. A method-comparison lab, not a certified inspection tool.</span>
</div>

It runs an offline heavy lane plus a browser live lane where the photo never leaves the device, and it is dataset-honest: the full open datasets live outside the repo. It is under active build-out, one vertical slice at a time, and the app says so. [Live](https://fisura.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_RES_Fisura).
