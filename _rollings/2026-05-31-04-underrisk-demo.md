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

Every machine-learning safety project I have worked on in mining hits the same wall, and it has nothing to do with the model. You build a weekly risk predictor — rockburst and slope-instability risk from seismic and geotechnical features — you validate it, you even add SHAP so it's explainable. And then it sits in a notebook, producing a number per extraction point per week that no shift supervisor will ever read. The model is fine. The last mile is missing. UnderMine Risk is a demo of that last mile.

It puts the risk on a map. Every extraction point (PEX) gets its predicted weekly risk rendered on a deck.gl top-down view of the mine, across multiple areas, with the SHAP history behind each point so an operator can see not just *that* a zone is escalating but *why*, week over week. The model output stops being a column in a CSV and becomes something you can point at in a meeting.

![UnderMine Risk — per-PEX weekly risk on an interactive mine map](/images/projects/geotechnical_risk.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Two design choices I would defend in any review:</strong><br/>
Aggregation layers (street / sub-sector / cluster) roll up by riskMax + maxDelta — never the mean.<br/>
<span style="color:#5a9ac0;font-size:13px;">In a safety context the whole reason to summarize is the one escalating point, and a mean is exactly the summary that buries it. Second: every view exports to a print-optimized monthly report, because the people who sign off on mine safety still sign on paper.</span>
</div>

The aggregation decision is the one I care about most. It is tempting to roll a sector up by its average risk, and it is exactly wrong: averaging is how a single dangerous point disappears into a calm neighborhood. So the roll-ups carry the maximum and the biggest week-over-week jump instead — the summary is designed to surface the outlier, not smooth it away. The actionables engine then turns an elevated point into concrete responses by lever, and the whole thing exports to a monthly PDF for the people whose workflow is still paper.

I need to be honest about what this is and isn't. The live app runs on **fully synthetic data** and is behind authentication — it is the engineering of an operator interface for explainable risk (deck.gl, aggregation logic, actionables, audit-ready reporting), not a claim that any production mine is running on it. It's a Next.js 16 + React 19 front end over a weekly Python pipeline, and it was industrialized this year out of a real geotechnical-risk modelling effort I mentored. Demo (auth-gated) at [underrisk.fasl-work.com](https://underrisk.fasl-work.com).
