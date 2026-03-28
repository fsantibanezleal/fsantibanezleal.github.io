---
title: 'Week in review: Vectorization, numerical stability, and biological accuracy'
date: 2026-03-27
permalink: /posts/2026/03/week-vectorization-stability/
tags:
  - open-source
  - vectorization
  - numerical-methods
  - week-in-review
---

Modernizing eight research codebases at once sounds like a terrible idea, and some weeks it feels like one. But working across optics, biophysics, robotics, and geostatistics in parallel has surfaced a pattern: the same three engineering challenges keep showing up in every domain, wearing different clothes.

Vectorization
======

The single biggest performance improvement across all projects has been replacing explicit Python loops with NumPy broadcasting and vectorized operations. The most dramatic example: in the [Cellular Potts Model](https://github.com/fsantibanezleal/SCIAN_LEO_CPM), the adhesion energy computation between all cell pairs used a triple-nested loop.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Adhesion energy (before):</strong><br/>
E_adh = Σ_i Σ_j Σ_neighbors J(σ_i, σ_j) · (1 − δ(σ_i, σ_j)) &nbsp; → &nbsp; O(n³)
</div>

Reshaping the interaction matrix and using broadcasting brought it down to a vectorized pairwise computation:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Adhesion energy (after):</strong><br/>
E_adh = J[σ_grid, σ_shifted] · mask &nbsp; → &nbsp; O(n²), vectorized
</div>

The constant factor shrank enough to handle hundreds of cells in real time. In the [SOFI pipeline](https://github.com/fsantibanezleal/FASL_SOFI_QDOTS), cumulant computation moved from frame-by-frame accumulation to windowed batch processing over the full time stack. The [optical tweezers](https://github.com/fsantibanezleal/CEFOP_DinHot) Gerchberg-Saxton algorithm now runs entirely as FFT-plus-array operations with no Python-level iteration inside the main loop. In every case, wall-clock time dropped by one to two orders of magnitude.

Numerical stability
======

Each domain brought its own flavor of "the math is right but the numbers are wrong."

![Phase overflow fix](/images/rollings/gs_phase_overflow.svg)

The optical tweezers had phase values overflowing at 10^16 radians because SI units produced a characteristic scale far beyond what float64 can resolve after a modulo operation. The fix was dimensionless reformulation:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Phase overflow fix:</strong><br/>
SI: K_j = (2π/λf) · Δp² · N · (u·x_j + v·y_j) → 10¹⁶ rad<br/>
Dimensionless: K_j = α(u·x_j + v·y_j), &nbsp; α ≈ π
</div>

The CPM collision resolver oscillated forever because naive repulsion and adhesion forces fought each other across time steps. The Darcy flow solver for well placement used a Jacobi iteration that diverged quietly when the permeability contrast exceeded 10³. In every case, the fix was not to change the physics but to change the numerical formulation -- dimensionless coordinates, relaxation sweeps, preconditioning. Stability is an engineering constraint, not a mathematical afterthought.

Biological accuracy
======

The most humbling part of working on biophysical simulations is that nature already ran the experiment.

![Collision resolution](/images/rollings/cpm_collision_passes.svg)

Contact Inhibition of Locomotion means cells repolarize away from collisions, not through them:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">CIL repolarization:</strong><br/>
polarity_new = normalize(polarity − 0.3 × contact_direction)
</div>

Hertwig's rule says cells divide along their longest axis -- implementing anything else produces tissue geometries that look wrong to any biologist in the room. The EVL elastic coupling in the [embryo simulator](https://github.com/fsantibanezleal/SCIAN_EVL_SpherSIM) must pull but never push, because that is what Oteiza and colleagues measured in 2015:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">EVL spring (pull-only):</strong><br/>
F_EVL = k₀ · exp(−d / 0.3) × max(0, θ_EVL − θ_cell)
</div>

These are not optional features or nice-to-haves. They are hard constraints from decades of experimental observation, and ignoring them produces simulations that converge beautifully to answers that are biologically meaningless.

All eight repositories now include test suites, documentation with SVG diagrams, and working web demonstrations where applicable. They are publicly available on GitHub -- not because the code is perfect, but because reproducibility matters more than polish.
