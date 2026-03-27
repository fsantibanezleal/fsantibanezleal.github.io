---
title: "Dual Photography Lab"
date: 2020-06-01
excerpt: "Computational imaging that reconstructs a scene from the projector's viewpoint using light transport matrices and Helmholtz reciprocity.<br/><img src='/images/projects/dual_photography.svg'>"
collection: portfolio
tags: [computational-photography, linear-algebra, svd, compressed-sensing, dash, python]
---

An interactive application implementing the **dual photography** technique — a computational imaging method that reconstructs how a scene looks from a projector's point of view, even though no camera exists there. Based on the foundational work by [Sen et al. (SIGGRAPH 2005)](https://doi.org/10.1145/1073204.1073257).

![Concept](/images/projects/dual_photography.svg)

## The idea

When a projector illuminates a scene and a camera captures the result, the relationship between projected patterns and captured images is encoded in a **light transport matrix T**. Helmholtz reciprocity tells us that light paths are reversible: transposing T yields the "dual image" — what the projector would see if it were a camera.

## What makes this interesting

This is not just a matrix transpose. The transport matrix encodes how every projector pixel contributes to every camera pixel through the scene's geometry and materials. Analyzing its singular value spectrum reveals the scene's optical complexity: rank, condition number, and how much information can be recovered from compressed measurements.

## Features

- **Ray-cast simulation**: 3D scenes with occlusion and Lambertian BRDF — no physical hardware needed
- **6 scene types**: From simple planes to multi-object arrangements with varying optical complexity
- **SVD analysis**: Interactive exploration of singular value spectra, effective rank, and condition numbers
- **10 illumination patterns**: Canonical, Hadamard, Bernoulli (compressed sensing), Gray code, and more
- **Physical capture mode**: Optional webcam + screen-as-projector for real-world experiments
- **70 automated tests** covering simulation, SVD computation, and UI interactions

## Technical stack

- **Backend**: Python with NumPy/SciPy for ray-casting, BRDF simulation, and linear algebra
- **Frontend**: Dash (Plotly + Bootstrap) for interactive visualization
- **BRDF models**: Lambertian reflectance with configurable material properties for realistic light transport
- **Patterns**: Compressed sensing connections through Bernoulli measurement matrices

[View on GitHub](https://github.com/fsantibanezleal/FASL_Coding_DualFotography)
