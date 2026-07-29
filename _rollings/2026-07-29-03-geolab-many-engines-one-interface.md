---
title: 'GeoLab: many WASM geospatial engines behind one interface, in the browser'
date: 2026-07-29 19:00:00
permalink: /rollings/2026/07/geolab-many-engines-one-interface/
tags:
  - geospatial
  - webassembly
  - gis
  - honesty
---

GeoLab: many WASM geospatial engines behind one interface, in the browser
======

![GeoLab: load a DEM, run real geoprocessing tools client-side, chain them into pipelines](/images/projects/geolab_app.png)

[GeoLab](https://geolab.fasl-work.com) is a browser-native, no-install geospatial platform. Load a DEM, GeoTIFF, vector or point cloud (a bundled sample or your own file), run real geoprocessing tools, chain them into a reproducible pipeline, and explore the result on a map or 3D canvas. No server, no Python, no GDAL install, and your data never leaves your machine.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">What runs today, counted honestly:</strong><br/>
<strong>747</strong> real WhiteboxTools / GeoLibre tools, live, via the geolibre WASM engine, in a Web Worker<br/>
<span style="color:#5a9ac0;font-size:13px;">The architecture (ADR-0059) is multi-engine by design (GDAL, GEOS, Turf, H3, ITK, OpenCV, ONNX land as adapters). The count is only what genuinely runs, never padded.</span>
</div>

The WebAssembly ecosystem now has real geospatial engines, but they are fragmented, each its own library. GeoLab aggregates them behind one uniform tool interface, adds its own tools (including a cross-engine comparison: run the same operation through two engines and see the difference), and shows every tool's source engine, authors and license. A visual node editor turns a workflow into a shareable JSON recipe. It is a research lab in the SimLab / PINN-Lab / QLab family, actively built out and openly labelled as such. [Live](https://geolab.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_GEOLAB).
