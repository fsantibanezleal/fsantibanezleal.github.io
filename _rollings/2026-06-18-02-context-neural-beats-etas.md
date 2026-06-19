---
title: 'When the Challenger Earns +0.075 Nats'
date: 2026-06-18
permalink: /rollings/2026/06/context-neural-beats-etas/
tags:
  - Seismic
  - NeuralNetworks
  - PointProcesses
  - Evaluation
---

When the Challenger Earns +0.075 Nats
======

In CAOS Seismic the baseline is sacred. A maximum-likelihood space–time ETAS model (Ogata 1998) is the de-facto operational standard, and any fancier model has to *earn* the public map by beating it — not on a vibe, but in our own prospective CSEP harness, measured in information gain per earthquake. This week the context-conditioned neural temporal point process cleared the in-loop gate: **+0.075 nats per earthquake over ETAS, calibrated**. Pseudo-prospective validation is still pending, so ETAS is still what ships — but the gate moved, and that is the whole game.

The unit matters. "Accuracy" is meaningless for rare events; what you score is how much more probable the model made the events that actually happened, relative to a reference, averaged per event:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:'Courier New',monospace;color:#e0e0e0;font-size:14px;line-height:1.9;">
<span style="color:#5a9ac0;"># exceedance probability (the one public formula, never changes)</span><br/>
P = 1 − e<sup>−N</sup><br/><br/>
<span style="color:#5a9ac0;"># information gain per earthquake, in nats</span><br/>
IG = (1/N) · Σ<sub>i</sub> log( λ<sub>model</sub>(t<sub>i</sub>,x<sub>i</sub>) / λ<sub>ref</sub>(t<sub>i</sub>,x<sub>i</sub>) )
</div>

Getting there was less about the network and more about plumbing. The neural challenger was over-forecasting absolute rates by roughly 490× until I calibrated `rate_cal` on the *same* grid the gate and the forecast use — grid-consistency turned out to be load-bearing. I also added a shape-only information-gain variant (renormalize the challenger to the ETAS total) to separate "is the *shape* of the intensity field better?" from "is the *level* right?", and a `recondition()` step that advances the neural's conditioning without retraining. Oh, and a 50-minutes-per-window expected-counts loop became seconds once I vectorized the triggering field — about a 13× speedup, which is what made the whole back-analysis tractable.

The honest footnote: a gain on the in-loop gate is necessary, not sufficient. It reaches the map only after it also wins prospectively and stays calibrated. Until then, the better baseline keeps the map.
