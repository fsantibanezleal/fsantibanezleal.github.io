---
title: 'Symbolic regression: a near-perfect fit that recovers nothing'
date: 2026-07-28
permalink: /rollings/2026/07/symlab-accuracy-is-not-recovery/
tags:
  - symbolic-regression
  - interpretability
  - honesty
---

Symbolic regression: a near-perfect fit that recovers nothing
======

![SymLab: genetic programming and sparse regression on known-law cases, accuracy and recovery in two columns](/images/projects/symlab_app.png)

[SymLab](https://symlab.fasl-work.com) is a lab about one distinction the symbolic-regression field mostly hides: accuracy and structural recovery are different claims. A method can fit the data almost perfectly and still hand back an expression that is nothing like the law that generated it. Reported as one averaged number, that failure is invisible, which is how "solved" benchmarks routinely reward the wrong equation.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Feynman Gaussian, on the same footing:</strong><br/>
sparse regression: R2 = 1 - 1.8e-09 in about <strong>zero seconds</strong>, recovered = <strong>no</strong><br/>
genetic programming (Koza, +linear scaling, +dedup): high R2, recovered = <strong>no</strong><br/>
<span style="color:#5a9ac0;font-size:13px;">Two search families with nothing in common; a near-perfect fit in ten milliseconds; neither finds the law.</span>
</div>

So SymLab reports the two separately, on every case, and never averages them. Recovery is scored exactly, by edit distance to the true structure, on known-law cases (the Feynman set), not guessed. It runs both search families live in the browser at published budgets, so you can watch a method clear R2 above 0.999 and still miss the equation. If the point of symbolic regression is a readable law rather than a black box of equal accuracy, then recovery is the number that matters, and it is the one most tooling declines to show. [Live](https://symlab.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_SYMLAB).
