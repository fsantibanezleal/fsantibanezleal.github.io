---
title: 'Rajo 0.02.007: the Spanish surface written in Spanish, numbers in the reader''s locale, and a gate that compares two screenshots'
date: 2026-09-08
permalink: /rollings/2026/09/rajo-the-spanish-surface-and-a-gate-that-compares-screenshots/
tags:
  - rajo
  - remote-sensing
  - i18n
  - gates
---

Rajo 0.02.007: the Spanish surface written in Spanish, numbers in the reader's locale, and a gate that compares two screenshots
======

![Rajo, open sources baked offline into frames, masks, series and elevation differences for thirty sites, two models exported to ONNX, and a static globe whose live lanes read the raw imagery in the browser](/images/projects/rajo_pipeline.svg)

Rajo has been live since 2026-09-03: thirty open-pit mines and lithium evaporation ponds on a globe with real relief, a yearly time-lapse per site from Landsat 1985 to Sentinel-2 today, nine indices computed live in the browser from the raw cloud-optimized GeoTIFFs, a random forest and a U-Net running on WebGPU or WASM, change points on the mined-area series, and the elevation difference between the year-2000 radar surface and the 2011 to 2015 Copernicus surface. The four patch releases since then were about the reader, not the data.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The Spanish surface shipped in ASCII.</strong><br/>
No written accents, no eñe, no opening question mark: "Ano" where "año" was meant on the timeline, "Que estoy mirando?" on the question tabs. 0.02.004 restored 254 strings and 88 diagram nodes, reading the context-dependent pairs (esta/está, aun/aún, publica/pública, como/cómo, bajo/bajó) sentence by sentence rather than substituting, and a test now fails the build on any unaccented form from the list.<br/>
<span style="color:#5a9ac0;font-size:13px;">Numbers are part of the language too. Every displayed number went through toFixed, so a Spanish reader saw "272.9 km2" and "11,506" with English separators; 0.02.005 routes 62 call sites through the reader's locale and scans the source for a toFixed in a component. 0.02.006 says "frame" for a satellite frame, not "cuadro", in 32 places.</span>
</div>

The last fix came from a diffusion deck. Two mask screenshots taken for it were byte-identical, so the deck was about to publish the same unmasked map twice as "the same frame, two methods": the year's mask only draped while the series drawer was open, because the overlay effect required the drawer, and closing the drawer to see the mask over the whole map, which is the reason to turn it on, removed it. The drawer is the control, not the view. The series gate now closes the drawer, screenshots the map under each method, and fails if the two images are equal or the mask layer disappears.

Rajo carries its own visual identity rather than the shared shell, by Felipe's instruction; the plan keeps its lifecycle at planned, and the deployment is measured live. Every number on screen traces to a computation the reader can rerun or to a named, dated source.

[Live](https://rajo.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_Rajo)
