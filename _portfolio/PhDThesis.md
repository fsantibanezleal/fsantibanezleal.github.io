---
title: "Information-Theoretic Sampling for Geological Image Recovery"
date: 2019-12-17
excerpt: "Doctoral thesis formalizing the Optimal Sensor Placement problem using Shannon entropy, conditional information, and adaptive sequential strategies for mining exploration.<br/><img src='/images/projects/ids_owp.svg'>"
collection: portfolio
tags: [phd-thesis, information-theory, entropy, geostatistics, optimal-sampling, mining]
---

## Overview

This doctoral thesis, completed at the Department of Electrical Engineering, Universidad de Chile (2013--2019), addresses a fundamental question in spatial data acquisition: **given a limited budget of N measurements in a spatial domain, where should you place them to minimize posterior uncertainty about the entire field?** This is the Optimal Sensor Placement (OSP) problem, with direct applications in mining exploration (drill hole placement), environmental monitoring (sensor networks), and remote sensing.

The research was supervised by Prof. Jorge F. Silva (Department of Electrical Engineering) and Prof. Julian M. Ortiz (Department of Mining Engineering, now at Queen's University), and was funded by a CONICYT National Doctoral Scholarship (Beca CONICYT Doctorado Nacional).

![Framework](/images/projects/ids_owp.svg)

## Theoretical Foundations

The thesis builds on a rigorous information-theoretic framework for spatial sampling design. The core machinery revolves around quantifying uncertainty and information gain through the following concepts.

**Shannon Entropy** measures the uncertainty of a random variable or random field. For a discrete random variable X with probability mass function p(x), the entropy is defined as:

H(X) = -Sum p(x) log p(x)

Entropy is maximized when the distribution is uniform, corresponding to maximum uncertainty. In the spatial context, entropy quantifies how much we do not know about unsampled locations before any data is collected.

**Conditional Entropy** captures the residual uncertainty about the unsampled field X^f after observing a subset of measurements X_f:

H(X^f | X_f)

This quantity is always less than or equal to H(X^f), with equality when the measurements are uninformative. The goal of optimal sampling is to choose X_f so that this residual uncertainty is minimized.

**Mutual Information** provides the natural objective function for sampling design. It measures the information gained about the unsampled field by observing the sampled subset:

I(X_f; X^f) = H(X^f) - H(X^f | X_f)

Maximizing mutual information is equivalent to minimizing conditional entropy, directly targeting the reduction of posterior uncertainty across the entire spatial domain.

## The Optimization Problem

The optimal sampling design is formulated as:

max I(X_f; X^f) subject to |X_f| <= N

where N is the sampling budget. This combinatorial optimization is NP-hard in general, meaning that an exhaustive search over all possible subsets of size N is computationally intractable for realistic domain sizes. However, a key theoretical result exploited in this thesis is that mutual information is a **submodular** set function. Submodularity guarantees that a simple greedy algorithm --- selecting one measurement at a time to maximize the marginal information gain --- achieves a solution within a factor of (1 - 1/e) of the global optimum, approximately 63.2%.

## AdSEMES Algorithm

A central methodological contribution of the thesis is the **Adaptive Sequential Empirical Maximum Entropy Sampling (AdSEMES)** algorithm. Unlike static designs that fix all sampling locations before any data is collected, AdSEMES operates in an adaptive sequential fashion: after each measurement is taken, the posterior model is updated with the newly acquired data, and the next sampling location is chosen to maximize the expected information gain given all previously observed values. This adaptive strategy is particularly powerful in geological settings where early measurements can dramatically reshape the posterior model and redirect subsequent sampling effort toward the most uncertain or informative regions of the domain.

The algorithm combines empirical estimation of entropy from geostatistical simulation ensembles with greedy sequential optimization, enabling practical deployment in high-dimensional spatial problems typical of mining exploration.

## Applications in Mining and Geosciences

The framework was validated on realistic geological scenarios including:

- **Drill hole placement for mineral resource estimation**, where each borehole is expensive and must be placed to maximize geological knowledge under strict budget constraints.
- **Ore-waste boundary discrimination**, where the goal is to classify spatial blocks as ore or waste with minimum misclassification, directly impacting mine planning and economic outcomes.
- **Geological facies recovery**, where the spatial arrangement of rock types must be reconstructed from sparse measurements to support geological modeling.

## Published Works

Three journal articles were derived from this thesis research:

1. **Sampling Strategies for Uncertainty Reduction in Categorical Random Fields: Formulation, Mathematical Analysis and Application to Multiple-Point Simulations** --- Published in *Mathematical Geosciences*, 2019. This paper presents the full theoretical framework and the AdSEMES algorithm with applications to geostatistical simulation.

2. **Optimal Sampling Strategy for Spatial Estimation of Ore-Waste Contacts Using Maximum Entropy** --- Published in *Natural Resources Research*, 2020. This paper applies the information-theoretic sampling framework to the specific problem of ore-waste discrimination in mining.

3. **Geological Facies Recovery Based on Weighted L1-Regularization** (with Calderon et al.) --- Published in *Mathematical Geosciences*, 2019. This paper addresses geological image recovery using sparse regularization techniques in combination with spatial sampling strategies.

## Resources

- **Thesis repository**: [Universidad de Chile Institutional Repository](http://repositorio.uchile.cl/handle/2250/175050)
- **Source code**: [IDS_OWP on GitHub](https://github.com/fsantibanezleal/IDS_OWP)
