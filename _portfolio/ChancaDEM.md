---
title: "ChancaDEM, Crusher-Comminution Studio (Population-Balance Engine)"
date: 2026-07-09
excerpt: "An in-browser crusher-comminution studio: you set the machine, closed-side setting, eccentric throw and speed and the feed gradation, and a pure-TypeScript closed-form engine (Whiten population balance + Evertsson capacity + Bond power) computes the product gradation, throughput and power in sub-millisecond. Despite the name it does NOT run DEM: the 3D chamber is a kinematic animation. The secondary-cone lane is calibrated against 10 published HP500 surveys (Rocha et al. 2024), with a leave-one-out cross-validation that includes negative controls.<br/><img src='/images/projects/chancadem_app.png'>"
collection: portfolio
tags: [mining-optimization, comminution, crushing, population-balance, whiten, evertsson, bond, cone-crusher, onnx, mining]
---

ChancaDEM is an in-browser **crusher-comminution studio**. You set the machine, closed-side setting, eccentric throw and speed and the feed gradation, and a pure-TypeScript closed-form engine computes the product gradation, throughput and power in sub-millisecond. Despite the name it does **not** run DEM: the 3D chamber is a kinematic animation, the offline 2-D DEM tracer is unwired and unbaked, and the app says so on its Introduction page. Live at [chancadem.fasl-work.com](https://chancadem.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) mining-analytics hub.

![ChancaDEM: a Whiten population balance solved live by LU, plus Evertsson capacity and Bond power, in the browser](/images/projects/chancadem_app.png)

## The model chain

A Whiten classification-breakage population balance solved live by LU over a 28-class root-2 sieve grid, a JKMRC t10 energy-fineness law (Narayanan and Whiten 1988), an Austin, Klimpel and Luckie 1984 appearance function, an Evertsson reduced-form flow capacity with its unimodal speed hump, and Bond 1952 power, plus nip-angle geometry and regime detection. Two ONNX models run in-browser: an MLP surrogate that emulates the engine, and a denoising autoencoder over the product-gradation signature that acts as a surrogate-extrapolation guard, not a plant anomaly detector, since it is trained on the engine's own sweep.

## The data, stated plainly

Only the secondary cone has a calibrated lane. It is fitted to 10 published HP500 surveys of a Metso HP500 secondary cone at Minas Rio (Anglo American), crushing itabirite iron ore, transcribed from Rocha et al., Minerals 2024 (DOI 10.3390/min14090919, CC BY), not from any campaign of the author. Jaw, gyratory, tertiary and short-head use illustrative constants that reproduce the correct trends, not any plant absolute numbers.

## The honest limit

The rigor is in a leave-one-out ridge cross-validation over the 10 real surveys, with negative controls. Strict LOO throughput MAPE 12.09 percent beats both a constant-mean control (18.29 percent) and a label-shuffle control (25.04 percent), a real if modest signal on n=10, and the repo also stores the leaky non-LOO block to show the optimism gap. The ONNX surrogate emulates the engine at R-squared 0.995 (P80) and 0.998 (throughput): that is fidelity to the engine, never accuracy against a plant. It is a cheap closed-form model, not a particle simulation or a plant twin.

[Live demo](https://chancadem.fasl-work.com) · [Source on GitHub](https://github.com/fsantibanezleal/CAOS_ChancaDEM)
