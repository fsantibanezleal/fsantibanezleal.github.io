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

Spatial queries use an octree partitioning structure (max depth of 4) that reduces broad-phase collision detection to O(n log n). For narrow-phase resolution, the system applies the Separating Axis Theorem (SAT) for exact triangle-triangle intersection testing across 11 potential separating axes (3 face normals per triangle plus 5 edge cross-products from the non-parallel edge pairs). This two-phase approach keeps the simulation responsive even with moderately complex meshes.

Force feedback model
======

Contact forces follow a spring-damper model based on Hooke's law with viscous damping — a Kelvin-Voigt formulation: F = -kd - bv, where k is the spring stiffness, d is the penetration depth, b is the damping coefficient, and v is the relative velocity at the contact point. The model produces stable, physically plausible resistance when the user's proxy intersects a surface. Wavefront OBJ mesh loading with fan triangulation handles arbitrary geometry, and Three.js with WebGL provides the rendering layer.

Origin and context
======

This was my 2008 undergraduate thesis project at Universidad de Concepcion, part of a FONDEF-funded project aimed at building arthroscopic surgical training simulators. The haptic device work was also the technology exploration that directly led to the [FeelIT project](/portfolio/FeelIT/) — a haptic interface for visually impaired people. The legacy C++/CLI code is preserved alongside the modern Python/FastAPI web application.

![Haptic Simulation](/images/projects/haptic_sim.svg)
