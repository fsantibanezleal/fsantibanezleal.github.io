---
title: 'StockTwin: a stockpile built the way one actually is, truck by truck'
date: 2026-08-02
permalink: /rollings/2026/08/stocktwin-built-truck-by-truck/
tags:
  - mining-simulation
  - stockpile
  - grade-control
  - honesty
---

StockTwin: a stockpile built the way one actually is, truck by truck
======

![StockTwin: a ROM stockpile built truck by truck, coloured by grade, with the reclaim and provenance readouts](/images/projects/stocktwin_app.png)

[StockTwin](https://stocktwin.fasl-work.com) builds a run-of-mine stockpile the way one is actually built: by trucks, one load at a time, following a dump plan, on ground they have to be able to climb. A truck routes over the trafficable surface, spots against the working face, tips, and leaves; the material stands at its angle of repose; a dozer turns the heaps into a floor so the next lift starts higher.

The fact the whole product turns on is a small one with large consequences:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">A truck never stands on fresh material.</strong><br/>
Fresh material stands at about 37&deg; and a haul truck climbs about two thirds of that.<br/>
<span style="color:#5a9ac0;font-size:13px;">So tips are positions inside a designed plan reachable over a ramp a dozer maintains, not arbitrary points on a pad. A tip a truck can no longer reach is refused and recorded (~17% of offered loads), because the plan is generated once while the pile grows away from it.</span>
</div>

It then measures the three questions that matter, each against the right bound: homogenisation as variance reduction against the `1/N` independent-layer bound (withheld where the layer count is unreliable), provenance as a per-cell lot ledger whose fractions sum to one on every cut, and size segregation with the Gray-Thornton kinetic-sieving model solved down a real face. 22 scenarios, 22,656 loads, every one relaxing to zero cell pairs over the angle of repose, gated on the actual artifact; two that would not relax were withdrawn rather than shipped broken. The engine is the separately published [`bedblend`](https://pypi.org/project/bedblend/) package. Synthetic and MineLib-public data only. A research workbench, not a blending optimizer, and it emits no plant setpoint. Part of the [Faena](https://faena.fasl-work.com) hub. [Live](https://stocktwin.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_StockTwin).
