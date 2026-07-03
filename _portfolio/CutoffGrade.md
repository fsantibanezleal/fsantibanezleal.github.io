---
title: "CutoffGrade Studio — Lane's Optimal Cut-off Grade"
date: 2026-06-30
excerpt: "An open, explainable studio for Lane's optimal cut-off grade: feed a grade-tonnage curve plus prices, costs and three stage capacities, and it computes the NPV-maximising declining cut-off trajectory, NPV, mine life and cashflow — live in the browser, with the exact algorithm as the authority and a learned surrogate only for speed.<br/><img src='/images/projects/cutoffgrade_studio.svg'>"
collection: portfolio
tags: [mining, optimization, economics, cutoff-grade, lane, npv]
---

An open, explainable studio for **Lane's optimal cut-off grade** — the NPV-maximising cut-off that *declines* over a mine's life and is set by whichever stage (mine, mill or market) is the binding constraint. Feed a grade-tonnage curve plus prices, costs and three stage capacities, and it returns the trajectory, NPV, mine life and cashflow, live in the browser. Live at [cutoffgrade.fasl-work.com](https://cutoffgrade.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) mining-analytics hub.

![CutoffGrade Studio — the declining optimal cut-off trajectory](/images/projects/cutoffgrade_studio.svg)

## Exact method as the authority

The engine implements Lane's method exactly — the six characteristic cut-offs, the balancing (Dagdelen) medians, and a year-by-year NPV simulator run to a fixed point — and shows it against a best-constant baseline and closed-form oracles, so the **~2.6% NPV uplift** it finds when a processing stage binds (and **0%** when the mine is the limit, exactly as theory predicts) is provable, not asserted. A real ten-tab workbench reacting to a case selector and live sliders, equations on screen.

## Honest about the AI, and the data

Two small models run live via **onnxruntime-web** — a surrogate that reproduces the trajectory instantly and an out-of-distribution guard — but they are **for speed and sanity, not to improve the answer** (the exact optimizer is always the authority). The base case is **100% synthetic** (a porphyry-copper example, openly labelled), and the repo discloses its two small divergences from textbook Lane. A faithful classic method, made legible — no "novel-beyond-SOTA" claim.

[Live demo](https://cutoffgrade.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_CutoffGrade)
