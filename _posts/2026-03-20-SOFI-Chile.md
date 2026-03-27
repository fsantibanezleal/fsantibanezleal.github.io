---
title: 'The first SOFI implementation in Chile, modernized'
date: 2026-03-20
permalink: /posts/2026/03/sofi-chile-modernized/
tags:
  - super-resolution
  - microscopy
  - open-source
---

In 2012, I started working on Super-resolution Optical Fluctuation Imaging at SCIAN-Lab, Universidad de Chile, collaborating with researchers at the III Physics Institute of the University of Gottingen in Germany. The goal was to implement SOFI from the ground up — cumulant computation, synthetic quantum dot simulators, deconvolution — and apply it to biological samples. After months of work, we achieved the first successful SOFI super-resolution imaging in Chile, resolving structures below the diffraction limit using nothing more than temporal statistics from blinking fluorescent emitters.

From MATLAB folder to web app
======

The original MATLAB code did its job well. It produced results, contributed to a SPIE publication, and then sat quietly in a folder for over a decade. That is the natural life cycle of most research code. But recently, while modernizing several old projects, I decided to give the SOFI pipeline a proper second life as a Python web application with FastAPI and interactive visualization.

The core mathematics have not changed — cumulants are cumulants — but wrapping them in a clean interface with synthetic blinking simulations and real-time parameter adjustment makes the ideas far more accessible. A student can now open a browser, generate a quantum dot field, compute cumulants from order 2 to 6, and watch the resolution improve before their eyes. No MATLAB license, no installation, no archaeology through uncommented scripts.

There is something satisfying about seeing computational optics work from a decade ago running again and being immediately useful. The physics does not expire. Making it accessible through a browser gives it new life — not just for research reproducibility, but as a teaching and demonstration tool for anyone curious about what happens when you push imaging beyond the diffraction limit.
