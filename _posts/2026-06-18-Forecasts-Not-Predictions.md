---
title: 'Forecasts, not predictions — two weeks of building honesty into the product'
date: 2026-06-18
permalink: /posts/2026/06/forecasts-not-predictions/
tags:
  - seismic
  - forecasting
  - calibration
  - devops
  - research
  - honesty
---

Forecasts, not predictions
======

The last two weeks had one quiet thread running through everything I shipped, and it wasn't a technology — it was a discipline. Honesty, made structural. Not as a value statement on an About page, but as a gate in the pipeline that won't let me lie even when it would be flattering to.

The clearest expression of it went live: [CAOS Seismic](https://seismic.fasl-work.com), a probabilistic earthquake *forecaster*. The word is load-bearing. A *prediction* is a deterministic "an earthquake will / will not happen"; a *forecast* is a probability strictly between 0 and 1. Deterministic earthquake prediction is, by the physics, effectively impossible (Geller et al., 1997) — so I built the honest alternative, Operational Earthquake Forecasting: a bounded, calibrated probability of an event in a region and magnitude band over the next 1, 2, or 7 days, always shown next to its long-term baseline.

![CAOS Seismic — heavy compute offline, the web is a pure viewer](/images/projects/seismic_pipeline.svg)

## Honesty as a release gate

It is easy to *say* a model is good. CAOS Seismic is built so that saying it isn't enough. Three rules do the work:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Three non-negotiables:</strong><br/>
<strong>1. Calibration is a release blocker.</strong> An uncalibrated probability does not ship; the reliability diagram ("when we said 5%, it happened ~5% of the time") is the headline artifact.<br/>
<strong>2. Skill is measured, not asserted.</strong> Information gain per earthquake in <em>nats</em>, via CSEP, against both a Poisson null and ETAS. ROC/AUC is banned — it's blind to calibration.<br/>
<span style="color:#5a9ac0;font-size:13px;"><strong>3. A stronger model must earn the map.</strong> The neural challenger only replaces the ETAS baseline if it wins prospectively <em>and</em> stays calibrated.</span>
</div>

This fortnight the context-conditioned neural challenger cleared the in-loop gate — +0.075 nats per earthquake over ETAS, calibrated — after I fixed a ~490× absolute-rate over-forecast by calibrating on the *same* grid the gate uses. It is a real result. It is also not enough: pseudo-prospective validation is still pending, so ETAS still owns the public map. The gate held even though I wanted to walk through it. That's the point of a gate.

## The same discipline, in a research surface

The seismic gate has a sibling in my hyperspectral topic-modelling work. A deep review this fortnight found that an earlier write-up had claimed a clean "triple-axis win" for one spectral representation. An audit knocked two of the three axes down to ties — and the honest, surviving claim is narrower and less impressive. I corrected it on the live app and in the manuscripts. A research surface that overclaims is worse than one that's a little behind, because the overclaim costs you the only thing that compounds: trust. (There was also a beautiful bug — a `NaN` from a `0/0` in normalized pointwise mutual information was silently choosing the number of topics. Fixed by taking the analytic limit.)

## And the unglamorous part

Honesty in infrastructure looks like *not leaving secrets lying around*. I gave a batch of my private apps a second deployment target on Azure Container Apps — dual-target alongside their VPS — with no long-lived credentials anywhere: OIDC federated identity for CI (a short-lived token exchanged at run time, nothing stored), and a user-assigned managed identity with a narrow `AcrPull` role so the container pulls its own image with no registry admin creds. Bicep describes it; scale-to-zero keeps idle cost near nothing. It produced no demo you can fly through, which is fine — some weeks the deliverable is that nothing can leak.

## Why this is the thread

I keep relearning the same manager's lesson: the deliverable is knowing *which claims are true*, and being structurally unable to ship the ones that aren't. A forecast next to its baseline. A skill number with its uncertainty. A research result with its corrections visible. A deploy with no secret to steal. None of it is the flashiest version of the work — and all of it is the version I'd actually stand behind. The seismic product just happens to be the place where that discipline is the entire product.

Live: [seismic.fasl-work.com](https://seismic.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_SEISMIC) · [wiki](https://github.com/fsantibanezleal/CAOS_SEISMIC/wiki).
