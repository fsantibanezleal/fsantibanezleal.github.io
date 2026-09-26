---
title: "Destello, the Whole Fly Nervous System Working Through Its Two Real Eyes"
date: 2026-09-24
excerpt: "The MaleCNS v1.0 connectome (166,700 neurons, brain and nerve cord, CC BY 4.0) driven through both real compound eyes and run with the published neuron models, so a visitor can watch real neurons fire at real positions, from the photoreceptors to the nerve cord, and intervene. The engine, flycns, is complete in Python and measured on the real connectome; the web product is not built and nothing is deployed, and this card says so.<br/><img src='/images/projects/destello_pipeline.svg'>"
collection: portfolio
tags: [connectome, drosophila, neuroscience, simulation, flycns, webgpu]
---

**Destello** was ordered on 2026-09-23 after Conectoma showed a type-level abstraction of one eye instead of the real connectome working. It drives the whole measured nervous system, neuron by neuron, through both real compound eyes (879 left and 892 right measured columns), with the published neuron models, a graded optic lobe and a leaky integrate-and-fire model elsewhere, and nothing learned inside the wiring.

![Destello, both real eyes into the flycns engine's four coupled models, read out against null wirings, shown as real neurons firing in 3D](/images/projects/destello_pipeline.svg)

## Engine first

The engine is **flycns**, its own repository and package: it compiles fly connectome releases into simulation-ready signed graphs with positions and per-eye column maps, models the two compound eyes, and simulates the whole central nervous system in Python and, for the browser, on WebGPU with a worker fallback, held together by parity tests. Version 0.06.000 couples the whole CNS in four engines, each measured on MaleCNS: the published leaky integrate-and-fire model everywhere (only the photoreceptors fire, because histaminergic inhibition of silent spiking neurons carries nothing); flyvis's trained numbers on the MaleCNS optic lobes (95,925 neurons, 9.07 million connections) bridged to the spiking model; flyvis's own network per eye mapped onto MaleCNS; and the hybrid with stabilisers. A flash reaches the nerve-cord motor neurons. The eye model's vertical was found one 60-degree lattice step off, which T4 tuning revealed and the dorsal rim now sets.

## What it will be, and what it is today

The plan holds three null wirings, readouts for motion, depth from parallax, time to contact and figure-ground (two of them learned), thirteen cases with at least six variants each, a three.js scene on WebGPU with the WebGL2 fallback, and a deployment decided by the measured export. Today: four verified dossiers, the plan, the engine complete in Python; the scene renderer, the cases, the export and the web product are not built; nothing is deployed; version 0.00.000. The package names flycns (PyPI) and @fasl-work/flycns (npm) are reserved and publishing waits on a pending publisher and an npm token, recorded as the blocker. Not a digital organism: the raw wiring under these models does not form a heading bump, turn toward objects or track small objects, and the product shows those as open with their named reason.

[Product repository](https://github.com/fsantibanezleal/CAOS_RES_Destello) · [flycns repository](https://github.com/fsantibanezleal/CAOS_FlyCNS)
