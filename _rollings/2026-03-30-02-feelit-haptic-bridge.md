---
title: 'The Bridge to Hardware'
date: 2026-03-30
permalink: /rollings/2026/03/feelit-haptic-bridge/
tags:
  - FeelIT
  - Haptics
  - Hardware
  - Bridge
  - Diagnostics
---

The bridge to hardware
======

Added native bridge bootstrap diagnostics to [FeelIT 2.0](https://github.com/fsantibanezleal/UDEC_FEELIT). This is the first step toward real haptic hardware integration — the system now detects at startup whether a physical haptic device is present, reports its capabilities, and gracefully falls back to the null backend if nothing is connected.

The architecture was designed for this moment from the beginning. The haptic backend is an abstraction layer:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Backend abstraction:</strong><br/>
HapticBackend.status() → {name, device_present, supported_features}<br/>
HapticBackend.start() / .stop()<br/>
<span style="color:#5a9ac0;font-size:13px;">NullBackend returns device_present=False, features=[] — the app works identically, just without force feedback</span>
</div>

The diagnostic output now shows at the `/api/health` endpoint and in the frontend header. When a real device driver is eventually integrated (likely USB HID or vendor SDK), the only change is swapping the backend implementation — zero changes to the 4 workspaces, the Braille engine, or the material profiles.

![FeelIT 2.0 architecture](/images/projects/feelit2_arch.svg)

The null backend isn't a limitation — it's a feature. It means every accessibility feature in FeelIT works on every computer, regardless of whether a haptic device is plugged in. The hardware is an enhancement, not a requirement.
