---
title: 'Adding the Third Dimension'
date: 2017-10-20
permalink: /rollings/2017/10/depth-cameras/
tags:
  - Depth Profiling
  - ALGES
  - Granulometry
  - 3D Reconstruction
---

Adding the third dimension
======

We've been capturing hyperspectral images of mineral samples for months now — VNIR and SWIR cameras giving us spectral information across hundreds of wavelengths. But spectral data alone doesn't tell you everything about a mineral sample. Particle size matters. Surface texture matters. And those are fundamentally 3D properties that a flat spectral image can't capture.

Today we started integrating depth cameras into the acquisition setup. The idea: capture depth maps alongside the spectral images, co-register them, and have both the "what it is" (spectral composition) and the "how it looks" (particle size, roughness) in a single dataset.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The granulometry connection:</strong><br/>
Sieve analysis takes hours and destroys the sample. Surface profiling from depth images takes minutes and the sample survives intact for spectral analysis. If we can correlate depth-derived roughness metrics with sieve-derived particle size distributions, we have a non-destructive, fast alternative.
</div>

The first challenge is the bilateral filter — standard smoothing destroys edges between particles, but bilateral filtering preserves them by weighting based on both spatial proximity and depth similarity. Getting the kernel parameters right for mineral samples (which have much sharper depth transitions than human faces, where this filter was originally designed) took most of the afternoon.

![Depth profiler processing pipeline](/images/projects/depth_profiler_pipeline.svg)

[3D Distance Profiler on GitHub](https://github.com/fsantibanezleal/FASL_3D_Distance_Profiler).
