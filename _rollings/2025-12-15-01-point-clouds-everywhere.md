---
title: 'Point Clouds Everywhere'
date: 2025-12-15
permalink: /rollings/2025/12/Post-2025-12-15-01/
tags:
  - Consulting
  - 3D
  - Point Cloud
---

Point Clouds Everywhere
======

Spent the day debugging cylindrical coordinate transformations for crusher liner profiles. Parsing raw DXF files from laser scanners is surprisingly tricky -- coordinate system conventions, noise filtering, alignment to the crusher axis. But seeing the wear profile emerge from a million scattered points is deeply satisfying. The geometry is beautiful when it finally works.

![Crusher wear system architecture](/images/projects/crusher_wear_system.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Coordinate transformation pipeline:</strong><br/>
Point cloud (x,y,z) &#8594; Cylindrical (r,&#952;,h) &#8594; Profile R(&#952;,h)<br/>
<span style="color:#5a9ac0;font-size:13px;">From a million points to a wear curve</span>
</div>
