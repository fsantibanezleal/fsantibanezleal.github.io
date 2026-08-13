---
title: "PhaseFlow — Open-Pit Production Schedule with a Certified Bound"
date: 2026-08-10
excerpt: "An open-pit production schedule solved with a certified bound and animated year by year over the block model. PitForge answers which blocks are worth mining; PhaseFlow answers when. Anchored to the published MineLib newman1.cpit solved AS PUBLISHED: the ultimate pit optimum reproduces exactly (26,086,899) and the joint LP bound lands at 24,486,184 against a published 24,486,549. The bound needs no LP solver, so the whole problem re-solves live in the browser.<br/><img src='/images/projects/phaseflow_app.png'>"
collection: portfolio
tags: [mining-optimization, mine-planning, scheduling, cpit, lagrangian-bound, max-flow, three-js]
---

An **open-pit production schedule**, solved with a certified bound and animated year by year over the block model. Live at [phaseflow.fasl-work.com](https://phaseflow.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) hub.

![PhaseFlow — a year-coloured pit with NPV, bound, gap and spatial-coherence readouts](/images/projects/phaseflow_app.png)

## Which blocks, then when

[PitForge](https://pitforge.fasl-work.com) answers *which* blocks are worth mining. PhaseFlow answers *when*, subject to slope precedence in every period and to the mining and processing capacity of each year, maximising discounted NPV. That is the constrained pit limit problem, and it is NP-hard, so nobody solves it to proven optimality at real size. Without a bound, a scheduling tool can report any NPV it likes.

## Measured against work that is not mine

The trust anchor is the published MineLib `newman1.cpit` solved **as published**, on its own six periods, its own eight percent discount rate and its own two capacities. The ultimate pit optimum reproduces exactly at **26,086,899**, the joint LP bound lands at **24,486,184** against a published **24,486,549**, and the shipped optimality gap is **2.49 percent against a published 1.26 percent**, which the app states rather than smooths over. The check that the bound is real is its ordering: a CPIT LP bound must sit below a PCPSP LP bound, and it does, by 365 units in 24.5 million.

## Three things that follow from the bound being cheap

The critical multiplier algorithm solves the CPIT LP relaxation exactly in `O(mn log n)` as parametric maximum closures, with **no LP solver**, which is why a TypeScript port re-solves the whole problem **live in the browser** with a parity test asserting it reproduces the Python bound. **Two bounds run on every case**, a certified-but-loose one and the joint Bienstock-Zuckerberg bound, and the app names which one it used, because the difference between them is the part of a gap that belongs to the bound rather than to the plan; on a single-resource instance the two agree to machine precision. And **spatial coherence is a first-class KPI** (components per period, largest-component share, narrowest mined run) because the algorithm's own authors predict block-level schedules scatter.

Honest scope, stated in the product: no stockpiles, no blending, no minimum-production constraints, no two-stage stochastic integer programming, and not for production mine planning. The engine is the separately published [`oreblocks`](https://pypi.org/project/oreblocks/) package; PhaseFlow declares none of its own. [Live](https://phaseflow.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_PhaseFlow).
