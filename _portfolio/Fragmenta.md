---
title: "Fragmenta, Blast Fragmentation Prediction Where the Learned Arms Explain Nothing on an Unseen Site"
date: 2026-09-10
excerpt: "Twelve arms predict the mean fragment size of a bench blast over sixteen cases from published corpora, scored under three split protocols. Under leave-one-site-out not one of the six learned arms explains any variance (best -0.034 against a null at -0.216); the only two arms positive on a site never seen are the two with fixed coefficients, the published regression at 0.802 and Kuznetsov at 0.311. Engine: the separately published blastfrag package.<br/><img src='/images/projects/fragmenta_pipeline.svg'>"
collection: portfolio
tags: [drill-and-blast, fragmentation, kuz-ram, machine-learning, negative-result, mining, faena]
---

Most learned fragmentation papers report a random split of blasts from the same site, where a model that memorises the site looks skilful. The question a mine planner needs answered is what a method knows about a site it has never seen. **Fragmenta** answers it with the same table scored three ways and a kill criterion written down before the run.

![Fragmenta, twelve arms over sixteen cases under three splits; on an unseen site only the fixed-coefficient arms stay positive](/images/projects/fragmenta_pipeline.svg)

## Twelve arms, three splits

Sixteen cases from 97 published bench blasts, a 14-blast published hold-out and 5 open-access field blasts. Six classical closed forms (Kuznetsov, Kuz-Ram, Swebrec, crush-zone, two published regressions) and six learned arms (a Levenberg-Marquardt network, support-vector regression, random forest, gradient boosting, a stack, a refit) appear on every case with a number or a refusal that names the missing input. Random, published hold-out, and leave-one-site-out.

## The result the product exists to report

![Fragmenta, the App on the Murgul copper mine case: predicted against measured, and every model scored on this case](/images/projects/fragmenta_app_dark.png)

Under leave-one-site-out, not one of the six learned arms explains any variance: the best, gradient boosting, scores -0.034 against a null model at -0.216, a margin between two failures rather than skill. The published regression at 0.802 and Kuznetsov at 0.311 are the only arms positive on an unseen site, and the classical arm improves under the honest protocol because it has nothing to overfit. The kill criterion requires both a positive score and a 0.10 margin; it was rewritten after an earlier version had declared success on two failures, and it fired.

## Engine, guards, boundary

The science lives upstream in **blastfrag**, published on PyPI from its own repository and consumed as a pinned dependency; the product declares no package of its own and a guard fails the build if one appears. The copyrighted source articles stay in a private vault and a guard fails on a tracked PDF. Reproducibility is stated as measured: byte-identical within an environment, better than 3e-08 relative across operating systems, both gated in CI. Deployed is a fact; at-bar is my call to make, and the lifecycle stays building.

[Live](https://fragmenta.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_Fragmenta) · [blastfrag on PyPI](https://pypi.org/project/blastfrag/)
