---
title: "3D Distance Profiler — Depth Maps for Granulometry"
date: 2017-08-01
excerpt: "RGB-D depth profiling for mineral sample surface characterization — enabling granulometry detection from 3D surface reconstruction, curvature analysis, and ISO 4287 roughness metrics.<br/><img src='/images/projects/depth_profiler_pipeline.svg'>"
collection: portfolio
tags: [depth-profiling, 3d-reconstruction, surface-analysis, granulometry, fastapi, three-js, python]
---

A web-based **RGB-D depth profiling system** designed for analyzing mineral sample surfaces using depth camera data. Originally developed during the clay and mineral characterization work at ALGES (2017-2018), this project creates depth maps from RGB, grayscale, or HSI-paired samples, providing the 3D surface information needed for **particle size (granulometry) estimation**.

## Business context

During hyperspectral mineral characterization campaigns, we captured not only spectral data (VNIR/SWIR) but also depth information. The goal was to complement spectral mineral identification with **physical surface properties** — particle size distribution, surface roughness, and texture — that directly affect processing behavior in grinding and flotation circuits.

## Key Performance Indicators — Process impact

Surface characterization from depth data provides granulometric information that traditionally requires physical sieve analysis (hours of manual lab work per sample).

| KPI | Baseline (physical sieve) | With depth profiling | Impact |
|-----|--------------------------|---------------------|--------|
| Characterization method | Destructive sieve analysis | Non-destructive surface imaging | Sample preservation for further analysis |
| Turnaround | Hours per sample | Minutes (image capture + processing) | Orders of magnitude faster |
| Spatial resolution | Bulk average | Per-pixel surface profile | Spatially resolved granulometry maps |
| Integration with HSI | Separate workflow | Co-registered depth + spectral data | Joint mineral-granulometry characterization |

![Processing pipeline](/images/projects/depth_profiler_pipeline.svg)

## How it works

The system implements a complete pipeline from raw depth images to quantitative surface metrics:

1. **Scene input**: Synthetic RGB-D scene generation (5 types) or upload of real depth camera data (e.g., SICK Ranger3D conveyor-belt profiling)
2. **Preprocessing**: Bilateral filter (edge-preserving smoothing, Tomasi & Manduchi 1998) + hole filling via nearest-neighbour interpolation
3. **3D reconstruction**: Depth-to-mesh conversion via pinhole camera model projection — each pixel becomes a 3D vertex, triangulated into a surface mesh
4. **Surface analysis**: Normal estimation via finite-difference gradients, Gaussian and mean curvature computation from second-order differential geometry
5. **Profile extraction**: 1D cross-section profiles along arbitrary lines with bilinear interpolation
6. **Roughness metrics**: ISO 4287 standard parameters from profile statistics

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Surface normals:</strong><br/>
n = (-∂z/∂x, -∂z/∂y, 1) / ‖(-∂z/∂x, -∂z/∂y, 1)‖<br/>
<br/>
<strong style="color:#e07830;">Gaussian curvature:</strong><br/>
K = (f<sub>xx</sub> · f<sub>yy</sub> - f<sub>xy</sub>²) / (1 + f<sub>x</sub>² + f<sub>y</sub>²)²<br/>
<br/>
<strong style="color:#e07830;">ISO 4287 roughness (Ra):</strong><br/>
Ra = (1/N) Σ |z<sub>i</sub> - z̄| — arithmetic mean deviation of the profile
</div>

## Technical stack

- **Backend**: Python/FastAPI with NumPy/SciPy for computational geometry
- **Frontend**: Three.js (r128) for interactive 3D mesh visualization with orbit controls
- **Render modes**: RGB texture, depth colormap (hot, viridis, jet), wireframe, point cloud
- **Export**: PLY, PCD, OBJ for external processing in MeshLab/CloudCompare/Blender
- **Communication**: REST API with base64-encoded images and flat arrays for Three.js geometry

![System architecture](/images/projects/depth_profiler_arch.svg)

## Connection to broader work

This project is the **enabling technology** for granulometry estimation from surface imaging. When combined with the [HSI Mineral Classification](/portfolio/HSIMineralClassification/) pipeline, it allows simultaneous characterization of both **what a mineral sample is** (spectral composition) and **how it looks physically** (particle size, roughness, texture). This joint characterization is critical for geometallurgical models that predict processing behavior.

[View on GitHub](https://github.com/fsantibanezleal/FASL_3D_Distance_Profiler)
