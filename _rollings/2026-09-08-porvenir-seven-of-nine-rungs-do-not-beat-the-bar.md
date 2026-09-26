---
title: 'Porvenir: seven of nine learned rungs do not beat holding the last value'
date: 2026-09-08
permalink: /rollings/2026/09/porvenir-seven-of-nine-rungs-do-not-beat-the-bar/
tags:
  - world-models
  - forecasting
  - mineral-processing
  - honesty
---

Porvenir: seven of nine learned rungs do not beat holding the last value
======

![Porvenir, records through a ladder of eleven rungs and a yardstick, every one scored against persistence](/images/projects/porvenir_pipeline.svg)

Porvenir 0.03.000 is live with its numbers re-baked. A forecaster maps history to a future; a world model takes a proposed action sequence as an argument and returns a distribution over futures, and that single difference is what makes what-if questions, planning and regime detection expressible at all. The product asks three questions of mineral-processing records and answers each with a measurement: whether a learned latent can track state the plant does not instrument, whether aleatoric and epistemic uncertainty can be separated and made separately actionable, and how far imagination drifts from reality when a plan is executed.

The ladder is ordered by what each rung can express, not by how modern it is: persistence, seasonal naive, VARX, GRU-D, DeepAR, MQ-RNN, a probabilistic ensemble, a patch transformer, a diagonal S4, a recurrent state-space model and an ensembled one, plus a Chronos zero-shot yardstick scored on the same windows. Every rung must beat holding the last value, per horizon, or the report says it did not.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">On the real iron-ore flotation record, at the hourly assay cadence, seven of nine learned rungs did not beat persistence.</strong><br/>
No action set beat it beyond the first step, so the case reports that the plant record does not identify controllable dynamics at that cadence. That sentence is on the case page, not in a footnote.<br/>
<span style="color:#5a9ac0;font-size:13px;">The first bake's numbers had been published and were withdrawn: a GRU-D rollout that never consumed the first future action, a biased CRPS estimator, unseeded rungs, a mismatched yardstick aggregation. Each is recorded in the findings, and every number now on the site comes from the re-bake.</span>
</div>

One more gate came out of this product: the deploy script drives a real browser against the live URL and refuses on an empty root or any console error, after a green deploy once shipped a blank page whose title and data index were both correct. A green deploy is evidence that the deploy ran.

[Live](https://porvenir.ml.fasl-work.com) · [latentplant on PyPI](https://pypi.org/project/latentplant/) · [preprint](https://doi.org/10.5281/zenodo.22135520).
