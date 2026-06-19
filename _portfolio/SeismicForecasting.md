---
title: "CAOS Seismic — Honest Probabilistic Earthquake Forecasting"
date: 2026-06-18
excerpt: "Earthquakes cannot be predicted, but their probability can be forecast — honestly. A daily, calibrated, conditional probability of seismic events over 1/2/7-day horizons, shown next to its baseline and scored prospectively against reality.<br/><img src='/images/projects/seismic_pipeline.svg'>"
collection: portfolio
tags: [seismology, forecasting, probability, etas, csep, calibration, geophysics]
---

A **probabilistic seismic forecaster** that reads the recent state of global seismicity and publishes bounded, calibrated, conditional probabilities of earthquakes over short horizons (1 / 2 / 7 days), for a region and a magnitude band — **always shown next to the long-term baseline** and **evaluated prospectively against reality**. It is a *forecaster*, never an alarm: every number is a probability strictly in (0, 1). Live at [seismic.fasl-work.com](https://seismic.fasl-work.com).

> Earthquakes cannot be predicted, but their probability can be forecast — reported honestly, with uncertainty, evaluated against reality, never as an alarm and never as a promise of safety.

## Why "forecast", not "prediction"

Following the ICEF definition (Jordan et al., 2011), a *prediction* is a deterministic statement that an event will or will not occur; a *forecast* gives a probability strictly between 0 and 1. Deterministic earthquake prediction is effectively impossible — whether a small rupture cascades into a great one depends on unmeasurably fine detail of the crust (Geller et al., 1997). What *is* achievable is Operational Earthquake Forecasting (OEF): conditional probabilities that stay low in absolute terms even when the relative gain during an active sequence is one-to-three orders of magnitude. A single outcome neither validates nor invalidates a probabilistic forecast — a 3% forecast is **not wrong** when the 3% outcome occurs.

## What makes a forecast honest here

- **A defensible baseline.** A maximum-likelihood space–time ETAS model (Ogata 1998), plus the mandatory smoothed-seismicity Poisson null any time-dependent model must beat.
- **Skill is proven, not asserted.** Every model is scored with the field-standard CSEP framework (pyCSEP) — consistency tests (N/M/S/L/CL) and comparison tests on information gain per earthquake, in *nats*, against both the null and ETAS. ROC/AUC is banned as a skill metric (it is calibration-blind).
- **Calibration is a release blocker.** An uncalibrated probability does not ship. The live **reliability diagram** ("when we said 5%, it happened ~5% of the time") is the headline artifact.
- **Leakage is structurally impossible.** A strict forecast clock hands the model only the catalog up to issue time; every past forecast is byte-reproducible and scored against the catalog as it was at issue time.
- **A stronger model must earn the map.** A GPU-trained, context-conditioned neural temporal point process is a *gated* challenger — it reaches the public map only if it beats ETAS in our own prospective CSEP harness and is calibrated. In June it cleared the in-loop gate (+0.075 nats/eq, calibrated), with pseudo-prospective validation still pending; until that passes, ETAS is what ships.

## Architecture

Heavy compute runs **once per day, offline**; the runtime is a pure static viewer with no processing backend.

![CAOS Seismic — offline compute, git-as-data, static viewer](/images/projects/seismic_pipeline.svg)

A local GPU workstation pulls public feeds (USGS ComCat + regional FDSN), runs the mandatory hygiene order (time-varying completeness Mc → moment-magnitude homogenization → dual declustering), fits ETAS and the gated challenger, simulates an ensemble, calibrates, runs the CSEP gate, and commits **one compact gzipped artifact** to a public repo. A Vite + React + TypeScript viewer reads the committed JSON — no server computes anything, so hosting is near-free and every forecast is auditable straight from the git history.

## Global by design

The model trains on global seismicity and runs inference across many countries — high-seismicity (Chile, Japan, Indonesia, Mexico, Türkiye, California, New Zealand) and low-seismicity (UK, Germany, Australia, Brazil) — precisely so the forecast can be audited for bias toward active zones. The single public exceedance formula `P = 1 − e^(−N)` never changes; only the quality of the conditional intensity improves.

## The honest limits

This is an independent research and education tool that **complements** official agencies (in Chile, the CSN; civil protection, SENAPRED) — it never replaces them, never issues an alarm or a countdown, and never declares a "safe" state. Blank on the map means *no forecast / out of coverage*, never "safe". The hardest part of any risk product is communicating uncertainty responsibly; the lesson of L'Aquila (2009) is that false reassurance is what causes harm, and this product is built to never over-reassure.

## Live application

▶ **[seismic.fasl-work.com](https://seismic.fasl-work.com)** — the world probability field, per-country drill-down, the reliability diagram, the multi-model back-analysis, and the honest experiment journey.

[GitHub repository](https://github.com/fsantibanezleal/CAOS_SEISMIC) · [Technical wiki](https://github.com/fsantibanezleal/CAOS_SEISMIC/wiki)
