---
title: "FrothSeg — Flotation-Froth Instance Segmentation Lab (Browser ML)"
date: 2026-07-16
excerpt: "A browser-native lab for instance segmentation of flotation froth: it delineates individual bubbles client-side via ONNX and compares seven classical methods against a real published model (LamellaStar, a three-seed ensemble with SAM2 / Cellpose-SAM teachers). The honest core is the data situation, stated openly: no real froth images exist publicly, so froth cases are synthetic and BBBC038 is an adjacent-domain transfer probe that does not clear the froth blocker.<br/><img src='/images/projects/frothseg_app.png'>"
collection: portfolio
tags: [computer-vision, instance-segmentation, flotation, froth, onnx, ensemble, negative-results]
---

A browser-native lab for **instance segmentation of flotation froth**: delineating individual bubbles in a froth image, entirely client-side via ONNX. Live at [frothseg.fasl-work.com](https://frothseg.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) hub.

![FrothSeg — seven classical methods vs a learned LamellaStar ensemble, with an honest real-transfer probe](/images/projects/frothseg_app.png)

## A real model, and a real classical ladder

Two tiers on the same cases: **seven classical** delineators (watershed and related morphology), and **LamellaStar**, a genuine four-head research model shipped as a three-seed logit-mean ensemble (top config N1: mean AP 0.5186, AP50 0.8279, panoptic quality 0.7359), with **SAM2 and Cellpose-SAM** as offline teachers (checkpoints checksum-recorded) distilled to a compact mask head for the browser.

## The honest core: the data does not exist, and it says so

The field's real blocker is that **there is no public labelled real froth dataset**. FrothSeg states this openly, records the data search as a null (Roboflow dropped), keeps the froth cases synthetic and labelled as such, and adopts **BBBC038** (64 real dense-touching images, CC0) as an adjacent-domain transfer probe, explicitly noting that an adjacent real domain **does not clear the froth blocker**. The transfer study even refuted its own hypothesis: the synthetic froth ranking is generator-specific and the model drops on real transfer. That published null, not a flattering synthetic score, is the deliverable. A research lab, not a plant tool.
