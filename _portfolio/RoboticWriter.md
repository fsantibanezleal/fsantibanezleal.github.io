---
title: "Robotic Writer"
date: 2009-01-01
excerpt: "Simulation and control of a 5-DOF robotic arm that picks letter blocks and spells words — kinematics, trajectory planning, and hardware integration.<br/><img src='/images/projects/robotic_writer.svg'>"
collection: portfolio
tags: [robotics, kinematics, denavit-hartenberg, simulation, dash, python, matlab]
---

A full simulation and control environment for a **5-DOF Scorbot III robotic arm** that picks letter blocks arranged on a circular arc and places them in a line to spell words. What started as a lab activity at the Universidad de Concepcion in 2004 has evolved into a complete kinematics exploration and trajectory planning tool.

![Robot Setup](/images/projects/robotic_writer.svg)

## The challenge

Given a word to spell, the robot must:
1. Compute the 3D position of each letter on the circular source arc
2. Plan a collision-free trajectory from the current position to the letter
3. Pick the letter with the gripper
4. Move to the corresponding target position on the output line
5. Place the letter and return for the next one

Each step requires solving the **inverse kinematics** problem: given a desired end-effector position and orientation, find the joint angles that achieve it.

## Kinematics

The system uses the **Denavit-Hartenberg (DH) convention** for systematic description of the 5-joint kinematic chain. Each joint i is described by four parameters: link length a_i, link offset d_i, link twist alpha_i, and joint angle theta_i. The homogeneous transformation between consecutive frames is T_i = Rot_z(theta_i) * Trans_z(d_i) * Trans_x(a_i) * Rot_x(alpha_i), and the end-effector pose is obtained by composing all five transformations: T_05 = T_01 * T_12 * T_23 * T_34 * T_45. Inverse kinematics are solved analytically (closed-form geometric solution) for real-time performance, avoiding the convergence issues of iterative numerical methods:

| Joint | Type | d (mm) | a (mm) |
|-------|------|--------|--------|
| Base | Revolute | 340 | 16 |
| Shoulder | Revolute | 0 | 220 |
| Elbow | Revolute | 0 | 220 |
| Pitch | Revolute | 0 | 0 |
| Roll | Revolute | 151 | 0 |

Forward kinematics compose the transformations; inverse kinematics are solved analytically for real-time performance.

## Features

- **Interactive 3D simulation** with animated trajectory playback (Dash + Plotly)
- **Kinematics explorer**: visualize forward/inverse solutions in real time
- **Multiple hardware backends**: Scorbot III (serial), Arduino steppers, MATLAB Engine
- **REST API** for programmatic control
- **Configurable workspace**: letter arc radius, target line spacing, approach heights

## From 2004 to today

The original 2004 lab used MATLAB scripts to command the physical Scorbot III. The modern version wraps the entire system — simulation, kinematics, planning, and optional hardware control — in a Python web application, making the project accessible without the physical robot.

## Live application

![Robotic Writer — 3D kinematics simulation and trajectory planning](/images/projects/screenshots/robotic_frontend.png)

### Demo video — The robot spells words

{% include youtube.html id="ubUdNsb0W-o" %}

[View on GitHub](https://github.com/fsantibanezleal/Udec_Robotic_Writer)
