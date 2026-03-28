---
title: 'Publication in Mathematical Geosciences: Sampling Strategies for Uncertainty Reduction'
date: 2019-09-20
permalink: /posts/2019/09/mathgeo-sampling-strategies/
tags:
  - publication
  - geostatistics
  - optimal sampling
  - information theory
---

After years of research, our paper "Sampling Strategies for Uncertainty Reduction in Categorical Random Fields" has been published in Mathematical Geosciences. [Read the paper (DOI)](https://doi.org/10.1007/s11004-018-09777-2).

A core piece of the doctoral puzzle
======

This paper represents one of the central chapters of my PhD thesis, and seeing it finally published brings a deep sense of relief and pride. I started my doctoral studies in 2013, and this core result did not see print until 2019 -- six years of formulation, simulation, revision, and persistence. The reviewer cycles were particularly grueling: rounds of comments, months of waiting, resubmissions that required rethinking entire sections. There were moments where I genuinely wondered if the mathematical framework would survive peer review intact. When the acceptance finally came, the feeling was not celebration so much as quiet vindication -- the math had been validated by experts in the field, and the ideas I had been carrying for years were now part of the literature. This work was developed under the guidance of Prof. Jorge Silva and Prof. Julian Ortiz, whose complementary expertise in information theory and geostatistics made the interdisciplinary formulation possible. The work formalizes the optimal sampling problem for categorical spatial models using information-theoretic measures -- specifically, how to decide where to place new measurements so that uncertainty about the underlying geology is reduced as efficiently as possible.

![Resolvability and sampling comparison](/images/rollings/owp_resolvability.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Mutual information — the quantity we maximize:</strong><br/>
I(X<sub>f</sub>; X<sup>f</sup>) = H(X<sup>f</sup>) − H(X<sup>f</sup> | X<sub>f</sub>)
</div>

The key contribution is a rigorous comparison between information-driven sampling strategies and the more conventional random or regular grid approaches. We show that by leveraging entropy and mutual information concepts from information theory, one can design sampling campaigns that extract significantly more knowledge per sample than standard approaches.

This is not just a theoretical exercise. In mining and geosciences, every drill hole or measurement point has a real cost. Being able to demonstrate, formally, that an adaptive information-driven strategy outperforms brute-force regular grids means tangible savings and better geological models. The implementation of these methods, including the entropy estimators and simulation backends, is available as open-source code. [View the code on GitHub](https://github.com/fsantibanezleal/IDS_OWP).

Why it matters to me
======

This paper took years of iterative work -- formulating the problem, running geostatistical simulations, debugging code, and refining the mathematical framework. There were moments where the path forward was unclear. But the result is something I am genuinely proud of: a solid contribution to the intersection of geostatistics and information theory that I hope will be useful to others working on spatial sampling problems.

Importantly, the theoretical framework developed here became the foundation for the applied ore-waste discrimination paper that followed in Natural Resources Research. That second paper could not have existed without the rigorous groundwork laid in this one -- the entropy estimators, the simulation-based evaluation methodology, and the formal comparison framework all carried over directly. Looking back, this publication was the keystone that made the rest of the doctoral narrative cohere.
