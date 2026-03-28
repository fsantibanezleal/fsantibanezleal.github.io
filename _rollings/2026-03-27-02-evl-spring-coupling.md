---
title: 'Cells on a Sphere'
date: 2026-03-27
permalink: /rollings/2026/03/Post-2026-03-27-02/
tags:
  - Biophysics
  - Embryo
  - Simulation
  - Morphogenesis
---

Cells on a Sphere
======

The EVL elastic coupling implementation for [SpherSIM](https://github.com/fsantibanezleal/SCIAN_EVL_SpherSIM) is finally producing biologically plausible migration patterns on the spherical embryo surface. The basic mechanics: DFC (dorsal forerunner) cells are attached to the EVL (enveloping layer) margin via spring-like forces, F_EVL = k × (θ_EVL - θ_cell), that activate when a cell sits above the margin latitude. The coupling strength decays exponentially with distance from the margin as e^(-d/0.3), so leader cells right at the EVL edge feel a strong pull while follower cells further back are mostly governed by cell-cell interactions and noise. The critical biological insight from Oteiza et al. (2015) is that this coupling must be asymmetric -- it pulls cells toward the vegetal pole when they lag behind the margin, but it never pushes them ahead of it. Getting the sign convention right in spherical coordinates was trickier than expected; a naive implementation kept pushing cells past the margin because the angular difference flipped sign at the boundary. Stochastic cell division runs at about 0.5% probability per cell per time step, with daughter cells splitting along the axis perpendicular to the local azimuthal direction at 85% of the parent cell size. The spherical coordinate system uses an AER (azimuth-elevation-radius) convention with pole wrapping -- cells that migrate past the south pole reappear at the correct azimuth on the other side rather than accumulating at a singularity. That wrapping logic alone took two full afternoons to get right, mostly because of edge cases where cells near the pole have azimuthal coordinates that are essentially undefined. The migration now looks like the real thing: a coherent cluster of DFC cells tracking the EVL margin as it advances vegetally, maintaining cohesion through adhesion while being shepherded by the elastic tether from above.
