---
title: "Hyperspectral Mineral Analysis by Topic Modelling"
date: 2022-09-01
excerpt: "Treats hyperspectral mineral images as documents and mines them with unsupervised topic models. A design-space sweep over 17 representations finds MI-weighted bands (V20) give the most separable mineral topics. From a 2022 conference paper to a live platform.<br/><img src='/images/projects/hsi_mineral_classification.svg'>"
collection: portfolio
tags: [hyperspectral, topic-modelling, lda, unsupervised, mineralogy, representation-learning]
---

This research line began in 2022 during postdoctoral work — presented as *"Geometallurgical estimation of mineral samples from hyperspectral images and topic modelling"* at the 18th International Conference on Mineral Processing and Geometallurgy — and has since grown into a live interactive platform. It is the **unsupervised counterpart** to the [supervised HSI classification line](/portfolio/HSIMineralClassification/) on the same data.

## The idea

Treat a hyperspectral mineral image as a **document**, its spectral patterns as **vocabulary**, and let unsupervised **topic models** (LDA, ProdLDA, ETM, HDP) discover mineral structure with no labelled training data — which is what makes it transferable across ore bodies and sensors.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The result:</strong><br/>
Across 17 representations (V1–V20) and topic counts Q = 8/16/32, mutual-information-weighted bands (V20) give the most separable mineral topics<br/>
<span style="color:#5a9ac0;font-size:13px;">V20 wins evaluation axes F-2 and F-7 on Indian Pines (396 labelled cells), lowest topic overlap (Jaccard 0.009 at Q=32), and keeps improving as topic count grows where others plateau. (On F-1 it ties — an honest reading after an internal audit.)</span>
</div>

A live **Q-extension API** serves topic counts at Q = 8/16/32, with a React/Vite frontend over a FastAPI backend, plus a companion manuscript.

## Technical stack

Python, FastAPI, scikit-learn, gensim, PyTorch; React/Vite frontend.

▶ Live at [lda-hsi.fasl-work.com](https://lda-hsi.fasl-work.com) · [GitHub](https://github.com/fsantibanezleal/CAOS_LDA_HSI)
