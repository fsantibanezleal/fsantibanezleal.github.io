---
title: "Porvenir, Learned World Models for Mineral Processing, Measured Against Holding the Last Value"
date: 2026-09-08
excerpt: "A world model takes a proposed action sequence as an argument and returns a distribution over futures, which is what makes what-if questions, planning and regime detection expressible. Eleven rungs plus a zero-shot yardstick, from persistence to ensembled recurrent state-space models, every one scored per horizon against holding the last value. On the real iron-ore flotation record, seven of nine learned rungs do not beat persistence, and the app says so.<br/><img src='/images/projects/porvenir_pipeline.svg'>"
collection: portfolio
tags: [world-models, forecasting, latent-dynamics, uncertainty, mineral-processing, honesty]
---

Plant historians hold years of process records, and the models trained on them are almost always forecasters: given the past, predict the next values. A forecaster cannot answer the question an operator has, what would happen if a different action were taken, because the action is not an argument of the model. **Porvenir** makes the action sequence an input and asks three questions of mineral-processing records, answering each with a measurement: can a learned latent track state the plant does not instrument, can aleatoric and epistemic uncertainty be separated and made separately actionable, and how far does imagination drift from reality when a plan is executed.

![Porvenir, records through a ladder of eleven rungs and a yardstick, every one scored against persistence; on the real flotation record most learned rungs do not beat it](/images/projects/porvenir_pipeline.svg)

## The ladder, ordered by what each rung can express

Persistence (the bar), seasonal naive, VARX, GRU-D, DeepAR, MQ-RNN, a probabilistic ensemble that separates the two kinds of uncertainty, a patch transformer, a diagonal S4, a recurrent state-space model with KL balancing and free bits, and an ensembled RSSM that adds a usable epistemic signal, plus a Chronos zero-shot yardstick scored on the same windows. The engine is **latentplant**, published on PyPI from its own repository; the browser imagination lane runs the exported ONNX. Cases: the CC0 iron-ore flotation table (737,453 rows at 20 s, aggregated to the hourly assay cadence), the Tennessee Eastman archive, and two in-house simulators with ground truth; each case declares its expectation and what would refute it before it runs.

![Porvenir, the App on the real flotation record: imagined trajectories against what happened, and the verdict that seven of nine learned rungs did not beat holding the last value](/images/projects/porvenir_app_dark.png)

## Numbers withdrawn, then re-baked

The first published bake had four defects, a GRU-D rollout that never consumed the first future action, a biased CRPS estimator, unseeded rungs and a mismatched yardstick aggregation, so every number from it was marked withdrawn and replaced by a re-bake, with the defects recorded in the product's findings. The deploy drives a real browser against the live URL and refuses on an empty root or any console error, after a green deploy once shipped a blank page. On the real flotation record at the hourly cadence, seven of nine learned rungs do not beat persistence and no action set beats it beyond the first step, and the case page says the record does not identify controllable dynamics at that cadence. A research product, not a plant control system; no setpoint advice. A CC-BY preprint on Zenodo carries the method and results.

[Live](https://porvenir.ml.fasl-work.com) · [latentplant on PyPI](https://pypi.org/project/latentplant/) · [Preprint](https://doi.org/10.5281/zenodo.22135520)
