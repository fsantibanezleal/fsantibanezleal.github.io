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

So I built the sweep. Nineteen spectral representations — V1 through V20 — spanning band intensities, wavelet responses, absorption/endmember fractions, learnt codebooks, manifold coordinates, spatial regions, and mutual-information-weighted bands, each scored on a multi-axis evaluation battery (the "F-axis" set) across four topic-model backbones (LDA, HDP, ProdLDA, ETM) and extended across topic counts Q = 8, 16, and 32, on six public labelled scenes with Indian Pines (16 classes) as the headline.

## What the sweep found

Most recipes plateau. You add topics, and past a point the extra topics just split hairs — the same structure at finer granularity, no real gain in how separable the mineral topics are. That's the expected, slightly disappointing behaviour. The interesting result is that the *representation* decides whether scaling helps at all — and that there is no single universal winner, but two clear poles.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Two poles, not one leaderboard:</strong><br/>
<strong>V8</strong> (NFINDR endmembers) is the <em>portable</em> recipe — highest topic–label coupling (F-7 NMI 0.431) averaged across all four backbones, and reliable across reseeds (F-18 ≈ 0.96).<br/>
<span style="color:#5a9ac0;font-size:13px;"><strong>V20</strong> (MI-weighted bands) is the <em>LDA Q-scaling peak</em>: its F-7 NMI climbs 0.520 → 0.534 → 0.563 across Q. At Q=8 it trails V12; the ranking <strong>inverts</strong> and by Q=32 V20 leads V12 by +0.030. Use V8 when the backbone is uncertain; V20 when LDA is fixed and Q ≥ 16 is affordable.</span>
</div>

So the headline isn't "one representation wins" — it's that V8 and V20 occupy two different, defensible corners of the design space, and which one you reach for depends on whether you value portability or peak LDA performance. Mutual-information weighting (V20) front-loads the bands that distinguish minerals, so under LDA the extra topics spend themselves on real structure; endmember fractions (V8) capture physically-meaningful mixtures that survive a change of backbone.

## The honesty beat

There's a detail I want to keep visible, because it's the kind of thing that's easy to bury. An earlier version of this write-up — on the live web app and in my own notes — claimed a cleaner "triple-axis win" for V20, sweeping classification, coherence, and topic–label coupling together. An internal audit knocked two of those down. **F-1 classification is a tie** — every recipe lands within an ~0.86–0.92 band, and on Indian Pines V2 actually edges V20 (V20's F-1 is even slightly label-leakage-contaminated by its own MI weighting). And on **F-2 coherence, V20 ties V12** rather than beating it (+0.0015, inside the noise). So the surviving, true claim is narrow: V20 is the LDA Q-scaling peak on topic–label coupling — not a winner on every axis. A research surface that overclaims is worse than one that's a little behind; the correction is part of the result, not a footnote to hide.

## From a slide to an endpoint

The thing I'm proudest of is mundane: the sweep answers in production. A Q-extension API serves topic counts at Q = 8 / 16 / 32, with a React/Vite frontend over a FastAPI backend, plus a companion manuscript set documenting the methodology in full. The 2022 conference slide became a thing you can click.

There's a manager's lesson hiding in here, the same one I keep relearning: knowing *which knob actually moves the result* — and being honest about which ones don't — is the actual deliverable. A leaderboard with a fake winner is worth less than a map with two honest poles. Live at [lda-hsi.fasl-work.com](https://lda-hsi.fasl-work.com).
