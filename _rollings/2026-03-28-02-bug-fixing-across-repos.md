---
title: 'Eight Repos, One Night'
date: 2026-03-28
permalink: /rollings/2026/03/bug-fixing-across-repos/
tags:
  - Bug Fixing
  - Open Source
  - Testing
---

Fixing bugs in 8 repos simultaneously is like being a doctor treating 8 patients with different conditions but the same underlying immune system. They all share the same architectural spine — FastAPI + WebSocket + NumPy — but each one lives in a completely different scientific domain. The haptic simulator speaks in triangles and force vectors. The optical tweezers think in Fourier transforms and phase masks. The well placement optimizer dreams of Darcy flow and permeability fields. And yet, a bug in one teaches you something about all the others.

Tonight was one of those nights. It started with a collision detection bug in the Cellular Potts Model — the contour extent was being compared against the base_radius when it should have been compared against the actual cell boundary. A subtle difference that only shows up when cells elongate during division. Speaking of division, Hertwig's rule for choosing the division axis had a sign error that made cells divide perpendicular to their longest axis instead of along it. Biology reversed.

![Cell model with Gaussian filopodia](/images/rollings/cpm_cell_model.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Hamiltonian energy:</strong><br/>
H = &lambda;<sub>A</sub>(A &minus; A<sub>target</sub>)&sup2; + &lambda;<sub>P</sub>(P &minus; P<sub>target</sub>)&sup2;<br/>
&lambda;<sub>A</sub> = 0.1, &lambda;<sub>P</sub> = 0.05
</div>

The contour extent bug reminded me of the octree bounding box logic in the haptic simulator — same class of error, different geometry. You define a spatial boundary, but when the object deforms or moves, the boundary does not update correctly. In the CPM it was a growing cell; in the haptic sim it was a stylus moving near the edge of a subdivided region. Same mistake, different universe.

And then, while fixing a numerical stability issue in the optical tweezers intensity normalization, I realized the Darcy solver in the well placement code had a nearly identical problem — dividing by a sum that could be zero when all weights collapsed. Two domains, two solvers, one floating-point trap.

The shared patterns make it possible to carry fixes across. The different domains make it interesting. Eight repos, one night, and a lot of coffee.
