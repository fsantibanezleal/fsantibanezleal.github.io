---
title: "TruckVitals, Onset Detection on Haul-Truck Telemetry (Regime First, Then Residual)"
date: 2026-08-11
excerpt: "Every haul-truck channel moves with payload, grade and speed, so a detector run on raw telemetry detects the truck going uphill, not a fault. TruckVitals segments the operating regime first, from context channels disjoint from the monitored ones, and detects on the within-regime residual. The headline carries no detector in it: 0.16 sigma of the pooled spread against 11.95 sigma of the within-regime spread, with single-condition subsets returning exactly 1.00 as a negative control. It ships a published null and a withdrawn claim.<br/><img src='/images/projects/truckvitals_app.png'>"
collection: portfolio
tags: [predictive-maintenance, condition-monitoring, change-point-detection, regime-segmentation, null-results, adversarial-review]
---

**Onset detection on haul-truck fleet telemetry**, built on regime-conditional residuals. Live at [truckvitals.fasl-work.com](https://truckvitals.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) hub.

![TruckVitals: a raw channel above with learned regime bands, the within-regime residual below, and the true onset marked](/images/projects/truckvitals_app.png)

## Detect the fault, not the ramp

Every channel on a haul truck moves with payload, road grade and speed. Run a change detector on raw telemetry and the largest changes it finds are the truck loading, climbing and tipping. So the pipeline puts segmentation first:

```
raw telemetry -> REGIME SEGMENTATION -> within-regime residual -> change point -> onset
```

with the regimes learned from **context** channels (payload, grade, speed) that are **disjoint** from the monitored ones. That disjointness is what stops the segmentation absorbing the very fault it exists to expose.

## A headline with no detector in it

The core claim is stated as an effect size, so no threshold rule, alarm convention or budget can move it. On six-operating-condition NASA C-MAPSS subsets the fault signature is **0.16 sigma of the pooled spread and 11.95 sigma of the within-regime spread**, a ratio of 90.2 on one pair and 62.3 on the second. The single-operating-condition subsets return **exactly 1.00**, a negative control nobody designed: with one regime, the pooled and within-regime spreads are the same quantity. Detection at a matched budget is reported separately: one to six operating conditions costs 0.93 to 0.17 and 0.73 to 0.24, and regime conditioning recovers to 0.98 and to 0.70, which on the second pair is **level with** the single-condition reference, not above it.

## What it does not claim

A published **null**: regime conditioning does not improve onset *localisation* (paired over five seeds, -0.08 ± 0.74 in chance-corrected skill, ahead in 2 of 5). A **withdrawn** claim: no false-alarm reduction is claimed anywhere, because on the synthetic lane the raw arm wins that metric outright. And the lane that does not exist is named: no public, redistributable dataset of continuous haul-truck telemetry with labelled faults was found, which is why onset error is measured on the synthetic lane.

The headline changed because a review was commissioned to **refute** it. Across eight attacks it confirmed the mechanism and broke three of the four original numbers, all three of which had flattered the result. The engine is the separately published [`regimecpd`](https://pypi.org/project/regimecpd/) package; TruckVitals declares none of its own. [Live](https://truckvitals.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_TruckVitals).
