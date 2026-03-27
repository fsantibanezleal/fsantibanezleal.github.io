---
title: 'Publication in Natural Resources Research: Ore-Waste Discrimination with Adaptive Sampling'
date: 2020-02-10
permalink: /posts/2020/02/nrr-ore-waste-discrimination/
tags:
  - publication
  - mining
  - grade control
  - adaptive sampling
---

Our paper "Ore-Waste Discrimination with Adaptive Sampling Strategy" has been published in Natural Resources Research. [Read the paper (DOI)](https://doi.org/10.1007/s11053-020-09625-3).

From theory to practice
======

If the Mathematical Geosciences paper laid the theoretical foundation, this paper is where the rubber meets the road. This was always intended as the "applied companion" to the theoretical work -- the proof that the formalism was not just elegant mathematics but something that could survive contact with real geological complexity. Here we take the information-driven sampling framework and apply it directly to real mining problems -- specifically, ore-waste discrimination for grade control and short-term mine planning.

The central question is practical: given a limited budget of samples, how should they be distributed to best distinguish ore from waste in a mining block? The standard industry practice relies on regular grid drilling patterns. Our work demonstrates that an adaptive, information-guided strategy can do significantly better.

Validation on real cases
======

What makes this paper particularly satisfying is the validation. We tested the approach on three real mining cases with distinct geological settings and orebody geometries, and in each one the adaptive strategy showed clear improvement over the standard regular grid approach. The feeling of watching the algorithm place samples in geologically sensible locations -- concentrating effort near ore-waste boundaries where uncertainty is highest -- was remarkable. The theory was not just working in the abstract; it was making decisions that an experienced geologist would recognize as intelligent.

This is not a marginal academic improvement -- it translates to better classification of ore and waste blocks, which directly impacts operational decisions and economic outcomes. It is worth emphasizing what this means in practice: mining companies overwhelmingly rely on regular drilling grids for grade control. Showing that an adaptive, information-driven approach consistently outperforms this industry standard, on real data from real mines, challenges deeply entrenched operational habits. The potential savings from better ore-waste boundary delineation are substantial.

For me, this paper closes a loop that started during my doctoral research. The theoretical framework needed to prove itself in realistic scenarios, and it did. Seeing the ideas work on actual mining data, with all the messiness and complexity that entails, was one of the most rewarding moments of my PhD journey. It confirmed that the years spent on formalization were not in vain. The code implementing the information-driven sampling framework used in both this paper and the earlier Mathematical Geosciences publication is openly available. [View the code on GitHub](https://github.com/fsantibanezleal/IDS_OWP).
