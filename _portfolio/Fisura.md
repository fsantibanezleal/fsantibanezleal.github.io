---
title: "Fisura, Materials-Damage Vision Lab (Crack Detection to Engineering Units)"
date: 2026-07-26
excerpt: "A public research lab on seeing damage in built materials: one image of a concrete wall, pavement or facade goes in, and Fisura detects the damage, quantifies it in engineering units (width, length, orientation, density, growth between inspections), and compares every method family (classical, learned SOTA, foundation models, anomaly detection) on the same open cases with the same metrics. Masks are only ever the input to a number.<br/><img src='/images/projects/fisura_app.png'>"
collection: portfolio
tags: [computer-vision, crack-detection, materials, segmentation, foundation-models, measurement]
---

A public research lab on **seeing damage in built materials**. One image of a concrete wall, a pavement, a masonry facade or an industrial surface goes in; Fisura detects the damage, **quantifies it in engineering units** (width, length, orientation, density, growth between inspection epochs), and shows how every method family gets there. Live at [fisura.fasl-work.com](https://fisura.fasl-work.com).

![Fisura, one image runs a classical-to-foundation method ladder, then measurement turns masks into engineering numbers](/images/projects/fisura_app.png)

## Masks are never the deliverable

Computer-vision papers stop at a segmentation mask and a benchmark score. An inspector needs a **number in millimetres** with a stated method. So the measurement layer turns masks into pixel-to-mm calibrated crack width and length, orientation, density, change detection across epochs, and vision-based deformation via 2D digital image correlation.

## The whole ladder, honestly compared

Classical pipelines (illumination correction, Hessian ridge filters, morphological path operators, skeleton geometry), learned SOTA (encoder-decoder and transformer segmentation), beyond-SOTA (promptable foundation models, unsupervised anomaly detection), all on the **same open cases with the same metrics**, with accuracy and measurement reported separately. It runs an offline heavy lane plus a browser live lane where **the photo never leaves the device**. Honest scope: a method-comparison research lab, not a certified inspection tool, dataset-honest (full open data lives outside the repo), and under active build-out one vertical slice at a time.
