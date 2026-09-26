---
title: 'GapTheo: eleven readings of one orbit, and a bespoke theme removed so the shell owns the visual layer again'
date: 2026-09-24
permalink: /rollings/2026/09/gaptheo-the-shell-owns-the-visual-layer-again/
tags:
  - gaptheo
  - mathematics
  - visualization
  - engineering
---

GapTheo: eleven readings of one orbit, and a bespoke theme removed so the shell owns the visual layer again
======

![GapTheo, one orbit and eleven exact readings, with the contrast regimes kept apart](/images/projects/gaptheo_pipeline.svg)

Place the first N multiples of an irrational number on a circle and the gaps between neighbours take at most three distinct lengths. That is the three-gap theorem, one of the cleanest statements in Diophantine approximation and one of the hardest to see, because the same finite orbit is at once points on a circle, a walk through the Farey tessellation, a truncated continued fraction, a cyclic word, an interval exchange and a lattice, and textbook figures show one of these at a time.

GapTheo keeps the sorted finite orbit as the primary live calculation, computed by an exact finite direct oracle, and derives eleven linked readings from it that stay in sync as N, the rotation number and the phase move: the circular gap partition, the Farey cells with their continued-fraction certificate, return gaps, cyclic words, the lattice schematic, the two-interval exchange lens and a finite 0D Rips topology view. Twelve canonical cases, generated certificates, a staged reference pipeline, a benchmark, the manuscript source and a 35-tab wiki ship together. Seeded random placement, a farthest-point allocator and a two-frequency extension are offered as contrast regimes, labelled apart and never fed to the classical theorem. No new theorem and no formal proof is claimed.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">0.03.002, today, is a correction of my own visual drift.</strong><br/>
v0.03.000 had shipped a bespoke teal and green theme, decorative gradients, custom fonts, local copies of the shared shell and promotional headings. All of it is removed: the shell owns palette, typography, themes, cards, buttons, tabs, page structure and callouts again, and CI now rejects app-owned theming.<br/>
<span style="color:#5a9ac0;font-size:13px;">Production QA covers every route and top-level tab in both languages, the five architecture plates in both themes, direct routes and a 390 by 844 viewport with no document overflow, no gradients and no opaque-black SVG marks.</span>
</div>

Runs locally in the browser, no account or server. Apache-2.0.

[Live](https://gaptheo.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_RES_GapTheo)
