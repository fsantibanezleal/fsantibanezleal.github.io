---
title: 'Conectoma: what the biology adds over a random graph, it does not add over a rewiring that keeps the degrees'
date: 2026-09-22
permalink: /rollings/2026/09/conectoma-what-the-biology-adds-and-does-not/
tags:
  - conectoma
  - neuroscience
  - computer-vision
  - null-controls
---

Conectoma: what the biology adds over a random graph, it does not add over a rewiring that keeps the degrees
======

![Conectoma, the MaleCNS wiring compiled and frozen, three regimes, video cases, and every result an effect size against three nulls](/images/projects/conectoma_pipeline.svg)

Conectoma went live today at its own domain, and the unit that shipped with it is the one the product exists for: the connectome used as a reservoir with a trained readout, against three null controls built from the same wiring with the same head and five seeds each. The Janelia MaleCNS v1.0 wiring of the male fruit fly, 166,691 neurons and 11,691 cell types, is compiled in memory by a compiler identical to flyvis's and frozen; synapse counts and signs are measurements and never move. The task is dense prediction the wiring did not evolve for in this form: depth from a moving camera and figure-ground segmentation, on video, because flies judge distance from motion parallax.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Paired per clip on the cases.</strong><br/>
+0.197 [+0.173, +0.214] against a size-matched random sparse graph. +0.136 [+0.121, +0.168] against a sign shuffle. -0.017 [-0.021, -0.008] against a degree-preserving rewiring.<br/>
<span style="color:#5a9ac0;font-size:13px;">The third number is the honest one. What the biology adds over a random graph of the same size and the same signs, it does not add over a rewiring that keeps every cell's degree. "The connectome helps" is a slogan until the nulls are built from the same wiring; with them it is a falsifiable claim, and this one is partly false.</span>
</div>

The activity is cached once per clip (0.13 s, 82 KB) so twenty heads train in half an hour. Building the compiler exposed six defects, the largest two inherited from the first unit: the placement rule collapsed tiling populations and dropped 3,270 connections, and the release's column frame was a half-turn of the engine's, so T4a would have read as T4b. The whole visual system runs neuron by neuron, 105,011 neurons and 12.45 million connections, as one recurrent component whose loop gain of 3.07 has to be bounded before it is stable.

Live is not validated: the plan was proposed and not validated, so the lifecycle reads planned. The fit gate ran against the HTTPS URL, 1,183 checks, every route with and without the trailing slash, all sixteen clips verified against their manifests. A certificate sat unissued for four days with correct DNS and was issued in seconds by unsetting and re-setting the custom domain through the Pages API; re-applying the same value did nothing, which is now written down.

[Live](https://conectoma.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_RES_Conectoma)
