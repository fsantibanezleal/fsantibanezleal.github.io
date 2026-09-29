---
title: "Sondara, Drillhole Estimation and Simulation Compared on Real Held-Out Holes"
date: 2026-09-12
excerpt: "Three public drillhole families through one reproducible pipeline, and twelve methods, from nearest neighbour and kriging to SNESIM, Direct Sampling, DeepKriging and KCN, predicting the same held-out holes under one scoring. On Rocklea iron, ordinary kriging holds its place and the learned methods learn the structure without beating it."
collection: portfolio
tags: [drillholes, geostatistics, mining, kriging, simulation, machine-learning, geocond]
---

Drillhole estimates are usually judged by the method that produced them. The question I wanted answered is a
different one: which method predicts a hole that never entered the model, on real data, and is the difference larger
than the noise between holes? **Sondara** is built to answer it, and to say so when a model learned nothing.

![Sondara, three public families through an eight-stage pipeline, twelve methods and a geochemical review on the same held-out holes, and what they showed](/images/projects/sondara_pipeline.svg)

## Real sources, the same targets

Rocklea Dome (CSIRO, 5,035 one-metre multielement intervals in 158 holes), Alberta MAR_19860002 (22 inclined holes
with logged geology) and NTGS 12LE002 (one hole with eleven measured survey stations) are pinned by hash and run
through eight stages: acquire, ingest, preprocess, dataset, features, train, infer, evaluate. Splits are by whole
hole, inside the drilled area and at its margins, and every method predicts the same targets.

## Twelve methods, one scoring

Nearest neighbour, inverse distance, simple, ordinary and universal kriging, LMC cokriging, indicator kriging and
sequential Gaussian simulation run on **geocond**, the engine published on PyPI from its own repository (0.8.0);
SNESIM (MPSlib) and Direct Sampling simulate the Alberta logs under two labelled training images; DeepKriging and KCN
train on the GPU and ship as audited ONNX models. Paired hole-block intervals decide whether a difference is real,
and shuffled-label controls and a training-mean reference say whether a model learned anything.

What it showed on Rocklea iron, 23 test holes: ordinary kriging at RMSE 13.53 wt%, simple kriging, inverse distance
and cokriging within 0.4 wt% of its error, DeepKriging at 14.11 and KCN at 14.56, both better than their own
controls by 2.3 to 5.4 wt% of error and neither better than kriging. Sequential Gaussian simulation keeps the variance
that kriging halves. On Alberta's hole-group split, with three test holes, no method beats the training mean.

## The data it came with

The collection also ships a hyperspectral export. Read against its own files, its `hem/goe` column is the wavelength
of an iron-oxide absorption in nanometres, not a ratio; its assay-like columns copy the assay workbook; and twelve
holes have spectral depths offset from the assays. Calibrated on training holes, the iron-oxide index predicts iron
with RMSE 11.99 wt% on 701 test rows.

## Not a resource estimate

Predictions are values at the sample centres, not block grades, and the simulations are conditional on interpretations
that are labelled as such. The live page still shows the earlier local-first viewer; the web product rebuilt on these
results comes after the export and validation stages. Version 0.12.000, in construction.

![Sondara, the earlier local-first viewer still on the live page: three surveyed holes, the ore shell, and the active support with its grade and P90 uncertainty](/images/projects/sondara_app_dark.png)

[Live](https://sondara.ml.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_Sondara) · [geocond on PyPI](https://pypi.org/project/geocond/)
