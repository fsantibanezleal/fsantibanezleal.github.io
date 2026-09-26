---
title: "QMine, Quantum Computing Measured on Real Mining Problems"
date: 2026-08-30
excerpt: "A private research app that measures what today's quantum providers can actually do on real mining problems: every case runs the same ladder on real engines, classical exact, field heuristics, quantum-inspired, gate-model simulators and credential-gated providers, with a money-denominated cost ledger and a computed verdict. Sixteen cases, 121 variants, 3,255 declared solver cells. No quantum advantage is claimed; today the classical baseline usually wins.<br/><img src='/images/projects/qmine_pipeline.svg'>"
collection: portfolio
tags: [quantum-computing, optimization, qaoa, annealing, mining, benchmark, honesty]
---

The claims around quantum computing for industrial optimization are loud and the measurements are scarce. **QMine** is measurement discipline for a mining company that asks whether an annealer or a gate-model device could schedule its trucks, design a flotation circuit or cut a pit: every real engine on the same instances with the same evaluation, every run denominated in money, every skip recorded with its reason, and a verdict computed from the measurements rather than written by an advocate. It is the private, provider-integrated counterpart of the public QLab.

![QMine, real instances through the same ladder on real engines, a cost ledger and a computed verdict; today the classical baseline usually wins](/images/projects/qmine_pipeline.svg)

## The ladder, on real engines

A Problem by Solver by Instance abstraction: a problem owns its dataset-backed instances, its audited QUBO encoding, its native constrained model with hard constraints, its evaluation and its baselines; a solver is a thin adapter over one real engine. OR-Tools CP-SAT, HiGHS, networkx max-closure and a treewidth-bounded exact decomposition; field heuristics and a random floor; dwave-samplers simulated annealing, tabu, steepest descent, path-integral quantum annealing and rotor-model annealing; dwave-hybrid; Torch simulated bifurcation; QAOA with warm-start, CVaR, recursive, DCQO and BF-DCQO variants, a hardware-efficient VQE and an independent PennyLane implementation; a quantum kernel and a variational regressor for a flotation soft sensor with leakage-safe temporal splits. Eleven provider lanes wired and credential-gated. Sixteen cases, 121 variants, 3,255 declared solver cells, baked completely with 1,631 explicit skips and zero completeness problems.

![QMine, the App on a supply-packing case: the quantum lane ties the classical baseline on objective, the classical solver is three times faster](/images/projects/qmine_app_dark.png)

## What the measurements say today

On tiny pit instances the problem-aware gate variants reach the proven optimum where plain QAOA and the problem-agnostic VQE do not; on supply packing the quantum lane ties the classical baseline while the classical solver is three times faster; on the flotation soft sensor ridge regression beats both quantum models and the quantum kernel is worse than the persistence floor. The honesty spine is on screen per case: as of the research date there is no third-party-confirmed quantum advantage for any industrial optimization problem. Two formulations have no located prior art (truck dispatch, flotation circuit design); crew rostering was miscounted as a third and its production prior art is recorded on its own case page. Deployed as a service on the ML VPS behind an operator session, with both browser gates re-run against the deployment; the repository stays private because the backend holds provider credentials. No adopter yet, and the lifecycle stays building.

[Live](https://qmine.ml.fasl-work.com) (operator session)
