---
title: "ADRA — Adversarial Dev Review Agent"
date: 2026-07-15
excerpt: "A deterministic-first, adversarial-validation engine for the software lifecycle: deterministic tools run first and become grounding the model may not contradict, a blocking critic tries to refute each artifact instead of blessing it, and the loop escalates to a human where nothing deterministic backs the verdict. Live console, offline-capable, published on PyPI as adra.<br/><img src='/images/projects/adra_app.png'>"
collection: portfolio
tags: [agentic-ai, code-review, adversarial-validation, llm, provenance, developer-tools]
---

A **deterministic-first, adversarial-validation engine** for the software lifecycle. The design premise: an LLM review that can only agree with itself is worthless, so the loop is built to disagree. Live console at [adra.fasl-work.com](https://adra.fasl-work.com), published on PyPI as [adra](https://pypi.org/project/adra/), Apache-2.0.

![ADRA — deterministic tools first, an adversarial critic, an LLM-as-judge, and human gates](/images/projects/adra_app.png)

## Deterministic first, adversarial always

- **Deterministic tools run FIRST** (git, the exact CI command, bundle validation, a language/leak scan, SQL probes) and their output becomes two things at once: grounding the model may not contradict, and evidence in an immutable provenance log.
- A **blocking adversarial critic** tries to refute each artifact instead of blessing it; an **LLM-as-judge** scores with swap-and-average to cancel position bias.
- Where nothing deterministic backs a verdict, the loop **escalates to a human** rather than guessing. Read-only by default, with human gates on PR create, push and merge.

Six skills (code review, PR evaluation, experiment, improve, document, decide) run the same loop over four real connectors plus an offline emulator, so the whole engine **runs offline with no API key**. Version 0.x on purpose: the connector-phase security controls are labelled planned, and the page says so.
