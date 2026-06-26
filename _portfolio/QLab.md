---
title: "QLab — Quantum Laboratory"
date: 2026-06-25
excerpt: "A public, didactic quantum-computing lab that runs real frameworks (Qiskit, PennyLane, Cirq, Stim) on 20 worked cases and puts every quantum method next to its classical baseline — and honestly shows that at lab scale, classical still wins.<br/><img src='/images/projects/qlab_architecture.svg'>"
collection: portfolio
tags: [quantum-computing, qiskit, pennylane, cirq, stim, honest-benchmarks]
---

An open, didactic **quantum-computing lab**. QLab runs the *real* frameworks — Qiskit + Aer, PennyLane, Cirq, Stim — on 20 worked cases, and for each one it puts the quantum method next to its classical baseline so you can see, with real numbers, which wins and at what cost. Live at [qlab.fasl-work.com](https://qlab.fasl-work.com).

![QLab — Problem × Solver, three lanes, honest verdict](/images/projects/qlab_architecture.svg)

## The honest thesis

Across all 20 cases, **none shows a practical, pay-for-it quantum speedup** — at lab scale, classical still wins, and QLab shows qubits / gates / shots / wall-time side by side so the verdict is evidence, not a slogan. It is careful about the difference between a genuine quantum *phenomenon* and a quantum *advantage*: the CHSH case really does violate the classical bound (S = 2√2 > 2), and QLab labels that as nonlocality — **not** a speedup.

## Architecture — Problem × Solver, replay is truth

A method-agnostic problem formulation meets a thin solver adapter; adapters self-register, so adding a framework is one adapter plus one registry line. A run is a pure function of `(params, seed)` → a committed JSON trace (119 of them, with manifests). The front end only replays traces, or runs an **exact TypeScript state-vector simulator** (≤ 12 qubits) for the live in-browser lane; heavier cases are precomputed offline by the real Python engines. Static GitHub Pages, no backend.

## What it is not

Every committed trace is `ran_on: simulator` — QLab makes **no real-hardware or quantum-advantage claims**. The IBM-Quantum adapter exists but is dormant and opt-in, with zero committed QPU runs. Qiskit runs offline only; the browser lane is the custom TS simulator. Flagship algorithms are at educational scale (Shor N = 15, VQE on H₂, small QEC codes).

[Live demo](https://qlab.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_QLAB)
