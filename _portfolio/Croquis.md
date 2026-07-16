---
title: "Croquis — On-Device 3D Reconstruction of Real Spaces on Android"
date: 2026-07-15
excerpt: "An Android app that turns a walk-through (camera, IMU and GPS, no lidar) into a metric, consistency-gated point-cloud reconstruction computed fully on the phone, stored on the phone as a scene library with an honest uncertainty budget. Imagery never leaves the device. In development (v0), Apache-2.0."
collection: portfolio
tags: [mobile-apps, android, 3d-reconstruction, on-device, arcore, privacy]
---

An Android app that turns a **walk-through into a metric 3D reconstruction, fully on the phone**: camera, IMU and GPS (explicitly no lidar), fused into a consistency-gated point cloud you can view, measure and export, with an honest uncertainty budget. Imagery never leaves the device. [Source on GitHub](https://github.com/fsantibanezleal/Croquis). **In development (v0)**, Apache-2.0.

## Design pillars

- **Sensors own the trajectory and the metric scale** (ARCore visual-inertial odometry, GPS geo-anchoring); the neural depth model contributes dense geometry only, never the trajectory.
- **Consistency over peak fidelity**: keyframe depth is fused only where it agrees with the sensor trajectory and neighbouring keyframes. Disagreeing or far-field geometry is not deleted; it stays visible in a low-confidence context tier.
- **General devices, not flagships**: keyframe processing with thermal duty-cycling and adaptive rates.
- **The scene is the product**: reconstructions persist on-device as tiled point/voxel stores with confidence, geo-anchor and uncertainty metadata, behind versioned data contracts.

## Two tiers, one metric scale

The phone reconstructs live with a light model and can reprocess itself with a heavier one. Above both sits [Croquis Station](https://github.com/fsantibanezleal/Croquis_Station): the same capture session reconstructed on a local GPU at settings no phone sustains (full keyframe set, high resolution, heavy models), anchored to the phone's own VIO metric scale so the output is in true metres. It is the mobile end of the same reconstruction line as [Lidar3D](https://lidar3d.fasl-work.com), with the same honesty rules.
