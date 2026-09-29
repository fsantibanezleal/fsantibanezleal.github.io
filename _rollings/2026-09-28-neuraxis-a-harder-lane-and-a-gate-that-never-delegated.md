---
title: 'Neuraxis 0.02.006: a harder lane where the planner helps, and a learned gate that still never delegated'
date: 2026-09-28
permalink: /rollings/2026/09/neuraxis-a-harder-lane-and-a-gate-that-never-delegated/
tags:
  - neuraxis
  - agent-systems
  - software-control
  - negative-results
---

Neuraxis 0.02.006: a harder lane where the planner helps, and a learned gate that still never delegated
======

![Neuraxis and reflexmesh, typed events through a fast path with verified effects, an allocation gate and a recruited slow path](/images/projects/neuraxis_pipeline.svg)

On 24 September I wrote that on the frozen 19,488-episode matrix both fitted allocation gates chose never to defer. That result has a weakness I should have named then: a fixed controller solves every core task, so the core cannot show when a slow reasoner helps, and a gate that never defers is simply right there. Neuraxis 0.02.006 and reflexmesh 0.1.1, released on 28 September, add a lane built to remove that ceiling.

The semantic-transfer lane keeps the twelve published methods and their frozen checkpoints and adds eight compositional task families, nominal and boundary variants and eight held-out seeds: 128 episodes per method, 1,536 in all. Each episode needs three dependent transformations of a seeded JSON list; at every stage three registered operations share the same types and the same numeric feature but produce different values, tool names are opaque hashes, and two families change the required transformation across seeds. The executor writes three real files, and an independent check reads them against the expected chain. An accepted receipt is not a success.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Verified successes out of 128, with the local model qwen3.5:4b as the slow path.</strong><br/>
M04 XGBoost 2 &nbsp;|&nbsp; M07 GRU 0 (128 invalid outputs) &nbsp;|&nbsp; M09 always-planner 38 (925 delegations, 18.9 s per episode) &nbsp;|&nbsp; M12 learned controller 18 (375 delegations, 7.7 s)<br/>
<span style="color:#5a9ac0;font-size:13px;">Paired, M12 beats M09 on 2 cases, loses on 22 and ties on 104. The lane removes the trivial ceiling, and on it the planner does help; the learned hand-off does not capture that help, it trades it for speed. An offline routing gate fitted on four families, calibrated on two and held out on the last two delegated zero times on the 32 held-out episodes and verified none; always-planner verified 10 and a hash-half selector 7.</span>
</div>

So the answer is still negative, and now it is negative on a lane where it could have come out the other way. The run is saved whole, checked by an audit script against its index (SHA-256 recorded with the model and source digests), and the routing study has its own audit over every paired first observation. Thirty-five method, case and variant cells vary across seeds, so the lane carries its own noise, which is reported with it. One correction to the September 24 entry: hosted CI, then blocked by account billing, passes again on both repositories. No AGI, no biological equivalence and no learned superiority are claimed.

[Live](https://neuraxis.ml.fasl-work.com) · [reflexmesh on PyPI](https://pypi.org/project/reflexmesh/) · [the semantic-transfer protocol and verdict](https://github.com/fsantibanezleal/reflexmesh/blob/main/docs/evaluation/semantic-transfer.md)
