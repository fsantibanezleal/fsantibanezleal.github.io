---
title: 'A negative result on every tile'
date: 2026-07-15
published: false
permalink: /posts/2026/07/a-negative-result-on-every-tile/
tags:
  - mining
  - analytics
  - honesty
  - machine-learning
---

A negative result on every tile
======

> Draft. The facts and numbers here are verified against the code; the voice is a first pass for me to rewrite before publishing.

Over the last stretch the [Faena](https://faena.fasl-work.com) hub went from three live mining tools to eleven. Writing that sentence, the easy move is to talk about coverage: exploration, drill and blast, load and haul, comminution, geotechnics, economics. The more useful thing to say is about a rule I gave myself while building them, and what it changed.

The rule is that each tool has to be honest about where its learned model does not help. Not in a footnote. On the tile, in the benchmark, where a user looking for a reason to trust the tool would land.

In practice that turned into a negative result per tool, and they are more interesting than the wins:

- In [TailWatch](https://tailwatch.fasl-work.com), an InSAR ground-deformation studio, I trained an anomaly autoencoder to flag accelerating slopes. On the held-out benchmark the classical velocity map (AUC 0.968) beats it (0.898). The learned model is the loser, and the page says so.
- In [DispatchLab](https://dispatchlab.fasl-work.com), a truck-shovel dispatch bench, the policy I most wanted to work was a distilled Monte-Carlo rollout under cycle-time uncertainty. It wins 0 of 8 random seeds against a simpler assignment. That is a published null, not a hidden one.
- In [PitForge](https://pitforge.fasl-work.com), the exact optimizer (a min-cut solving the ultimate pit limit to within 2e-9 of three published MineLib optima) is the star; the grade neural net ties ordinary kriging (0.9613 vs 0.958) and never beats it.
- In [ProspectMap](https://prospectmap.fasl-work.com), on a real mineral belt, a trivial distance-to-deposit null (0.783) ties the best model. Most of the apparent skill is spatial proximity, and the app commits that verdict as `ranking_win: false`.
- Even [ChronoScope](https://chronoscope.fasl-work.com), a forecasting atlas, keeps a case where a one-line SeasonalNaive beats a foundation model on real data.

None of this is self-deprecation. Each tool has a real, exact or classical core doing the work, and the learned layer is measured against it in public. What the rule bought me is trust that survives contact: an operator who finds the one place the tool is honest about its own failure has a reason to believe the rest. A single flattering accuracy number buys the opposite, and it is the number most tools show.

There is a version of a portfolio that is a list of things that worked. This is the other kind: a list of things I measured, including when the fashionable method lost to the boring one. I think it is the more valuable list to have built.
