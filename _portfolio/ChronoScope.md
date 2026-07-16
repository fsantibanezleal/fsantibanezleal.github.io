---
title: "ChronoScope — Univariate Forecasting Atlas with a Foundation-Model Tier"
date: 2026-07-15
excerpt: "A univariate time-series forecasting atlas: 15 diagnostic cases (4 real licensed + 11 seeded synthetic), each run through the same 19-method ladder with backtested MASE/sMAPE/coverage, from classical baselines up to four zero-shot foundation models (Chronos-Bolt, Chronos-2, TimesFM-2.5, TiRex-2). Baked offline, replayed in a static SPA, with a Pyodide numpy live lane.<br/><img src='/images/projects/chronoscope_app.png'>"
collection: portfolio
tags: [scientific-ml, time-series, forecasting, foundation-models, chronos, timesfm, onnx, benchmark]
---

A univariate **time-series forecasting atlas**. Fifteen diagnostic cases, each forecast by the same **19-method ladder** and scored by backtested MASE / sMAPE / interval coverage, so you can read one method against another on the same footing. Live at [chronoscope.fasl-work.com](https://chronoscope.fasl-work.com).

![ChronoScope — 15 cases through a 19-method ladder up to a foundation-model tier](/images/projects/chronoscope_app.png)

## One ladder, four tiers

Classical and statistical baselines (SeasonalNaive, Theta, AutoARIMA, AutoETS), a gradient-boosting tier (LightGBM), deep nets (NHITS, DLinear, NLinear), and a **foundation-model tier**: Chronos-Bolt, Chronos-2, TimesFM-2.5 and TiRex-2, run **zero-shot**. TiRex-2 needs a purpose-built WSL2/CUDA lane because its kernels have no Windows wheels.

## Real data, and honest limits

Four cases are real and licensed (UCI Electricity, UCI Beijing PM2.5, Monash/M4 hourly and daily, all CC-BY-4.0); the other eleven are seeded synthetic with a licence guard that blocks non-redistributable sources. The **foundation models run offline only** (the browser lane is numpy, not an in-browser transformer). And the atlas shows where the hype breaks: on real M4-hourly a one-line **SeasonalNaive (MASE 0.641) beats TimesFM-2.5 (0.729)**, while TiRex-2 gives the best 0.476. White-noise and random-walk controls are on the board too.
