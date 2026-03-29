---
title: 'Counting Grains from Depth'
date: 2018-07-10
permalink: /rollings/2018/07/grain-size-watershed/
tags:
  - Granulometry
  - Watershed
  - Depth Profiling
  - ALGES
  - Mineral Processing
---

Counting grains from depth
======

The depth profiler gives us surface height maps. The HSI system tells us mineral composition. But the question from the processing engineers was always the same: "How big are the particles?"

Today we got the watershed segmentation working on the depth gradient images. The idea is elegant: each grain creates a local maximum in the depth map (the top of the grain is the highest point). These maxima become markers for the watershed algorithm, which then "floods" from each marker outward until it meets the flood from a neighboring grain — and that boundary becomes the grain edge.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Equivalent diameter:</strong><br/>
d<sub>eq</sub> = √(4A/π)<br/>
<span style="color:#5a9ac0;font-size:13px;">where A is the pixel area of the segmented grain — the diameter of a circle with the same area</span>
</div>

The tricky part is the gradient threshold for finding markers. Too sensitive and you get over-segmentation — every surface bump becomes a "grain." Too conservative and adjacent grains merge into one blob. We spent the afternoon tuning this with real mineral samples from the lab, comparing our segmented grain count against manual counts on the same image.

Once you have individual grains, the metrics cascade: equivalent diameter, major/minor axis from PCA, circularity, aspect ratio, depth-integrated volume. Then aggregate into a Rosin-Rammler PSD curve with D-values.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Rosin-Rammler PSD:</strong><br/>
R(d) = 100 × exp(-(d/d')ⁿ)<br/>
<span style="color:#5a9ac0;font-size:13px;">d' ≈ D63.2 (characteristic size), n = uniformity index (higher = narrower distribution)</span>
</div>

The three systems now work together: HSI tells us what the mineral is, the depth profiler tells us its surface shape, and the grain sizer tells us the particle size distribution. For the processing engineers, this is the complete picture — composition, texture, and size in one non-destructive measurement pass.

![Granulometry pipeline](/images/projects/grainsize_pipeline.svg)

[GrainSight on GitHub](https://github.com/fsantibanezleal/FASL_3D_GrainSize).
