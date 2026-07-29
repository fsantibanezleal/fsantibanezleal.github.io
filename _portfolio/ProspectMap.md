---
title: "ProspectMap — Mineral Prospectivity Workbench with a Published Null Result"
date: 2026-07-06
excerpt: "A mineral-prospectivity workbench that computes a Weights-of-Evidence posterior P(deposit|evidence) live in the browser over stacked geophysical, geochemical and structural layers, and whose real reason to exist is adversarial honesty. On real US Midcontinent MVT Zn-Pb belt data (Lawley et al. 2022, USGS public domain) it publishes a recorded null: the proposed PU-Conformal method loses to 1989-vintage Weights of Evidence, and a trivial distance-to-deposit baseline already ties the best learned model, so most apparent skill is spatial proximity, not learned geology.<br/><img src='/images/projects/prospectmap_app.png'>"
collection: portfolio
tags: [mining-analytics, mineral-prospectivity, weights-of-evidence, null-result, spatial-cv, conformal, mvt, geoscience, onnx, mining]
---

ProspectMap is a **mineral-prospectivity** workbench. It computes a Weights-of-Evidence posterior P(deposit|evidence) live in the browser over stacked geophysical, geochemical and structural layers, and its reason to exist is adversarial honesty: it makes first-class the two ways prospectivity maps lie (conditional-independence violation and random-CV inflation), and it publishes a recorded null result on real data. Live at [prospectmap.fasl-work.com](https://prospectmap.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) mining-analytics hub.

![ProspectMap — a Weights-of-Evidence posterior with its failure modes made first-class, in the browser](/images/projects/prospectmap_app.png)

## No AlphaEarth, no foundation-model embeddings

To be exact about scope: AlphaEarth is not used, anywhere. It appears once, in an attribution file, as a candidate future dataset. There is no embedding, no Earth Engine call, no 64-D feature in the pipeline. Random forest and gradient boosting are computed offline only; they never run live.

## The real-data story is a null result

On the US Midcontinent MVT Zn-Pb belt (Lawley et al. 2022, USGS public domain; 25,344 cells, 4 real measured geophysical layers plus 2 derived proximity layers), six models are scored on identical contiguous spatial-block folds with bootstrap confidence intervals: Weights of Evidence 0.732, logistic regression 0.846, random forest 0.745, gradient boosting 0.725, naive MLP 0.783, PU-Conformal 0.656. The committed verdict is ranking_win: false: the proposed PU-Conformal method does not beat 1989-vintage Weights of Evidence. And the trivial distance-to-known-deposit null already scores 0.783, so most apparent skill is spatial proximity, not learned geology. The leaky 0.9456 headline that a lenient interleaved-fold protocol produces is never quoted.

## The honest limit

Negative controls collapse as they must: label permutation drops WofE to 0.506 and PU to 0.490, and a pure noise layer earns zero lift. The split-conformal band delivers its coverage guarantee (empirical 0.977 vs nominal 0.90), but only by flagging 88 percent of the belt, an honest near-vacuous set that correctly reports that regional geophysics cannot localize MVT under spatial transfer, rather than a false-confidence point map. This is target generation with its uncertainty stated, not a JORC or NI 43-101 resource estimate.

[Live demo](https://prospectmap.fasl-work.com) · [Source on GitHub](https://github.com/fsantibanezleal/CAOS_ProspectMap)
