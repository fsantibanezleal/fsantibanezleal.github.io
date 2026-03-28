---
title: 'The first SOFI implementation in Chile, modernized'
date: 2026-03-20
permalink: /posts/2026/03/sofi-chile-modernized/
tags:
  - super-resolution
  - microscopy
  - open-source
---

In 2012, I started working on Super-resolution Optical Fluctuation Imaging at SCIAN-Lab, Universidad de Chile, collaborating remotely with researchers at the III Physics Institute of the University of Gottingen in Germany. Working across continents and time zones with the Gottingen team was both challenging and exhilarating -- SOFI was a relatively new technique at the time, and there was limited local expertise in Chile to draw on. Every implementation decision, from the cumulant computation pipeline to the deconvolution strategy, required careful coordination through emails and video calls, often debugging numerical issues with a six-hour time difference. The goal was to implement SOFI from the ground up -- cumulant computation, synthetic quantum dot simulators, deconvolution -- and apply it to biological samples. After months of work, we achieved the first successful SOFI super-resolution imaging in Chile, resolving structures below the diffraction limit using nothing more than temporal statistics from blinking fluorescent emitters. The pride of being the first group in Chile to produce these results was immense -- it proved that cutting-edge computational optics could be done here, not just in European labs with larger budgets and established traditions in the field. That work contributed to a [publication at SPIE Photonics West](https://doi.org/10.1117/12.2006215), presenting the cumulant-based framework and validation results.

![Cumulant vs moment decomposition](/images/rollings/sofi_cumulant_vs_moment.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">PSF narrowing:</strong><br/>
σ<sub>n</sub> = σ / √n — at order 4, resolution doubles
</div>

From MATLAB folder to web app
======

The original MATLAB code did its job well. It produced results, contributed to the SPIE publication, and then sat quietly in a folder for over a decade -- untouched, gathering digital dust until the recent modernization effort gave me a reason to open it again. The modernized code is now [available on GitHub](https://github.com/fsantibanezleal/FASL_SOFI_QDOTS). That is the natural life cycle of most research code. But recently, while modernizing several old projects, I decided to give the SOFI pipeline a proper second life as a Python web application with FastAPI and interactive visualization.

The core mathematics have not changed — cumulants are cumulants — but wrapping them in a clean interface with synthetic blinking simulations and real-time parameter adjustment makes the ideas far more accessible. A student can now open a browser, generate a quantum dot field, compute cumulants from order 2 to 6, and watch the resolution improve before their eyes. No MATLAB license, no installation, no archaeology through uncommented scripts.

There is something satisfying about seeing computational optics work from a decade ago running again and being immediately useful. The physics does not expire. Making it accessible through a browser gives it new life — not just for research reproducibility, but as a teaching and demonstration tool for anyone curious about what happens when you push imaging beyond the diffraction limit.
