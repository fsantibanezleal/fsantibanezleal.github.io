---
title: 'Building a crusher wear management platform from scratch'
date: 2025-12-20
permalink: /posts/2025/12/crusher-wear-platform/
tags:
  - consulting
  - point-cloud
  - 3D analysis
  - wear forecasting
---

Over the past few months I have been building an end-to-end software platform for managing crusher liner wear in minerals processing, working as a consultant for a mining equipment services company. It has been one of the most technically demanding projects I have taken on.

From raw scans to production
======

The system starts with raw 3D laser scans of crusher liners -- point clouds with millions of points in DXF and PTS formats. These get parsed, aligned, and transformed into cylindrical wear profiles that engineers can actually interpret. From there, the platform tracks wear progression across campaigns and surveys, fits trend models, and forecasts when liners need to be changed.

What made this project particularly interesting -- and particularly demanding -- is the dual deployment requirement. Mine sites often have limited or no internet connectivity, so the platform needed to work as a standalone desktop application (Streamlit and Dash packaged with PyInstaller). At the same time, a centralized web version (Next.js, FastAPI, PostgreSQL, Redis) was needed for multi-site management. Building for both contexts simultaneously meant thinking carefully about what logic could be shared and what had to be adapted. The challenge is not just technical; it is architectural. You have to design abstractions that are clean enough to work in a single-user offline context and robust enough to scale to multi-site, multi-user production. Getting that balance right was one of the most intellectually satisfying aspects of the project.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">From 3D scan to wear profile:</strong><br/>
Point cloud (x, y, z) → Cylindrical (r, θ, h) → Radial profile R(θ, h)
</div>

![Crusher wear platform — dual deployment](/images/projects/crusher_wear_system.svg)

The infrastructure side was its own challenge: Docker Swarm orchestration, Traefik for routing, Ansible for automated provisioning. Going from a prototype running on a laptop to a production deployment with proper monitoring and backups is a journey that teaches you things no tutorial covers.

There is a particular satisfaction in seeing raw 3D point clouds -- millions of noisy laser-scanned coordinates -- transform step by step into actionable maintenance decisions. The moment when an engineer looks at a wear forecast and says "we need to change those liners next week" based on data that started as a cloud of points in space -- that is the payoff. It makes the long hours of coordinate transformations and alignment algorithms feel worthwhile.

The breadth of this project is what stands out to me. In one week I would be deep in 3D geometry and coordinate transformations; the next, building React components or writing Ansible playbooks. Working as a consultant means wearing all the hats simultaneously: data scientist, full-stack developer, DevOps engineer, and sometimes even project manager. It is exhausting but genuinely rewarding to see all the pieces come together into something that works and that people actually use.
