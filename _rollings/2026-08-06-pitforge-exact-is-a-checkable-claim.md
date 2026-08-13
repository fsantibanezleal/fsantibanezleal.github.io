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
newman1 (1,060 blocks, 5.2 ms), zuck_small (9,400 blocks, 237 ms), kd (14,153 blocks and 219,778 precedences, 259 ms median).<br/>
<span style="color:#5a9ac0;font-size:13px;">Two further instances are excluded, with the reasons committed rather than omitted. Every solve also asserts the max-flow duality identity, pitValue = sum(positive) - maxflow, so a wrong answer cannot pass quietly.</span>
</div>

The learned layer is scoped by the same rule. A grade neural net reaches R2 0.9613 against ordinary kriging at 0.958, which is a tie, and the app says so: it is offered as a fast approximation, never as something that beats the exact result. The CPIT LP relaxation that gives a certified NPV upper bound publishes its **10.46 percent integrality gap** rather than hiding it, and it is an artifact rendered from JSON, never a live claim.

That last point is where [PhaseFlow](https://phaseflow.fasl-work.com) picks the problem up: PitForge answers which blocks are worth mining, PhaseFlow answers when. [Live](https://pitforge.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_PitForge).
