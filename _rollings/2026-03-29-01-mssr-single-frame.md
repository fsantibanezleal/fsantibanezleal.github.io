---
title: 'Super-Resolution from a Single Frame'
date: 2026-03-29
permalink: /rollings/2026/03/mssr-single-frame/
tags:
  - SOFI
  - MSSR
  - Super-Resolution
  - Single Frame
---

Standard SOFI needs hundreds of frames of blinking emitters to beat the diffraction limit. You acquire a long temporal stack, compute cumulants across time, and the nonlinear statistics sharpen the point spread function beyond what any single exposure can resolve. It works beautifully — but it demands fluorophores that blink stochastically, and it demands patience while you collect enough frames for the statistics to converge.

MSSR (Mean-Shift Super-Resolution) throws all of that out. It extracts super-resolution information from a single frame. One image. No temporal stack, no blinking requirement, no stochastic photoswitching. The trick is spatial rather than temporal: instead of exploiting fluctuations over time, MSSR analyzes local intensity gradients within the image itself.

![SOFI pipeline — now with MSSR option](/images/rollings/sofi_pipeline.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">MSSR:</strong><br/>
Each pixel refined by local mean-shift weighted by intensity gradient &mdash; sub-pixel localization without temporal statistics
</div>

The idea is that each pixel's true emitter position can be refined by computing a mean-shift vector: a weighted average of neighboring pixel positions, where the weights come from the local intensity gradient. Bright pixels pull the estimate toward them, and the gradient ensures that the shift converges toward the true center of emission rather than just the geometric center of the PSF. It is essentially kernel density estimation applied to the spatial domain of a single fluorescence image.

What makes this genuinely exciting is the practical impact. You no longer need special fluorophores that blink. Conventional fluorescent labels — the kind every biology lab already uses — work just fine. And because there is no temporal requirement, you can apply MSSR to live imaging at full camera speed. No more trading temporal resolution for spatial resolution.

The implementation slots into the existing SOFI pipeline as an alternative processing mode. Where the cumulant path expects a temporal stack and computes second-order (or higher) statistics, the MSSR path takes a single frame and iterates the mean-shift refinement until convergence. The output is an upsampled image where each pixel has been relocated to its gradient-weighted centroid. The resolution gain is not as dramatic as high-order SOFI on a perfect blinking sample, but it is real, consistent, and immediate.

I keep thinking about how many experiments this would have simplified during the quantum dot work. Half the battle was getting the QDots to blink reliably under the right excitation conditions. With MSSR, you could have skipped that entire optimization and just imaged. [SOFI on GitHub](https://github.com/fsantibanezleal/FASL_SOFI_QDOTS).
