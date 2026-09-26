---
title: 'blastfrag on PyPI, and the numbers did not move'
date: 2026-09-26
permalink: /rollings/2026/09/blastfrag-on-pypi-and-the-numbers-did-not-move/
tags:
  - fragmenta
  - packaging
  - reproducibility
  - benchmarks
---

blastfrag on PyPI, and the numbers did not move
======

![Fragmenta's engine pin moves from a git tag to a PyPI release and the artifacts stay identical](/images/projects/blastfrag_pin.svg)

[Fragmenta](https://fragmenta.fasl-work.com) predicts the mean fragment size of a bench blast with twelve arms over sixteen cases, and the science lives upstream in [blastfrag](https://pypi.org/project/blastfrag/), a separate repository that the product consumes as a dependency and never re-implements. Until today the PyPI project did not exist, so the pin was a git tag. I registered the project this morning, the release published through a trusted publisher, and Fragmenta 0.04.005 now pins `blastfrag==0.2.2` from PyPI like any other dependency.

The interesting part is what did not happen. A pin is a claim about numbers, so the release was treated as one: change the pin, re-bake all sixteen cases, diff the committed artifacts. Every published number is identical, and the bake gate that re-reads and re-hashes what it wrote agrees. I get to say "identical" because the diff said so, not because nothing should have changed.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The morning release existed because of my own mistake.</strong><br/>
A version bump done by substitution across the tree had rewritten the <code>app_version</code> field inside thirty-four committed artifacts, which is a way of forging provenance without meaning to. 0.04.004 regenerated all of them under the pinned engine with the bake gate passing; only then was the pin changed. The bump tool now moves version sources and nothing else.<br/>
<span style="color:#5a9ac0;font-size:13px;">Reproducibility stated precisely, as the product does: byte-identical within an environment, better than 3e-08 relative across operating systems, because two builds of the same pinned numpy reduce a dot product in a different order and no pin removes that.</span>
</div>

The headline the product exists to report has not changed either, and it is a negative one. Under leave-one-site-out, not one of the six learned arms explains any variance: the best, gradient boosting, scores -0.034 against a null model at -0.216, a margin between two failures rather than skill. The only two arms that stay positive on a site they have never seen are the two whose coefficients are fixed rather than fitted, the published regression at 0.802 and Kuznetsov at 0.311. The kill criterion was written down before the run and required both a positive score and a 0.10 margin. It fired, and the site says so on its front page.

[Fragmenta](https://fragmenta.fasl-work.com) · [blastfrag](https://pypi.org/project/blastfrag/) · [source](https://github.com/fsantibanezleal/CAOS_Fragmenta)
