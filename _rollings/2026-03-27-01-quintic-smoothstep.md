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

Spent the morning comparing cubic versus quintic smoothstep for the [robotic writer's](https://github.com/fsantibanezleal/Udec_Robotic_Writer) trajectory interpolation, and the difference is immediately visible in the letter quality. The cubic smoothstep S₁(t) = 3t² - 2t³ gives C¹ continuity -- velocity is zero at both endpoints, which avoids sudden starts and stops, but the acceleration is discontinuous at the transitions. That discontinuity translates directly into a mechanical jerk that makes the pen skip or dig in slightly at the beginning of each stroke segment. The quintic smoothstep S₂(t) = 6t⁵ - 15t⁴ + 10t³ gives C² continuity -- both velocity and acceleration are zero at the endpoints, producing genuinely smooth motion through the transitions. The letters went from "readable but wobbly" to "clean and consistent" just from that one change. The trapezoidal velocity profile handles the cruise phase: accelerate at a_max until reaching v_max, cruise at constant speed, then decelerate symmetrically. When the segment is too short to reach v_max -- which happens often in tight curves and small letters -- the profile degrades gracefully to a triangular shape, accelerating to whatever peak velocity the distance allows and immediately decelerating. No special-case code needed, just a min() on the cruise duration. The combination of quintic blending at segment boundaries and trapezoidal speed limiting along each segment gives the robot a very natural writing cadence. The cursive lowercase 'e' was the acid test -- it requires a tight loop with a direction reversal, and it finally looks like a letter instead of a squashed oval.
