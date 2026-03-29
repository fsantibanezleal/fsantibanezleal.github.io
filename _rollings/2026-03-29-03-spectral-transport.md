---
title: 'Light at Every Wavelength'
date: 2026-03-29
permalink: /rollings/2026/03/spectral-transport/
tags:
  - Optics
  - Dual Photography
  - Spectral
  - Transport Matrix
---

The original dual photography transport matrix treats light as a single channel — or at most three channels for RGB. You project white patterns, capture color images, and the transport matrix T maps projector pixels to camera pixels as if all wavelengths behave the same way through the scene. For many materials, this is a reasonable approximation. For many others, it is not even close.

Different wavelengths interact with matter differently. A red photon and a blue photon hitting the same piece of tissue will scatter at different angles, penetrate to different depths, and get absorbed at different rates. Fluorescent materials absorb at one wavelength and emit at another entirely. A single RGB transport matrix cannot capture any of this. You need a transport matrix for each wavelength.

![Helmholtz reciprocity](/images/rollings/dual_helmholtz.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Spectral transport:</strong><br/>
T(&lambda;) &mdash; each wavelength has its own transport matrix.<br/>
Total image: c(&lambda;) = T(&lambda;) &middot; p(&lambda;)
</div>

The new spectral transport feature replaces the single matrix T with a family of matrices T(lambda), one per wavelength band. The acquisition is more involved — you need either a tunable narrowband projector or a broadband projector paired with spectral filters on the camera side. Each wavelength band gets its own structured light sequence, its own set of captures, and its own transport matrix.

The payoff is spectral relighting. Instead of asking "what would the scene look like from the projector's viewpoint?" you can now ask "what would it look like under illumination at 450nm? At 550nm? At 650nm?" You can synthesize images under illumination spectra that never physically existed in the lab. Want to see how the scene responds to a sodium vapor lamp? Multiply each T(lambda) by the lamp's emission spectrum and sum.

Helmholtz reciprocity still holds wavelength by wavelength — T(lambda) transposed gives you the dual image at that wavelength. The SVD compression also works per-wavelength, though the rank structure varies. Blue transport matrices tend to be higher rank than red ones in biological tissue because short wavelengths scatter more and create more complex light paths.

The data volume is significant. Where the original system stores one transport matrix, this stores dozens. But the per-wavelength matrices are often lower rank individually than the combined RGB matrix, so the SVD truncation is more aggressive and the total storage is manageable. The real cost is acquisition time — you need N times more captures for N wavelength bands. [Dual Photography on GitHub](https://github.com/fsantibanezleal/FASL_Coding_DualFotography).
