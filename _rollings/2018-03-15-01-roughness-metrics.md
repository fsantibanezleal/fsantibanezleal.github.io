---
title: 'ISO 4287 on Mineral Surfaces'
date: 2018-03-15
permalink: /rollings/2018/03/roughness-metrics/
tags:
  - Surface Analysis
  - Roughness
  - ISO 4287
  - Granulometry
  - ALGES
---

ISO 4287 on mineral surfaces
======

Implemented the standard surface roughness metrics (ISO 4287) for the depth profiler. These are the same parameters used in precision manufacturing to characterize machined surfaces — now applied to mineral samples to quantify particle size and texture.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">ISO 4287 roughness parameters:</strong><br/>
Ra = (1/N) Σ |z<sub>i</sub> - z̄| — arithmetic mean deviation<br/>
Rq = √((1/N) Σ (z<sub>i</sub> - z̄)²) — root mean square roughness<br/>
Rz = max(peaks) - min(valleys) — maximum height<br/>
Rsk = (1/N·Rq³) Σ (z<sub>i</sub> - z̄)³ — skewness (asymmetry)<br/>
Rku = (1/N·Rq⁴) Σ (z<sub>i</sub> - z̄)⁴ — kurtosis (peakedness)
</div>

The interesting finding: Ra and Rq correlate well with the coarser size fractions from sieve analysis, but for fine particles the relationship breaks down because the depth camera resolution becomes a limiting factor. We need sub-millimeter depth accuracy for the finer fractions, and the current setup gives us about 0.5mm — fine for coarse characterization but not for complete granulometry replacement.

Also added cross-section profile extraction — draw a line on the depth map and get a 1D height profile with bilinear interpolation. This is surprisingly useful for identifying particle boundaries and measuring individual grain sizes.

The Gaussian curvature analysis K = (f_xx · f_yy - f_xy²) / (1+fx²+fy²)² helps identify flat regions (K≈0, bulk material), convex peaks (K>0, particle tops), and saddle points (K<0, particle boundaries). This topological classification could feed directly into an automated particle counter.

![3D Distance Profiler architecture](/images/projects/depth_profiler_arch.svg)

[3D Distance Profiler on GitHub](https://github.com/fsantibanezleal/FASL_3D_Distance_Profiler).
