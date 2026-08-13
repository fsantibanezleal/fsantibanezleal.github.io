---
title: 'CutoffGrade: the exact optimizer is the authority, the learned model is only speed'
date: 2026-08-13
permalink: /rollings/2026/08/cutoffgrade-the-exact-optimizer-is-the-authority/
tags:
  - mining-optimization
  - mine-planning
  - optimization
  - honesty
---

CutoffGrade: the exact optimizer is the authority, the learned model is only speed
======

![CutoffGrade Studio: Lane's declining cut-off trajectory with its binding stage](/images/projects/cutoffgrade_app.png)

[CutoffGrade Studio](https://cutoffgrade.fasl-work.com) computes Lane's optimal cut-off grade: the NPV-maximising declining cut-off trajectory, the NPV and the mine life, from a grade-tonnage curve plus economic and capacity inputs, live in the browser. Six characteristic cut-offs, Dagdelen medians and a year-by-year NPV fixed point, with the binding stage named at each step, because knowing whether mine, mill or market is the constraint is most of the insight.

The division of labour is the part worth stating plainly:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The exact optimizer is the authority. The learned surrogate is for speed only, never for accuracy.</strong><br/>
<span style="color:#5a9ac0;font-size:13px;">The ONNX surrogate exists so a sweep is instant, with an out-of-distribution guard beside it. Every reported answer comes from the exact solve. This is a faithful classic method, not a novel-AI claim.</span>
</div>

The measured result is modest and stated at that size: about **2.6 percent NPV uplift** for the exact Lane trajectory over the best constant cut-off, and only when a stage actually binds. If nothing binds, the sophisticated answer and the simple one agree, and a tool that hides that is selling its own complexity.

The base case is 100 percent synthetic porphyry copper and openly labelled as such, so nobody reads the NPV as a claim about a real deposit. Part of the [Faena](https://faena.fasl-work.com) hub. [Live](https://cutoffgrade.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_CutoffGrade).
