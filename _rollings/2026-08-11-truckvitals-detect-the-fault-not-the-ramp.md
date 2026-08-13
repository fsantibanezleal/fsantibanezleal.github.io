---
title: 'TruckVitals: detect the fault, not the ramp'
date: 2026-08-11
permalink: /rollings/2026/08/truckvitals-detect-the-fault-not-the-ramp/
tags:
  - predictive-maintenance
  - condition-monitoring
  - negative-results
  - honesty
---

TruckVitals: detect the fault, not the ramp
======

![TruckVitals: a raw channel with learned regime bands above, the within-regime residual below, true onset marked](/images/projects/truckvitals_app.png)

Condition monitoring on a haul truck has a problem that fixed machinery does not: the truck changes what it is doing constantly. Payload, road grade and speed all move, and every monitored channel moves with them. Run a change detector straight on that telemetry and the biggest changes it finds are the truck loading, climbing and tipping.

[TruckVitals](https://truckvitals.fasl-work.com) puts the segmentation first: raw telemetry, then regimes, then the within-regime residual, then the change point, then the onset. The regimes are learned from **context** channels (payload, grade, speed) that are **disjoint** from the monitored ones, and that disjointness is the whole point, because a segmentation trained on the monitored channel would absorb the very fault it exists to expose.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The headline has no detector in it.</strong><br/>
On six-operating-condition C-MAPSS subsets the fault signature is <strong>0.16 sigma</strong> of the pooled spread and <strong>11.95 sigma</strong> of the within-regime spread.<br/>
<span style="color:#5a9ac0;font-size:13px;">Stated as an effect size, so no threshold rule, alarm convention or budget can move it. The single-operating-condition subsets return <strong>exactly 1.00</strong>, a negative control nobody designed: with one regime, the two spreads are the same quantity.</span>
</div>

What it does not claim is on the page too. Regime conditioning does **not** improve onset localisation, and that null is published (paired over five seeds: -0.08 ± 0.74 in chance-corrected skill, ahead in 2 of 5). No false-alarm-reduction claim is made anywhere, because on the synthetic lane the raw arm wins that metric outright. And the missing lane is named rather than papered over: there is no public, redistributable dataset of continuous haul-truck telemetry with labelled faults, so onset error is measured on a synthetic fleet and the app says so.

The headline reads the way it does because I commissioned a review to **refute** it. It confirmed the mechanism through eight attacks and broke three of the four numbers I had, and every one of those three had flattered the result. That is a separate story, and a better one than the numbers it replaced. Engine is the separately published [`regimecpd`](https://pypi.org/project/regimecpd/). [Live](https://truckvitals.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_TruckVitals).
