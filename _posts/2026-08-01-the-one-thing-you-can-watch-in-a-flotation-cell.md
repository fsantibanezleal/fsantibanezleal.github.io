---
title: 'The one thing you can watch in a flotation cell'
date: 2026-08-01
published: true
permalink: /posts/2026/08/the-one-thing-you-can-watch-in-a-flotation-cell/
tags:
  - flotation
  - computer-vision
  - mineral-processing
  - mining
---

The one thing you can watch in a flotation cell
======

Inside a flotation cell almost nothing can be watched continuously. The froth is the exception: it is the one part of the process permanently exposed to a camera. That is why froth vision exists as an industrial instrument at all. What the camera sees is the top face of the topmost layer of bubbles, a two-dimensional projection of a three-dimensional dispersion, and what it sees moves with what you manipulate. Air rate, frother dose, level and the mineral loading on the bubbles all change the size, shape and stability of what reaches the surface. That is why the literature treats bubble size as a soft sensor: cheap to measure optically, and correlated with things that are expensive or slow to measure, such as grade and recovery.

That is the part that touches the operation. Air, frother and level are decided today on the judgement of whoever is looking, and that judgement changes by shift, by operator and by lighting. Turning it into a metric is what lets it enter a control loop and be compared across cells. A reliable measurement would give the same criterion in every cell and every shift, make drift visible while it happens instead of at the next assay, and produce a reading that can sit in a loop rather than in a report.

The measurement is hard to get right. Bubbles are packed and touching, and the border two of them share is the only evidence separating them. On top of that come specular glare, defocus, noise, bursting and motion. And there is a quieter problem underneath: there is no openly licensed froth dataset with per-bubble annotation, so anyone building this validates on whatever images they can get. That is easy to paper over with a synthetic benchmark and a flattering number.

I built a bench to take it seriously. It has exact per-bubble ground truth on synthetic froth, orders fifteen segmentation methods under one protocol, and then runs the same list, unchanged, over other real images. The order flipped, and the methods that had only learned my own generator lost the most. The model carrying a large external prior held up when the images changed; the ones trained only on my data did not. That is the honest shape of the field right now, and I would rather publish it than hide it behind the synthetic ranking.

Two things are worth stating plainly about why this is still open. Segmenting each bubble as an object, rather than producing a binary mask, is what makes a size distribution possible at all, and a sequence rather than a still is what gives each bubble an identity, so bursting and motion become measurable instead of impressions. And what would settle it for a given plant is validation on frames from that plant, which the absence of a public dataset makes harder than it should be. I left the work open for exactly that: [FrothSeg](https://frothseg.fasl-work.com) is a method-comparison lab with the data situation stated in full, not a plant tool and not a claim that the problem is solved.
