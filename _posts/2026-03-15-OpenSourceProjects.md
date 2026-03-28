---
title: 'Giving Legacy Research Code a Second Life'
date: 2026-03-15
permalink: /posts/2026/03/open-source-projects/
tags:
  - open source
  - scientific code
  - modernization
---

I recently pushed five old research projects to GitHub, modernized and documented. It felt like reopening time capsules.

Dusting off the archives
======

Over the past weeks, I have been revisiting code from across my academic career and preparing it for public release. The projects span over a decade of work, and each one carries its own story. The [Robotic Writer](https://github.com/fsantibanezleal/Udec_Robotic_Writer) is the oldest -- a robotic arm controller from 2004, built as a lab activity when I was a second-year undergraduate at UdeC. It was written in C++/CLI, and looking at that code now is like reading a letter from a younger self who was just discovering what programming could do. [CEFOP_DinHot](https://github.com/fsantibanezleal/CEFOP_DinHot) came from my first real research job at CEFOP around 2010, working on optical tweezers dynamics -- that was where I learned what it means to do science systematically, not just write code that works. [SCIAN_LEO_CPM](https://github.com/fsantibanezleal/SCIAN_LEO_CPM) and [SCIAN_EVL_SpherSIM](https://github.com/fsantibanezleal/SCIAN_EVL_SpherSIM) are from SCIAN-Lab, where I worked on biophysics simulations during what I consider the most formative years of my research career -- the rigor and intellectual ambition of that lab shaped how I approach problems to this day. And the [Dual Photography implementation](https://github.com/fsantibanezleal/FASL_Coding_DualFotography) was a personal exploration that connected computational optics to my growing interest in imaging science.

![Biological context — zebrafish development](/images/rollings/cpm_biological_context.svg)

![Haptic simulator frontend](/images/projects/screenshots/haptic_frontend.png)

Each of these sat in private folders for years, some in formats that were becoming increasingly difficult to run. Modernizing them meant updating dependencies, adding documentation, and in several cases building simple web interfaces so that anyone can interact with the core ideas without wrestling with outdated toolchains.

Why bother?
======

Scientific code has a short shelf life. Papers get published, and the code that produced the results quietly rots on a forgotten hard drive. I think that is a loss -- not just for reproducibility, but because these projects represent real ideas and real effort that deserve to be accessible.

There is also something deeply satisfying about seeing a simulation from 2004 running again in a modern browser. The robotic arm controller, the optical tweezer dynamics, the cellular automata -- they all still work, and they all still teach something. The code itself is a timeline of technological evolution: C++/CLI from the early 2000s, MATLAB from the research years, and now Python/FastAPI wrappers that make everything accessible through a web browser. Seeing code that is 10 to 20 years old still implementing valid science -- the physics has not changed, the algorithms still converge, the simulations still produce meaningful results -- is a quiet reminder that good ideas outlast their implementation language.

Making this code open is a small act, but it matters. If even one student finds these projects useful or interesting, the effort will have been worth it.
