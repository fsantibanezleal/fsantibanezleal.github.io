---
title: 'A Forecast, Never a Prediction'
date: 2026-06-18
permalink: /rollings/2026/06/seismic-honest-forecast/
tags:
  - Seismic
  - Forecasting
  - Probability
  - Calibration
---

A Forecast, Never a Prediction
======

I have wanted to build this one for a long time, and I was scared of it for exactly the right reason: earthquakes are the canonical example of a thing you must not pretend to predict. So I built the opposite of a prediction. CAOS Seismic is now live at [seismic.fasl-work.com](https://seismic.fasl-work.com) — it reads the recent state of global seismicity and publishes a *probability*, strictly between 0 and 1, of an event in a region and magnitude band over the next 1, 2, or 7 days, always shown next to its long-term baseline.

The distinction is not pedantic. Following the ICEF definition (Jordan et al., 2011), a *prediction* is a deterministic "it will / will not happen"; a *forecast* is a probability. Deterministic prediction is effectively impossible — whether a small rupture cascades into a great one depends on unmeasurably fine detail of the crust (Geller et al., 1997). What is achievable is Operational Earthquake Forecasting, and the whole craft is in being honest about it.

![CAOS Seismic — calibration is the credibility artifact](/images/projects/seismic_honest.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The creed, carried into the product verbatim:</strong><br/>
Earthquakes cannot be predicted, but their probability can be forecast — reported honestly, with uncertainty, evaluated against reality, never as an alarm and never as a promise of safety.
</div>

A few non-negotiables fell out of that creed. Calibration is a release blocker: an uncalibrated probability does not ship, and the live reliability diagram ("when we said 5%, it happened about 5% of the time") is the headline artifact, not an accuracy number. ROC/AUC is banned, because it is blind to calibration. A single outcome neither confirms nor refutes a probabilistic forecast — a 3% forecast is *not wrong* when the 3% thing happens. And blank on the map never means "safe"; it means *no forecast / out of coverage*. The dangerous failure mode in this domain is not a missed event, it is false reassurance — the lesson of L'Aquila — so the product never reassures and never alarms. It complements official agencies; it does not replace them. [GitHub](https://github.com/fsantibanezleal/CAOS_SEISMIC) · [wiki](https://github.com/fsantibanezleal/CAOS_SEISMIC/wiki).
