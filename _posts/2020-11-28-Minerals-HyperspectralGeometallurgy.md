---
title: 'Publication in Minerals: Hyperspectral Analysis for Geometallurgy'
date: 2020-11-28
permalink: /posts/2020/11/minerals-hyperspectral-geometallurgy/
tags:
  - publication
  - hyperspectral imaging
  - geometallurgy
  - mineral characterization
---

Our paper "A Robust Stochastic Approach to Mineral Hyperspectral Analysis for Geometallurgy" has been published in Minerals. [Read the paper](https://www.mdpi.com/2075-163X/10/12/1139).

Collaborative work at the intersection of imaging and mining
======

This paper was born from a collaboration with Alvaro Egana's team at ALGES (Advanced Laboratory for Geostatistical Supercomputing), bringing together expertise in hyperspectral imaging and geostatistical modelling. Working with Alvaro's group was a formative experience -- they had been pushing the boundaries of hyperspectral mineral characterization for years, and joining forces meant access to both cutting-edge imaging equipment and deep domain knowledge. The challenge we addressed is fundamental to geometallurgy: how to reliably characterize mineral composition from hyperspectral data, accounting for the inherent uncertainty in both the measurements and the mineralogical interpretation.

A significant part of the work involved spending long hours in the lab with SWIR and VNIR cameras, acquiring spectral data from mineral samples under varying conditions. One of the persistent headaches was the sensitivity of spectra to ambient conditions -- temperature, humidity, and illumination angle all introduce variability that can mask the very mineralogical signals you are trying to detect. This practical reality motivated the stochastic approach: if the measurement conditions themselves are noisy, your analysis framework must acknowledge and handle that noise explicitly.

Our approach introduces a stochastic formulation for mineral hyperspectral analysis. Rather than producing a single deterministic estimate of mineral abundance, we explicitly model the uncertainty through a probabilistic framework. This is paired with a hierarchical regression scheme that handles the complex, nested structure of spectral-to-mineral relationships.

![SOFI pipeline (spectral processing analogy)](/images/rollings/sofi_pipeline.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Hierarchical regression:</strong><br/>
y = f(spectrum) + random_effects(ambient) + ε — separating signal from environmental noise
</div>

Why stochastic matters
======

Deterministic approaches to mineral identification from hyperspectral images tend to be brittle -- they give you a single answer with no indication of how confident you should be in it. The stochastic formulation we developed handles the variability that deterministic approaches simply cannot: spectral overlap between minerals, mixed pixels at grain boundaries, and the measurement noise introduced by ambient conditions all get folded into the probabilistic model rather than being swept under the rug. In a mining context, where decisions about processing routes and ore blending depend on accurate mineralogical information, understanding the uncertainty is just as important as the estimate itself.

The hierarchical regression scheme allows the model to capture relationships at multiple scales, from broad spectral features down to subtle absorption bands that differentiate closely related minerals. This was technically challenging work, but the result is a more robust and honest characterization of mineral composition. I am grateful to the team for pushing this work forward -- it opened doors to problems I continue to work on today.
