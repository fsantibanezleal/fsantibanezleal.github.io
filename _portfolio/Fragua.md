---
title: "Fragua, Ensembles of Phenomenological Models for Mining and Industrial Processes"
date: 2026-09-18
excerpt: "Instead of selecting one kinetic equation per unit process, Fragua fits many realizations, model families times multistarts times bootstrap resamples, from a curated bank and aggregates them into calibrated ensembles with structural inclusion probabilities: which model describes this process, with what confidence. BAPE is rung 6 of a twelve-rung ladder baked over 30 variants; the browser runs a live lane through the published phenoforge wheel.<br/><img src='/images/projects/fragua_pipeline.svg'>"
collection: portfolio
tags: [phenomenological-models, ensembles, bootstrap, model-selection, scientific-ml, mining]
---

A flotation cell or a leach tank is usually modelled by picking one kinetic equation and fitting its parameters, and the choice of equation, made once, carries more uncertainty than the parameters ever will. **Fragua** treats structure as an estimated quantity: over a bank of published phenomenological families, which ones does the data support, with what probability, and how wide is the prediction band once that doubt is carried instead of hidden. The research pass found the concept absent from the literature and from vendor tooling.

![Fragua, a record fitted by many realizations from a bank of families, aggregated with inclusion probabilities, compared against the other rungs](/images/projects/fragua_pipeline.svg)

## BAPE, and the rungs around it

The engine is **phenoforge**, published on PyPI from its own repository: the family bank, the multistart fitting, the bootstrap aggregation and the samplers. Fragua is the product: a 14-case matrix over seven unit processes with clean, dense, noisy, rough and sparse variants and a misspecified control whose truth lies outside every family; a twelve-rung ladder baked canonically over 30 variants, with controls, the ensemble core (BAPE at rung 6), a BIC-weighted Bayesian model average through a Goodman-Weare sampler, ensemble SINDy with seeded bagging, a Kennedy-O'Hagan Gaussian-process hybrid, and deep ensembles with a mixture of phenomenological experts on deterministic torch; a 360-row benchmark artifact.

![Fragua, the workbench on the misspecified control: the fan of realizations and the structural fingerprint per family](/images/projects/fragua_app_dark.png)

## The question, then the estimate

The workbench answers in the right order: the structural fingerprint first, which families the data supports and how much, then the fan of realizations, what that structural uncertainty means for prediction beyond the training envelope. A real live lane installs the published phenoforge wheel in the browser through Pyodide and micropip. Every benchmark number is a committed artifact aggregated from traces after a completeness validator passes; the web reads only artifacts. The plan was validated on 2026-08-25 before the build; CI had a workflow whose triggers had never registered, found and fixed on 2026-09-18. Private repository, MIT; the lifecycle stays building and the at-bar review is mine to make. Its sibling Porvenir learns latent dynamics where Fragua ensembles closed-form equations.

[Live](https://fragua.ml.fasl-work.com) · [phenoforge on PyPI](https://pypi.org/project/phenoforge/)
