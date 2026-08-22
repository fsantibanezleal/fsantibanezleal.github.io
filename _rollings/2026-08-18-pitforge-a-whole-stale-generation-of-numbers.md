---
title: 'PitForge: the app was right and every number I had published was a generation old'
date: 2026-08-18
permalink: /rollings/2026/08/pitforge-a-whole-stale-generation-of-numbers/
tags:
  - mining-optimization
  - mine-planning
  - honesty
  - benchmarks
---

PitForge: the app was right and every number I had published was a generation old
======

![PitForge: the ultimate pit and nested Whittle shells, solved in the browser](/images/projects/pitforge_app.png)

I ran an eleven-dimension adversarial review over [PitForge](https://pitforge.fasl-work.com), 438 claims opened and 145 findings surviving refutation. Its most useful finding was not about the optimiser at all. It was that the working tree I had reviewed was not the product. The checkout sat on a task branch at version 0.12.000; `origin/main` was 28 commits ahead at v0.13.001, fully merged, and the live site was byte-identical to it on all fourteen artifacts.

So six of the eleven dimensions had been reviewing a superseded branch. Worse, so had my public writing.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Not one stale number. A whole stale generation of them, on five external surfaces plus a DOI'd PDF.</strong><br/>
grade-nn: an apparent R2 0.9613 <em>tie</em> with ordinary kriging at 0.958, published as a tie, was in fact a 0.8757 <strong>loss</strong> to kriging at 0.9333.<br/>
pit-surrogate: AUC 0.9811 against a "baseline" of 0.7642 became AUC 0.9123 against 0.5. The 0.7642 was a majority-class accuracy and had never been an AUC baseline at all.<br/>
scheduling: a 10.46 percent gap that no longer existed as a field became 3.81 percent on the published <code>newman1.cpit</code> scenario and 11.29 percent on a separate synthetic twin.<br/>
<span style="color:#5a9ac0;font-size:13px;">v0.13.000 had replaced a leaky random-row split with a grouped leave-one-geology-out split, and re-parsed the published scenario. Every headline I had written predated it.</span>
</div>

The mechanism is worth naming because it is not carelessness, it is structure. **The app never drifted, because the app reads the JSON. The prose drifted, because the prose types it.** Every figure in the application is rendered from the committed artifacts at run time, so when the artifacts moved, the application moved with them, silently and correctly. Every figure in a product page, a post, a CV line and a report was a human transcription made on a particular afternoon, and transcriptions do not update themselves.

The two honest consequences. First, the smaller numbers are the real ones, and the grade network losing outright to ordinary kriging is a better result to publish than a tie, because it is what a fast approximation is supposed to do next to a proper geostatistical estimator. Second, a correction is not finished when the prose is fixed: it is finished when the number can no longer be typed by hand.

All five surfaces were corrected the same day. The exact optimiser was never in question: it still reproduces the published optima of newman1, zuck_small and kd to relative errors near 1e-10, and those, unlike anything above, are properties of the algorithm rather than of the afternoon.

[Live](https://pitforge.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_PitForge).
