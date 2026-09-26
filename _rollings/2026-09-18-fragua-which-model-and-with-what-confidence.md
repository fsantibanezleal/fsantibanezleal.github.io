---
title: 'Fragua: which model describes this process, and with what confidence'
date: 2026-09-18
permalink: /rollings/2026/09/fragua-which-model-and-with-what-confidence/
tags:
  - fragua
  - ensembles
  - scientific-ml
  - mining
---

Fragua: which model describes this process, and with what confidence
======

![Fragua, a record fitted by many realizations from a bank of families, aggregated with inclusion probabilities, compared against the other rungs](/images/projects/fragua_pipeline.svg)

Fragua's CI went green today for a reason that is its own small lesson: the workflow's triggers had never registered, so the checks had never run on a push; re-enabling the workflow fixed it and 0.05.001 is the release that carries the fix. The product underneath has been live since late August.

A flotation cell or a leach tank is usually modelled by picking one kinetic equation and fitting its parameters, and the choice of equation, made once, carries more uncertainty than the parameters ever will. Fragua treats structure as an estimated quantity. Over a bank of published phenomenological families it fits many realizations, families times parameter multistarts times bootstrap resamples, and aggregates them into calibrated ensembles with structural inclusion probabilities. The coined method is BAPE, Bootstrap-Aggregated Phenomenological Ensembles, and the research pass found the concept absent from the literature and from vendor tooling.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The question first, then the estimate.</strong><br/>
The structural fingerprint answers which families the data supports and how much; the fan of realizations shows what that structural uncertainty means for prediction, especially beyond the shaded training envelope. A misspecified control, whose truth lies outside every family, is in the case matrix so the fingerprint can be seen behaving when the bank is wrong.<br/>
<span style="color:#5a9ac0;font-size:13px;">BAPE is rung 6 of a twelve-rung ladder baked over 30 variants: controls, a BIC-weighted Bayesian model average, ensemble SINDy, a Kennedy-O'Hagan hybrid, deep ensembles and a mixture of phenomenological experts. A 360-row benchmark artifact carries the comparison.</span>
</div>

The engine is phenoforge, published on PyPI from its own repository; the product declares none. The browser runs a real live lane that installs the published wheel through Pyodide and micropip. The plan was validated on 2026-08-25 before the build, and the at-bar review of the shipped product is my call, still to be made.

[Live](https://fragua.ml.fasl-work.com) · [phenoforge on PyPI](https://pypi.org/project/phenoforge/)
