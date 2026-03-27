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

What made this project particularly interesting is the dual deployment requirement. Mine sites often have limited or no internet connectivity, so the platform needed to work as a standalone desktop application (Streamlit and Dash packaged with PyInstaller). At the same time, a centralized web version (Next.js, FastAPI, PostgreSQL, Redis) was needed for multi-site management. Building for both contexts meant thinking carefully about what logic could be shared and what had to be adapted.

The infrastructure side was its own challenge: Docker Swarm orchestration, Traefik for routing, Ansible for automated provisioning. Going from a prototype running on a laptop to a production deployment with proper monitoring and backups is a journey that teaches you things no tutorial covers.

The breadth of this project is what stands out to me. In one week I would be deep in 3D geometry and coordinate transformations; the next, building React components or writing Ansible playbooks. It is exhausting but genuinely rewarding to see all the pieces come together into something that works and that people actually use.
