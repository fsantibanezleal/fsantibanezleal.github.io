---
title: "Veta — Agentic Mineral-Tracking Decision Support"
date: 2026-06-10
excerpt: "A private decision-support system that turns a natural-language question — typed or spoken — about a mineral-processing operation into a traceable, evidence-backed answer.<br/><img src='/images/projects/veta_architecture.svg'>"
collection: portfolio
tags: [mining, decision-support, agents, rag, private]
---

> **Private product.** This is proprietary work; the live deployment is private. This page describes the architecture and intent without exposing internal data or logic.

**Veta** is a decision-support system for mineral-processing operations. Ask it a question — typed or spoken — and a multi-stage agent pipeline interprets the intent, assembles the relevant plant state, routes to the right solver tier (cheap heuristics first, heavier optimization only when warranted), and answers with the **supporting evidence attached** via retrieval over the tracked sites' data (RAG).

## Why it exists

In a plant, the knowledge needed to answer *"what should we do about this feed and these constraints?"* is spread across telemetry, historical runs, and expert intuition. Pulling it together is slow and hard to audit — and an answer with no traceable evidence is hard to trust on the floor. Veta compresses the loop from question to *defensible* recommendation and keeps the reasoning auditable rather than a black box.

![Veta — agentic mineral-tracking decision support](/images/projects/veta_architecture.svg)

## What it demonstrates

- A single conversational front door (text + voice) to plant decisions.
- A staged agent pipeline with **solver tiers** that spend compute only when justified.
- **RAG-grounded** answers — every recommendation carries its evidence.
- Reproducibility by construction: an offline pipeline builds per-site, content-addressed (sha256-manifested) artifacts.
- Deployed live (private), dual-target across a VPS and Azure Container Apps.

A working pattern for agentic decision support in heavy industry — fast, defensible, reproducible.
