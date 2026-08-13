---
title: 'ProspectMap: most of the apparent skill was proximity'
date: 2026-08-05
permalink: /rollings/2026/08/prospectmap-most-of-the-skill-was-proximity/
tags:
  - mining
  - machine-learning
  - negative-results
  - honesty
---

ProspectMap: most of the apparent skill was proximity
======

![ProspectMap: six models on identical spatial-block folds over a real MVT belt, with the nulls beside them](/images/projects/prospectmap_app.png)

[ProspectMap](https://prospectmap.fasl-work.com) runs mineral prospectivity on a real belt: the US Midcontinent MVT zinc-lead belt from the public Lawley et al. 2022 compilation, 25,344 cells, four real measured geophysical layers and two derived proximity layers, with real-versus-derived provenance tracked per layer. Six models run on identical contiguous spatial-block folds with bootstrap confidence intervals.

The headline is the one I did not want:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">A trivial distance-to-known-deposit null scores AUC 0.783.</strong><br/>
That ties the best model on the board.<br/>
<span style="color:#5a9ac0;font-size:13px;">The modern PU-Conformal approach reaches <strong>0.656</strong> and does not beat 1989 Weights of Evidence at <strong>0.732</strong>. The app commits that as a verdict (<code>ranking_win: false</code>) instead of quietly reordering the table.</span>
</div>

Two controls make that reading trustworthy rather than merely modest. A **label permutation** sends Weights of Evidence to 0.506 and PU to 0.490, so a pure noise layer earns no lift and the pipeline is not manufacturing skill. And the **conformal coverage** is reported with its cost: 0.977 against a nominal 0.90, achieved only by flagging 88 percent of the belt, which is a coverage number that means very little on its own and is presented that way.

Most of the apparent skill in this problem is spatial proximity to what has already been found. That is worth knowing before anyone spends a drilling budget on a heat map. Not a JORC or NI 43-101 resource estimate. [Live](https://prospectmap.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_ProspectMap).
