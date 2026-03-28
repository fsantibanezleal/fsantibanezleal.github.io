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

The [holographic optical tweezers](https://github.com/fsantibanezleal/CEFOP_DinHot) phase mask computation was producing garbage, and it took an embarrassingly long time to figure out why. The Gerchberg-Saxton algorithm itself was correct -- iterate between the SLM plane and the focal plane via FFT, impose the target intensity constraint, keep the phase, repeat. The problem was units. Using SI throughout -- wavelength λ = 532 × 10⁻⁹ m, focal length f = 0.2 m, pixel pitch ΔP = 8 × 10⁻⁶ m -- the quadratic phase term (2π/λf) × ΔP² × N² produces values on the order of 10¹⁶ radians before the mod 2π operation. At that scale, floating-point quantization eats the phase information alive; the mod operation returns essentially random values because the significand cannot represent the fractional part of a number that large. The fix was to reformulate everything in dimensionless coordinates where the characteristic phase scale comes out to roughly π. Define normalized pixel coordinates, express the lens phase as a simple quadratic in those coordinates, and suddenly the GS algorithm converges in about 50 iterations with clean intensity equalization across all trap positions. The other key improvement was replacing the hard circular aperture at the SLM boundary with a Super-Gaussian of order 8 -- exp(-(r/R)⁸). The hard edge was producing Gibbs-like ringing artifacts that showed up as ghost traps at high spatial frequencies. The Super-Gaussian rolls off smoothly enough to suppress the ringing while still using most of the SLM area. Two fixes, both about respecting the numerics rather than trusting the algebra blindly.
