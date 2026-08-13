---
title: 'CoreLog: the useful output is knowing when the core is unfamiliar'
date: 2026-08-03
permalink: /rollings/2026/08/corelog-knowing-when-the-core-is-unfamiliar/
tags:
  - computer-vision
  - mining
  - out-of-distribution
  - honesty
---

CoreLog: the useful output is knowing when the core is unfamiliar
======

![CoreLog: per-window lithology with an out-of-distribution flag, running client-side](/images/projects/corelog_app.png)

[CoreLog](https://corelog.fasl-work.com) reads drill-core trays and returns lithology per window. The classifier itself does well (accuracy 0.994 against a 0.9286 colour and texture baseline), but a classifier that is always confident is a liability on core, because the next hole can carry rock the model has never seen and it will still return a class.

So the shipped output is two things, not one: **a lithology and a flag for when the core is unfamiliar.**

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The out-of-distribution detector was chosen by measurement, not by fashion.</strong><br/>
Nine detectors benchmarked offline on identical splits.<br/>
<span style="color:#5a9ac0;font-size:13px;">Shipped: Mahalanobis distance in the CNN's 64-d feature space, <strong>AUROC 0.9463</strong>. The incumbent pixel autoencoder scored <strong>0.3078</strong>, which is worse than a coin, and it was replaced rather than defended.</span>
</div>

Two guards keep the accuracy honest. The split is **grouped by hole** (14 train, 4 test), not by tray, so a model cannot pass by memorising the hole it is looking at. And a **label-permutation null** collapses the whole thing to chance (0.1387 against the 0.1429 you would expect from six classes), which is what tells you the signal is in the rock rather than in the pipeline.

Real drill-core photographs (DCID, CC BY-NC 4.0) are used as an out-of-distribution and real-head evaluation lane only, and the app says so rather than implying it was trained on them. Everything runs 100 percent client-side. [Live](https://corelog.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_CoreLog).
