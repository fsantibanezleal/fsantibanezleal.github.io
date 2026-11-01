---
title: 'DinHot, keep the evidence path visible'
date: 2026-10-31
permalink: /rollings/2026/10/dinhot-evidence-path-visible/
tags:
  - product-engineering
  - data-quality
  - technology-leadership
---

DinHot, keep the evidence path visible
======

![DinHot's case, artifact and execution contracts](/images/projects/dinhot_architecture_data_contracts.svg)

A result in a product can come from a precomputed artifact or a live run. DinHot separates the offline bake, static replay and the browser lane so the interface can show where each result came from. The live lane is gated; it only re-runs the combinations admitted for browser execution.

For release 0.02.001, 13 of the 14 synthetic cases are baked. C11 is refused by contract 1. Keeping that status visible is part of the evidence, not a number to smooth away.

![Offline, replay and live lanes in the DinHot workbench](/images/projects/dinhot_architecture_lanes.svg)
