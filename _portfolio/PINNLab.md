---
title: "PINN-Lab — A Runnable Catalogue of Physics-Informed Neural Networks"
date: 2026-06-25
excerpt: "A live catalogue of 19 Physics-Informed Neural Network cases — each trained offline (DeepXDE → ONNX), validated against an analytic, benchmark, or real-data anchor, and re-inferred live in the browser: move a physical parameter and watch the trained network re-solve the PDE.<br/><img src='/images/projects/pinnlab_architecture.svg'>"
collection: portfolio
tags: [scientific-ml, pinn, deepxde, onnx, pde, inverse-problems]
---

A runnable catalogue of **19 Physics-Informed Neural Network cases**. Each is trained offline with DeepXDE/PyTorch, validated against an analytic, benchmark, or real-data anchor, and exported to ONNX — then the static web app loads that ONNX and **re-infers it live in the browser** (onnxruntime-web). Because the physical parameter is a network input, you move a slider and the trained network re-solves the PDE client-side, in real time. Live at [pinnlab.fasl-work.com](https://pinnlab.fasl-work.com).

![PINN-Lab — two worlds joined by an artifact contract](/images/projects/pinnlab_architecture.svg)

## The full method ladder

It is not one forward problem — it exercises the real range of scientific ML: **forward** PDE solving, **inverse** problems (parameter and field recovery), **uncertainty quantification** (Bayesian / ensemble), and **operator learning** (a Fourier Neural Operator generalizing across coefficient fields). Nine SOTA method families appear, each in a per-case workbench with an interactive field heatmap, a live slider, a per-variant error chart, and a bilingual write-up with the governing equations in KaTeX.

## Honest about accuracy and scope

Benchmarks are measured, not curated: ONNX parity is `< 1e-4` everywhere, and relative-L2 is published per case — including the cases that sit at known PINN limits (**Helmholtz ~10%, Navier-cavity ~17%, a soil-barrier case ~19%** from spectral bias and the CPU training lane). PINN-Lab is **not** an FEM/FVM replacement, **not** an industrial digital twin, and **not** trained on real industrial data — only one of the 19 cases (soil heat, NOAA USCRN) uses real measurements; the rest are analytic anchors or synthetic-illustrative reduced models, all labeled as such. It is deliberately a 0.x release while predominantly synthetic.

[Live demo](https://pinnlab.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_PINNLAB)
