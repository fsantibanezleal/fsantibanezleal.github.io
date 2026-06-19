---
title: 'A NaN That Was Quietly Picking K'
date: 2026-06-18
permalink: /rollings/2026/06/lda-hsi-deep-review/
tags:
  - HSI
  - TopicModelling
  - DeepReview
  - i18n
---

A NaN That Was Quietly Picking K
======

I spent a chunk of the fortnight on a deep review of the HSI topic-modelling platform, and the most satisfying bug was the kind that hides in plain sight: the recommended number of topics, K, was being chosen by a `max()` over an array that secretly contained `NaN`.

The culprit was normalized pointwise mutual information. For a pair of topics with perfect co-occurrence, `p_ij → 1`, the NPMI numerator `−log(p_ij) → 0`, and you land on `0/0 = NaN`. That `NaN` propagated into `npmi_mean`, and "argmax of an array with NaNs" silently fell through to K = 4 for several scenes — a fake recommendation that looked principled.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:'Courier New',monospace;color:#e0e0e0;font-size:14px;line-height:1.9;">
<span style="color:#5a9ac0;"># perfect co-occurrence: take the analytic limit, not 0/0</span><br/>
NPMI(p<sub>ij</sub> → 1) = +1<br/>
<span style="color:#5a9ac0;"># and filter non-finite values before aggregating</span><br/>
npmi_mean = mean( [ v for v in npmi if isfinite(v) ] )
</div>

With NPMI handled as its analytic limit and non-finite values filtered, `recommended_K` became a genuine argmax again — and the honest result is that the score monotonically favors small K (perplexity rises and stability falls as K grows), so K = 4 is now *earned* rather than a NaN artifact.

The rest of the review was less dramatic but mattered more for users: I migrated the entire benchmarks subtree and the workspace wizard to `react-i18next`, so the EN/ES toggle now covers the whole explore-and-benchmarks surface (technical terms and symbols kept verbatim); fixed a HIDSAG explore crash from a type that didn't match the served data; corrected several conceptual and equation errors a math review caught; and added the funding and data-provider acknowledgements where they belong. Deep reviews rarely produce a headline — they produce a product you can trust.
