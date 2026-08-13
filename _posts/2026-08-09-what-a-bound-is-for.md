---
title: 'What a bound is for'
date: 2026-08-09
published: true
permalink: /posts/2026/08/what-a-bound-is-for/
tags:
  - optimization
  - mine-planning
  - benchmarks
  - engineering
---

What a bound is for
======

Most of the optimization problems worth solving in mining are NP-hard, which means nobody solves them to proven optimality at real size. That fact is usually mentioned once in an introduction and then quietly dropped, and what follows is a number: a net present value, a schedule, a plan. The number looks the same whether it is two percent from the best possible answer or thirty. Without something to compare it against, there is no way to tell, and no way for a reader to tell either.

A bound is what closes that gap in the reader's favour. If I can compute a value that provably cannot be beaten, then reporting my plan next to it turns an unverifiable claim into a measured one: this is the plan, this is the ceiling, this is the distance between them. The distance is the honest part. It says how much value might still be on the table, which is a more useful thing to hand a decision-maker than a confident single figure.

I have been building this discipline into the open-pit tools, and it has taught me three things I did not expect at the start.

The first is that a bound has to be checkable, not just present. In [PhaseFlow](https://phaseflow.fasl-work.com) the scheduling bound is verified by its ordering: the bound for the constrained pit limit problem must sit below the bound for the richer problem that relaxes fewer things, because a richer problem can only be worth more. It does, by 365 units in 24.5 million. That is a small consistency check and it is worth more than a paragraph of assurance, because it is the kind of thing that breaks loudly when the implementation is wrong. The same instinct runs through [PitForge](https://pitforge.fasl-work.com), where every ultimate-pit solve asserts the max-flow duality identity, so a wrong answer cannot pass quietly.

The second is that the comparison has to be against work that is not mine. PhaseFlow solves a published MineLib instance as published, on its own six periods, its own eight percent discount rate and its own two capacities, and puts the results beside the published ones. The ultimate pit optimum reproduces exactly at 26,086,899. The bound lands at 24,486,184 against a published 24,486,549. And the optimality gap is 2.49 percent against a published 1.26 percent, which is to say the published schedule is better than mine. That number stays on the page. An anchor you only keep when you win is not an anchor, it is decoration, and the version of this work where I invent my own scenario and report a flattering gap would have been easier to build and worth considerably less.

The third took longer to see. A gap has two halves, and they are not the same kind of problem. If the reported distance between plan and bound is five percent, some of that is a weak plan and some of it is a loose bound, and until you separate them you do not know what to fix. So PhaseFlow computes two bounds on every case: one that relaxes the resource constraints one at a time, which is certified but loose, and the joint one, which is tighter and much more expensive. The difference between them is the share of the gap that belongs to the mathematics rather than to the schedule. On a single-resource instance the two agree to machine precision, which is the strongest correctness check in the repository, and on the deposit twins they also agree, which is a result in itself: it says one resource alone determines the answer there, and only a joint bound could have told me that.

There is a version of all this that is just rigour for its own sake. The reason it is not, in my experience, is that a bound changes what the conversation is about. Without one, a review of a mine plan turns into an argument about whether the number is believable, which is really an argument about who produced it. With one, the question becomes how much value is provably still available, and that is a question the mathematics can answer rather than a matter of standing. I would rather hand someone a plan with a measured limit attached than a better-looking plan with nothing behind it.
