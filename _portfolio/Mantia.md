---
title: "Mantia — Agentic Industrial-Maintenance Suite"
date: 2026-06-12
excerpt: "A private suite of agentic assistants for industrial asset maintenance, shaped to enterprise EAM data via OData — a portal hub plus three specialist agents on one shared agent core.<br/><img src='/images/projects/mantia_architecture.svg'>"
collection: portfolio
tags: [agentic-ai, maintenance, odata, eam, private]
---

> **Private product.** This is proprietary work; the live deployment is private and behind access control. This page describes the architecture and intent without exposing client data, names, or internal logic.

**Mantia** is a hub-and-agents suite for industrial asset maintenance. A portal hub presents a data-driven catalog of agents with lifecycle tiles and a business case per agent; three specialist agents sit behind it — one drafts maintenance **work orders**, one plans **spares and reservations** against material stock, one **triages notifications** — and all share a single agent core.

## The pattern

The shared core is a generic **OData V2 connector** (with CSRF), an agent base, and a common web baseline. The connector runs against a faithful **mock** of the enterprise schema in development and a **real** backend in production — so the same agent code is developed, demoed, and validated without ever touching production, then promoted unchanged.

![Mantia — agentic industrial-maintenance suite](/images/projects/mantia_architecture.svg)

## What it demonstrates

- A reusable accelerator: each new use case becomes a *thin* specialist agent on the shared core.
- A business-legible hub (catalog, lifecycle, business case) over the technical agents.
- Mock-first integration that de-risks working against heavyweight enterprise systems.
- Deployed live (private), dual-target across a VPS and Azure Container Apps.
