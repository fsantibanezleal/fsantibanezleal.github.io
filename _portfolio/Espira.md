---
title: "Espira, Optimal Control of Magnetization Switching in Two-Dimensional Magnets"
date: 2026-09-23
excerpt: "Given a magnetic bit in a two-dimensional van der Waals magnet and a target switching time, compute the field or current pulse that flips it for the least dissipated energy. Espira reproduces its kickoff paper as a verification floor, extends it beyond the macrospin, and answers to two codes it does not own: Spirit on the barrier to 1.4e-06 and VAMPIRE on the equation of motion to 4.7e-06. The engine is the separately published spinoct package.<br/><img src='/images/projects/espira_pipeline.svg'>"
collection: portfolio
tags: [optimal-control, spintronics, magnetization-switching, van-der-waals, llg, reproducible-research]
---

Writing a bit in a magnetic memory costs energy, and most of it is wasted: a pulse strong enough to flip the magnetization reliably is far larger than the pulse that would flip it for the least dissipation over the same time. Optimal control over the Landau-Lifshitz-Gilbert dynamics answers what the cheapest pulse is; the answer depends on the material, on whether the bit is driven by a field or a spin-orbit torque, and on whether the bit is one macrospin at all. **Espira** computes those pulses for the two-dimensional van der Waals magnets that are the current candidates.

![Espira, material and switching time into the spinoct engine, a least-dissipation pulse out, checked against a replication and two independent codes](/images/projects/espira_pipeline.svg)

## A floor that someone else published

The kickoff paper (Badarneh, Cai and Santos, Adv. Mater. 2026, doi 10.1002/adma.202523059) is reproduced as case C10 and recomputed live in the browser against its artifact. From that floor the product extends: analytic optimal paths for uniaxial and spin-orbit-torque switching, a numerical optimal-control problem for the biaxial case, conventional baselines, GRAPE and CRAB, a reliability front, and the beyond-macrospin question answered on a free chain, where domain walls become the optimal reversal above a crossover length at long switching times. Two independent codes agree with the engine: Spirit on the barrier to 1.4e-06 over six lattices, chains and patches, and VAMPIRE on the equation of motion to 4.7e-06, both trajectories crossing the equator at 78.7319 ps.

## Honesty, in units

![Espira, the App: a trajectory on the sphere, the optimal cost and the parameters with their provenance](/images/projects/espira_app_dark.png)

The switching cost is in tesla-squared-seconds, not joules; a circuit model has to convert it. No public experimental switching dataset exists, so the data is the spin-Hamiltonian parameter database with a DOI on every value. The energy floor is linear in the Gilbert damping, the least pinned parameter, so every energy is reported as a band. FePS3 is a declared negative control. The reliability preprint corrects its own earlier reading of its table: a reliable switch costs 2.5 to 15.8 times the bare cost, and the field pays only below a stability factor of about ten. Two CC-BY Zenodo preprints carry the results (concept DOIs 10.5281/zenodo.22736005 and 10.5281/zenodo.22736065), each table pinned to its artifact by a test.

## Engine, cases, gates

The engine is **spinoct**, published on PyPI from its own repository (numpy and scipy core, a torch extra for a batched lane), because an optimal-control solver over LLG dynamics is domain-agnostic and no such package existed. 25 of 26 cases are baked; two run live in the browser. Fourteen browser gates run in CI and again against production after every release, 4,175 checks on 0.16.000 with zero console errors, and the record keeps the two production-only defects gating found after a deploy rather than before. MIT, product and engine.

[Live](https://espira.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_RES_Espira) · [spinoct on PyPI](https://pypi.org/project/spinoct/)
