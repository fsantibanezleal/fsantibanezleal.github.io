---
title: 'Smooth Moves'
date: 2026-03-27
permalink: /rollings/2026/03/Post-2026-03-27-01/
tags:
  - Robotics
  - Trajectory
  - Kinematics
  - Motion Planning
---

Smooth Moves
======

Spent the morning comparing cubic versus quintic smoothstep for the [robotic writer's](https://github.com/fsantibanezleal/Udec_Robotic_Writer) trajectory interpolation, and the difference is immediately visible in the letter quality.

![Smoothstep comparison](/images/rollings/smoothstep_comparison.svg)

The cubic smoothstep gives C1 continuity -- velocity is zero at both endpoints, but acceleration jumps at the transitions:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Cubic smoothstep (C&#185; continuous):</strong><br/>
s(t) = 3t² − 2t³
</div>

The quintic version gives C2 continuity -- both velocity and acceleration are zero at the endpoints:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Quintic smoothstep (C&#178; continuous):</strong><br/>
s(t) = 6t⁵ − 15t⁴ + 10t³
</div>

Why does C2 matter? Zero acceleration at both endpoints means **no jerk** at segment transitions. That discontinuity in the cubic version translates directly into mechanical jerk that makes the pen skip or dig in slightly at the beginning of each stroke. The quintic version produces genuinely smooth motion through the transitions -- letters went from "readable but wobbly" to "clean and consistent" from that one change.

The trapezoidal velocity profile handles the cruise phase: accelerate at `a_max` until reaching `v_max`, cruise at constant speed, then decelerate symmetrically. When the segment is too short to reach `v_max` -- which happens often in tight curves and small letters -- the profile degrades gracefully to a triangular shape. No special-case code needed, just a `min()` on the cruise duration.

The cursive lowercase 'e' was the acid test -- it requires a tight loop with a direction reversal, and it finally looks like a letter instead of a squashed oval. [Repository here](https://github.com/fsantibanezleal/Udec_Robotic_Writer).
