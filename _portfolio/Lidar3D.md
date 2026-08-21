---
title: "Lidar3D, Streaming 3D Reconstruction Lab"
date: 2026-07-02
excerpt: "An early research lab for feed-forward streaming 3D reconstruction: an ordered RGB or LiDAR stream becomes a camera trajectory, dense metric depth and a fused colored point cloud. The heavy engine runs offline on a GPU; the site replays the baked cloud across four renderers under one unified transform, with a strict renderer-honesty discipline as the point.<br/><img src='/images/projects/lidar3d_renderers.svg'>"
collection: portfolio
tags: [3d-visualization, research, computer-vision, point-cloud, reconstruction]
---

An **early research lab** for feed-forward streaming 3D reconstruction: an ordered RGB or LiDAR stream becomes a camera trajectory, dense metric depth and a fused colored point cloud, with no per-scene optimization. The heavy engine runs **offline on a GPU**; the public site is a static SPA that **replays the baked cloud** across four point-cloud renderers. Live at [lidar3d.fasl-work.com](https://lidar3d.fasl-work.com).

![Lidar3D, one baked cloud, four honest renderers](/images/projects/lidar3d_renderers.svg)

## What is actually wired

Two reconstruction engines: a **from-scratch depth-and-pose network** (ResNet-18 backbone, a Siamese SE(3) pose head, aleatoric depth) with a real **~0.28 m held-out trajectory error** on TUM, reconstructing eight real indoor scenes (TUM / 7-Scenes / ICL); and a genuinely **vendored** 2026 model (kept clearly labelled as vendored) for four outdoor scenes. Plus Open3D ICP LiDAR odometry and a CPU synthetic engine.

## Renderer honesty is the headline

Four renderers (three.js, deck.gl, surfels and Potree LOD) all draw the **same baked cloud under one unified `(x, −y, −z)` transform** (a deck.gl mirror bug was found and fixed). Where a renderer physically cannot do per-frame replay, the app **approximates and says so in the UI** rather than faking it, and any metric without ground truth is shown as "none" with a reason.

## Honest scope

A lab, framed as one: it **replays** baked artifacts (it is **not real-time** and **not SLAM** by default: loop closure and global bundle adjustment are opt-in), it does **not** claim to beat the state of the art, the outdoor model is vendored not ours, and there is no textured mesh or Gaussian-splat output. The value is the discipline and the negative-results ledger, not a fidelity claim.

[Live demo](https://lidar3d.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_RES_Lidar3D)
