---
title: "Rajo, Open Pits Seen from Orbit"
date: 2026-09-08
excerpt: "An open observatory of the world's great open-pit mines and lithium evaporation ponds over four decades: a 3D globe with real relief, a yearly time-lapse per site from Landsat 1985 to Sentinel-2 today, spectral and mineral indices computed live in the browser from the raw cloud-optimized GeoTIFFs, a learned mine-footprint segmentation running in the browser, change points on the mined-area signal and the elevation difference between the 2000 and the 2011 to 2015 surfaces. Thirty sites, Chilean copper at the core; no backend, nothing uploaded. Live since 2026-09-03.<br/><img src='/images/projects/rajo_pipeline.svg'>"
collection: portfolio
tags: [remote-sensing, landsat, sentinel-2, mining, open-pit, maplibre, onnx, webgpu, chile]
---

**Rajo** ("open pit" in Chilean Spanish) shows each of thirty sites on a MapLibre globe with real relief, replays a yearly time-lapse from 1985 (Landsat) to today (Sentinel-2), computes nine spectral and mineral indices live in the browser from the raw cloud-optimized GeoTIFFs, runs a learned mine-footprint segmentation on WebGPU or WASM, detects change points on the mined-area series and shows where and how much rock moved between the year-2000 radar surface and the 2011 to 2015 Copernicus surface. Everything runs in the browser or comes from a baked, checksummed artifact: there is no backend, no account, and nothing is uploaded anywhere.

![Rajo, open sources baked offline into frames, masks, series and elevation differences for thirty sites, two models exported to ONNX, and a static globe whose live lanes read the raw imagery in the browser](/images/projects/rajo_pipeline.svg)

## Four questions per site

The Observatory and the Atlas are built around what a reader asks: what am I looking at, how did it grow, where did the rock go, and how sure is the mask. The offline pipeline bakes the yearly frames, the classical and learned masks, the mined-area series with its change points (ruptures), the dense series of every clear Sentinel-2 date since 2017 with its harmonic breaks, and the elevation difference, 7,107 validated files committed as compact WebP frames and JSON. A random forest and a U-Net trained on the Jasansky 2024 tiles are exported to ONNX; the U-Net scores a test IoU of 0.378 on held-out tiles and 0.502 on the catalog, and the Methods page reads that benchmark rather than restating it.

![Rajo, the Observatory: the globe, a site, its time-lapse and series](/images/projects/rajo_app_dark.png)

## Measured, sourced, and honest about its licences

Every site card carries sourced facts, Cochilco and the operators' own disclosures, and the Atlas prints the USGS copper table by country. The derived polygon layers stay CC BY-SA 4.0 (Maus 2022); the EOX Sentinel-2 cloudless basemap is CC BY-NC-SA 4.0, so Rajo is a non-commercial research showcase with the attribution rendered verbatim; the GRID tailings portal is permission-only and is not redistributed. Version 0.02.007 (2026-09-08) wrote the Spanish surface in Spanish, 254 strings and 88 diagram nodes with their accents, formatted every number in the reader's locale, and added a series gate that screenshots the map under each mask method and fails if the two are equal, after a diffusion deck had published the same unmasked map twice. It carries its own visual identity rather than the shared shell, by Felipe's instruction; the plan keeps its lifecycle at planned, and the deployment is measured live.

[Live](https://rajo.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_Rajo)
