---
title: 'Neuraxis: a controller that can be trusted with the write, and fitted gates that chose never to defer'
date: 2026-09-24
permalink: /rollings/2026/09/neuraxis-the-fitted-gates-chose-never-to-defer/
tags:
  - neuraxis
  - agent-systems
  - software-control
  - honesty
---

Neuraxis: a controller that can be trusted with the write, and fitted gates that chose never to defer
======

![Neuraxis and reflexmesh, typed events through a fast path with verified effects, an allocation gate and a recruited slow path, measured over 19,488 episodes](/images/projects/neuraxis_pipeline.svg)

Neuraxis 0.02.000 is deployed today, rebuilt after I rejected the first version: simulation-first, with a page structure it had invented. Agent frameworks either route everything through a language model, slow, expensive and unaccountable for effects on files and systems, or they hard-code fast paths and lose the ability to think when the situation is new. Fast-and-slow routing alone is prior art. The research question is whether a controller can learn, from outcomes, when deliberation is worth its cost.

The rebuilt App does real work on supplied files: verify a software release (map input files, validate source and configuration, check records and relationships, verify declared hashes, build a content manifest, resolve dependencies, separate accepted and rejected rows, nine verified steps in an execution map with an action inspector), reconcile CSV records, audit sources; the originals stay untouched and the outputs are independently checked and exported. The reusable core is reflexmesh, public on PyPI from its own repository, Rust/PyO3 admission, a typed event model and the learned control; the private app declares no installable package of its own.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The corrected evaluation does not establish learned superiority, and the app says so.</strong><br/>
19,488 frozen episodes: 14,400 core, 288 structural transfer, 4,800 ablations. The learned controller M12 reached 1,160 of 1,200 core successes against 1,200 of 1,200 for the exact baseline. Both fitted allocation gates chose never to defer, and four fixed-gate ablations matched M12.<br/>
<span style="color:#5a9ac0;font-size:13px;">Novelty would require the declared ablations and held-out experiments to come out differently than they did. No AGI and no biological equivalence is claimed; private hosted CI is blocked by account billing, and the record states it.</span>
</div>

[Live](https://neuraxis.ml.fasl-work.com) · [reflexmesh on PyPI](https://pypi.org/project/reflexmesh/)
