---
title: 'QMine: quantum computing measured on mining problems, and today the classical solver usually wins'
date: 2026-08-30
permalink: /rollings/2026/08/qmine-measured-not-advocated/
tags:
  - quantum-computing
  - optimization
  - mining
  - honesty
---

QMine: quantum computing measured on mining problems, and today the classical solver usually wins
======

![QMine, real instances through the same ladder on real engines, a cost ledger and a computed verdict](/images/projects/qmine_pipeline.svg)

QMine went live today on the ML box. It is the private, provider-integrated counterpart of QLab, and it exists to answer a question I keep being asked in industry with a measurement instead of an opinion: what can today's quantum providers actually do on a real, data-driven mining problem?

Every case runs the same ladder end to end on real engines: proven-optimal classical solvers (CP-SAT, HiGHS, a max-closure, a treewidth-bounded exact decomposition), the field heuristics a plant actually uses, the strongest quantum-inspired algorithms (simulated annealing, tabu, path-integral quantum annealing, simulated bifurcation), the gate-model family on simulators (QAOA with warm-start, CVaR, recursive and counterdiabatic variants, a hardware-efficient VQE, an independent PennyLane implementation), and eleven provider lanes that run only when their credentials exist and record an explicit skip otherwise. Sixteen cases, 121 variants, 3,255 declared solver cells, plus a flotation soft-sensor prediction problem with leakage-safe temporal splits. Every run is denominated in money.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The verdict is computed from the measurements, never written.</strong><br/>
On tiny pit instances the problem-aware gate variants reach the proven optimum where plain QAOA and the problem-agnostic VQE do not. On supply packing the quantum lane ties the classical baseline on objective while the classical solver is three times faster. On the flotation soft sensor, ridge regression beats both quantum models, and the quantum kernel is worse than the persistence floor.<br/>
<span style="color:#5a9ac0;font-size:13px;">The honesty spine is on screen per case: as of the research date there is no third-party-confirmed quantum advantage for any industrial optimization problem.</span>
</div>

Two things I got smaller on the way. I had counted three formulations with no prior art; the searches support two (truck dispatch and flotation circuit design), and crew rostering has production prior art that is now recorded on its own case page. And the deploy installer refuses a foreign process on its port and a bundle carrying data, then verifies health, artifacts, an unauthenticated 401, deep links and a missing asset, because both browser gates are re-run against the deployment, not a local build.

[Live, behind an operator session](https://qmine.ml.fasl-work.com) · the public didactic lab is [QLab](https://qlab.fasl-work.com).
