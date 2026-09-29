---
title: "Neuraxis and reflexmesh, an Event-Driven Software Controller with Learned Metacontrol"
date: 2026-09-24
excerpt: "A fast, typed controller for software, files, tools and agents that recruits slower language-model reasoning only where the outcome justifies it. reflexmesh, the public Rust/PyO3 and Python core on PyPI; Neuraxis, the private app that does real work on supplied files. The evaluation over 19,488 episodes does not establish learned superiority, and the app says so.<br/><img src='/images/projects/neuraxis_pipeline.svg'>"
collection: portfolio
tags: [software-control, agent-systems, learned-metacontrol, rust, pyo3, honesty]
---

Agent frameworks either route everything through a language model, slow, expensive and unaccountable for effects on files and systems, or hard-code fast paths and lose the ability to think when the situation is new. Fast-and-slow routing alone is prior art. The question **Neuraxis** asks is whether a controller can learn, from outcomes, when deliberation is worth its cost.

![Neuraxis and reflexmesh, typed events through a fast path with verified effects, an allocation gate and a recruited slow path, measured over 19,488 episodes](/images/projects/neuraxis_pipeline.svg)

## Two repositories, one boundary

**reflexmesh**, public and on PyPI (0.1.1, nine wheels plus a source distribution), owns the Rust/PyO3 admission layer, the typed event model, the learned control and the Python integration. **Neuraxis**, the private app, owns orchestration, canonical artifacts, the API and the bilingual workbench, with no installable package of its own.

## Real work on supplied files

![Neuraxis, the App: verify a software release, nine verified steps in an execution map with an action inspector](/images/projects/neuraxis_app_dark.png)

The 0.02.000 rebuild made the App do real work: verify a software release (map input files, validate source and configuration, check records and relationships, verify declared hashes, build a content manifest, resolve dependencies, separate accepted and rejected rows), reconcile CSV records and audit sources, with independently checked outputs exported and the originals untouched. Matched controller executions compare runs and expose the controller's evidence; the five scientific routes carry shared tabs, per-paragraph citations and a bibliography. The first version, simulation-first with an invented page structure, was rejected and replaced.

## The claim, measured and not established

On the corrected matrix of 19,488 episodes (14,400 core, 288 structural transfer, 4,800 ablations) the learned controller M12 reached 1,160 of 1,200 core successes against 1,200 of 1,200 for the exact baseline; both fitted allocation gates chose never to defer, and four fixed-gate ablations matched M12.

Because a fixed controller solves every core task, the core cannot show when a slow reasoner helps, so 0.02.006 adds a separate, hash-audited semantic-transfer lane: eight compositional families, nominal and boundary variants and eight held-out seeds, 1,536 episodes across the twelve methods, each writing real files that an independent check verifies. No method is perfect: always-planner verified 38 of 128 episodes and M12 18, winning 2 paired cases, losing 22 and tying 104, faster because it calls the planner less. An offline routing gate fitted on four families and held out on two delegated zero times on the 32 held-out episodes and verified none, where always-planner verified 10.

Learned superiority is not established and no AGI or biological equivalence is claimed. Private hosted CI was blocked by account billing for a time, and the record kept that failure; product and engine CI pass again, and the app is live at 0.02.006.

[Live](https://neuraxis.ml.fasl-work.com) · [reflexmesh on PyPI](https://pypi.org/project/reflexmesh/) · [reflexmesh repository](https://github.com/fsantibanezleal/reflexmesh)
