---
title: "3D Haptic Simulation with Octree Collision Detection"
date: 2009-06-01
excerpt: "Web-based 3D haptic simulation with octree spatial partitioning, SAT collision detection, and spring-damper force feedback.<br/><img src='/images/projects/haptic_sim.svg'>"
collection: portfolio
tags: [haptics, collision-detection, octree, three-js, fastapi, simulation, python]
---

A web-based 3D simulation system that recreates the experience of haptic (touch-based) interaction with virtual objects. Originally developed in 2008 at Universidad de Concepcion using C++/CLI, OpenGL, and a physical PHANToM Omni haptic device, the modern version replaces hardware dependencies with browser-based mouse and slider interaction while preserving the core physics engine.

Collision detection
======

Spatial queries use an **octree** partitioning structure (max depth of 4) that recursively subdivides 3D space into eight axis-aligned octants, reducing broad-phase collision detection from O(N^2) to O(N log N). Child nodes are indexed by a 3-bit code: index = (x >= center_x) + 2*(y >= center_y) + 4*(z >= center_z). For narrow-phase resolution, the system applies the **Separating Axis Theorem (SAT)** for exact triangle-triangle intersection testing across 11 potential separating axes (2 face normals + 9 edge-edge cross products from 3 edges of each triangle). For each candidate axis, the 6 vertices are projected onto the axis; if the projection intervals [min_A, max_A] and [min_B, max_B] do not overlap on any axis, the triangles are separated. Each SAT test is O(1) -- exactly 11 axis checks with 6 dot products each. This two-phase approach keeps the simulation responsive even with moderately complex meshes.

Force feedback model
======

Contact forces follow a spring-damper model based on Hooke's law with viscous damping -- a **Kelvin-Voigt formulation** (spring and dashpot in parallel): F = -k*(p_probe - p_contact) - b*v_probe, where k is the spring stiffness (N/m), p_contact is the nearest surface point (computed via Voronoi region classification with barycentric coordinates), b is the damping coefficient (Ns/m), and v_probe is the probe velocity. The force is clamped at F_max to match physical device limits. Stability requires k_max = 2*b/T (the Z-width constraint from Colgate & Brown, 1994), which is relaxed in the web version due to the lower update rate (~10 Hz vs. 1 kHz for physical haptic devices). Wavefront OBJ mesh loading with fan triangulation handles arbitrary geometry, and Three.js with WebGL provides the rendering layer.

Origin and context
======

This was my 2008 undergraduate thesis project at Universidad de Concepcion, part of a FONDEF-funded project aimed at building arthroscopic surgical training simulators. The haptic device work was also the technology exploration that directly led to the [FeelIT project](/portfolio/FeelIT/) — a haptic interface for visually impaired people. The legacy C++/CLI code is preserved alongside the modern Python/FastAPI web application.

![Haptic Simulation](/images/projects/haptic_sim.svg)

[View on GitHub](https://github.com/fsantibanezleal/UDEC_Haptic_SIM)
