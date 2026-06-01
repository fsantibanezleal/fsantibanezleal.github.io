---
title: "LDA-HSI — Wordification Design-Space Platform"
date: 2026-05-15
excerpt: "A research platform that asks which representation a hyperspectral topic model should see: 19 wordification recipes × 4 topic-model backbones × Q∈{8,16,32}, scored on a 12-axis battery, with a live web app and API.<br/><img src='/images/projects/lda_hsi_platform.svg'>"
collection: portfolio
tags: [hyperspectral, topic-modelling, representation-learning, lda, etm, fastapi, react]
---

The current state of the hyperspectral topic-modelling line that began as a [2022 conference paper](/portfolio/HyperspectralTopicModelling/). **LDA-HSI** is a local-first research and validation platform that treats spectral variability as a *corpus* — pixel spectra become documents of quantised spectral tokens — and then asks the question the original paper only gestured at: **which "wordification" should a topic model actually see, and does that choice change the conclusions?** The offline experiments are the product; the public web app is a validated projection of their outputs.

## Business impact

In hyperspectral analysis almost all of the methodological attention goes to the *model* and almost none to the *representation* fed into it. LDA-HSI is built to show that the representation is not a detail — it can flip which method "wins". By systematically sweeping **19 wordification recipes across four topic-model backbones** and scoring every combination on a multi-axis battery, the platform turns an unexamined modelling assumption into a measured design space, and produces a defensible, reproducible recommendation: which recipe to use when reproducibility matters, and which when you can afford to scale topic count under a fixed backbone.

| Metric | Baseline | With platform |
|--------|----------|---------------|
| Wordification recipes compared | 1 (the field default) | **19** (V1–V15, V17–V20) |
| Topic-model backbones swept | 1 (LDA) | **4** (LDA, HDP, ProdLDA, ETM) |
| Evaluation axes | accuracy only | **12-axis battery** + extended F-axes |
| Benchmark scenes | ad-hoc | **6** public labelled scenes + HIDSAG mineral subsets |
| Reproducible artefacts | — | **~1726** committed JSON/figures; live API smoke 133/133 |

## Strategic context

The honest, defensible headline is not a single accuracy record — it is a *finding about methodology*: the wordification choice materially changes the conclusions, and there is no universal winner. The platform identifies **two poles and a non-discriminating axis**, which is a more useful result for a practitioner than a leaderboard. It also demonstrates engineering maturity: a fully reproducible offline experiment grid (100% populated at the base setting), a hierarchical-Bayesian dominance test per axis rather than cherry-picked wins, and a public surface that never claims more than the artefacts support — including walking back an earlier over-claim once an internal audit caught it.

![LDA-HSI design-space sweep and evaluation battery](/images/projects/lda_hsi_platform.svg)

## Key Performance Indicators — the two-pole verdict

Numbers below are the audited ground truth (tie threshold |Δ| < 0.005); they deliberately avoid the retired over-claims.

| Finding | Recipe | Result | When to use it |
|---------|--------|--------|----------------|
| Portability / reproducibility leader | **V8** (NFINDR endmembers) | Highest cross-backbone F-7 NMI **0.431** (+0.034 over rank 2); reseed reliability F-18 **≈0.96**, stable across Q | When the backbone is uncertain or reproducibility matters |
| LDA Q-scaling peak | **V20** (MI-weighted bands) | F-7 NMI climbs to **0.563 @ Q=32**; *trails* V12 at Q=8, then **the ranking inverts** and V20 leads V12 by +0.030 at Q=32 (5/6 scenes) | When LDA is fixed and Q ≥ 16 is affordable |
| Backbone specialist | **V11** (product quantisation) | Wins HDP (0.571) and ETM (0.530) outright, collapses under LDA/ProdLDA | When the backbone is fixed to HDP or ETM |
| Non-discriminating axis | — | **F-1 macro-F1 is a tie** (~0.86–0.92 across recipes); no recipe headlines an accuracy win | Don't pick a recipe on accuracy alone |

## The challenge

