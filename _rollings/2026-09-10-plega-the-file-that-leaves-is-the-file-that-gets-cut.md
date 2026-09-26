---
title: 'Plega: the file that leaves the workshop is the file that gets cut'
date: 2026-09-10
permalink: /rollings/2026/09/plega-the-file-that-leaves-is-the-file-that-gets-cut/
tags:
  - plega
  - paper-engineering
  - geometry
  - fabrication
---

Plega: the file that leaves the workshop is the file that gets cut
======

![Plega, one editable design moved as rigid panels, diagnosed, repaired with pinned comparisons and exported at actual size](/images/projects/plega_pipeline.svg)

A paper mechanism is designed flat, judged in motion and fabricated at actual size, and the three usually live in three tools that do not agree: a drawing that cannot move, a rendering that cannot be cut, and a print whose millimetres drifted somewhere in between. Plega, live at its own domain since yesterday and corrected today with direct editing on the canvas, keeps one editable design as the source and does the rest from it.

The rigid-paper view moves the design as zero-thickness panels. The diagnoses are explicit: overlap within a lane, collision, separation. Repair proposals are finite, pinned and compared side by side against the original. Export is calibrated PDF and SVG at actual size, plus FOLD and JSON, with every physical coordinate in millimetres. Twelve cutwork compositions, six original starters over two restricted mechanism families and up to six separated lanes, and two deliberately invalid repair cases, shipped so the diagnoses can be seen failing correctly.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The model says what it is not.</strong><br/>
Rigid zero-thickness panels do not predict material stiffness, fold forces, glue performance, printer calibration or physical assembly success. A lane-bound overlap means uncertified separation, not necessarily a collision. Finite repair proposals do not claim global optimality.<br/>
<span style="color:#5a9ac0;font-size:13px;">The physical build stays the maker's responsibility, and the site says so instead of implying a guarantee.</span>
</div>

Each release is recorded with its exact commit, a release identifier and the Quality and Pages run that verified source and data, the production build, a locked Chromium, artifact immutability and the custom-domain publication. Apache-2.0 code, MIT design data, the embedded Noto Sans under its OFL attribution. It is separate from its sibling Floraria and keeps its own history.

[Live](https://plega.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_Plega)
