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

The EVL elastic coupling implementation for [SpherSIM](https://github.com/fsantibanezleal/SCIAN_EVL_SpherSIM) is finally producing biologically plausible migration patterns on the spherical embryo surface. The basic mechanics: DFC cells are tethered to the EVL margin via spring-like forces that activate when a cell sits above the margin latitude.

![EVL spring coupling](/images/rollings/evl_spring_coupling.svg)

The coupling force is angular and decays exponentially with distance from the margin:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">EVL spring force with exponential decay:</strong><br/>
F_EVL = k × (θ_EVL − θ_cell)<br/>
k(d) = k₀ · exp(−d / 0.3)
</div>

Leader cells right at the EVL edge feel a strong pull while follower cells further back are mostly governed by cell-cell interactions and noise.

The critical biological insight from **Oteiza et al. (2015)** is that this coupling must be **asymmetric** -- it pulls cells toward the vegetal pole when they lag behind the margin, but it never pushes them ahead of it. This is a pull-only constraint. Getting the sign convention right in spherical coordinates was trickier than expected; a naive implementation kept pushing cells past the margin because the angular difference flipped sign at the boundary.

Stochastic cell division runs at about **0.5% probability per cell per time step**, with daughter cells splitting along the axis perpendicular to the local azimuthal direction at **85% of the parent cell size**. This produces realistic tissue growth without requiring explicit cell-cycle modeling.

The spherical coordinate system uses an **AER (azimuth-elevation-radius) convention** with pole wrapping -- cells that migrate past the south pole reappear at the correct azimuth on the other side rather than accumulating at a singularity. That wrapping logic alone took two full afternoons to get right, mostly because cells near the pole have azimuthal coordinates that are essentially undefined.

The migration now looks like the real thing: a coherent cluster of DFC cells tracking the EVL margin as it advances vegetally. [Repository here](https://github.com/fsantibanezleal/SCIAN_EVL_SpherSIM).
