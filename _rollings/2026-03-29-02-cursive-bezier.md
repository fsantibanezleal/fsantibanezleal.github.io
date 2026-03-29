---
title: 'The Robot Learns Cursive'
date: 2026-03-29
permalink: /rollings/2026/03/cursive-bezier/
tags:
  - Robotics
  - Bezier
  - Cursive
  - Trajectory
---

The original robotic writer picks up letter blocks and places them one at a time. It is a pick-and-place operation — move to the letter, grasp, move to the writing line, place, return. Each letter is a discrete event with its own approach, grasp, and retract cycle. For printed text, this works. For cursive, it is fundamentally wrong. Cursive means the pen never leaves the paper between letters. The trajectory is one continuous, flowing curve.

The new cursive mode replaces the pick-and-place paradigm with Bezier spline tracing. Each letter is defined as a sequence of cubic Bezier segments, and the connections between letters are themselves Bezier curves that ensure smooth tangent continuity at the joints.

![Robot workspace and DH frames](/images/rollings/robot_dh_frames.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Cubic B&eacute;zier:</strong><br/>
B(t) = (1-t)&sup3;P&#8320; + 3(1-t)&sup2;tP&#8321; + 3(1-t)t&sup2;P&#8322; + t&sup3;P&#8323;, &nbsp; t &isin; [0,1]
</div>

The four control points P0 through P3 define everything. P0 and P3 are the start and end of the segment; P1 and P2 are the control handles that determine the curvature. The tangent at P0 points toward P1, and the tangent at P3 points away from P2. To get smooth cursive — no sharp corners between letters — you enforce that the outgoing tangent of one segment aligns with the incoming tangent of the next. This is C1 continuity, and it is what makes the strokes look like handwriting rather than a sequence of arcs glued together.

The trajectory planning is completely different from the block-placement mode. Instead of a sequence of discrete waypoints with lift-move-place cycles, you now have a parametric curve that must be sampled at a rate matching the robot's servo loop. Too few samples and the curve becomes a polygon. Too many and the servo buffer overflows. The sampling density also needs to vary with curvature — tight loops need more points than straight runs.

Getting the Scorbot to trace smooth curves exposed every weakness in the inverse kinematics. Small Cartesian displacements near workspace boundaries can demand large joint-space jumps, and the pen wobbles. The solution was to plan the entire word in joint space after converting the Bezier curves, then smooth the joint trajectories directly. It is slower to compute but the strokes are cleaner.

The letters themselves are hand-designed as Bezier templates — each one a small library of control points that gets scaled, rotated, and translated to fit the writing line. There is something satisfying about watching a robot produce something that looks genuinely handwritten, even if every curve was computed to six decimal places. [Robotic Writer on GitHub](https://github.com/fsantibanezleal/Udec_Robotic_Writer).
