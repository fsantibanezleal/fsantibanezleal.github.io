---
title: "Conectoma, a Fly Connectome Used as a Frozen Vision Network, Measured Against Its Own Nulls"
date: 2026-09-22
excerpt: "The Janelia MaleCNS v1.0 wiring of the male fruit fly (166,691 neurons, CC-BY) frozen and used as the architecture of a vision network for depth from a moving camera and figure-ground segmentation. Synapse counts and signs never change; every result is an effect size against nulls built from the same wiring. Reservoir plus trained readout, paired per clip: +0.197 against a random sparse graph, +0.136 against a sign shuffle, -0.017 against a degree-preserving rewiring.<br/><img src='/images/projects/conectoma_pipeline.svg'>"
collection: portfolio
tags: [connectome, drosophila, computer-vision, null-controls, flyvis, neuroscience]
---

Lappalainen et al. (Nature 2024) constrained a network with the optic-lobe connectome and trained it on optic flow, which is what fly vision evolved for. **Conectoma** asks whether the same frozen wiring supports dense prediction tasks it did not evolve for, on a newer and larger connectome, with the controls that make the attribution testable.

![Conectoma, the MaleCNS wiring compiled and frozen, three regimes, video cases, and every result an effect size against three nulls](/images/projects/conectoma_pipeline.svg)

## The wiring is a measurement and never moves

The MaleCNS v1.0 wiring is compiled in memory by a compiler identical to flyvis's on the published connectome and frozen: wiring, synapse counts and signs stay fixed, with parity to the published model voltage for voltage. Three regimes share one starting point and differ only in what is learned: a readout head alone, the per-cell-type biophysics in the published 734-parameter form, or a per-edge gain. Null controls are matched in size at the level of cells: degree-preserving rewiring, a size-matched random sparse graph, a sign shuffle. Twenty-two methods plus three controls over sixteen video cases with six physical variants each, on TartanAir with Spring, Hypersim, Sintel and rendered fly-eye scenes as transfer and control domains.

## The number that matters is the third one

![Conectoma, the App: the pathway's chain animated, what the eye receives, what the network concludes, what is really there](/images/projects/conectoma_app_dark.png)

With the connectome as a reservoir and a trained readout, paired per clip on the cases: +0.197 [+0.173, +0.214] against a size-matched random sparse graph, +0.136 [+0.121, +0.168] against a sign shuffle, and -0.017 [-0.021, -0.008] against a degree-preserving rewiring. What the biology adds over a random graph of the same size and the same signs, it does not add over a rewiring that keeps every cell's degree. Building it exposed six defects, two inherited: a placement rule that dropped 3,270 connections and a column frame a half-turn off the engine's.

## Live, measured, and superseded on purpose

Live at its custom domain with 1,183 checks run against the HTTPS URL and all sixteen clips verified against their manifests; version 0.10.001 animates the pathway. Its plan was not validated, so the lifecycle reads planned. My own verdict after 0.10 was that it showed a type-level abstraction of one eye rather than the real connectome working, and a successor, Destello, was ordered to drive the whole nervous system through both real eyes; Conectoma stays as it is. It does not claim that flies perform semantic segmentation or single-image depth estimation, and a negative answer to its central question is a valid outcome.

[Live](https://conectoma.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_RES_Conectoma)
