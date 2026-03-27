---
title: 'Feeling Virtual Objects'
date: 2009-08-20
permalink: /rollings/2009/08/haptic-collision/
tags:
  - Haptics
  - Collision Detection
  - UdeC
  - Thesis
---

The octree collision detection is finally working properly with the PHANToM Omni device. You move the stylus and when it hits a virtual object, you actually feel resistance. It is one thing to see it on screen, another to feel it in your hand.

The tricky part was getting the force computation fast enough — the haptic loop needs to run at 1 kHz or the force feedback feels unstable. The octree helps enormously by pruning the search space, but even so, every microsecond counts. The SAT triangle-triangle intersection test was the last piece — more robust than the vertex-proximity approach we had before.

The surgeons who will eventually use the arthroscopic training simulator would never guess how much math goes into making a virtual knee feel right. [Haptic simulator on GitHub](https://github.com/fsantibanezleal/UDEC_Haptic_SIM).
