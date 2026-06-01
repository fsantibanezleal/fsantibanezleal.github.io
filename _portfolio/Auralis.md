---
title: "Auralis — 6D Audio Embedding Visualizer"
date: 2026-04-24
excerpt: "Turns any sound into a navigable six-dimensional universe — seven embedding tracks, ten render modes, 102 curated clips — making abstract audio-ML representations tangible.<br/><img src='/images/projects/auralis_embedding_space.svg'>"
collection: portfolio
tags: [audio, embeddings, visualization, threejs, clap, yamnet, fastapi]
---

A **browser-based audio visualization platform** that maps any sound onto seven different machine-learning embedding spaces and renders it as a luminous, navigable 3D trajectory. Auralis exists to answer a question that is normally invisible: *how does a model actually "hear" a sound, and how do different representations disagree about it?*

## Business impact

Audio embeddings quietly power search, recommendation, classification, and generative audio — but they are abstract high-dimensional vectors that no stakeholder can inspect. Auralis turns that black box into something you can see, compare, and reason about. By projecting seven representations of the same clip into one shared 6D space, it becomes both an **analytical instrument** (which representation separates these sounds? where does a model confuse them?) and a **communication tool** (showing a non-specialist what "semantic audio similarity" means, live, in a browser tab).

| Metric | Result |
|--------|--------|
| Embedding tracks | 7 (Features, PCA, t-SNE, UMAP, Tonnetz, YAMNet, CLAP) |
| Render modes | 10 (Comet, Tube, Galaxy, Aurora, Light-painting, …) |
| Curated library | 102 licensed clips (space, nature, music, human-made) |
| Deployment | Live, browser-only; heavy CLAP runtime precomputed offline |

## Strategic context

Most audio tools stop at the spectrogram — useful to an engineer, opaque to everyone else — and the embedding spaces inside modern audio models are never shown at all. Auralis closes that gap. It is the difference between *telling* someone that CLAP groups "the sound of rain" near actual rain and *showing* them the two clips landing in the same region of space while their raw spectra look nothing alike. As a portfolio piece it demonstrates fluency across the full stack of audio intelligence — classical DSP, deep audio models, dimensionality reduction, and real-time 3D rendering — fused into one coherent product rather than a notebook.

![6D embedding architecture](/images/projects/auralis_embedding_space.svg)

## Key Performance Indicators — what it surfaces

The value is in making representation differences legible and comparable, not in a single accuracy number.

| KPI | Baseline (typical audio tooling) | With Auralis | Impact |
|-----|----------------------------------|--------------|--------|
| Representation visibility | One spectrogram view | 7 embedding tracks, switchable | Compare what each model "hears" of the same sound |
| Exploration | Flat 2D waveform / spectrogram | Navigable 6D trajectory (XYZ + color + size + time) | Sound becomes a space, not a signal |
| Semantic grouping | Not exposed | CLAP audio-text track clusters by meaning | Semantically similar sounds group even when spectra differ |
| Accessibility of ML | Notebook + NumPy arrays | Interactive browser app with shareable URLs | A non-specialist can explore embeddings directly |
| Reproducibility | Ad-hoc per analysis | Persisted per-track projection models | Every clip maps into the same, comparable space |

## The challenge

A sound is a time series; an embedding is a high-dimensional vector per frame; a screen is two-dimensional. Bridging all three in real time is the core problem. Each clip is analyzed into **seven embedding tracks** — interpretable spectral Features, PCA/t-SNE/UMAP projections of MFCC frames (one linear, two manifold methods), the Tonnetz harmonic space, YAMNet's 1024-D AudioSet event embeddings, and CLAP's 512-D contrastive audio-text embeddings — and every track is min-max normalized to a common 6D so that *any* feature can drive *any* visual axis. The CLAP model is heavy (a full torch/transformers stack), so its embeddings are computed offline and the production app ships only the precomputed vectors, keeping the deployed surface light enough to run entirely in the browser.

## System architecture

1. **Offline analysis pipeline**: librosa extracts spectral features and MFCCs per frame; scikit-learn and UMAP fit the corpus-wide PCA / t-SNE / UMAP projections; TensorFlow/YAMNet and CLAP produce the deep embeddings. Per-track projection models are persisted so every clip maps into a consistent, comparable space.
2. **6D → visual mapping**: spatial position (X, Y, Z) plus color (4th dimension), point size (5th), and time as the implicit 6th axis — past frames fade into a trail, so the *shape* of the trajectory itself encodes the structure of the sound.
3. **Real-time renderer**: a React + Three.js (`@react-three/fiber`) frontend draws the trajectory in ten render modes, synchronized to Web Audio API playback; full panel state (clip, track, axis mapping, render mode) round-trips through the URL hash for shareable views.
4. **Serving layer**: a FastAPI backend serves the precomputed per-clip JSON and the audio assets; the SPA is static and CDN-friendly.

## Technology stack

- **Backend / pipeline**: Python, FastAPI, librosa, scikit-learn, UMAP, TensorFlow (YAMNet), CLAP (offline)
- **Frontend**: TypeScript, React, Vite, Three.js / @react-three/fiber, Zustand, Web Audio API
- **Representations**: spectral DSP, MFCC, Tonnetz, PCA / t-SNE / UMAP, deep audio embeddings (YAMNet, CLAP)
- **Deployment**: systemd + nginx on a Hetzner VPS; CLAP embeddings precomputed so production stays light

## Live application

▶ **[Live demo — auralis.fasl-work.com](https://auralis.fasl-work.com)** — pick a clip, choose an embedding track, and fly through its 6D trajectory.

[View on GitHub](https://github.com/fsantibanezleal/CAOS_6D_Sounds)
