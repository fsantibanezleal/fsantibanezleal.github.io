---
title: "DinHot, a workbench for programmable light-field decisions"
date: 2010-04-01
excerpt: "A browser-based workbench for comparing optical-trap designs under stated assumptions. It makes the case, method, modeled device and modeled output reviewable together.<br/><img src='/images/projects/dinhot_00_cover_proposal.svg'>"
collection: portfolio
tags: [optics, product-engineering, simulation, technology-leadership]
---

DinHot is a browser-based simulator and evaluator for optical trap arrays and shaped light fields. It began at CEFOP as DinHotSys, a C++ desktop tool. The current released product, 0.02.001, makes the work reviewable through a versioned pipeline and a static browser workbench.

## The decision behind the interface

A method name is not enough to judge a design. The case, optical setup, device assumptions and comparison metrics all shape what the result means. I organized DinHot around those inputs so a user can see what is being compared and which evidence supports it.

![The modeled bench, device response and camera-feedback loop in DinHot](/images/projects/dinhot_00_cover_proposal.svg)

The executive view starts from the operational problem and the handoffs around the bench, then shows the modeled proposal. These are scenarios and simulations, not a report from a physical instrument.

![Where uneven trap arrays and handoffs create a review problem](/images/projects/dinhot_pain.svg)

![Roles and calibration handoffs around a shared optical bench](/images/projects/dinhot_situation.svg)

## How I structured the product

The released comparison has 24 methods and 14 defined synthetic cases. Its execution is split into an offline Python bake, static replay of versioned artifacts, and browser execution for the cases and methods admitted by the live-lane gate. The release bakes 13 cases; contract 1 refuses C11. That refusal stays visible in the record instead of being presented as a completed result.

![DinHot execution lanes from offline evidence to replay and eligible browser runs](/images/projects/dinhot_architecture_lanes.svg)

For me, this is product engineering as much as algorithm implementation: make inputs explicit, hold the comparison conditions steady, keep the execution paths distinct, and show where a result came from. The method overview shows the breadth of the comparison without implying that every method is appropriate for every case.

![The method families included in the released comparison](/images/projects/dinhot_method_ladder.svg)

## Current boundary

DinHot does not drive a physical spatial light modulator or camera. Device behavior and camera feedback are modeled; all 14 cases are synthetic. It is a software workbench for reviewing design choices, not evidence of measured laboratory or customer outcomes.

[Open the live workbench](https://dinhot.fasl-work.com) · [View the source repository](https://github.com/fsantibanezleal/CEFOP_DinHot)
