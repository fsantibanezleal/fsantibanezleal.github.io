---
title: 'Where Can the Robot Reach?'
date: 2026-03-28
permalink: /rollings/2026/03/robot-workspace/
tags:
  - Robotics
  - Kinematics
  - Workspace
---

The Scorbot III has 5 degrees of freedom, and you might think that means it can reach anywhere in a sphere around its base. It cannot. The reachable workspace is a complex torus-like volume carved out by joint limits, link lengths, and the coupling between joints. Some orientations are simply unreachable at certain positions. The workspace is not a sphere — it is a strange, asymmetric solid that you only truly understand by sweeping through all joint combinations and plotting the result.

![Robot workspace and DH frames](/images/rollings/robot_workspace.svg)

For the robotic writer, the letters are arranged on a circular arc at radius 280mm from the base, the writing line sits at 300mm, and the safe travel height is 75mm above the surface. These numbers were not chosen for aesthetics — they were chosen because they fall inside the reachable workspace for the approach angle we need.

The approach angle of -70 degrees (near-vertical) was the result of a long search. You want the pen to come down as close to perpendicular as possible for clean strokes, but a truly vertical approach at the required distance pushes joint 3 past its limit. So -70 degrees it is — a compromise between calligraphy quality and kinematic feasibility.

![Denavit-Hartenberg reference frames](/images/rollings/robot_dh_frames.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Forward kinematics chain:</strong><br/>
T<sub>0</sub><sup>5</sup> = T<sub>0</sub><sup>1</sup> &middot; T<sub>1</sub><sup>2</sup> &middot; T<sub>2</sub><sup>3</sup> &middot; T<sub>3</sub><sup>4</sup> &middot; T<sub>4</sub><sup>5</sup><br/>
<em>5 transformations compose the end-effector pose</em>
</div>

The Denavit-Hartenberg convention gives you a systematic way to assign coordinate frames to each joint and compute the full chain. Each 4x4 homogeneous transformation encodes a rotation and a translation, and the product of all five gives you the end-effector position and orientation in the base frame. Inverse kinematics — going from a desired pen position back to joint angles — is where the real pain lives, especially with 5 DOF where you have to sacrifice one degree of orientation freedom.

Every letter the robot writes is a sequence of these inverse kinematics solutions, interpolated smoothly so the pen does not jerk. The workspace analysis tells you which letters are even possible. The rest is just path planning. [Robotic Writer](https://github.com/fsantibanezleal/Udec_Robotic_Writer).

{% include youtube.html id="ubUdNsb0W-o" %}
