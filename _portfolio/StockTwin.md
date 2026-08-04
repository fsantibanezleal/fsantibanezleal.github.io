---
title: "StockTwin — Run-of-Mine Stockpile Twin (Built Truck by Truck)"
date: 2026-08-02
excerpt: "A run-of-mine stockpile built the way one actually is: by trucks, one load at a time, following a dump plan, on ground they have to be able to climb. It measures how much the pile homogenises the feed (variance reduction against the 1/N layer bound, withheld where unreliable), where each reclaimed tonne came from (a lot ledger summing to one on every cut), and how much size segregation biases the cut. 22 scenarios, 22,656 loads, every one relaxing to zero cell pairs over the angle of repose. Synthetic + MineLib-public data only; not a blending optimizer and no plant setpoint.<br/><img src='/images/projects/stocktwin_app.png'>"
collection: portfolio
tags: [mining-simulation, stockpile, blending, grade-control, kinetic-sieving, three-js, digital-twin]
---

A **run-of-mine stockpile twin** built the way one actually is: by trucks, one load at a time, following a dump plan, on ground they have to be able to climb. Live at [stocktwin.fasl-work.com](https://stocktwin.fasl-work.com), part of the [Faena](https://faena.fasl-work.com) hub.

![StockTwin — a ROM stockpile built truck by truck, coloured by grade, with the reclaim and provenance readouts](/images/projects/stocktwin_app.png)

## The fact the whole product turns on

Fresh material stands at about 37 degrees and a haul truck climbs about two thirds of that, so **a truck never stands on fresh material**. That is why there is a dump plan, a ramp and a dozer at all: tips are positions inside a designed plan reachable over a ramp the dozer maintains, not arbitrary points on a pad. As the pile grows, a tip a truck can no longer reach is **refused and recorded** (about 17% of offered loads in most scenarios), because the plan is generated once while the pile grows away from it, and saying so is more useful than teleporting a truck.

## The three questions, measured against the right bounds

**How much does the pile homogenise the feed?** As the variance reduction ratio drawn against the `1/N` independent-layer bound, with the bound **withheld** where the effective layer count cannot be estimated reliably (a bare ratio overstates the benefit by roughly an order of magnitude). **Where did this reclaimed tonne come from?** A per-cell ordered lot ledger where each reclaim cut reports the fraction from each dump, and those fractions **sum to one, checked on every cut**. **How much is size segregation biasing the cut?** The Gray-Thornton kinetic-sieving model solved down a **real face** taken from the terrain.

## The scenario matrix is the validation design

22 cases across six axes, 22,656 placed loads, each stating in advance what result would mean the code is wrong, with the bake gate enforced on the **actual artifact**: zero cell pairs over the angle of repose, the lot ledger agreeing column by column, mass conserved to one part in a million. Two scenarios that would not relax were **withdrawn** rather than shipped with a surface the product's own invariant rejects. The physics is the separately published [`bedblend`](https://pypi.org/project/bedblend/) package; the repo declares none of its own. Synthetic and MineLib-public data only. Not metal accounting, not a blending optimizer, and it emits no plant setpoint. [Live](https://stocktwin.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_StockTwin).
