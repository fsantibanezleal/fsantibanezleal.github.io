---
title: 'Enunciado: sixteen models, an oracle that is not a model, and the cap that decides the reasoning models'
date: 2026-09-23
permalink: /rollings/2026/09/enunciado-sixteen-models-and-the-cap-that-decides-them/
tags:
  - enunciado
  - llm-evaluation
  - optimization
  - honesty
---

Enunciado: sixteen models, an oracle that is not a model, and the cap that decides the reasoning models
======

![Enunciado, statements to models to an oracle that is not a model, to faithfulness rates recounted from the ledger](/images/projects/enunciado_pipeline.svg)

Enunciado grew today from two Claude models to sixteen models from four providers, eleven of them open-weight models on one 8 GB laptop GPU, 320 calls with every row complete. *Enunciado* is the statement of a problem, the text as it is handed to you before anyone has decided what the variables are, and the product measures how faithfully a language model turns it into a formal, solvable optimization model. The field scores whether the returned model ran; four separate literatures admit on a close reading that the measured faithfulness is lower. So the judge here is not a language model: executable, structural and property layers over a solver, with a duality certificate, over twenty authored cases across five complexity tiers with every trap covered and four controls without one.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The best local model, phi4, is faithful on 5 of 20. The output cap decides the reasoning models.</strong><br/>
DeepSeek-V4-Pro is faithful on 2 of 20 at an 8192-token cap and on 11 of 20 at 32768. A rank without its cap is not a result, so the cap-sensitivity table and the at-cap counts are published beside the ranks.<br/>
<span style="color:#5a9ac0;font-size:13px;">Both Claude gaps of +0.050 rest on one refutation each that lands exactly on the reference's whole-number optimum in a statement that never fixes integrality; read as allowed they are 0.000, and the page says so.</span>
</div>

Ten defects were caught by gates rather than by review while building this: three wrong claimed optima in the corpus, a solver wrapper that raised on the deliberately infeasible case instead of reporting infeasibility, two sweeps that shared one ledger and interleaved records from different code versions, a report that printed a gap of +0.000 when it meant no measurement, vendor names found in the CLI by the seam test, a deep link that answered 404 while rendering correctly. Four times a gate caught itself. The first version of this measurement read +0.000 and was wrong.

The three repositories keep their boundary: planteo is the representation and copela the harness, both on PyPI from their own repositories; Enunciado is the product and declares no package. Every rate on the site is recounted from the committed ledger in CI.

[Live](https://enunciado.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_Enunciado)
