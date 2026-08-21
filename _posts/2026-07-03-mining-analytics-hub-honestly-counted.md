---
title: 'A mining-analytics hub, honestly counted'
date: 2026-07-03
permalink: /posts/2026/07/mining-analytics-hub-honestly-counted/
tags:
  - mining
  - analytics
  - honesty
  - portfolio
---

A mining-analytics hub, honestly counted
======

Over the last stretch I've been building a set of small, independent mining-analytics tools (each one its own browser app, its own repo, its own data) and the moment there was more than a handful, I needed a way to see them as a whole. That's [Faena](https://faena.fasl-work.com): a single open launcher that catalogues the tools across the value chain (exploration → drill & blast → load/haul → comminution → processing → tailings → asset health → economics) and links out to each one. It doesn't bundle or run anything; it lists and links.

The design decision I care about is the counting. It would be easy, and dishonest, to say "39 mining apps." So the registry that drives the whole site carries a lifecycle on every tile, and the site shows it:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The honest count, on the tiles:</strong><br/>
<strong>3 live</strong> (ChargeCascade, RotorVitals, CutoffGrade Studio) · <strong>7 in active development</strong> · <strong>~29 planned</strong>.<br/>
<span style="color:#5a9ac0;font-size:13px;">"Live" here means brought to the quality bar, not merely deployed. Several of the seven have reachable subdomains; they're still not called live, because they aren't finished.</span>
</div>

![Faena: value-chain swimlanes, the live tiles lit, the rest planned](/images/projects/faena_hub.svg)

I like this because it makes the roadmap a feature instead of a fib. A visitor sees at a glance the few things that actually work today and the many that are in progress or planned, and no single tool gets to oversell itself under the cover of a big number. It's the same discipline I've been applying tool by tool: [ChargeCascade](https://chargecascade.fasl-work.com) says out loud that its 3D is a kinematic view, not a DEM run, and that its data is synthetic-but-realistic; [RotorVitals](https://rotorvitals.fasl-work.com) shows where its deep model *loses* to plain physics rather than hiding it behind an accuracy number.

The two that reached the bar this round are worth a line each. ChargeCascade turns the scattered comminution equations (critical speed, the Davis regime, Hogg-Fuerstenau/Morrell/Bond power) into one live, tunable studio, with a thin ONNX layer for speed and a sanity guard that never gets to overrule the exact engine. RotorVitals grew from bearing envelope analysis into a full condition-monitoring-and-prognostics workbench on real measured vibration, with a four-model remaining-useful-life ladder benchmarked over 36 real run-to-failure trajectories.

None of this is the flashiest way to present a portfolio. A catalogue that admits most of itself is still a plan is less impressive than "39 apps." But it's the version I'd actually stand behind, and the honest count is the point, the hub is only useful if you can trust what the tiles say. [Faena](https://faena.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_FAENA).
