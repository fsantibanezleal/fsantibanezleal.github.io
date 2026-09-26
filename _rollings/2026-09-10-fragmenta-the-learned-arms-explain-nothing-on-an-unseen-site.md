---
title: 'Fragmenta: on a site it has never seen, not one learned arm explains any variance'
date: 2026-09-10
permalink: /rollings/2026/09/fragmenta-the-learned-arms-explain-nothing-on-an-unseen-site/
tags:
  - fragmenta
  - drill-and-blast
  - benchmarks
  - negative-result
---

Fragmenta: on a site it has never seen, not one learned arm explains any variance
======

![Fragmenta, twelve arms over sixteen cases under three splits; on an unseen site only the fixed-coefficient arms stay positive](/images/projects/fragmenta_pipeline.svg)

Fragmenta is live today with HTTPS enforced. It predicts the mean fragment size of a bench blast with twelve arms over sixteen cases, six classical closed forms (Kuznetsov, Kuz-Ram, Swebrec, the crush-zone model, two published regressions) and six learned (a Levenberg-Marquardt network, support-vector regression, random forest, gradient boosting, a stack and a refit), and it scores the same table three ways: a random split, the published hold-out, and leave-one-site-out.

Most learned fragmentation papers report the random split, where a model that memorises the site looks skilful. The question a mine planner needs answered is what a method knows about a site it has never seen.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Under leave-one-site-out, not one of the six learned arms explains any variance.</strong><br/>
The best, gradient boosting, scores -0.034 against a null model at -0.216: a 0.182 margin that is two models failing by different amounts, not skill. The only two arms that stay positive on an unseen site are the two whose coefficients are fixed rather than fitted, the published regression at 0.802 and Kuznetsov at 0.311.<br/>
<span style="color:#5a9ac0;font-size:13px;">The classical arm improves under the honest protocol, from negative on the random split, because it has nothing to overfit. The kill criterion, written before the run, requires both a positive score and a 0.10 margin; it was rewritten after an earlier version had declared success on two failures, and it fired.</span>
</div>

The science lives upstream in blastfrag, a separate repository consumed as a pinned dependency; the product declares no package of its own and a guard fails the build if one appears. The corpus is 97 published bench blasts, a 14-blast published hold-out and 5 open-access field blasts, reused as cited experimental facts; the source articles are copyrighted, stay in a private vault, and another guard fails the build if a PDF is ever tracked. Reproducibility is stated as measured: byte-identical within an environment, better than 3e-08 relative across operating systems, both gated in CI.

[Live](https://fragmenta.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_Fragmenta)
