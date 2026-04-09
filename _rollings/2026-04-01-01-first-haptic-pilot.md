---
title: 'First Touch'
date: 2026-04-01
permalink: /rollings/2026/04/first-haptic-pilot/
tags:
  - FeelIT
  - Haptics
  - Hardware
  - Pilot
  - Milestone
---

First touch
======

The null backend served its purpose. For weeks, FeelIT 2.0 ran entirely on visual feedback — keyboard-driven pointer emulation, no force feedback, no physical sensation. Everything worked, but it was like building a musical instrument and never hearing it play.

Today we ran the first bounded native haptic pilot. Real force feedback through a physical device. The stylus pushes back when it touches a virtual surface. The material profiles — stiffness, damping, friction — are no longer just numbers in a JSON file. They're physical sensations.

![FeelIT 2.0 architecture with haptic backend](/images/projects/feelit2_arch.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The backend abstraction paid off:</strong><br/>
NullBackend → NativeBackend: same API, same workspaces, same tests<br/>
<span style="color:#5a9ac0;font-size:13px;">Only the force computation changed. Everything else — Braille cells, material profiles, scene controls — worked unchanged.</span>
</div>

The pilot is bounded — limited workspace, limited force range, careful safety constraints. But it works. The architecture decision to make the haptic backend a pluggable abstraction from day one meant that integrating real hardware required zero changes to the 4 workspaces, the Braille engine, or the material profiles. Only the backend implementation changed.

Version jumped to 2.18.000. The configuration review flow lets you inspect and adjust haptic parameters before committing to a session — important when force feedback can be physically felt by the user.

From v0.1.0 (Braille preview only) to v2.18.000 (native haptic execution) in one month. The project that was frozen for 14 years is moving fast. [FeelIT 2.0 on GitHub](https://github.com/fsantibanezleal/UDEC_FEELIT).
