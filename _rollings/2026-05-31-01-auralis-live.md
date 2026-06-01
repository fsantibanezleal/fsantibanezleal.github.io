---
title: 'Hearing Sound as a 6D Space'
date: 2026-05-31
permalink: /rollings/2026/05/auralis-live/
tags:
  - Auralis
  - Audio
  - Embeddings
  - Visualization
---

Hearing Sound as a 6D Space
======

I have spent a lot of my career looking at high-dimensional data and wishing I could just *see* it. Audio embeddings are the worst offenders: a model listens to a sound and emits a vector of hundreds of numbers that supposedly captures what the sound "is", and there is no honest way to inspect that vector. You trust it, or you don't. Auralis is my attempt to stop trusting blindly — it turns any sound into a luminous trajectory you can fly through in three dimensions, and it's now live in the browser.

The core idea is that a sound doesn't have *one* representation, it has many, and they disagree in interesting ways. So Auralis computes seven of them per clip and lets you switch between them live. Each one is a different answer to the question "where does this sound sit?"

![Auralis — seven embedding tracks rendered as a 6D trajectory](/images/projects/auralis_embedding_space.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Seven embedding tracks, one shared 6D space:</strong><br/>
Features (interpretable spectral) · PCA · t-SNE · UMAP (three projections of MFCC frames) · Tonnetz (harmonic) · YAMNet (1024-D AudioSet events) · CLAP (512-D audio-text semantics)<br/>
<span style="color:#5a9ac0;font-size:13px;">All min-max normalized so any feature can drive any axis: position X/Y/Z, color (4D), point size (5D), and time as the implicit 6th — past frames fade into a trail, so the <em>shape</em> of the path is the structure of the sound.</span>
</div>

The track I keep coming back to is CLAP, a contrastive language-audio model. Where the spectral features describe *how* a sound is built and YAMNet labels *what kind of event* it is, CLAP captures something closer to *meaning* — it was trained to line up "the sound of rain" with actual rain. Pick that track and the NOAA underwater recordings drift away from the spacecraft telemetry in a way the raw spectra never manage, because two clips that *mean* similar things land near each other even when their frequency content looks nothing alike.

I want to be precise about what's actually deployed, because it would be easy to oversell this. CLAP can in principle do text-to-audio search — type a phrase, get the nearest sounds — and that part is **not** live: the model runtime is a heavy torch/transformers stack and I parked the text endpoint until I decide where to host it. What ships is the embedding *track*: all 102 clips already have their CLAP coordinates computed offline and PCA-projected, so the visualization is real and the deployed app stays light enough to run entirely in a browser tab.

The library is half the fun — 102 curated, individually-licensed clips spanning NASA space audio (Perseverance, the Voyager Golden Record, Cassini, Apollo), a NOAA underwater set, birds, machines, music. Ten render modes (Comet, Tube, Galaxy, Aurora, Light-painting…), and every view round-trips through the URL so you can paste a link and someone sees the exact same trajectory. Live at [auralis.fasl-work.com](https://auralis.fasl-work.com) · [GitHub](https://github.com/fsantibanezleal/CAOS_6D_Sounds).
