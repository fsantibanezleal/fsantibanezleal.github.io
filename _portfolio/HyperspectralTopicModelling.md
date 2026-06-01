---
title: "Hyperspectral Mineral Analysis by Topic Modelling (2022)"
date: 2022-09-01
excerpt: "The original 2022 conference work that reframed hyperspectral mineral characterisation as a topic-modelling problem: spectra as documents, LDA topics as a routing layer for per-topic regression. Cut copper-recovery error an order of magnitude on drill-core data.<br/><img src='/images/projects/hsi_mineral_classification.svg'>"
collection: portfolio
tags: [hyperspectral, topic-modelling, lda, geometallurgy, mineralogy, regression]
---

The **founding 2022 work** behind the hyperspectral topic-modelling line, presented as *"Geometallurgical Estimation of Mineral Samples from Hyperspectral Images and Statistical Topic Modelling"* at the 18th International Conference on Mineral Processing and Geometallurgy (Procemin Geomet 2022, Gecamin), from my postdoctoral research at ALGES / AMTC, Universidad de Chile. It is the seed that later grew into the full [LDA-HSI research platform](/portfolio/LDA-HSI/); this entry stays faithful to what the conference paper actually did.

## Business impact

Geometallurgical estimation — predicting how an ore will behave in processing (copper recovery, molybdenum recovery, acid consumption, Bond work index) — traditionally needs slow, expensive laboratory assays on every drill-core composite. Hyperspectral imaging is fast and cheap by comparison, but a raw spectrum is hundreds of correlated bands with no obvious link to a recovery number. This work showed that **borrowing the document/topic metaphor from text mining** turns that raw spectral variability into a usable structure: cluster the spectra into mineral "topics", then let each topic carry its own regression. The result was an order-of-magnitude error reduction on real drill-core data — evidence that topic models are a viable bridge from cheap spectra to expensive lab targets.

| Metric | Result |
|--------|--------|
| Problem | Geometallurgical target estimation from HSI |
| Method | LDA topic clustering → per-topic regression |
| Wordification recipes | 3 (Version 1 band-frequency, V2 intensity-bins, V3 joint) |
| Data | A few small private mineral sets — drill-core DB1 (146 samples), DB2 (27 samples), and the early HIDSAG geological subsets — VNIR+SWIR. No public benchmark scenes. |

## Strategic context

This was, to my knowledge, the first formalisation of HSI mineral-sample characterisation as a **probabilistic topic-modelling** problem. The prior art at ALGES (Egaña et al., *Minerals* 2020) used a hierarchical clustered-regression scheme; the 2022 contribution was to make the *clustering stage* probabilistic and interpretable by modelling each sample as a mixture of latent mineral topics inferred by LDA. That single change — a soft, interpretable topic membership instead of a hard cluster — is what carried the accuracy gain, and it is the idea the whole later platform is built on.

![Spectra-as-documents pipeline](/images/projects/hsi_mineral_classification.svg)

## Key Performance Indicators — Estimation accuracy (DB1, copper recovery)

The headline was measured on a 20% holdout of the DB1 drill-core set, as mean absolute error (MAE) on copper recovery (RECCU) and molybdenum recovery (RECMO).

| Model | RECCU MAE | RECMO MAE | Impact |
|-------|-----------|-----------|--------|
| Naive per-spectrum baseline | 4.568 | 18.639 | Reference |
| Hierarchical + NN clustering | 0.680 | 2.871 | Prior art (Egaña 2020) |
| **Hierarchical + LDA Version 1** | **0.422** | **2.227** | ~10× error reduction vs baseline |
| Hierarchical + LDA Version 3 | 0.432 | 2.218 | Comparable to V1 |
| Hierarchical + LDA Version 2 | 0.714 | 3.105 | Weaker variant |

On the smaller DB2 set (7 topics), estimation error dropped ~10–15% versus baselines. **Version 1 — each wavelength band as a word, document = summed quantised intensities — was the strong, interpretable recipe**, and it survives as the canonical baseline in the modern platform.

## The challenge

A hyperspectral sample is a stack of spectra (VNIR 400–1000 nm, 942 bands + SWIR 1000–2500 nm, 268 bands), and lab targets exist only at the *sample* level. Mapping that high-dimensional, highly-correlated spectral evidence to a single recovery number is the core difficulty — a naive per-spectrum regressor scored an MAE of 4.57, effectively useless. The insight was to treat each sample as a **document**: quantise the reflectance, turn bands (or intensity levels) into a finite vocabulary, and let LDA infer a small set of latent mineral topics shared across the corpus. The scope here was deliberately modest — a handful of small private mineral datasets (the drill-core sets plus the early HIDSAG subsets), three wordification recipes, one backbone (LDA). The breadth — 19 recipes, four backbones, and six public benchmark scenes — came later, in the [LDA-HSI platform](/portfolio/LDA-HSI/).

## System architecture (2022)

1. **Wordification**: convert each sample's spectra into an LDA corpus. Three recipes were compared — V1 (word = wavelength band, count = summed quantised intensity), V2 (word = quantised intensity level), V3 (joint per-spectrum band intensities). Reflectance quantised to Q levels; topic count chosen by coherence score.
2. **Topic inference**: gensim LDA (collapsed Gibbs) infers a per-sample topic distribution; pyLDAvis for inspection.
3. **Topic-routed regression**: train a separate regressor per topic; for a new sample, infer its topic mixture, run the per-topic regressors, and weight their outputs by the topic distribution — a soft, probabilistic extension of the earlier hierarchical scheme.
4. **Targets**: copper/molybdenum recovery, pH, calcium-carbonate consumption, Bond work index.

## Technology stack

- **Topic modelling**: gensim LDA (Gibbs), pyLDAvis, coherence-score model selection
- **Regression**: per-topic hierarchical regressors (scikit-learn)
- **Data**: VNIR (400–1000 nm) + SWIR (1000–2500 nm) hyperspectral cameras; private drill-core composites with lab geometallurgical targets
- **Funding**: AMTC Basal CONICYT AFB180004 + FONDECYT 3220094

## Where it went next

This conference paper is the origin point. The idea — spectra as documents, topics as structure — was scaled into a full research platform that compares 19 wordification recipes across four topic-model backbones on public benchmarks, with a live web app and API. See **[LDA-HSI](/portfolio/LDA-HSI/)** for the current state.

▶ Conference paper, Procemin Geomet 2022 · the line continues at [lda-hsi.fasl-work.com](https://lda-hsi.fasl-work.com)
