---
title: 'First SOFI Results'
date: 2012-08-15
permalink: /rollings/2012/08/sofi-first-results/
tags:
  - SOFI
  - Super-Resolution
  - SCIAN-Lab
  - Microscopy
---

After weeks of debugging MATLAB code and calibrating the microscope, we got the first SOFI super-resolution images working. Second-order cumulants on quantum dot samples. The resolution improvement is visible — structures that were blurred blobs in the widefield image become distinguishable points in the SOFI reconstruction.

This is apparently the first time anyone has done this in Chile. The collaboration with the group in Göttingen has been essential — they have years of experience with the technique and helped us avoid several pitfalls with the cumulant computation.

Still a lot to do. Higher orders (3rd, 4th) should give even better resolution, but the noise gets worse. Need more frames.

![SOFI vs conventional microscopy](/images/rollings/sofi_vs_palm.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">2nd-order cumulant:</strong><br/>
&kappa;&#x2082; = &langle;&delta;F(t) &middot; &delta;F(t+&tau;)&rangle;<br/>
<em>Resolution improvement: &radic;2 &asymp; 1.41&times;</em>
</div>

[SOFI project on GitHub](https://github.com/fsantibanezleal/FASL_SOFI_QDOTS).
