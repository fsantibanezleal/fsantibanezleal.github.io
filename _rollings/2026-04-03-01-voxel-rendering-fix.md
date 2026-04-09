---
title: 'When Voxels Go Black'
date: 2026-04-03
permalink: /rollings/2026/04/voxel-rendering-fix/
tags:
  - Visualization
  - Three.js
  - WebGL
  - Mining
  - Debugging
---

When voxels go black
======

Spent two days debugging a 3D rendering issue in the [Mine Pile Visualizer](https://github.com/fsantibanezleal/MINE_PILE_VIZ_TS). Stockpile voxels were rendering as solid black blocks instead of showing quality-based colors. The data was correct — the voxel cells had valid quality values. The color mapping was correct — tested in isolation. But the rendered scene was black.

The problem was in how Three.js handles `instancedMesh` colors. The instance-color attribute approach (`setColorAt`) is fragile — it silently fails when the buffer geometry doesn't have the expected color attribute size, or when React's reconciliation cycle disposes and recreates the mesh between renders. No error, no warning. Just black.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The fix:</strong><br/>
instancedMesh + setColorAt (fragile) → merged visible-geometry (explicit)<br/>
<span style="color:#5a9ac0;font-size:13px;">Build one merged BufferGeometry where each voxel face carries its color directly in the vertex attributes. No instance-color buffer, no silent disposal.</span>
</div>

The merged geometry approach is slightly more memory-intensive (each voxel's vertices carry their own color) but completely deterministic. The color is in the geometry, not in a side-channel attribute that can be silently dropped.

![3D stockpile with categorical quality — after fix](/images/projects/screenshots/minepile_3d_stockpile.png)

The debugging process itself was worth documenting. Created an issue-evidence folder with before/after screenshots at each iteration — shader version, instance-color version, merged-geometry version. Each approach had different failure modes that narrowed the root cause.

This is the kind of bug that makes you appreciate the difference between "it works on my machine in dev mode" and "it works reliably across re-renders, data refreshes, and view transitions." The former is easy. The latter requires understanding how the rendering pipeline actually manages state.
