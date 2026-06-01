---
title: "Auralis — 6D Audio Embedding Visualizer"
date: 2026-04-24
excerpt: "Maps any sound onto seven embedding tracks and renders it as a navigable 3D trajectory across a library of 102 curated sounds.<br/><img src='/images/500x300.png'>"
collection: portfolio
tags: [audio, embeddings, visualization, threejs, clap, yamnet, fastapi]
---

**Auralis** turns a sound into a place you can fly through. Each clip is analyzed into a six-dimensional embedding space and rendered as a luminous 3D trajectory, with ten render modes and a curated library of 102 sounds (space, nature, music, human-made).

## The idea

Spectrograms show the signal but not its structure or meaning. Auralis instead projects seven different representations of the same sound into one navigable 6D space — so you can see what each representation "hears" and compare them directly.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Seven embedding tracks:</strong><br/>
Features (interpretable spectral) · PCA / t-SNE / UMAP (projections of MFCC frames) · Tonnetz (harmonic space) · YAMNet (1024-D AudioSet events) · CLAP (512-D audio-text semantics)<br/>
<span style="color:#5a9ac0;font-size:13px;">All min-max normalized so any feature can drive any axis (X/Y/Z + color + size, time as the implicit 6th). CLAP is precomputed offline so the deployed app stays light.</span>
</div>

Ten render modes (Comet, Tube, Galaxy, Light-painting, Aurora, …), 102 curated clips with verified per-clip licensing, shareable URL state, bilingual UI.

## Technical stack

Backend: Python, FastAPI; offline pipeline with librosa, scikit-learn/UMAP, TensorFlow/YAMNet, CLAP. Frontend: TypeScript, React, Vite, Three.js (@react-three/fiber), Web Audio API.

▶ Live at [auralis.fasl-work.com](https://auralis.fasl-work.com) · [GitHub](https://github.com/fsantibanezleal/CAOS_6D_Sounds)
