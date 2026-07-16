---
title: 'A 3D reconstruction lab whose point is keeping the viewer honest'
date: 2026-07-15
permalink: /rollings/2026/07/lidar3d-renderer-honesty/
tags:
  - 3d-reconstruction
  - point-cloud
  - computer-vision
  - honesty
---

A 3D reconstruction lab whose point is keeping the viewer honest
======

[Lidar3D](https://lidar3d.fasl-work.com) is an early research lab for feed-forward streaming 3D reconstruction: an ordered RGB or LiDAR stream becomes a camera trajectory, dense metric depth and a fused colored point cloud. Before anything else, the honest framing: it replays baked artifacts, it is not real-time and not SLAM by default, and the outdoor model is vendored, not mine. The heavy engine runs offline on a GPU and the public site is a static SPA that replays the result.

What is actually wired is a from-scratch depth-and-pose network (ResNet-18 backbone, a Siamese SE(3) pose head, aleatoric depth) with a real held-out trajectory error, reconstructing eight real indoor scenes from TUM, 7-Scenes and ICL. Alongside it, a genuinely vendored 2026 model handles four outdoor scenes and is kept labelled as vendored, plus Open3D ICP LiDAR odometry and a CPU synthetic engine.

The differentiator is not the network. It is a strict renderer-honesty discipline:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Own depth+pose net, held-out on TUM:</strong><br/>
trajectory error (ATE) <strong>~0.28 m</strong> · depth AbsRel <strong>0.38 to 0.22</strong> · ~12.8 M params<br/>
<span style="color:#5a9ac0;font-size:13px;">Four renderers (three.js, deck.gl, surfels, Potree LOD) draw the same baked cloud under one unified (x, minus-y, minus-z) transform. Where a renderer cannot do per-frame replay, the app approximates and says so in the UI; a metric without ground truth reads "none" with a reason.</span>
</div>

The reason I built it this way is that reconstruction demos are usually the least honest part of the pipeline: a polished cloud that hides where the pose drifted, which numbers had no ground truth, or that two viewers are quietly showing different data. Here a deck.gl coordinate-mirror bug was found and fixed precisely because the four renderers are held to one transform, so a discrepancy is visible instead of pretty.

It does not claim to beat the state of the art, there is no textured mesh or Gaussian-splat output, and loop closure and global bundle adjustment are opt-in. The value is the discipline and the negative-results ledger, not a fidelity claim. [Live](https://lidar3d.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_RES_Lidar3D).
