---
title: 'A portfolio of things I measured, not just things that worked'
date: 2026-07-15 15:00:00
permalink: /rollings/2026/07/portfolio-measured-not-just-worked/
tags:
  - portfolio
  - honesty
  - design
  - engineering
---

A portfolio of things I measured, not just things that worked
======

![The restructured portfolio: six families, each card a real app screenshot](/images/projects/portfolio_grid.png)

I rebuilt the [portfolio](https://fasl-work.com) from the ground up. The old version was 22 category chips over a wall of text: every project described in the register a project describes itself in, which is to say the flattering one. What bothered me was not the design. It was that nothing on the page could lose.

The new structure is six families, each product with a real screenshot of its running app and, on every product, a negative result stated on the card. Not in a footnote. Where a visitor looking for a reason to trust the thing would actually land. That constraint did more to shape the writing than any layout decision, because it forced each card to answer a question the marketing version never asks: where does this tool's fashionable method lose to the boring one?

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">One honest result carried onto the cards:</strong><br/>
TailWatch: the classical velocity map (AUC 0.968) beats the learned autoencoder (0.898)<br/>
CardioPINN: the PINN does not beat Tikhonov on any of 4 beats<br/>
ChronoScope: a one-line SeasonalNaive beats a foundation model on a real series<br/>
<span style="color:#5a9ac0;font-size:13px;">Every card also carries the real, verified numbers: silhouettes against a null control, min-cut optima to within 2e-9, calibrated uncertainty. The negatives sit next to the positives, not instead of them.</span>
</div>

The screenshots matter for the same reason the negatives do. A category chip and a paragraph let a project stay abstract. A screenshot of the actual running app, next to a sentence admitting where its learned layer trails a classical baseline, is a much harder thing to oversell.

The verified facts came first: every number on a card was read out of the committed artifacts and code, not transcribed from a README, and anything that could not be verified from disk was left off. The cards that describe a null (a rollout policy winning 0 of 8 seeds, a grade net tying kriging, a distance-to-deposit baseline tying the best prospectivity model) are describing results I actually ran, not modesty.

That is the whole shift. The old portfolio was a list of things that worked. This one is a list of things I measured, including the times the interesting method lost to the plain one. I think it is the more valuable list to have built, and the more honest one to put my name on. [Portfolio](https://fasl-work.com) · [source](https://github.com/fsantibanezleal/FASL_WEB_Portfolio).
