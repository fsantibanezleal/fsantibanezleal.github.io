---
title: 'The engine leaves the product, and the re-bake finds a lane that was never reproducible'
date: 2026-09-26
permalink: /rollings/2026/09/the-engine-leaves-the-product/
tags:
  - pulso
  - packaging
  - reproducibility
  - honesty
---

The engine leaves the product, and the re-bake finds a lane that was never reproducible
======

![Pulso's in-repo package becomes fracpta on PyPI; two processes under the same seed differed until Python's random was pinned](/images/projects/fracpta_extraction.svg)

[Pulso](https://pulso.fasl-work.com) catalogues flow behaviours of fractured reservoirs from the shape of pressure transients. Until this week its science lived inside the product as an internal package: forty modules, 5,058 lines, `lab` in the name, installed with `pip install -e .`, and a `__version__` that read 0.07.000 while the product was at 0.25.001, eighteen releases behind because nobody moves a constant nobody reads. I had listed that as a decision to make. It was never one. The rule in my own conventions is that a product declares no package of its own: a required package is its own repository with a real PyPI project, consumed as a pinned dependency. Presenting the violation as a choice was itself the error.

So the package left. It is now [fracpta](https://pypi.org/project/fracpta/) on PyPI, from its own repository: the analytic pressure-transient ensembles, the GeoDFN network generation and descriptors, the open-DARTS wrappers, the input contracts, the clustering ladder, attribution, the learned tier and the study stages. Pulso 0.26 keeps what is the product's and nothing else, its twenty-one cases, the manifest contract, the artifact writer and the lane gate, invoked by path and never installed, with `fracpta==0.1.1` pinned.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Re-baking the consumer's cases found what eighteen releases had not.</strong><br/>
Two processes given the same seed produced different fracture networks: 2,854 leaves of the DFN06 artifact differed between them. GeoDFN draws its spatial seed positions from Python's <code>random</code>, and the adapter had only ever pinned numpy. <code>PYTHONHASHSEED</code> was not the cause; I checked that first because it is the usual suspect.<br/>
<span style="color:#5a9ac0;font-size:13px;">One line, <code>random.seed(seed)</code> beside <code>np.random.seed(seed)</code>, and two processes now reproduce the case byte for byte. The trace also stopped recording the absolute path of a temporary directory. Both shipped as fracpta 0.1.1.</span>
</div>

Nine cases were re-baked under the extracted engine. The study numbers are identical, the DARTS anchor byte for byte; the DFN cases changed, because they had never been reproducible and now are; the cases that were not re-baked keep the provenance of the bake that produced them, and the manifests say so rather than pretending. I did not learn this from a test. I learned it because the extraction forced a re-bake, and a re-bake is a reproducibility check whether or not you meant it as one. Seed every generator a dependency uses, not only the one you call, and prove it across two processes, not within one.

One more, found after the deploy went green: the file the optional browser lane needs had been written into an ignored build directory, so it was never committed and the live site answered 404 for it. It lives with the other derived artifacts now (0.26.001). A green deploy is evidence that the deploy ran, not that a file is served.

[Pulso](https://pulso.fasl-work.com) · [fracpta](https://pypi.org/project/fracpta/) · [source](https://github.com/fsantibanezleal/CAOS_RES_Pulso)
