---
title: "GeoLab — Browser-Native Multi-Engine Geospatial Tool Platform"
date: 2026-07-24
excerpt: "A browser-native, no-install geospatial platform: load a DEM, GeoTIFF, vector or point cloud, run real geoprocessing tools, chain them into reproducible pipelines, and explore the result on a map or 3D canvas, entirely client-side. Today it runs 747 real WhiteboxTools / GeoLibre tools via the geolibre WASM engine; the architecture is multi-engine by design and the tool count is only what genuinely runs.<br/><img src='/images/projects/geolab_app.png'>"
collection: portfolio
tags: [geospatial, gis, webassembly, gdal, whiteboxtools, pipelines, browser]
---

A **browser-native, no-install, multi-engine geospatial platform**. Load a DEM, GeoTIFF, vector or point cloud (a bundled sample or your own file), run real geoprocessing tools, chain them into reproducible pipelines, and explore the result on a map or 3D canvas. No server, no Python, no GDAL install, and your data never leaves your machine. Live at [geolab.fasl-work.com](https://geolab.fasl-work.com), a CAOS lab in the SimLab / PINN-Lab / QLab family.

![GeoLab — many WASM geospatial engines behind one tool interface, with reproducible pipelines](/images/projects/geolab_app.png)

## Many engines, one interface

The WebAssembly ecosystem has real geospatial engines, but they are fragmented. GeoLab aggregates them behind one uniform tool interface. Live today it runs **747 real WhiteboxTools / GeoLibre tools** via the geolibre WASM engine, in a Web Worker so the UI stays responsive. The architecture ([ADR-0059](https://github.com/fsantibanezleal/CAOS_GEOLAB)) is multi-engine by design: adding an engine is one adapter, and GDAL, GEOS, Turf, H3, mapshaper, ITK-Wasm, OpenCV.js and ONNX Runtime Web land incrementally.

## Honest by construction

Each result becomes a layer you inspect with a colormap and a value read-out at the cursor. A visual node editor chains tools into a shareable JSON recipe, re-runnable on new data, and every tool shows its source engine, authors and license. The tool count is only ever what genuinely runs, never padded; the sample data is labelled synthetic; and it is openly an actively-built-out lab, not a finished app.
