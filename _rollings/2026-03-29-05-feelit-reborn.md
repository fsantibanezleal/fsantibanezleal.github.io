---
title: 'Fourteen Years Later'
date: 2026-03-29
permalink: /rollings/2026/03/feelit-reborn/
tags:
  - FeelIT
  - Accessibility
  - Haptics
  - Braille
  - Personal Projects
---

Fourteen years later
======

Started rebuilding FeelIT. The original pin-array project from my undergrad days at UdeC, frozen since 2012. The hardware that stopped us — miniaturized electromechanical pin arrays at reasonable cost — still isn't quite there. But the software side of the equation has changed completely.

In 2008 I was writing Windows Forms with OpenGL. Now it's a FastAPI server with Three.js rendering. The Braille reader already works — loads Gutenberg texts, converts to 3D positioned cells, navigates with scene-native controls. 49 tests passing. Four distinct workspaces routed on port 8101.

![FeelIT 2.0 workspaces](/images/projects/feelit2_modes.svg)

The part I'm most proud of is the methodological honesty. There's an Implementation Gap Audit document that explicitly states what works and what doesn't. No over-claiming. The 3D Object Explorer is "staged" — visually functional but waiting for physical haptic integration. The Braille Reader is "active" — fully working with keyboard interaction. The Haptic Desktop is "prototype" — demonstrates the concept but expanding.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Material profiles:</strong><br/>
8 tactile materials: Polished Metal, Carved Stone, Unfinished Wood, Rubber, Foam, Textured Polymer, Coated Paper, Glazed Ceramic<br/>
<span style="color:#5a9ac0;font-size:13px;">Each with stiffness (N/mm), static/dynamic friction, texture amplitude/spacing, vibration Hz</span>
</div>

![Braille Reader workspace](/images/projects/screenshots/feelit2_braille_reader.png)

Strange feeling revisiting a project after 14 years. The 20-year-old me who built pin arrays with electromagnets would be amazed that the Braille cells are now floating in a Three.js scene. The 35-year-old me building this version is more concerned with whether the tests pass and the gap audit is honest. [FeelIT 2.0 on GitHub](https://github.com/fsantibanezleal/UDEC_FEELIT).
