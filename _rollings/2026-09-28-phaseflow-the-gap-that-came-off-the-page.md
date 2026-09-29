---
title: 'PhaseFlow, a follow-up: the 2.49 percent was a bug, and the 1.26 percent belonged to another problem'
date: 2026-09-28
permalink: /rollings/2026/09/phaseflow-the-gap-that-came-off-the-page/
tags:
  - mining-optimization
  - mine-planning
  - optimization
  - corrections
---

PhaseFlow, a follow-up: the 2.49 percent was a bug, and the 1.26 percent belonged to another problem
======

![PhaseFlow: a year-coloured pit with NPV, bound, gap and spatial-coherence readouts](/images/projects/phaseflow_app.png)

On 9 and 10 August I wrote that PhaseFlow's optimality gap on the MineLib `newman1.cpit` instance was 2.49 percent against a published 1.26 percent, that the published schedule was better than mine, and that the number would stay on the page. Entries here are not edited after they go out, so this is the follow-up. The number is gone, for two reasons, and both were mine to find sooner.

The first is a bug. The sliding-time-window rung, the method that produced the shipped schedule, took a `window` argument that changed nothing: it was a one-period-at-a-time greedy carrying the citation of a look-ahead method. Once the window really looked ahead, the best schedule on newman1 rose to 24,149,869, which is 1.37 percent below its own LP bound.

The second is the comparison itself. The 1.26 percent comes from Tables 3 and 4 of Jelvez, Morales and Nancel-Penard (MPES 2018), and it is measured against their PCPSP LP bound, the bound of a richer problem than the one PhaseFlow solves. Two percentages over two different denominators are not a contest. The product now shows the two side by side and says so. The ordering check I described in August still holds: a CPIT bound has to sit below a PCPSP bound, and 24,486,184 sits below 24,486,549 by 365 units.

What made the remaining gap readable is a number that is not mine. A public AMPL notebook that parses the MineLib files reports a Gurobi 13 solve of newman1 as CPIT, with an integer objective of 24,176,864.82 and a matching best bound. PhaseFlow cites that log and has not reproduced its branch-and-bound tree. Against it, the schedule is 0.11 percent lower.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Four value levels on newman1, and where the distance between them comes from.</strong><br/>
Resource-at-a-time bound 24,487,410.43 &nbsp;|&nbsp; joint CPIT LP bound 24,486,184.09 &nbsp;|&nbsp; external integer optimum 24,176,864.82 &nbsp;|&nbsp; sliding-window schedule 24,149,869.40<br/>
bound minus schedule = 1,226.34 (the looser bound) + 309,319.27 (the LP's integrality gap) + 26,995.42 (the scheduling method)<br/>
<span style="color:#5a9ac0;font-size:13px;">Add value differences, not the displayed percentages: each percentage has its own denominator. Most of the 1.37 percent is integrality, which no schedule can close. For the other twelve cases no integer optimum is verified, so their gaps cannot be split this way.</span>
</div>

The August post said that an anchor you only keep when you win is decoration. The same holds for an anchor you keep after it stops being true. PhaseFlow 0.07.005 is live, with the corrected table on its Benchmark page and the source comparison in its documentation. [Live](https://phaseflow.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_PhaseFlow) · [the comparison, with its limits](https://github.com/fsantibanezleal/CAOS_PhaseFlow/blob/main/docs/cases/newman1-external-optimum.md)
