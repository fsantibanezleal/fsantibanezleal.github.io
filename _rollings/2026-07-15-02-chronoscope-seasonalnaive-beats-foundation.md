---
title: 'A forecasting atlas where a one-line baseline beats a foundation model'
date: 2026-07-15
permalink: /rollings/2026/07/chronoscope-baseline-beats-foundation/
tags:
  - forecasting
  - foundation-models
  - honesty
  - timeseries
---

A forecasting atlas where a one-line baseline beats a foundation model
======

[ChronoScope](https://chronoscope.fasl-work.com) is a univariate time-series forecasting atlas: fifteen diagnostic cases, four of them real and licensed (UCI Electricity, UCI Beijing PM2.5, Monash/M4 hourly and daily), each run through the same nineteen-method ladder and scored by backtested MASE, sMAPE and interval coverage. The ladder goes from classical baselines up through gradient boosting and deep nets to a foundation-model tier: Chronos-Bolt, Chronos-2, TimesFM-2.5 and TiRex-2, all zero-shot.

The reason I built it as an atlas rather than a leaderboard is the result you only see when everything runs on the same footing:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Real M4-hourly, best MASE (lower is better):</strong><br/>
TiRex-2 <strong>0.476</strong> (a foundation model earns its place here)<br/>
SeasonalNaive <strong>0.641</strong><br/>
TimesFM-2.5 <strong>0.729</strong><br/>
<span style="color:#5a9ac0;font-size:13px;">A one-line SeasonalNaive beats a foundation model on this real series. White-noise and random-walk controls sit on the board too, so a method that "wins" on noise is visible as such.</span>
</div>

The foundation models are real and they run, but offline: the checkpoints are heavy and one of them (TiRex-2) needs a WSL2/CUDA lane because its kernels have no Windows wheels, so the browser lane is a numpy core and the foundation-model numbers are baked. Zero-shot forecasting is genuinely useful, and sometimes it is the best thing on the board. It is also, sometimes, beaten by a method you can write in one line, and I would rather show both. [Live](https://chronoscope.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_RES_ChronoScope).
