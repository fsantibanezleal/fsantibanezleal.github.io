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

I presented our work "Geometallurgical Estimation from Hyperspectral Images and Topic Modelling" at the 18th International Conference on Mineral Processing and Geometallurgy (Procemin 2022).

An unconventional idea
======

The core idea behind this work is to borrow a technique from natural language processing -- Latent Dirichlet Allocation (LDA) -- and apply it to hyperspectral mineral images. In text analysis, LDA discovers hidden topics that explain collections of documents. Our insight was to treat hyperspectral pixels as "documents" and spectral features as "words," letting the algorithm discover latent mineral assemblages as "topics."

This reframing is not just a clever analogy. It provides a principled, probabilistic way to decompose complex mineral mixtures without requiring prior knowledge of the exact minerals present. The model learns the characteristic spectral patterns directly from the data, grouping pixels into coherent mineral assemblages.

Why this matters for geometallurgy
======

Traditional mineral characterization from hyperspectral data relies on spectral libraries and expert knowledge to identify specific minerals. Our topic modelling approach offers a complementary, data-driven path. It can reveal mineralogical patterns that might be missed by library-matching methods, and it naturally handles mixed pixels where multiple minerals coexist.

Presenting this at Procemin was a great experience. The mineral processing community is pragmatic and demanding -- they want methods that work on real ores. The questions and feedback from the audience were sharp and constructive, and they helped refine the direction of the research going forward. It was encouraging to see genuine interest in this cross-disciplinary approach.
