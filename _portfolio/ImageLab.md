---
title: "ImageLab, One Image Across Eleven Mathematical Representations"
date: 2026-07-18
excerpt: "An interactive lab that writes one image across eleven mathematical representations, orthonormal transforms (Fourier/DCT/wavelet/KLT), overcomplete sparse dictionaries, geometric primitives, an implicit neural field (SIREN), symbolic CPPN formula art, Fourier-descriptor epicycles, and learned generative latents (VAE, diffusion), and lets you edit each one's parameters to see when a perturbation stays meaningful and when it collapses into noise. Computed live in WebGL2 or baked by a seed-deterministic Python pipeline.<br/><img src='/images/projects/imglab_app.png'>"
collection: portfolio
tags: [scientific-ml, image-representation, signal-processing, fourier, wavelet, generative-models, webgl, benchmark]
---

An interactive lab that represents **a single image in eleven ways** and lets you edit each representation's parameters directly. It spans the full arc from designed orthonormal transforms to learned generative manifolds, so you can read one representation against another on the same image. Live at [imglab.fasl-work.com](https://imglab.fasl-work.com).

![ImageLab, one image across eleven representations, from orthonormal transforms to learned generative latents](/images/projects/imglab_app.png)

## The eleven representations

Four orthonormal transforms (Fourier, DCT, wavelet, KLT), overcomplete **sparse dictionaries**, **geometric primitives**, an **implicit neural field** (SIREN), symbolic **CPPN** formula art, **Fourier-descriptor epicycles**, and two **learned generative latents** (a VAE and a diffusion model). Each is a tab with live parameter controls, the governing math in KaTeX, and a bilingual (EN/ES) write-up. Everything is either computed live in the browser (TypeScript + WebGL2 shaders) or baked offline by an open, seed-deterministic Python pipeline (numpy, scipy, PyWavelets, scikit-image, scikit-learn, PyTorch, diffusers).

## The organizing thesis, editability is U-shaped

Measured on the Experiments and Benchmark pages: editability peaks at the **designed-structure pole** (local, exact edits) and again at the **learned-manifold pole** (semantic, entangled edits), and collapses to noise between them. The cross-family benchmark makes this concrete, an editability-locality metric where **KLT and wavelet score ~1.0** (local, exact edits) against **Fourier and DCT at ~0.16-0.23** (global, entangled edits), alongside a rate-distortion curve and a fixed-budget fidelity table.

## Shared, honest measurement

PSNR / SSIM / MS-SSIM are computed the same way in Python and in TypeScript, so the browser numbers match the offline bake. Bilingual EN/ES, light/dark, static GitHub Pages deploy. It is a CAOS Research-group lab (educational and research, not a commercial product) a sibling of [PINN-Lab](https://pinnlab.fasl-work.com), [QLab](https://qlab.fasl-work.com), [ChronoScope](https://chronoscope.fasl-work.com) and [SimLab](https://simlab.fasl-work.com).

[Live demo](https://imglab.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_IMGLAB)
