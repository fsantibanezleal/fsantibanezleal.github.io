---
title: 'Sondara 0.12.000: twelve methods on held-out drillholes, and ordinary kriging keeps its place'
date: 2026-09-28
permalink: /rollings/2026/09/sondara-twelve-methods-on-held-out-holes/
tags:
  - sondara
  - geostatistics
  - mining
  - machine-learning
---

Sondara 0.12.000: twelve methods on held-out drillholes, and ordinary kriging keeps its place
======

![Sondara, three public families through an eight-stage pipeline, twelve methods and a geochemical review on the same held-out holes](/images/projects/sondara_pipeline.svg)

On 12 September I described Sondara as a local-first viewer and listed its learned methods as planned. Between 26 and 28 September the pipeline underneath it was rebuilt, and 0.12.000 closes the unit that compares every method on the same held-out holes. The data comes first, and it is other people's work: CSIRO's Rocklea Dome collection (5,035 one-metre multielement intervals in 158 holes), Alberta MAR_19860002 (22 inclined holes with logged geology) and the Northern Territory Geological Survey hole 12LE002, each pinned by hash.

Twelve methods predict the same targets under one scoring: nearest neighbour, inverse distance, simple, ordinary and universal kriging, LMC cokriging, indicator kriging and sequential Gaussian simulation on geocond 0.8.0 (the engine, published from its own repository), SNESIM through MPSlib and Direct Sampling on the Alberta logs, and two learned methods, DeepKriging (Chen, Li, Reich and Sun, Statistica Sinica 2024) and Kriging Convolutional Networks (Appleby, Liu and Liu, AAAI 2020), trained on the GPU and exported to audited ONNX. Splits are by whole hole, inside the drilled area and at its margins.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Rocklea iron, hole-group split, one-metre support: test RMSE in wt% Fe.</strong><br/>
ordinary kriging 13.53 &nbsp;|&nbsp; DeepKriging 14.11 &nbsp;|&nbsp; KCN 14.56 &nbsp;|&nbsp; their shuffled-label controls 17.42 and 17.69 &nbsp;|&nbsp; training mean 17.65<br/>
<span style="color:#5a9ac0;font-size:13px;">Paired MAE difference with kriging over 95 % hole-block intervals: DeepKriging -0.14 [-0.91, +0.51], KCN +0.76 [+0.21, +1.36]. Both learned methods beat their own controls by 2.3 to 5.4 wt% of MAE, so they learned the spatial structure; neither beats kriging on the drilled area, and at the margins no learned method separates from it in either direction.</span>
</div>

The result I learned most from is at the margin. Given only the position, DeepKriging scores 13.25 inside the drilled area, better than with its basis functions, and 33.94 at the one-metre margin, where 497 of the 527 test targets lie outside the training box: it predicts down to -58.8 wt% Fe. A ReLU network is piecewise linear and continues its last pieces beyond the data. With the basis, the fitted networks stayed inside the training range at the margin, yet inside the drilled area DeepKriging still made six predictions outside the training range, the lowest -3.2 wt%: nothing in the network bounds a grade at zero, and the page says so.

The collection also ships a hyperspectral export, and read against its own files its `hem/goe` column is the wavelength of an iron-oxide absorption in nanometres, not a ratio, and twelve holes have spectral depths offset from the assays. Calibrated monotonically on training holes, the iron-oxide index predicts iron on 701 test rows with RMSE 11.99 against kriging's 13.85, but the interval of the MAE difference reaches zero and the index carries a bias of +2.7 wt%. It measures the interval itself, which is a different task from interpolation, not an improvement of it. None of this is a resource estimate: predictions are values at sample centres, not block grades. The live page still shows the earlier viewer; the web product rebuilt on these results comes after the export and validation stages.

[Live](https://sondara.ml.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_Sondara) · [geocond on PyPI](https://pypi.org/project/geocond/)
