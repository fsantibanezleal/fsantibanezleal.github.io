---
title: 'When Cells Bounce Forever'
date: 2026-03-26
permalink: /rollings/2026/03/Post-2026-03-26-01/
tags:
  - CPM
  - Simulation
  - Numerical Stability
  - Collision
---

When Cells Bounce Forever
======

The [Cellular Potts Model simulator](https://github.com/fsantibanezleal/SCIAN_LEO_CPM) had a maddening oscillation problem: two cells bouncing against each other forever, never settling, burning CPU cycles on a biological impossibility. When cells overlap, the naive approach is straightforward -- compute the overlap, push them apart. But that push always overshoots.

![Two-pass collision resolution](/images/rollings/cpm_collision_passes.svg)

The naive repulsive correction is proportional to the overlap, but if it overshoots even slightly, the adhesion gradient pulls the cells right back into overlap on the next step. Classic numerical ping-pong:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Overlap correction:</strong><br/>
overlap = (r_a + r_b) − dist(a, b)<br/>
push = overlap × (1 − 0.5 × factor)
</div>

The fix was a two-pass Gauss-Seidel-like sweep inspired by constraint solvers in game physics. The **forward pass** applies soft repulsion with `factor = 1.0`, resolving the worst overlaps first while allowing some residual. The **backward pass** then sweeps in reverse order with `factor = 0.0` (full correction), ensuring that the first pass did not introduce new overlaps with already-processed neighbors. Convergence typically happens in 2-3 iterations instead of the hundreds the old method needed.

On top of that, I implemented Contact Inhibition of Locomotion. When two cells collide, each one repolarizes its migration direction away from the contact normal:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">CIL repolarization:</strong><br/>
polarity_new = normalize(polarity − 0.3 × contact_direction)
</div>

This is not just a numerical trick; CIL is a well-documented phenomenon in neural crest cells and many epithelial tissues. The combination of stable collision resolution and CIL produces migration patterns that finally look biologically plausible. [Repository here](https://github.com/fsantibanezleal/SCIAN_LEO_CPM).
