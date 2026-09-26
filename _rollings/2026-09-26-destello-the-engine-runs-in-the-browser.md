---
title: 'Destello: the engine runs in the browser, and matches the reference spike for spike'
date: 2026-09-26
permalink: /rollings/2026/09/destello-the-engine-runs-in-the-browser/
tags:
  - destello
  - neuroscience
  - simulation
  - webgpu
---

Destello: the engine runs in the browser, and matches the reference spike for spike
======

![The browser engine of flycns: one LIF step as seven WebGPU kernels, one graded frame of the hybrid, and three engines held to one Python reference](/images/projects/flycns_browser_engine.svg)

The models here are not mine. The spiking brain is the leaky integrate-and-fire model of Shiu and colleagues (Nature, 2024), the visual system is the connectome-constrained network of Lappalainen and colleagues (Nature, 2024), and the wiring is the MaleCNS v1.0 connectome of Berg and colleagues (Cell, 2026). What I build is the software that runs them in a visitor's browser, held to one reference.

Two things happened since the last note. On the 24th, Destello's visual world was built: an analytic renderer of what each ommatidium of both eyes sees, integrating 19 rays over its acceptance, with the exact truth per ommatidium and frame (depth, object, optic flow, time to contact), and the thirteen cases with their 222 stimuli, split by scene layout. Today, flycns 0.07.000 carries the engine into the browser, in TypeScript on the CPU and in WGSL on WebGPU.

On the whole MaleCNS, 166,700 neurons and 25.6 million connections, under the moderate gustatory drive the tests use, the CPU engine gives the Python reference's 18,063 spikes in 200 ms: the same neurons at the same steps. The WebGPU engine fires the same neurons the same number of times, and runs those 200 ms in about 0.4 s on a laptop GPU. Its spike order parts from the reference after 6,281 spikes, at the first threshold that float32 and float64 decide differently, which is where the PyTorch engine parts too; from there the two are samples of one process, and they are compared as such.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">What made the GPU sums reproducible: integers.</strong><br/>
Spikes are delivered by GPU threads in whatever order the hardware runs them, and floating-point sums depend on order. So the delivery is summed in int32 fixed point, on a scale chosen so that no neuron's largest possible input can overflow. The graded optic lobe has no such bound, so there each neuron gathers its own inputs in their original order instead.<br/>
<span style="color:#5a9ac0;font-size:13px;">Both packages are published: flycns on PyPI and @fasl-work/flycns on npm. The npm one waited until it carried the engine rather than ship an empty package. Nothing is deployed yet; the engine runs over the thirteen cases come next, then the readouts, the export and the 3D brain.</span>
</div>

One thing went wrong on the way: the first GPU test run died with no message at all. The GPU instance in Node was being garbage-collected under the device; holding a reference to it for the life of the process fixed it. It is written down in the engine's documentation.

[Product repository](https://github.com/fsantibanezleal/CAOS_RES_Destello) · [flycns](https://github.com/fsantibanezleal/CAOS_FlyCNS) · [the browser engine, documented](https://github.com/fsantibanezleal/CAOS_FlyCNS/blob/main/docs/models/06_browser.md)
