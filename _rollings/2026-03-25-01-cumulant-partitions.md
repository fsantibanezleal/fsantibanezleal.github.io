---
title: 'Partition Counting at 2 AM'
date: 2026-03-25
permalink: /rollings/2026/03/Post-2026-03-25-01/
tags:
  - SOFI
  - Super-Resolution
  - Mathematics
  - Cumulants
---

Partition Counting at 2 AM
======

Half past two in the morning, third coffee going cold, and I am staring at the [SOFI pipeline](https://github.com/fsantibanezleal/FASL_SOFI_QDOTS) wondering why the 6th-order cumulant image looks subtly wrong. The moment-to-cumulant conversion is not just a formula you plug in -- it requires summing over all partitions of a set, weighted by Mobius function values on the partition lattice. Let me walk through the orders, because the escalation in complexity is the whole story.

![Cumulant orders and PSF narrowing](/images/rollings/sofi_cumulant_orders.svg)

At 2nd order, life is simple. You subtract the squared mean from the second moment and you are done:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Second-order cumulant:</strong><br/>
κ₂ = ⟨I²⟩ − ⟨I⟩²  =  ⟨δI(t) · δI(t+τ)⟩
</div>

At 4th order things get busier. The point of higher-order cumulants is that they subtract out the Gaussian contributions -- everything that could be explained by a normal distribution gets removed, leaving only the "interesting" fluctuation structure. The 4th-order expression has five terms:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Fourth-order cumulant:</strong><br/>
κ₄ = ⟨I⁴⟩ − 4⟨I³⟩⟨I⟩ − 3⟨I²⟩² + 12⟨I²⟩⟨I⟩² − 6⟨I⟩⁴
</div>

But 6th order is the worst. Three distinct partition types contribute -- pair-quartet, triple-triple, and triple-pair configurations -- each with its own combinatorial prefactor. The expression expands to:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Sixth-order cumulant (partition terms):</strong><br/>
κ₆ = Σ_pair-quartet [ (−1)^(k−1) (k−1)! · μ₂μ₄ ]<br/>
&nbsp;&nbsp;&nbsp;&nbsp;+ Σ_triple-triple [ (−1)^(k−1) (k−1)! · μ₃² ]<br/>
&nbsp;&nbsp;&nbsp;&nbsp;+ Σ_triple-pair [ (−1)^(k−1) (k−1)! · μ₂³ ]
</div>

The symptom was subtle -- PSF narrowing looked geometrically correct following the expected √n rule, but relative intensities between bright and dim emitters were wrong by about 15%. That kind of error does not scream "bug"; it whispers "maybe the sample is just uneven." After stepping through the partition enumeration by hand on paper, I found that the triple-pair partition count was being **divided by 3** instead of **multiplied by 3** in the symmetry correction step. One character in the code, hours of confusion.

√6 ≈ 2.45x resolution improvement. Structures at roughly 90 nm become resolvable from a conventional widefield setup with a 220 nm diffraction limit. Worth the partition headache. [Repository here](https://github.com/fsantibanezleal/FASL_SOFI_QDOTS).
