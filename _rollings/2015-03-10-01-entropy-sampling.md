---
title: 'Entropy and Sampling'
date: 2015-03-10
permalink: /rollings/2015/03/entropy-sampling/
tags:
  - PhD
  - Information Theory
  - Sampling
  - Geostatistics
---

The adaptive entropy sampling algorithm is starting to converge to something useful. The idea is simple in principle — place your next measurement where the posterior uncertainty is highest — but implementing it efficiently on large fields with complex spatial dependencies is another story.

Spent the last month implementing the conditional entropy estimator from scratch in MATLAB. The multiple-point statistics backend is slow but it works. Comparing against regular grids and random sampling, the information-theoretic approach consistently recovers the field better with fewer samples. The (1-1/e) approximation guarantee from the submodularity property is elegant — theory and practice agreeing for once.

Professor Silva's guidance on the information-theoretic formulation has been invaluable. This might actually become a publishable framework.
