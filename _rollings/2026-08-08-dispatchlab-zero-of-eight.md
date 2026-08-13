---
title: 'DispatchLab: the policy I most wanted to work wins 0 of 8 seeds'
date: 2026-08-08
permalink: /rollings/2026/08/dispatchlab-zero-of-eight/
tags:
  - mining
  - simulation
  - negative-results
  - honesty
---

DispatchLab: the policy I most wanted to work wins 0 of 8 seeds
======

![DispatchLab: nine dispatch policies on one discrete-event simulation with common random numbers](/images/projects/dispatchlab_app.png)

[DispatchLab](https://dispatchlab.fasl-work.com) is a truck-and-shovel dispatch bench: a deterministic next-event-time-advance discrete-event simulation with an integer-tick clock, seeded common random numbers, rimpull and grade kinematics, road traffic and match factor, with nine policies scored on it against a closed-form capacity oracle. Five heuristics, a Hungarian joint assignment, two learned policies and a distilled Monte-Carlo rollout.

The Monte-Carlo rollout under cycle-time uncertainty was the one I expected to win. It does not:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Published null: the certainty-equivalent rollout wins 0 of 8 evaluation seeds.</strong><br/>
<span style="color:#5a9ac0;font-size:13px;">The only claim that survives is the deterministic one, and it is small: at or above the base policy on three cases by +0.42%, +1.16% and +1.64%. Under uncertainty there is nothing to report, so nothing is reported.</span>
</div>

The imitation lane is more interesting for being honest about what it imitates. Trained on 141,149 logged decisions, rollout distillation reaches 0.841 accuracy against 0.771 and 0.740 for the alternatives, and the best policy it is imitating is the plain Hungarian assignment. A learned model that reproduces an operations-research solution quickly is a useful thing; a learned model presented as beating one it is actually copying is not.

There is zero real fleet data in it, and that is stated rather than implied: ten samples come from [`minehaulsim`](https://pypi.org/project/minehaulsim/), my own Apache-2.0 package, and two are desensitized OpenMines configurations. [Live](https://dispatchlab.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_DispatchLab).
