---
title: 'CareerTwin at 0.14: a match score that cannot be read as a hiring probability'
date: 2026-09-18
permalink: /rollings/2026/09/careertwin-a-score-that-is-not-a-probability/
tags:
  - careertwin
  - agentic
  - privacy
  - engineering
---

CareerTwin at 0.14: a match score that cannot be read as a hiring probability
======

![CareerTwin, from confirmed evidence to a deterministic match, to ranked gaps and grounded drafts, with a bounded agent that only proposes](/images/projects/careertwin_pipeline.svg)

CareerTwin's 0.14 line started today with a guards job in CI, re-pinned base image digests and dependabot targeting develop, the maintenance a live product accumulates. The product itself is the seeker's own instrument: job-search tooling is built for the other side of the table, it ranks people for employers and scores them with numbers that read like probabilities, and it asks the seeker to hand their history to a service that keeps it. Here one account owns one evidence-centred profile and any number of opportunities, applications, tasks and generated artifacts, on hardware the seeker controls.

The match score is a versioned alignment measure with coverage and uncertainty. Required, preferred and eligibility requirements are kept apart, the score states how much of each is covered by confirmed evidence, and every component is explained reproducibly, lowest-supported first. It tells the seeker what to fix, not whom to beat. A recommendation matrix over repeated gaps across a target portfolio turns dozens of postings into a short list of capabilities to build or to evidence, and drafts are grounded in confirmed evidence so no fabricated line reaches an application.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The agent proposes; the seeker approves; the product runs fully with no provider at all.</strong><br/>
Deterministic services own scoring and every canonical write. The agent harness is bounded, evidence-cited workflows behind adapters for four model providers, and every proposed canonical write needs explicit approval. It does not rank candidates for employers, infer protected traits, scrape unrestricted job sites, auto-apply or send outreach.<br/>
<span style="color:#5a9ac0;font-size:13px;">Release gates: 82 backend tests, strict MyPy and Ruff, six agent contracts, 22 frontend tests, CodeQL, container scans, an SBOM, and a load contract of 10 users over 1,000 opportunities at 8.059 ms p95 against a 2.5 s limit.</span>
</div>

Two gates stay honestly open and are tracked as issues: operator-consented activation of the official ESCO 1.2.1 archive, and a product-scoped managed model key followed by a real production agent and voice smoke. No named external adopter and no measured job-search outcome exist, and the plan records the value axis as an internal demonstration.

[Live](https://careertwin.ml.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_CareerTwin)
