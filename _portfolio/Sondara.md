---
title: "Sondara, a Local-First Drillhole Intelligence Workbench"
date: 2026-09-12
excerpt: "Collar, survey, assay and geology sources rendered as a WebGL subsurface reconstruction in the browser, no login, uploaded data staying on the machine. A support-weighted estimate with its uncertainty, cross-validation and grade profile recomputed locally through the separately published geocond engine. Not a production resource estimate, and the workbench says which steps remain outside it.<br/><img src='/images/projects/sondara_pipeline.svg'>"
collection: portfolio
tags: [drillholes, geostatistics, mining, webgl, local-first, geocond]
---

Drillhole data is where a mineral project's value is decided and where its data is most fragmented: a collar table, a survey table, assay intervals and geology logs that only make sense desurveyed together and looked at in three dimensions. **Sondara** does that reconstruction in the browser, keeps the data on the machine, and shows the estimate's doubt next to its number.

![Sondara, four tables desurveyed and reconstructed in WebGL, a local support-weighted estimate through geocond, and what the workbench is not](/images/projects/sondara_pipeline.svg)

## Reconstruct locally

Surveyed borehole tubes, assay supports, an ore continuity shell, geology contacts and depth slicing, with orbit, section and plan views and a selection that follows the 3D scene. The source loader parses assay CSV depth and value columns into the browser-side support set; seed cases are explicit planning fixtures.

![Sondara, the Copper Ridge case: three surveyed holes, the ore shell, and the active support with its grade and P90 uncertainty](/images/projects/sondara_app_dark.png)

## Estimate with the doubt attached

The local estimate action recomputes support-weighted values, uncertainty, cross-validation and the grade profile for the selected method. The spatial-conditioning engine, support-aware conditioning, covariance estimation and sequential simulation, is **geocond**, published on PyPI from its own repository on 2026-09-26; the product declares no package of its own.

## Not a resource estimate

QA and QC, compositing, variogram fitting, full covariance solvers, categorical simulation and competent-person review are outside the public workbench; the learned method matrix and the bounded numerical server lane are recorded as planned, not shown as done. A public alpha with its plan as the implementation authority, on GitHub Pages plus a static mirror on the ML VPS; the lifecycle stays building.

[Live](https://sondara.ml.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_Sondara) · [geocond on PyPI](https://pypi.org/project/geocond/)
