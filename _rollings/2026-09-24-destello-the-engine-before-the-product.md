---
title: 'Destello: the whole fly nervous system through both real eyes, engine complete, product not yet'
date: 2026-09-24
permalink: /rollings/2026/09/destello-the-engine-before-the-product/
tags:
  - destello
  - neuroscience
  - simulation
  - honesty
---

Destello: the whole fly nervous system through both real eyes, engine complete, product not yet
======

![Destello, both real eyes into the flycns engine's four coupled models, read out against null wirings, shown as real neurons firing in 3D](/images/projects/destello_pipeline.svg)

I ordered Destello yesterday after Conectoma showed a type-level abstraction of one eye rather than the real connectome working. Conectoma stays as it is and is not reused. Destello drives the whole measured nervous system, the MaleCNS v1.0 connectome of 166,700 neurons, brain and nerve cord, through both real compound eyes, 879 columns on the left and 892 on the right, with the published neuron models and nothing learned inside the wiring. Visitors will watch real neurons fire at real soma positions with real arbors lighting up, from the photoreceptors to the descending neurons and the nerve cord, in slow motion with the biological clock on screen, and intervene.

Today the engine is complete in Python. flycns 0.06.000, its own package, couples the whole CNS in the plan's four engines, each measured on MaleCNS: the published leaky integrate-and-fire model everywhere, where only the photoreceptors fire because histaminergic inhibition of silent spiking neurons carries nothing; flyvis's trained numbers on the MaleCNS optic lobes, 95,925 neurons and 9.07 million connections, bridged to the spiking model; flyvis's own network per eye mapped onto MaleCNS; and the hybrid with stabilisers. A flash reaches the nerve-cord motor neurons through the last three.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Found on the way: the eye model's vertical was one 60-degree lattice step off.</strong><br/>
T4 tuning exposed it; the dorsal rim now sets it. An engine measured against the real connectome before a product exists is the point of doing it in this order: four verified dossiers, a plan, the engine in its own package, and only then the web product.<br/>
<span style="color:#5a9ac0;font-size:13px;">Nothing is deployed. The scene renderer, the thirteen cases with exact ground truth, the export and the 3D brain are next. The package names flycns and @fasl-work/flycns are reserved; publishing waits on a pending publisher and an npm token, which I record as the blocker rather than work around.</span>
</div>

It will not be a digital organism or a complete behavioural model: the raw wiring under these models is known not to form a heading bump, turn toward objects or track small objects, and the product will show those as open with their named reason. The connectome stays frozen; only readouts learn; the body is a kinematic readout display.

[Product repository](https://github.com/fsantibanezleal/CAOS_RES_Destello) · [flycns](https://github.com/fsantibanezleal/CAOS_FlyCNS)
