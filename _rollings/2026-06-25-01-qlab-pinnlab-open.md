---
title: 'Two More Labs, and the Honesty Tax'
date: 2026-06-25
permalink: /rollings/2026/06/qlab-pinnlab-open/
tags:
  - Quantum
  - PINN
  - ScientificML
  - OpenSource
---

Two More Labs, and the Honesty Tax
======

Two more open, in-browser labs are live, and both made me pay what I've started calling the honesty tax — the cost of reporting the result that doesn't sell.

**[QLab](https://qlab.fasl-work.com)** is a quantum-computing lab that runs the real frameworks — Qiskit, PennyLane, Cirq, Stim — on 20 worked cases, and for each one it runs the *classical* baseline right next to the quantum one. The honest finding, with the numbers on screen, is the one nobody markets:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Across 20 cases: 0 practical, pay-for-it quantum speedups.</strong><br/>
At lab scale, classical still wins. QLab does flag the genuinely quantum stuff — CHSH really violates the classical bound, S = 2√2 > 2 — but it labels that as <em>nonlocality</em>, not a speedup. Every committed trace ran on a simulator; there is no real-hardware claim hiding anywhere.
</div>

The interesting engineering is the *Problem × Solver* shape: a method-agnostic problem meets a thin adapter over each framework, so the same MaxCut or Grover case runs through five engines and you compare them like-for-like. The browser runs an exact TypeScript state-vector simulator for the small cases (≤ 12 qubits) live; the rest are precomputed and replayed.

**[PINN-Lab](https://pinnlab.fasl-work.com)** is the other one — a runnable catalogue of 19 Physics-Informed Neural Network cases. The architecture I like: train each PINN offline with DeepXDE, validate it against an analytic / FEM / real-data anchor, export to ONNX, and then let the browser **re-infer it live** with onnxruntime-web. Because the physical parameter is a network input, you drag a slider and the trained network re-solves the PDE in real time.

![PINN-Lab — train offline, re-solve live in the browser](/images/projects/pinnlab_architecture.svg)

And the honesty tax again: I publish the relative-L2 for every case, including the ones that sit at the known PINN limits — Helmholtz around 10%, the lid-driven cavity around 17% — because pretending PINNs are uniformly accurate would make the whole catalogue useless as a map of *where they actually work*. Only one of the 19 cases is trained on real data (NOAA soil temperatures); the rest are honest synthetic anchors, labeled as such. It is not a replacement for a good FEM solver, and it says so. [QLab source](https://github.com/fsantibanezleal/CAOS_QLAB) · [PINN-Lab source](https://github.com/fsantibanezleal/CAOS_PINNLAB).
