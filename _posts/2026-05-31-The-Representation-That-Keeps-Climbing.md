---
title: 'The representation that keeps climbing — topic modelling on hyperspectral minerals'
date: 2026-05-31
permalink: /posts/2026/05/representation-that-keeps-climbing/
tags:
  - hyperspectral
  - topic-modelling
  - representation-learning
  - mineralogy
  - research
---

The representation that keeps climbing
======

In 2022, during my postdoc, I presented a small idea at the 18th International Conference on Mineral Processing and Geometallurgy: *what if you treat a hyperspectral mineral image like a document?* Each pixel or region is a document, recurring spectral patterns are the vocabulary, and an unsupervised topic model — LDA and its descendants — discovers mineral "topics" with no labelled training data. No lab assays, no ground-truth masks. That property, label-free, is the whole point: it's what lets the method travel to a new ore body or a new sensor without retraining on someone's hand-drawn polygons.

Three years later that idea is a live platform. But the result I actually care about isn't the platform — it's an answer to a question the 2022 paper only gestured at.

## The question nobody asks out loud

A topic model is only as good as what you feed it. Everyone tunes the model — LDA vs ProdLDA vs ETM, how many topics, which priors. Almost nobody systematically asks the upstream question: *which representation of the spectrum should the topic model even see?* Raw bands? A wavelet transform? A learned dictionary? A UMAP embedding? Each one reshapes what "co-occurrence" means before the model ever runs.

So I built the sweep. Seventeen spectral representations — V1 through V20, including continuous-wavelet (CWT-Morlet), sparse-dictionary coding, UMAP embeddings, VQ-VAE codes, graph-Laplacian features, and mutual-information-weighted bands — each scored on an evaluation battery (the "F-axis" set) and extended across topic counts Q = 8, 16, and 32. The benchmark is Indian Pines, the standard labelled hyperspectral scene (396 labelled cells once you clean it up).

## What the sweep found

Most representations plateau. You add topics, and past a point the extra topics just split hairs — the same structure at finer granularity, no real gain in how separable the mineral topics are. That's the expected, slightly disappointing behaviour.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">V20 — mutual-information-weighted bands — is the one that doesn't plateau.</strong><br/>
It wins evaluation axes F-2 and F-7 on Indian Pines, with the lowest topic overlap in the whole sweep (Jaccard 0.009 at Q=32)<br/>
<span style="color:#5a9ac0;font-size:13px;">And it keeps improving as the topic count grows, exactly where the others give up. MI weighting front-loads the bands that actually carry mineral-discriminative signal — so the extra topics have somewhere useful to go instead of fragmenting noise.</span>
</div>

That's the headline: one representation gets *more* separable precisely where everything else saturates. The interpretation is honest and not over-claimed — mutual-information weighting emphasizes the bands that distinguish minerals, so as you grant the model more topics, it spends them on real structure rather than on slicing noise more finely.

## The honesty beat

There's a detail I want to keep visible, because it's the kind of thing that's easy to bury. An earlier version of this write-up — on the live web app and in the internal notes — claimed a cleaner "triple-axis win." An internal audit caught that on one of the axes (F-1) V20 doesn't win, it **ties**. So the claim is now "wins F-2 and F-7, ties F-1," not "wins everything." A research surface that overclaims is worse than one that's a little behind; the correction is part of the result, not a footnote to hide.

## From a slide to an endpoint

The thing I'm proudest of is mundane: the sweep answers in production. A Q-extension API serves topic counts at Q = 8 / 16 / 32, with a React/Vite frontend over a FastAPI backend, plus a companion manuscript documenting the methodology in full. The 2022 conference slide became a thing you can click.

There's a manager's lesson hiding in here, the same one I keep relearning: knowing *when more model stops helping* is the actual deliverable. Ten representations that saturate are worth less than one that scales. Live at [lda-hsi.fasl-work.com](https://lda-hsi.fasl-work.com).
