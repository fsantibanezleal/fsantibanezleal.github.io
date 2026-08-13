---
title: 'I commissioned a review to break my own result'
date: 2026-08-13
published: true
permalink: /posts/2026/08/i-commissioned-a-review-to-break-my-own-result/
tags:
  - honesty
  - benchmarks
  - machine-learning
  - engineering
---

I commissioned a review to break my own result
======

I had a result I liked. On haul-truck telemetry, segmenting the operating regime before running a change detector looked like it recovered almost everything that multiple operating conditions had destroyed: 0.96 down to 0.05 and back up to 0.98, and 0.69 down to 0.06 and back up to 0.88. The mechanism was sound, the story was clean, and the numbers were large.

That combination is exactly when I have learned to stop. A large effect with a tidy explanation is the easiest thing in the world to believe, and belief is not evidence. So instead of writing it up, I commissioned a review whose brief was not to check the work but to refute it, with the default set against me: attack the claim from every angle available, and treat anything not clearly established as broken.

It confirmed the mechanism and broke three of the four numbers.

None of the three failures was subtle once found, and this is the part I think is worth writing down: all three flattered the result. The raw comparison arm had been given a third of the healthy data the residual arm got, so the baseline was handicapped by the harness rather than by the method. The detection threshold was being chosen on the same data it was then scored against, and the code accepted a calibration argument that it never actually read, which is the kind of defect that produces a good number and no error message. And the arm carrying the 0.88 had been run with the number of regimes set to one, which is a global context regression with no segmentation in it at all, so the strongest evidence for segmentation came from a configuration that did not segment.

Three defects, three directions, one direction of error. That is not coincidence, it is selection: a defect that made the result worse would have been found and fixed weeks earlier, because I would have gone looking. The ones that survive to be reported are the ones that made things look right.

What I did next was the part I would recommend to anyone in the same position. I moved the headline off the detector entirely. The claim is now an effect size, computed from the eligible arms in code: on the six-operating-condition subsets, the fault signature is 0.16 sigma of the pooled spread and 11.95 sigma of the within-regime spread. No threshold rule, alarm convention or detection budget can move that number, because none of them appear in it. Then I quoted the worse of the two pairs alongside the better one, published the null (regime conditioning does not improve onset localisation, and the paired comparison over five seeds is a wash), and withdrew the false-alarm claim completely, because neither lane demonstrated it and on the synthetic lane the plain arm wins that metric outright.

The review also left a gift I did not expect. Chasing the discrepancies turned up three genuine defects in the underlying engine, including a change-detector cut threshold that matched neither the original paper nor the reference implementation, and a budget-threshold search that could not see qualifying thresholds sitting below a local violation and was quietly costing the multi-condition arms a factor of three to six. Those are fixed and released in the package, which means the correction outlived the argument that produced it.

The result is smaller than the one I started with. It is also the first version of it I would defend in front of someone trying to take it apart, which is the only version worth having. There is a habit I keep returning to: the failure mode in this kind of work is rarely that you cannot find evidence for your idea. It is that you find it too easily, and stop. Commissioning someone to break the thing is how I make stopping harder.

The tool is [TruckVitals](https://truckvitals.fasl-work.com), and the numbers on its benchmark page are the post-review ones.
