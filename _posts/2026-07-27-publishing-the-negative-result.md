---
title: 'Publishing the negative result'
date: 2026-07-27
published: true
permalink: /posts/2026/07/publishing-the-negative-result/
tags:
  - honesty
  - benchmarks
  - machine-learning
  - engineering
---

Publishing the negative result
======


Every tool I ship has a benchmark page. It is one of the fixed pages in the app, the same slot in every product, and it has one job that the rest of the app does not: to be the place where the tool is allowed to lose. Over the last stretch of building I have come to think of that page as the most important one, and I want to write down why, using the actual results that live on those pages.

The temptation a benchmark page resists is the single flattering number. It is easy to pick the metric, the split and the baseline that make a method look good, put it on the front, and never build the page that would contradict it. A benchmark page built honestly does the opposite: it runs the fashionable method and the boring one on the same footing, on the same data, and commits whichever verdict comes out. In practice that has meant the fashionable method losing more often than I expected, and the page saying so.

The concrete cases are the argument.

In [TailWatch](https://tailwatch.fasl-work.com), an InSAR ground-deformation studio, I trained an anomaly autoencoder to flag accelerating slopes. On the held-out benchmark the classical velocity map scores AUC 0.968 and the learned autoencoder scores 0.898. The learned model is the loser, and that is the number on the page.

In [DispatchLab](https://dispatchlab.fasl-work.com), a truck-shovel dispatch bench, the policy I most wanted to work was a Monte-Carlo rollout under cycle-time uncertainty. It wins 0 of 8 random seeds against a simpler assignment. A published null, not a quiet omission.

In [PitForge](https://pitforge.fasl-work.com), the exact core (a min-cut solving the ultimate pit limit to within 2e-9 of three published MineLib optima) is the star, and the grade neural net ties ordinary kriging (0.9613 vs 0.958) and never beats it.

In [ProspectMap](https://prospectmap.fasl-work.com), on a real mineral belt, a trivial distance-to-deposit baseline (0.783) ties the best model. Most of the apparent skill is spatial proximity, and the app commits that as a verdict rather than hiding it.

In [CardioPINN](https://cardiopinn.fasl-work.com), the physics-informed reconstruction sits at parity with a 1970s Tikhonov baseline on point accuracy, on all four ECGi beats, and the benchmark page states it. The lesson there was about my own scorecard: replacing classical accuracy was never the goal, so parity is not a defeat. The method earns its place with the outputs the baseline cannot give, a calibrated per-node uncertainty (2-sigma coverage 0.89-0.90) and a resolved relative-pressure field, and the page states that positioning too.

Even [ChronoScope](https://chronoscope.fasl-work.com), a forecasting atlas where a foundation model does earn its place on some series, keeps the case where a one-line SeasonalNaive beats a foundation model on real data.

Six tools, six places where the method I was most excited about lost to the plain one. None of these is self-deprecation, and none of them makes the tools worse. Each has a real, exact or classical core doing the work; the learned layer sits on top and is measured against it in public, including when it trails. What the discipline buys is trust that survives contact. Someone who finds the one page where the tool is honest about its own failure has a reason to believe the numbers on all the others. A tool with no such page is asking to be taken on faith.

There is a version of this work that reports only the wins and never builds the page that could embarrass it. It looks more impressive and it is worth less. I would rather have the benchmark page that lets the boring method win when it deserves to, because a result I can stand behind when it goes against me is the only kind that is actually mine.
