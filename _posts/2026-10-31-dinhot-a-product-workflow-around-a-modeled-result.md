---
title: 'DinHot, a product workflow around a modeled result'
date: 2026-10-31 21:18:00 -0300
published: true
permalink: /posts/2026/10/dinhot-a-product-workflow-around-a-modeled-result/
tags:
  - product-engineering
  - technology-leadership
  - optical-design
  - data-quality
---

DinHot, a product workflow around a modeled result
======

When a technical result reaches a decision-maker, its setup and evidence have to travel with it. I have been reshaping DinHot around that requirement: a reader should be able to follow the case, the modeled device, the method and the measures that support a comparison.

![The modeled optical bench, device response and camera-feedback loop](/images/projects/dinhot_00_cover_proposal.svg)

DinHot began at CEFOP as DinHotSys, a C++ desktop tool. The product has since been rebuilt as a static browser workbench with an offline Python pipeline and a TypeScript engine for the cases and methods admitted to live execution. Its released version is 0.02.001.

That release defines fourteen synthetic cases and compares twenty-four methods under common tasks, seeds and metrics. In the released bake, thirteen cases are processed and C11 is refused by contract 1. I want that refusal to remain visible: it tells the reader where the current evidence stops, instead of turning an unsupported case into a blank or a success.

## One product, three evidence paths

The offline lane builds and checks the versioned cases and benchmark. The static site replays committed artifacts. The browser re-runs only the combinations that pass the live-lane gate. Each path has a distinct role, and that separation lets a reviewer trace an output back to how it was produced.

![DinHot's offline, replay and live execution lanes](/images/projects/dinhot_architecture_lanes.svg)

The product compares methods in a shared framework. The method ladder shows the scope of those comparisons, while the case and data contracts state what each result represents. That structure supports a more useful review than a method name or chart on its own: the setup is explicit, the comparison criteria are common, and the evidence source stays visible.

![The released method scope grouped into six families](/images/projects/dinhot_method_ladder.svg)

![The data contracts that carry DinHot's case and result evidence](/images/projects/dinhot_architecture_data_contracts.svg)

## The boundary is part of the product

DinHot is a simulator and evaluator. It does not talk to a physical spatial light modulator or camera. Its device response and camera-feedback loop are modeled, and all cases are synthetic. The absolute outputs belong to the stated model; they are not calibration results from a laboratory instrument or evidence of a customer outcome.

As I take on broader business and management responsibilities, this is the kind of applied technical leadership I want to make visible: frame the decision, align the comparison, keep data lineage clear and state the product boundary. The algorithm matters, and so does the operating model that makes its output reviewable.

[Open the live workbench](https://dinhot.fasl-work.com) · [View the source repository](https://github.com/fsantibanezleal/CEFOP_DinHot)
