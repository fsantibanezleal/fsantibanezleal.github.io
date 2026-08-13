---
title: 'PhaseFlow: a schedule is only as good as the bound you can check it against'
date: 2026-08-10
permalink: /rollings/2026/08/phaseflow-a-bound-you-can-check/
tags:
  - mining-optimization
  - mine-planning
  - optimization
  - honesty
---

PhaseFlow: a schedule is only as good as the bound you can check it against
======

![PhaseFlow: a year-coloured pit with NPV, bound, gap and spatial-coherence readouts](/images/projects/phaseflow_app.png)

[PhaseFlow](https://phaseflow.fasl-work.com) schedules an open pit period by period: which blocks come out in which year, under slope precedence in every period and the mining and processing capacity of each one, maximising discounted NPV. The problem is NP-hard, so nobody solves it to proven optimality at real size, and that is exactly why the number on its own is worth little.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Anchored to a published instance, solved as published.</strong><br/>
MineLib <code>newman1.cpit</code>, on its own six periods, its own 8% rate and its own two capacities.<br/>
<span style="color:#5a9ac0;font-size:13px;">Ultimate pit optimum <strong>26,086,899</strong>, an exact match. Joint LP bound <strong>24,486,184</strong> against a published 24,486,549. Optimality gap <strong>2.49%</strong> against a published 1.26%, stated rather than smoothed over.</span>
</div>

Two things make that bound useful rather than decorative. It is **checkable by ordering**: a CPIT LP bound must sit below a PCPSP LP bound because PCPSP is the richer problem, and it does, by 365 units in 24.5 million. And it is **cheap**: the critical multiplier algorithm gives the CPIT LP relaxation exactly in `O(mn log n)` as parametric maximum closures, with no LP solver at all, which is why a TypeScript port re-solves the whole problem live in the browser and a parity test asserts it reproduces the Python bound.

The part I would keep if I could keep only one: **two bounds run on every case** and the app reports the difference. A certified-but-loose bound relaxes the resources one at a time; the joint Bienstock-Zuckerberg bound does not. The gap between them is the part of a reported optimality gap that belongs to the *bound* rather than to the *plan*, and without it you cannot tell a weak schedule from slack in the mathematics you measured it with. On a single-resource instance the two agree to machine precision, which is the strongest correctness check in the repository.

Honest scope, in the product: no stockpiles, no blending, no minimum-production constraints, and not for production mine planning. Engine is the separately published [`oreblocks`](https://pypi.org/project/oreblocks/). [Live](https://phaseflow.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_PhaseFlow).
