---
title: 'Sondara: the drillholes stay on the machine, and the estimate shows its doubt'
date: 2026-09-12
permalink: /rollings/2026/09/sondara-the-drillholes-stay-on-the-machine/
tags:
  - sondara
  - mining
  - geostatistics
  - local-first
---

Sondara: the drillholes stay on the machine, and the estimate shows its doubt
======

![Sondara, four tables desurveyed and reconstructed in WebGL, a local support-weighted estimate, and what the workbench is not](/images/projects/sondara_pipeline.svg)

Sondara v0.2.0 is public today, with no login. Drillhole data is where a mineral project's value is decided and where its data is most fragmented: a collar table, a survey table, assay intervals and geology logs that only make sense desurveyed together and looked at in three dimensions. The commercial workbenches that do this are desktop products; the open alternatives ask for a server or a notebook.

Sondara does the reconstruction in the browser: surveyed borehole tubes, assay supports, an ore continuity shell, geology contacts, depth slicing, orbit, section and plan views, with a selection that follows the 3D scene. The source loader parses assay CSV depth and value columns into the browser-side support set, and uploaded data stays on the machine. The local estimate action recomputes support-weighted values, uncertainty, cross-validation and the grade profile for the selected method, so the number and its doubt appear together.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">It is not a production resource estimate, and it says which steps remain outside it.</strong><br/>
QA and QC, compositing, variogram fitting, full covariance solvers, categorical simulation and competent-person review are outside the public workbench; the learned method matrix and the bounded numerical server lane are recorded as planned, not shown as done.<br/>
<span style="color:#5a9ac0;font-size:13px;">The spatial-conditioning engine is a separate package, geocond, with the boundary set deliberately: support-aware conditioning, covariance estimation and sequential simulation, published from its own repository; the product declares no package of its own.</span>
</div>

A public alpha with its plan as the implementation authority, on GitHub Pages plus a static mirror on the ML VPS, grown from the same rebuild discipline as Aerovia.

[Live](https://sondara.ml.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_Sondara)
