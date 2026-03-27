---
title: 'Presentation at Procemin 2022: Topic Modelling for Hyperspectral Geometallurgy'
date: 2022-10-05
permalink: /posts/2022/10/procemin-topic-modelling/
tags:
  - conference
  - geometallurgy
  - topic modelling
  - hyperspectral imaging
---

I presented our work "Geometallurgical Estimation from Hyperspectral Images and Topic Modelling" at the 18th International Conference on Mineral Processing and Geometallurgy (Procemin 2022). Procemin is the premier international conference for mineral processing in Latin America, bringing together researchers and practitioners from across the global mining industry to discuss advances in geometallurgy, comminution, flotation, and process optimization.

An unconventional idea
======

The core idea behind this work is to borrow a technique from natural language processing -- Latent Dirichlet Allocation (LDA) -- and apply it to hyperspectral mineral images. In text analysis, LDA discovers hidden topics that explain collections of documents. The "aha" moment came when I realized that spectral pixels are structurally identical to words in documents. Each pixel is a "document" composed of spectral features ("words"), and the minerals present are the hidden "topics" that explain the observed spectral patterns. Once that analogy clicked, the entire formulation fell into place almost naturally -- the mathematics of topic modelling mapped onto the spectral unmixing problem with surprising elegance.

This reframing is not just a clever analogy -- it opened new possibilities that go well beyond traditional spectral unmixing. It provides a principled, probabilistic way to decompose complex mineral mixtures without requiring prior knowledge of the exact minerals present. The model learns the characteristic spectral patterns directly from the data, grouping pixels into coherent mineral assemblages.

Why this matters for geometallurgy
======

Traditional mineral characterization from hyperspectral data relies on spectral libraries and expert knowledge to identify specific minerals. Our topic modelling approach offers a complementary, data-driven path. It can reveal mineralogical patterns that might be missed by library-matching methods, and it naturally handles mixed pixels where multiple minerals coexist. Where conventional unmixing requires you to specify the endmembers upfront, LDA discovers them from the data itself -- and it does so probabilistically, giving you a distribution over possible mineral compositions rather than a single hard assignment. This means the model can capture gradational contacts and complex mineral assemblages that rigid library-matching approaches struggle with.

Presenting this at Procemin was a great experience. The mineral processing community is pragmatic and demanding -- they want methods that work on real ores. The questions and feedback from the audience were sharp and constructive, and they helped refine the direction of the research going forward. It was encouraging to see genuine interest in this cross-disciplinary approach.
