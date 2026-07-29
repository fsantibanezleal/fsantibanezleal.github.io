---
title: 'A review agent that tries to refute its own findings'
date: 2026-07-15 17:00:00
permalink: /rollings/2026/07/adra-adversarial-review/
tags:
  - agents
  - code-review
  - llm
  - honesty
---

A review agent that tries to refute its own findings
======

![ADRA: a deterministic-first adversarial dev-review console](/images/projects/adra_app.png)

[ADRA](https://adra.fasl-work.com) (Adversarial Dev Review Agent) is a deterministic-first, client-agnostic validation engine. It reviews PRs, designs and runs validation experiments, writes documentation back, and escalates to a human where a senior engineer would. It is on PyPI (`pip install adra`) and runs offline with no API key. The specific problem it targets is the one that made me build it: a code-review model that states a finding confidently and wrongly.

The AI-review market splits in two and both halves miss the same spot. Reviewers (CodeRabbit, Greptile, Qodo and the like) feed linters into an LLM, but the model's prose is the verdict, so a plausible-but-false finding leaks through. Autonomous coders (Devin, OpenHands, SWE-agent) write code and treat "tests pass" as success rather than trying to prove the change wrong. ADRA sits in the gap: a deterministic spine grounds a blocking adversarial critic whose job is to refute each artifact, not bless it.

The mechanism is the part I care about:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Deterministic-first, then adversarial:</strong><br/>
tools (git, the exact CI command, bundle validate, language and leak scan, SQL probe) run <strong>first</strong> and become the grounding the model may not contradict<br/>
a blocking critic then tries to <strong>refute</strong> every finding; each finding carries its evidence, and the run escalates when nothing deterministic backs the verdict<br/>
<span style="color:#5a9ac0;font-size:13px;">Because the deterministic floor carries the verdict, the whole loop (and the test suite) runs offline with no API key. Connecting a real provider adds the semantic layer on top; it never becomes the gate.</span>
</div>

Six skills share one loop, differing only by domain prompt and tools: code review, PR evaluation, a hypothesis-driven validation experiment, a minimum-functional improvement proposal, documentation write-back, and a human-owned routing decision. Every run leaves an immutable provenance record, writes English only, and scans anything written to disk for AI-authorship leaks.

It stays honest about its own maturity: the GitHub, Azure DevOps, Databricks and Azure connectors are implemented and an offline emulator runs the full flow, but it stays on `0.x` while the connectors are partly untested live, and the dual-LLM capability split and sandboxed egress filtering for reading untrusted repo content are planned, not yet built. The engine is the public OSS tool; a separate private console is the connected instance. [Live](https://adra.fasl-work.com) · [source](https://github.com/fsantibanezleal/ADRA) · `pip install adra`.
