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

Vectorization everywhere
======

The single biggest performance improvement across all projects has been replacing explicit Python loops with NumPy broadcasting and vectorized operations. In the [Cellular Potts Model](https://github.com/fsantibanezleal/SCIAN_LEO_CPM), the adhesion energy computation between all cell pairs used a triple-nested loop -- O(n³) in the number of cells. Reshaping the interaction matrix and using broadcasting brought it down to O(n²) with a constant factor small enough to handle hundreds of cells in real time. In the [SOFI pipeline](https://github.com/fsantibanezleal/FASL_SOFI_QDOTS), cumulant computation moved from frame-by-frame accumulation to windowed batch processing over the full time stack. The [optical tweezers](https://github.com/fsantibanezleal/CEFOP_DinHot) Gerchberg-Saxton algorithm now runs entirely as FFT-plus-array operations with no Python-level iteration inside the main loop. In every case, the algorithmic complexity stayed the same or improved, but the wall-clock time dropped by one to two orders of magnitude simply by letting NumPy do what it was designed to do.

Numerical stability is never free
======

Each domain brought its own flavor of "the math is right but the numbers are wrong." The optical tweezers had phase values overflowing at 10¹⁶ radians because SI units produced a characteristic scale far beyond what float64 can resolve after a modulo operation. The CPM collision resolver oscillated forever because naive repulsion and adhesion forces fought each other across time steps. The Darcy flow solver for well placement used a Jacobi iteration that diverged quietly when the permeability contrast exceeded 10³. In every case, the fix was not to change the physics but to change the numerical formulation -- dimensionless coordinates, relaxation sweeps, preconditioning. Stability is an engineering constraint, not a mathematical afterthought.

Biology sets the rules
======

The most humbling part of working on biophysical simulations is that nature already ran the experiment. Hertwig's rule says cells divide along their longest axis -- implementing anything else produces tissue geometries that look wrong to any biologist in the room. Contact Inhibition of Locomotion means cells repolarize away from collisions, not through them. The EVL elastic coupling in the embryo simulator must pull but never push, because that is what Oteiza and colleagues measured in 2015. These are not optional features or nice-to-haves. They are hard constraints from decades of experimental observation, and ignoring them produces simulations that converge beautifully to answers that are biologically meaningless.

All eight repositories now include test suites, documentation with SVG diagrams, and working web demonstrations where applicable. They are publicly available on GitHub -- not because the code is perfect, but because reproducibility matters more than polish.
