---
title: "CareerTwin, a Single-Seeker Career Evidence and Job-Search Workbench"
date: 2026-09-18
excerpt: "A self-hosted workbench where one seeker owns one evidence-centred profile and any number of opportunities, applications, tasks and generated career artifacts. The match score is a versioned alignment measure with coverage and uncertainty, never a hiring probability; the agent side is bounded, cites evidence and may only propose writes the seeker approves. Live at v0.14.5; no external job-search outcome is claimed.<br/><img src='/images/projects/careertwin_pipeline.svg'>"
collection: portfolio
tags: [career, evidence-graph, job-search, agentic, self-hosted, privacy, fastapi, postgresql, react]
---

Job-search tooling is built for the other side of the table: it ranks people for employers, scores them with numbers that read like probabilities, and asks the seeker to hand their history to a service that keeps it. **CareerTwin** is the seeker's own instrument. One account owns one evidence-centred profile and any number of opportunities, applications, tasks, agent conversations and generated career artifacts, on hardware the seeker controls.

![CareerTwin, from confirmed evidence to a deterministic match, to ranked gaps and grounded drafts, with a bounded agent that only proposes](/images/projects/careertwin_pipeline.svg)

## The score is not a probability

The match score is a **versioned alignment measure with coverage and uncertainty**. Required, preferred and eligibility requirements are kept apart, the score states how much of each is covered by confirmed evidence, and every component is explained reproducibly, lowest-supported first. It tells the seeker what to fix rather than whom to beat. A recommendation matrix over repeated gaps across a target portfolio turns dozens of postings into a short list of capabilities to build or to evidence; drafts (resume, cover letter, interview, follow-up) are grounded in confirmed evidence, so no fabricated line reaches an application.

## What it refuses to do

It does not rank candidates for employers, infer protected traits, scrape unrestricted job sites, auto-apply or send outreach. Deterministic services own scoring and every canonical write; the agent harness is bounded, evidence-cited LangGraph workflows behind Pydantic AI adapters (xAI, OpenAI, Anthropic, Google), **every proposed canonical write needs explicit approval**, and the whole product runs with no provider at all.

## Nine modules, one boundary

Profile and evidence (encrypted document ingestion, a confirmation inbox, GitHub portfolio snapshots, a STAR bank, immutable resume variants, JSON Resume import and export), opportunity intelligence (manual, pasted, file, bounded-URL and revocable browser-extension capture), deterministic matching, improvement and grounded drafts, search operations (board, contacts, tasks, RFC 5545 calendar, consent-bound calendar and email connectors, funnel analytics), the agent concierge, invite-only administration, occupational intelligence (ESCO 1.2.1 and O*NET 30.3 importers with checksums, a pinned 20-case EN/ES retrieval benchmark and a non-degradation gate; O*NET active with 1,150 concepts and 12,684 relations), and eight versioned repository skills over the same CLI and API contracts. Production secrets, documents, databases and backups never enter the public repository; tenant filters and PostgreSQL row-level security are both enforced; uploads pass ClamAV before extraction; URL capture pins every destination and redirect against SSRF and DNS rebinding.

## Gates and what stays open

![CareerTwin, the public entry of the self-hosted space](/images/projects/careertwin_app_dark.png)

v0.14.5 passed 82 backend tests, strict MyPy and Ruff, six agent contracts, 22 frontend tests, dependency and secret audits, CodeQL, container scans, an SBOM, and a load contract of 10 users over 1,000 opportunities at 8.059 ms p95 against a 2.5 s limit. Production is detached at the reviewed commit on one VPS (PostgreSQL 17.11, pgvector 0.8.6, an isolated 39-table restore verified off-host). Two gates stay open and named: operator-consented activation of the official ESCO 1.2.1 archive, and a product-scoped managed model key followed by a real production agent and voice smoke. No named external adopter and no measured job-search outcome exist, and the plan records the value axis as an internal demonstration.

Stack: FastAPI, Pydantic, SQLAlchemy, Alembic, SQLite locally and PostgreSQL 17 with pgvector hosted, LangGraph, Pydantic AI, React, TypeScript, Vite, Sigma.js, ECharts, Docker Compose. Public, MIT.

[Live](https://careertwin.ml.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_CareerTwin)
