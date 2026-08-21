---
title: "FragmentIQ, Post-Blast Muckpile Fragmentation Analysis Workbench"
date: 2026-07-07
excerpt: "A post-blast fragmentation workbench that delineates muckpile fragments by watershed in the browser and derives a mass-weighted particle-size distribution with a Rosin-Rammler fit and P10/P50/P80. It is scored against generator truth on synthetic muckpiles, with a real-photo lane of 5 CC BY images from an Iranian iron-ore mine where every number is explicitly RELATIVE, because no sieve ground truth exists, the scale is unknown, and n is small. Honest by design: the over-segmentation bias is shown directly in the artifact (116 recovered vs 70 true fragments), and the learned refinement gain is reported as indicative, not significant, on n=8.<br/><img src='/images/projects/fragmentiq_app.png'>"
collection: portfolio
tags: [mining-analytics, fragmentation, muckpile, watershed, particle-size, rosin-rammler, computer-vision, onnx, blasting, mining]
---

FragmentIQ is a post-blast **fragmentation** workbench. It delineates muckpile fragments by watershed in the browser and derives a mass-weighted particle-size distribution with a Rosin-Rammler fit and P10/P50/P80. Live at [fragmentiq.fasl-work.com](https://fragmentiq.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) mining-analytics hub.

![FragmentIQ, watershed muckpile delineation and a Rosin-Rammler size curve, run live in the browser](/images/projects/fragmentiq_app.png)

## The full classical chain, run live

Grayscale foreground and Otsu thresholding, a distance transform, marker non-maximum suppression (one marker per fragment), a descending-flood watershed to labelled fragments (the WipFrag / Split-style method), connected components and morphological granulometry. Areas become equivalent diameters, percent-passing is built proportional to diameter cubed, and a Rosin-Rammler least-squares fit gives P10/P50/P80 with xc, n and r-squared. A learned frag-edge CNN (ONNX) refines the foreground to reduce over-segmentation and is the one learned model that runs live; a separate fines-bias regressor is committed but evaluated offline only.

## What is cited, and what is not built

To be exact: Kuz-Ram, Swebrec and Segment Anything (SAM) are cited but not implemented. FragmentIQ fits Rosin-Rammler (which underlies Kuz-Ram) and delineates by watershed; there is no SAM, no SAM weights, no SAM inference. The real images come from a public mirror that happens to be named for SAM, and FragmentIQ borrows only the images.

## The honest limit

The over-segmentation bias is shown directly in the artifact: on one coarse case the method recovers 116 fragments against 70 true, skewing the curve fine, a known property of image-based delineation. The learned refinement cuts P50 error 27.2 percent to 23.8 percent with boundary F1 0.9974, but this is stated as indicative not significant at n=8, with hyperparameters selected on a disjoint tune bank and reported on a disjoint test bank. And the 5 real Gole-Gohar photos (CC BY 4.0, DOI 10.17632/z78ghz96bn.1) ship as an explicitly RELATIVE lane: the scale is unset, no sieve ground truth exists, and the app says so in English and Spanish, so no millimetre P80 is ever printed for a real photo.

[Live demo](https://fragmentiq.fasl-work.com) · [Source on GitHub](https://github.com/fsantibanezleal/CAOS_FragmentIQ)
