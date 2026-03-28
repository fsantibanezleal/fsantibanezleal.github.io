---
title: "Hyperspectral Mineral Classification Platform"
date: 2025-11-01
excerpt: "ML platform for mineral identification and abundance estimation from hyperspectral imagery using ensemble methods, CNNs, and compositional constraints.<br/><img src='/images/projects/hsi_mineral_classification.svg'>"
collection: portfolio
tags: [hyperspectral, machine-learning, mineral-classification, cnn, fastapi, dash]
---

A **machine learning platform** for classifying minerals and estimating their abundances from hyperspectral imagery (VNIR/SWIR), designed for deployment at mining and exploration sites.

## Business impact

This platform automated mineral identification that previously required manual laboratory analysis, compressing turnaround from days to minutes for routine characterization. Faster mineralogical feedback enables tighter process control in geometallurgical workflows. Compositional constraints (abundances sum to 100%) ensure that results are physically meaningful and directly usable by geologists without manual correction.

| Metric | Result |
|--------|--------|
| Models | XGBoost, ExtraTrees, CNN 1D/2D, ensemble |
| Constraint | Predicted abundances sum to 100% |
| Minerals | Clays, sulfates, iron oxides, phyllosilicates |
| Deployment | Desktop application for field use |

## Strategic context

Laboratory mineral analysis (XRD/XRF) takes days and requires sample preparation; this system provides estimates in minutes directly from spectral data. For geometallurgical applications, faster characterization means tighter feedback loops between ore properties and processing parameters — enabling operators to adapt process settings to changing ore in near real-time rather than reacting to stale lab results.

![Pipeline](/images/projects/hsi_mineral_classification.svg)

## The challenge

Hyperspectral cameras capture hundreds of narrow spectral bands across the visible, near-infrared, and short-wave infrared ranges. Each pixel in the resulting raster encodes a spectral signature that can reveal the mineral composition of rock samples, drill core, or conveyor belt material. However, translating raw spectral data into reliable mineral maps requires careful calibration, robust models, and domain-aware constraints -- particularly the requirement that predicted mineral abundances at each pixel must sum to 100%.

## System architecture

1. **Data ingestion**: The platform accepts hyperspectral rasters from VNIR/SWIR cameras alongside laboratory reference measurements (XRD for mineral phases, XRF for elemental composition). Regions of interest (ROIs) are defined to link spectral patches with ground-truth mineral labels.
2. **Spectral patch database**: ROI-aligned spectral patches are extracted and organized into training databases, with augmentation and normalization pipelines to handle varying illumination and sensor conditions.
3. **Multi-model training**: Several model architectures are trained in parallel -- XGBoost, ExtraTrees, Ridge regression, Partial Least Squares Regression (PLSR), and 1D/2D Convolutional Neural Networks. An ensemble layer and meta-learning strategies combine predictions across models and datasets.
4. **Compositional constraints**: A post-processing layer enforces that predicted mineral abundances satisfy closure (sum to 100%) and non-negativity. This is formulated as a constrained least-squares problem: min ||a - a_pred||^2 subject to sum(a_i) = 1 and a_i >= 0, solved via quadratic programming or simplex projection.
5. **Output products**: Mineral classification maps, per-pixel abundance estimates with confidence intervals, and summary statistics for geological interpretation.

## Minerals handled

The system has been applied to a range of mineral assemblages relevant to mining and exploration, including clays (kaolinite, chlorite, smectite, muscovite), sulfates (alunite), iron oxides (limonite), and various phyllosilicates. Model configurations are adapted per mineral system.

## Technology stack

- **ML**: XGBoost, ExtraTrees, scikit-learn, TensorFlow/Keras for CNN architectures
- **Backend**: FastAPI (Python), NumPy, SciPy for spectral processing
- **Frontend/Visualization**: Dash for interactive mineral maps and model exploration
- **Desktop deployment**: Packaged for field use at sites with limited connectivity
- **Data**: HDF5 and GeoTIFF for raster storage, pandas for tabular data

*This project is part of proprietary consulting work. Source code is not publicly available.*
