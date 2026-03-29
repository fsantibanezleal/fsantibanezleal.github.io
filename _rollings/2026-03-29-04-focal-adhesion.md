---
title: 'Cells That Grip'
date: 2026-03-29
permalink: /rollings/2026/03/focal-adhesion/
tags:
  - CPM
  - Biophysics
  - Focal Adhesion
  - Mechanobiology
---

The Cellular Potts Model already had filopodia — Gaussian-shaped membrane protrusions that extend, retract, and sense the local environment. But they were floating. They could push into the substrate, detect chemical gradients, and influence the Hamiltonian, but they had no concept of gripping. A real filopodium that contacts a stiff substrate forms focal adhesion complexes — clusters of integrin receptors that physically anchor the cell to the extracellular matrix. And those adhesions are not passive anchors. They are mechanosensors.

The new focal adhesion dynamics give filopodia the ability to form adhesion complexes on contact with the substrate. When a filopodium tip reaches the surface, adhesion molecules begin to accumulate. The adhesion strength grows with time as more integrins cluster and the complex matures.

![Cell model with Gaussian filopodia](/images/rollings/cpm_cell_model.svg)

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Focal adhesion strength:</strong><br/>
F<sub>adh</sub>(t) = F&#8320; &times; (1 - exp(-t/&tau;)) &mdash; adhesion matures with time, &tau; = lifetime constant
</div>

The exponential maturation curve is a simplification, but it captures the essential behavior: adhesions start weak and strengthen over time toward a plateau F0. The lifetime constant tau controls how fast the complex matures — on stiff substrates tau is short (fast maturation), on soft substrates tau is long (slow maturation, often the adhesion disassembles before reaching full strength). This is the core of mechanosensing.

The really interesting part is what happens under tension. When the cell body contracts and pulls on a filopodium, the force is transmitted through the focal adhesion to the substrate. On a stiff substrate, the substrate does not deform much, so the adhesion complex experiences sustained tension — and sustained tension promotes further integrin recruitment, making the adhesion stronger. On a soft substrate, the substrate deforms, the tension dissipates, and the adhesion weakens and eventually releases. The cell literally feels the difference.

This is durotaxis — the tendency of cells to migrate toward stiffer regions. It emerges naturally from the adhesion dynamics without any explicit gradient-sensing rule. Filopodia on the stiff side form stronger adhesions, generate more traction, and win the tug-of-war that determines the cell's net direction. Filopodia on the soft side lose their grip and retract. The migration bias is a mechanical consequence, not a programmed behavior.

In the CPM Hamiltonian, the adhesion energy now depends on the local substrate stiffness, the adhesion maturation state, and the current mechanical tension. It adds three new terms to an already complex energy landscape, but the phenomenology it produces — durotaxis, rigidity sensing, adhesion-dependent spreading — justifies the complexity. Cells without focal adhesion dynamics just slide around. Cells with it grip, spread, and make decisions. [CPM on GitHub](https://github.com/fsantibanezleal/SCIAN_LEO_CPM).
