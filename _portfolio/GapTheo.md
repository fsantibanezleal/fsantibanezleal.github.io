---
title: "GapTheo, a Visual Atlas of the Three-Gap Theorem"
date: 2026-09-24
excerpt: "Place the first N multiples of an irrational number on a circle and the gaps between neighbours take at most three lengths. GapTheo keeps that sorted finite orbit as the primary live calculation and synchronises it with eleven linked readings: Farey cells, continued fractions, return gaps, cyclic words, a lattice, a two-interval exchange and a finite Rips topology. Twelve canonical cases, an exact oracle, certificates, a benchmark, the manuscript and a deep wiki. No new theorem is claimed.<br/><img src='/images/projects/gaptheo_pipeline.svg'>"
collection: portfolio
tags: [mathematics, dynamical-systems, three-gap-theorem, continued-fractions, visualization, education]
---

The three-gap theorem is one of the cleanest statements in Diophantine approximation and one of the hardest to see. The same finite orbit is at once a set of points on a circle, a walk through the Farey tessellation, a truncated continued fraction, a cyclic word over two or three letters, an interval exchange and a lattice. Textbook figures show one of these at a time. **GapTheo** shows them all, as one object.

![GapTheo, one orbit and eleven exact readings, with the contrast regimes kept apart](/images/projects/gaptheo_pipeline.svg)

## One orbit, eleven exact readings

The sorted finite orbit is the primary live calculation, computed by an exact finite direct oracle; every other view is derived from it and kept in sync as N, the rotation number and the phase move: the circular gap partition, the Farey-cell geometry with its continued-fraction certificate, return gaps, cyclic words, the lattice schematic, the two-interval exchange lens and a finite 0D Rips topology view. Twelve canonical cases cover the rotation numbers a reader would reach for, each with generated certificates and validation scripts, and a staged reference pipeline bakes them for the artifact-backed benchmark.

## Contrasts kept apart

Seeded random placement, a farthest-point allocator and a two-frequency extension are offered on purpose and labelled as contrast regimes; none is treated as an input to the classical theorem. No new theorem, no formal proof and no adoption are claimed; the value axis of the plan is recorded as unvalidated.

## A visual regression, owned

![GapTheo, the circular gap partition for the golden rotation with N equal to 34](/images/projects/gaptheo_app_dark.png)

v0.03.000 had shipped a bespoke teal and green theme, decorative gradients, custom fonts and local copies of the shared shell. v0.03.002 removed all of it so that the shell owns palette, typography, themes, cards, buttons, tabs, page structure and callouts again, and CI now rejects app-owned theming. Six routes, 35 documentation tabs and five architecture plates render in English and Spanish, in both themes, down to a 390 pixel viewport; the manuscript source and a public deep research review ship in the repository. Runs locally in the browser, no account or server. Apache-2.0.

[Live](https://gaptheo.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_RES_GapTheo)
