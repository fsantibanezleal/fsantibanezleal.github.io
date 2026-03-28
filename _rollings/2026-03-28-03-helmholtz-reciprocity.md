---
title: 'Light Goes Both Ways'
date: 2026-03-28
permalink: /rollings/2026/03/helmholtz-reciprocity/
tags:
  - Optics
  - Dual Photography
  - Helmholtz
  - SVD
---

There is something philosophically satisfying about the idea that every observation contains, embedded within it, the reverse observation. Helmholtz saw this in 1856. Light paths are reversible — if a photon can travel from point A to point B through a scene, bouncing off surfaces and scattering through media, then a photon can travel the exact same path from B back to A. The physics does not care about direction.

Dual photography takes this principle and turns it into a computational tool. You project structured patterns from a projector onto a scene and capture the result with a camera. Each pixel in the projector illuminates the scene, and each pixel in the camera records the aggregate response. The entire relationship between projector pixels and camera pixels is captured in a transport matrix T.

![Helmholtz reciprocity](/images/rollings/dual_helmholtz.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Transport matrix:</strong><br/>
c = T &middot; p &nbsp;&nbsp;(forward)<br/>
p' = T<sup>T</sup> &middot; c &nbsp;&nbsp;(dual)<br/>
<em>The transpose is all you need</em>
</div>

The forward image is c = T*p, where p is the projector pattern and c is the camera capture. The dual image — what the scene would look like if the camera were the light source and the projector were the sensor — is simply p' = T^T * c. The transpose is all you need. Helmholtz reciprocity guarantees that this transposed matrix is physically meaningful.

But the transport matrix is large and measuring it naively requires as many captures as there are projector pixels. This is where the SVD becomes essential. Decomposing T = USV^T lets you approximate the matrix with far fewer measurements, and it also enables relighting — synthesizing images under novel illumination conditions without physically changing the light.

The low-rank structure of most real scenes means that a handful of singular values capture most of the transport. The rest is noise and high-frequency inter-reflections that rarely matter perceptually.

I keep coming back to this project because it sits at the intersection of linear algebra and physical optics in a way that feels almost too clean. The math works because the physics is symmetric, and the physics is symmetric because... well, that is a deeper question. [Dual Photography project](https://github.com/fsantibanezleal/FASL_Coding_DualFotography).
