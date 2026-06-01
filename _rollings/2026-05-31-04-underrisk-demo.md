---
title: 'An Operator Dashboard for Explainable Risk'
date: 2026-05-31
permalink: /rollings/2026/05/underrisk-demo/
tags:
  - Geotechnical
  - Mining
  - Visualization
  - SHAP
---

An Operator Dashboard for Explainable Risk
======

UnderMine Risk is a demo of the operator-facing last mile for explainable geotechnical risk: weekly per-extraction-point risk on a deck.gl mine map.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Two design choices I'd defend:</strong><br/>
aggregation rolls up by riskMax + maxDelta, never the mean — so an escalating point can't hide in an average · every view exports to a printable monthly report<br/>
<span style="color:#5a9ac0;font-size:13px;">SHAP history per point explains why the risk moved week over week. Runs on fully synthetic data behind authentication — the engineering of an operator UI, not a production safety system.</span>
</div>

Next.js 16 + React 19 over a weekly Python pipeline. Demo (auth-gated) at [underrisk.fasl-work.com](https://underrisk.fasl-work.com).
