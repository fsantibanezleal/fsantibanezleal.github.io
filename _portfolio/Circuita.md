---
title: "Circuita — Stochastic Mineral-Tracking Engine & Console"
date: 2026-06-08
excerpt: "A private analysis console built on a stochastic cellular-automaton engine that tracks material through a processing circuit, with a self-contained bilingual report export."
collection: portfolio
tags: [mining, cellular-automaton, simulation, reporting, private]
---

> **Private product.** This is proprietary work; the deployment is private. This page describes the architecture and intent without exposing internal data or logic.

**Circuita** drives a **stochastic cellular-automaton** engine that simulates how material moves, mixes, and lags through a processing circuit — the behavior a static mass balance misses. The result renders in an operator-grade console: per-pile **fan, balance, delta and inventory** views, with monitor tabs for the circuit and for individual objects.

## What it demonstrates

- A principled stochastic engine paired with a legible console — *see where material actually goes*, not where a static balance says it should.
- A one-click report that downsamples the original series per analyzed pile and emits a **self-contained, bilingual HTML** export with inline-SVG charts — opens anywhere, no server needed.
- An architecture modal documenting the engine and the full pipeline flow.
- Deployed privately on Azure Container Apps (a Next build feeding a Python service).

The same approach — simulate the real stochastic behavior, then make it legible and shareable — generalizes to any flow system where mixing and lag defeat naive accounting.
