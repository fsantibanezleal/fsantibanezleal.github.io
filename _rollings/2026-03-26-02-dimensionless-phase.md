---
title: 'Overflow at 10¹⁶ Radians'
date: 2026-03-26
permalink: /rollings/2026/03/Post-2026-03-26-02/
tags:
  - Optics
  - Holography
  - Numerical Methods
  - Phase Mask
---

Overflow at 10¹⁶ Radians
======

The [holographic optical tweezers](https://github.com/fsantibanezleal/CEFOP_DinHot) phase mask computation was producing garbage, and it took an embarrassingly long time to figure out why. The Gerchberg-Saxton algorithm itself was fine -- iterate between the SLM plane and the focal plane via FFT, impose the target intensity constraint, keep the phase, repeat. The problem was units.

![Dimensionless phase reformulation](/images/rollings/gs_phase_overflow.svg)

Using SI throughout -- wavelength lambda = 532 nm, focal length f = 0.2 m, pixel pitch Dp = 8 um -- the quadratic phase kernel produces values that explode:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Phase kernel (SI units):</strong><br/>
K_j(u,v) = (2π / λf) × Δp² × N × (u·x_j + v·y_j)  →  phase ≈ 10¹⁶ rad
</div>

At that scale, float64 quantization eats the phase information alive; `mod 2pi` returns essentially random values because the significand cannot represent the fractional part of a number that large.

The fix was to reformulate everything in dimensionless coordinates. Define a characteristic scale alpha that absorbs all the physical constants:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Dimensionless phase kernel:</strong><br/>
α = (2π / λf) · Δp² · N ≈ π<br/>
K_j = α(u·x_j + v·y_j) − β(u² + v²)·z_j, &nbsp; where α ≈ π
</div>

Suddenly the GS algorithm converges in about 50 iterations with clean intensity equalization across all trap positions.

The other key improvement was replacing the hard circular aperture at the SLM boundary with a **Super-Gaussian of order 8** -- `exp(-(r/R)^8)`. The hard edge was producing Gibbs-like ringing artifacts that showed up as ghost traps at high spatial frequencies. The Super-Gaussian rolls off smoothly enough to suppress the ringing while still using most of the SLM area.

Convergence criterion: 50 iterations, monitored via RMS intensity error between target and reconstructed trap pattern. Two fixes, both about respecting the numerics rather than trusting the algebra blindly. [Repository here](https://github.com/fsantibanezleal/CEFOP_DinHot).
