---
title: 'PitForge: "exact" is a checkable claim, so check it'
date: 2026-08-06
permalink: /rollings/2026/08/pitforge-exact-is-a-checkable-claim/
tags:
  - mining-optimization
  - mine-planning
  - optimization
  - honesty
---

PitForge: "exact" is a checkable claim, so check it
======

![PitForge: the ultimate pit and nested Whittle shells, solved in the browser](/images/projects/pitforge_app.png)

[PitForge](https://pitforge.fasl-work.com) solves the ultimate pit limit exactly, as a maximum-weight closure of the block-precedence graph reduced to a minimum cut (Picard's 1976 reduction) on a Dinic max-flow engine, live in the browser, and derives the nested Whittle pit shells from it.

"Exact" is the kind of word that should cost something to say, so it is tied to numbers somebody else published:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Three published MineLib optima, reproduced to 2e-9 relative error or better.</strong><br/>
newman1 (1,060 blocks, 1.9 ms), zuck_small (9,400 blocks, 111 ms), kd (14,153 blocks and 219,778 precedences, 207 ms median), as Node medians of three on the same TypeScript engine the browser runs.<br/>
<span style="color:#5a9ac0;font-size:13px;">Three further instances are excluded, with the reasons committed rather than omitted. The max-flow duality identity, pitValue = sum(positive) - maxflow, is asserted in the explicit-precedence MineLib lane and displayed as a live check on the interactive one, so a wrong answer cannot pass quietly.</span>
</div>

The learned layer is scoped by the same rule, and it loses. A grade neural net reaches R2 0.8757 against ordinary kriging at 0.9333, on a split that leaves one whole geology out, and the app says so: it is offered as a fast approximation, never as something that beats the exact result. That number used to read 0.9613 against 0.958, a near-tie, until a leaky random-row split was replaced by the grouped one, so the smaller figure is the honest one. The CPIT LP relaxation that gives a certified NPV upper bound parses the published newman1.cpit scenario (6 periods, 8 percent discount, two resource constraints), reproduces MineLib's own published LP bound to 3.7e-9, and publishes a **3.81 percent bound-to-feasible gap**, with a separate synthetic twin at 11.29 percent labelled non-comparable. It is an artifact rendered from JSON, never a live claim.

That last point is where [PhaseFlow](https://phaseflow.fasl-work.com) picks the problem up: PitForge answers which blocks are worth mining, PhaseFlow answers when. [Live](https://pitforge.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_PitForge).