Comparing representations fairly is harder than comparing models. Each of the 19 recipes maps a pixel spectrum to a different doc-term vocabulary — band intensities, wavelet responses, absorption/endmember fractions, learnt codebooks, manifold coordinates, spatial regions, label-aware MI weights — and they have to be evaluated on the *same* footing across four very different topic-model families (a Gibbs LDA, a nonparametric HDP, and two neural variants, ProdLDA and ETM) and three quantisation levels. The platform handles this with a single offline grid (the Q=8 base is 1140 cells, 100% populated) plus a Q=16/32 spot-check, and a battery of axes — coherence, topic–label mutual information, seed stability, reliability, diversity, counterfactual robustness, cross-scene transfer, spatial coherence, endmember and LLM-judge baselines — each adjudicated by a hierarchical-Bayesian dominance test rather than a single run.

## Datasets covered

Where the 2022 work used a few small private mineral sets, the platform spans a deliberately broad data surface so a representation's win has to hold across very different sensors and scene types — Indian Pines is just the *headline* scene, not the benchmark:

- **6 public labelled scenes** (the V-sweep panel): Indian Pines (AVIRIS, 16 classes — headline), Salinas, Salinas-A, Pavia University (ROSIS), Kennedy Space Center, Botswana (EO-1 Hyperion).
- **Public spectral libraries**: USGS splib07 (~2450 spectra), ECOSTRESS.
- **Unmixing benchmarks** (Borsoi): Samson, Jasper Ridge, Urban.
- **HIDSAG** mineral subsets (GEOMET, MINERAL1/2, GEOCHEM, PORPHYRY) — the bridge back to the geometallurgy origin and the 2022 work.
- **MicaSense MSI** field samples (RedEdge-3 + Altum).

## System architecture

1. **Input**: the multi-family data surface above — six public labelled HSI scenes (Indian Pines the headline, not the only one), public spectral libraries, unmixing benchmarks, the HIDSAG mineral subsets, and MSI field data.
2. **Wordification (design-space fan-out)**: 19 recipes (V1..V20, V16 reserved) in 7 families convert spectra to doc-term counts, with a Q ∈ {8, 16, 32} quantisation knob.
3. **Topic-model backbones (4-way branch)**: LDA (gensim), HDP (tomotopy), ProdLDA and ETM (Pyro), with GPU deep baselines (CAE-1D/2D/3D, β-VAE, PCA/NMF/ICA-K) for fair K-dim comparison.
4. **Evaluation battery (fan-in)**: a 12-axis battery (classification, coherence, topic–label NMI, seed stability, reliability, diversity, counterfactual robustness, cross-scene transfer, spatial coherence, endmember baseline, LLM-judge) with per-axis Bayesian dominance.
5. **Surfaces**: a React/Vite web app (28-tab interactive workspace + benchmarks), a public Q-extension API, the P3/P4/P5 preprints, and ~1726 committed reproducible artefacts.

## Technology stack

- **Data pipeline**: NumPy/SciPy/scikit-learn; gensim + tomotopy (LDA/HDP/CTM/DMR); PyTorch + Pyro (ProdLDA/ETM/VAE); pysptools (NFINDR/ATGP/SAM unmixing); PyWavelets, nanopq, umap-learn, SHAP, Optuna; spectral/rasterio/h5py for HSI I/O
- **Backend**: FastAPI + uvicorn, ORJSON + GZip; stateless, read-only, serves committed JSON
- **Frontend**: React 19 + Vite 6 + TypeScript, Three.js / @react-three/fiber (3D embedding views), KaTeX, TanStack Query, XState, bilingual EN/ES
- **Deployment**: Hetzner VPS, nginx + systemd; ships continuously behind 133/133 API smoke checks

## Live application

▶ **[Live demo — lda-hsi.fasl-work.com](https://lda-hsi.fasl-work.com)** — explore the recipes, backbones, and the full evaluation battery in an interactive workspace.

[View on GitHub](https://github.com/fsantibanezleal/CAOS_LDA_HSI) · companion manuscripts (P3 nineteen-recipe sweep, P4 backbone factorial, P5 interpretability) in preparation.
