---
title: "PitForge — Exact Ultimate Pit Limit & Nested Whittle Pit-Shell Workbench"
date: 2026-07-15
excerpt: "An open-pit mine-design workbench that solves the ultimate pit limit exactly, as a maximum-weight closure of the block-precedence graph reduced to a minimum cut on a Dinic max-flow engine, running live in the browser, and derives the nested Whittle pit shells by revenue factor. It reproduces the published optima of three real MineLib instances to at most 2e-9 relative error, and self-checks every solve with the max-flow duality identity. This is the only one of the Faena four whose headline is validated against third-party published optima rather than its own generator.<br/><img src='/images/projects/pitforge_app.png'>"
collection: portfolio
tags: [mining-optimization, open-pit, ultimate-pit-limit, max-flow, min-cut, whittle, dinic, minelib, kriging, mining]
---

PitForge is an open-pit **mine-design** workbench. It solves the **ultimate pit limit exactly**, as a maximum-weight closure of the block-precedence graph reduced to a minimum cut on a Dinic max-flow engine, running live in the browser, and derives the nested Whittle pit shells by revenue factor. Live at [pitforge.fasl-work.com](https://pitforge.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) mining-analytics hub.

![PitForge — an exact ultimate pit via Dinic min-cut, with nested Whittle shells, in the browser](/images/projects/pitforge_app.png)

## Say what the engine is

The exact result is the max-closure / min-cut equivalent of Lerchs-Grossmann, via Picard's 1976 reduction on a Dinic engine. It is not a re-implementation of Lerchs-Grossmann, and it is not Hochbaum's pseudoflow, which is referenced only as computing the same cut. From the exact pit, nested Whittle shells over an ascending revenue-factor schedule give value, tonnage and strip-ratio curves. Grade estimation runs three ways live (IDW, ordinary kriging, and a grade-nn ONNX surrogate).

## Validated against MineLib, not against itself

The exact pit reproduces the published optima of three real MineLib instances: newman1 (1,060 blocks, 5.2 ms, relative error 9.96e-10), zuck_small (9,400 blocks, 237 ms, 1.86e-10), and kd (14,153 blocks / 219,778 precedences, 259 ms, 1.30e-10). All three match. Two further instances (marvin, mclaughlin_limit) are excluded with committed reasons rather than silently dropped. In real mode the scenario knobs are locked, because the instances publish their own net values and precedences and re-deriving them would break comparability with the published optimum.

## The honest limit

Every solve asserts the duality identity pitValue = sum(positive) minus maxflow, so the optimiser checks itself. The learned grade-nn is a tie, not a win: R2 0.9613 versus ordinary kriging 0.958, a 0.0033 margin the artifact itself calls a fast approximation that never beats the exact result. Scheduling is a CPIT LP relaxation computed offline with scipy HiGHS, rendered from JSON, never live; it publishes a certified NPV upper bound with a 10.46 percent integrality gap, and states plainly that the rounded schedule is a heuristic and is never optimal. It is a design optimiser, not a JORC or NI 43-101 resource estimate.

[Live demo](https://pitforge.fasl-work.com) · [Source on GitHub](https://github.com/fsantibanezleal/CAOS_PitForge)
