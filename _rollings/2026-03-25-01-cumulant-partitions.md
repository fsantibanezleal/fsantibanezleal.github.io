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

I spent half the night debugging the 6th-order cumulant implementation for the [SOFI pipeline](https://github.com/fsantibanezleal/FASL_SOFI_QDOTS) and the bug turned out to be a single division-by-3 error buried inside a nested loop. The moment-to-cumulant conversion is not just a formula you plug in -- it requires summing over all partitions of a set, weighted by Mobius function values on the partition lattice. At 2nd order, life is simple: κ₂ = ⟨I²⟩ - ⟨I⟩². At 4th order things get busier: κ₄ = ⟨I⁴⟩ - 4⟨I³⟩⟨I⟩ - 3⟨I²⟩² + 12⟨I²⟩⟨I⟩² - 6⟨I⟩⁴. But at 6th order there are three distinct partition types that contribute: pair-quartet, triple-triple, and triple-pair configurations, each with its own combinatorial prefactor. The symptom was subtle -- the reconstructed PSF narrowing looked geometrically correct, following the expected √n rule, but the relative intensities between bright and dim emitters were wrong by about 15%. That kind of error does not scream "bug" at first glance; it whispers "maybe the sample is just uneven." After stepping through the partition enumeration by hand on paper, I found that the triple-pair partition count was being divided by 3 instead of multiplied by 3 in the symmetry correction step. One character in the code, hours of confusion. The payoff at 6th order is real though -- the PSF narrows by √6 ≈ 2.45×, which means structures at roughly 90 nm become resolvable from a conventional widefield setup with a 220 nm diffraction limit. Worth the partition headache, worth the 2 AM coffee.
