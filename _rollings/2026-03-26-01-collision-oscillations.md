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

The [Cellular Potts Model simulator](https://github.com/fsantibanezleal/SCIAN_LEO_CPM) had a maddening oscillation problem during collision resolution. When two cells overlap, the naive approach applies a repulsive force proportional to the overlap area to push them apart. But if that repulsion overshoots -- and it always does when the time step is not infinitesimally small -- the cells end up too far apart, and in the next step the adhesion energy gradient pulls them right back into overlap. The result is two cells bouncing against each other forever, never settling, burning CPU cycles on a biological impossibility. The fix was a two-pass Gauss-Seidel-like sweep inspired by constraint solvers in game physics. The forward pass applies soft repulsion with a relaxation factor of 1.0, resolving the worst overlaps first. The backward pass then sweeps in reverse order with a factor of 0.0, ensuring that the corrections from the first pass did not introduce new overlaps with neighbors that were already processed. Convergence typically happens in 2-3 iterations instead of the hundreds the old method needed. On top of that, I implemented Contact Inhibition of Locomotion -- when two cells collide, each one repolarizes its migration direction away from the contact normal by about 30%, mimicking the biological response where cells retract their protrusions upon touching a neighbor. This is not just a numerical trick; CIL is a well-documented phenomenon in neural crest cells and many epithelial tissues. The combination of stable collision resolution and CIL produces migration patterns that finally look biologically plausible.

![Cell model](/images/projects/cpm_simulator.svg)
