---
title: "GrainSight — Particle Size Distribution from RGB-D Data"
date: 2018-06-01
excerpt: "3D granulometry analyzer using marker-based watershed segmentation, per-grain geometric measurement, and Rosin-Rammler PSD fitting from depth camera data.<br/><img src='/images/projects/grainsize_pipeline.svg'>"
collection: portfolio
tags: [granulometry, particle-size, watershed, depth-profiling, rosin-rammler, fastapi, python]
---

A **3D particle size and granulometry analyzer** that estimates grain size distributions from RGB-D (depth) data. Developed during 2018 at ALGES as the third component of a mineral characterization trio: spectral composition (HSI), surface geometry (Depth Profiler), and now particle size (GrainSight).

## Business context

Particle size distribution (PSD) is one of the most critical parameters in mineral processing. It directly affects grinding energy consumption, flotation recovery, and leaching kinetics. Traditional PSD measurement requires physical sieve analysis — a destructive, time-consuming laboratory procedure that provides only batch-level averages.

## Key Performance Indicators — Process impact

GrainSight replaces physical sieve analysis with non-destructive image-based measurement, enabling continuous monitoring that was previously impossible.

| KPI | Baseline (sieve analysis) | With GrainSight | Impact |
|-----|--------------------------|-----------------|--------|
| Measurement method | Destructive sieve stacking | Non-destructive depth imaging | Sample preserved for further analysis |
| Turnaround | Hours per sample (manual sieving) | Minutes (image capture + processing) | Near real-time PSD feedback |
| Spatial resolution | Bulk average per sieve fraction | Per-grain measurement (18 metrics each) | Spatially resolved size maps |
| D-value extraction | Manual interpolation from sieve data | Automatic D10/D25/D50/D75/D80/D90 | Consistent, repeatable analysis |
| Integration | Standalone lab procedure | Co-registered with HSI + depth data | Joint composition-size characterization |

## The characterization trio

This project completes a three-system pipeline for comprehensive mineral sample characterization:

1. **[HSI Mineral Classification](/portfolio/HSIMineralClassification/)** — *what it is* (spectral composition, mineral abundances)
2. **[3D Distance Profiler](/portfolio/DepthProfiler/)** — *how it looks* (surface depth maps, roughness, curvature)
3. **GrainSight** — *how big it is* (particle size distribution, grain shapes)

Together, these three systems provide the data needed for **geometallurgical models** that predict processing behavior from ore properties.

![Granulometry analysis pipeline](/images/projects/grainsize_pipeline.svg)

## How it works

### 1. Grain segmentation
Marker-based **watershed segmentation** on the depth gradient magnitude image. Local maxima in the depth map identify grain peaks (markers), and the watershed algorithm floods from these markers to delineate grain boundaries. Small fragments are merged based on area thresholds.

### 2. Per-grain measurement
18 geometric properties extracted per segmented grain:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Per-grain metrics:</strong><br/>
d<sub>eq</sub> = √(4A/π) — equivalent diameter from pixel area<br/>
AR = d<sub>major</sub> / d<sub>minor</sub> — aspect ratio from PCA axes<br/>
C = 4πA / P² — circularity (1.0 = perfect circle)<br/>
V = Σ (z<sub>i</sub> - z<sub>base</sub>) × Δx × Δy — depth-integrated volume above base plane
</div>

### 3. PSD analysis and Rosin-Rammler fitting

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Rosin-Rammler distribution:</strong><br/>
R(d) = 100 × exp(-(d/d')ⁿ)<br/>
<span style="color:#5a9ac0;font-size:13px;">d' = characteristic size (63.2% passing), n = uniformity index<br/>
Fitted by least-squares on log-log transformed cumulative data</span>
</div>

D-values (D10, D25, D50, D75, D80, D90) are extracted from the cumulative PSD curve, and a sieve simulation matches the ISO 565 standard series.

![PSD cumulative curve with D-values](/images/projects/grainsize_psd.svg)

## Technical stack

- **Backend**: Python/FastAPI with scikit-image for watershed segmentation, NumPy/SciPy for PSD analysis
- **Frontend**: HTML5 Canvas with dark theme, real-time PSD chart, grain measurement table
- **Calibration**: Pixel-to-mm conversion via reference object or direct pixel size
- **Export**: CSV with 18 metrics per grain, PSD summary with D-values
- **Standards**: ISO 565 (sieve series), ISO 13322-1 (image-based particle sizing)

[View on GitHub](https://github.com/fsantibanezleal/FASL_3D_GrainSize)
