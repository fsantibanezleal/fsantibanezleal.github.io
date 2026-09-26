---
title: 'Espira: two codes I do not own agree with the engine, and the Spanish site is Spanish'
date: 2026-09-23
permalink: /rollings/2026/09/espira-two-codes-i-do-not-own-agree/
tags:
  - espira
  - spintronics
  - optimal-control
  - reproducibility
---

Espira: two codes I do not own agree with the engine, and the Spanish site is Spanish
======

![Espira, material and switching time into the spinoct engine, a least-dissipation pulse out, checked against a replication and two independent codes](/images/projects/espira_pipeline.svg)

Espira 0.16.000 is live. Given a magnetic bit in a two-dimensional van der Waals magnet and a target switching time, it computes the field or current pulse that flips the bit for the least dissipated energy, from the spinoct engine that lives in its own published package because an optimal-control solver over Landau-Lifshitz-Gilbert dynamics is domain-agnostic and no such package existed.

The kickoff paper (Badarneh, Cai and Santos, Adv. Mater. 2026) is reproduced as a verification floor and recomputed live in the browser against its artifact. From that floor the product extends: analytic optimal paths for uniaxial and spin-orbit-torque switching, a numerical optimal-control problem for the biaxial case, GRAPE and CRAB, a reliability front, and the beyond-macrospin question answered on a free chain, where domain walls become the optimal reversal above a crossover length at long switching times.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">A product that only agrees with itself is not evidence of anything.</strong><br/>
Spirit recomputes the energy barrier to 1.4e-06 over six lattices, chains and patches; VAMPIRE re-integrates the equation of motion to 4.7e-06, both trajectories crossing the equator at 78.7319 ps. Two codes written by other people with other methods.<br/>
<span style="color:#5a9ac0;font-size:13px;">Honesty in units: the switching cost is in tesla-squared-seconds, not joules; no public experimental switching dataset exists, so the data is a parameter database with a DOI on every value; the energy floor is linear in the damping, the least pinned parameter, so every energy is a band. FePS3 is a declared negative control.</span>
</div>

What 0.16.000 fixed is embarrassing in a useful way: the Spanish site had English fallbacks and unaccented Spanish in the data strings the pages render. Every rendered string is now translated in a map held to the artifacts, and a browser gate walks every tab in both languages and fails on an English fallback or a missing accent. Fourteen gates run in CI and again against production after every release, 4,175 checks on this version; two production-only defects (a trailing-slash 404, a readout mixing case number and name while loading) were found by gating after a deploy, and are recorded as such.

[Live](https://espira.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_RES_Espira) · [spinoct on PyPI](https://pypi.org/project/spinoct/)
