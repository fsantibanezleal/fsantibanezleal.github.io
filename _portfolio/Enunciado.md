---
title: "Enunciado, How Faithfully Language Models Turn a Problem Statement into a Solvable Model"
date: 2026-09-26
excerpt: "The field reports whether a generated model ran and calls that correct. Enunciado measures faithfulness: 20 authored optimization statements across five tiers, sixteen models from four providers, 320 calls, and an oracle that is not a language model (executable, structural and property layers over a solver, with a duality certificate). The best local model is faithful on 5 of 20; the output cap moves DeepSeek-V4-Pro from 2 of 20 to 11 of 20. The first version of the measurement read +0.000 and was wrong.<br/><img src='/images/projects/enunciado_pipeline.svg'>"
collection: portfolio
tags: [formalization, optimization, llm-evaluation, benchmark, pyomo, ollama, reproducible-research]
---

*Enunciado* is the Spanish word for the statement of a problem: the text as it is handed to you, before anyone has decided what the variables are. Turning it into a formal, solvable model is the step the published evaluations skip. Four separate literatures report that the artifact ran and call that correct, and each admits on a close reading that the measured faithfulness is lower: reaching the reference objective does not imply a correct model (arXiv:2508.10047); the strongest formalization agent compiles 89.5 per cent of the time and is faithful 60.5 (arXiv:2606.31002); every model is weak at datasets, baselines and metrics in experiment design (arXiv:2608.03501); simulation models run but reason weakly about causes (arXiv:2605.28994). A 2025 position paper says these are one problem and supplies none of the machinery (arXiv:2509.09810).

![Enunciado, statements to models to an oracle that is not a model, to faithfulness rates recounted from the ledger](/images/projects/enunciado_pipeline.svg)

## Three repositories, one product

**planteo** (its own repository, on PyPI) is the representation: dimensions on every quantity, provenance on every element, a record of what the statement left open. **copela** (its own repository, on PyPI) is the harness: a provider seam, an append-only ledger, four verdict layers and a budget guard that refuses to call a model without a declared budget. **Enunciado** is the product and declares no package: the corpus, the bake, the measurement and the web surface.

## The measurement

Twenty authored cases, four per tier over five complexity tiers, every trap covered and four controls without one; written rather than imported because the community benchmarks carry 8.13 to 54.0 per cent error rates, two of the most cited cannot be redistributed, and the adjacent machine-learning family is contaminated. The bake verifies that every reference solves, every claimed optimum matches the solver and every property relation holds; it caught three wrong claimed optima out of twenty. Sixteen models from four providers (Anthropic, Z.AI, DeepSeek, eleven open-weight models through Ollama on one 8 GB laptop GPU), 320 calls with every row complete in a 640-record ledger. The best local model, phi4, is faithful on 5 of 20. The output cap decides the reasoning models: DeepSeek-V4-Pro is faithful on 2 of 20 at 8192 tokens and 11 of 20 at 32768, and the at-cap counts are published next to the ranks.

## What the gates caught

![Enunciado, the workbench on a control case: sensitivity of the optimum, the models on this case, and the drift readout](/images/projects/enunciado_app_dark.png)

Ten defects were caught by gates rather than by review: three wrong claimed optima; a solver wrapper that raised on the deliberately infeasible case instead of reporting infeasibility; two sweeps that shared one ledger and interleaved records from different code versions; a report that printed a gap of +0.000 when it meant no measurement; vendor names found in the CLI by the seam test; a deep link that answered 404 while rendering correctly. Four times a gate caught itself. Both Claude gaps of +0.050 rest on one refutation each that lands exactly on the reference's whole-number optimum in a statement that never fixes integrality; read as allowed they are 0.000, and the page says so. Every rate on the site is recounted from the committed ledger in CI, and 197 browser checks pass against the live origin. The other target families, the manuscripts and any frontier-model measurement beyond the sixteen are not built and not claimed.

[Live](https://enunciado.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_Enunciado) · [planteo on PyPI](https://pypi.org/project/planteo/) · [copela on PyPI](https://pypi.org/project/copela/)
