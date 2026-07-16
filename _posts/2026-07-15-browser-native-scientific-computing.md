---
title: 'Browser-native scientific computing'
date: 2026-07-15
published: false
permalink: /posts/2026/07/browser-native-scientific-computing/
tags:
  - scientific-computing
  - web
  - reproducibility
  - honesty
---

Browser-native scientific computing
======

> Draft for me to rewrite before publishing.

A pattern has settled across most of the tools I have built this year, and it took me a while to name it. Each one runs a real scientific method client-side, in a static single-page app, with an offline precompute lane behind it doing the heavy work. There is no server. The method itself runs in the browser, or the browser replays an artifact the offline lane baked. I want to write down why that shape is worth committing to, and where it honestly does and does not run live.

The live examples are real, not decorative. [ChronoScope](https://chronoscope.fasl-work.com), a univariate forecasting atlas, runs a numpy forecasting core in a Pyodide worker so you can bring your own series and get a backtested result without a round trip. [Pulso](https://pulso.fasl-work.com), a well-test shape catalogue, runs its classical physics core (a Bourdet derivative plus a Warren-Root dual-porosity model via Stehfest inversion) in Pyodide, and runs four ONNX models through onnxruntime-web to classify a pasted curve against baked cluster medoids, in the tab. [FrothSeg](https://frothseg.fasl-work.com) goes furthest: a SAM-family foundation model (SlimSAM) segments flotation-froth bubbles zero-shot, in the browser, on an image the user uploads, via transformers.js and onnxruntime-web with a WASM fallback. That is a foundation model doing inference on your data, on your machine, with nothing sent anywhere.

The honest counterpoint matters just as much. Not everything runs live, and I say which. ChronoScope's four time-series foundation models (Chronos-Bolt, Chronos-2, TimesFM-2.5, TiRex-2) are heavy checkpoints that run offline, and one of them needs a WSL2 and CUDA lane because its kernels have no Windows wheels; the browser lane is the numpy core, and those foundation-model numbers are baked. The min-cut that solves PitForge's ultimate pit limit and the Whiten population balance in the crusher tool run in the precompute lane and ship as artifacts. So the shape is really two lanes: a light method that genuinely runs in the browser, and a heavy method that is computed once offline, seeded, and committed as a result the static site reads.

Why build it this way. Three reasons, and none of them is that it looks modern.

First, no server means nothing to run, secure, pay for or keep alive. A static site on GitHub Pages does not have a backend that can leak a dataset or go down. For the tools where the model runs client-side, the user's data never leaves their browser, which is not a privacy slogan but a property of where the compute happens.

Second, it is reproducible in a way a live API is not. The offline lane is seeded and its outputs are committed, so the numbers a visitor sees are the numbers in the repo, not whatever a service returned today. When a foundation-model result is baked, it is baked from a specific checkpoint on a specific run, and that run is in version control. A benchmark you cannot re-derive is a screenshot; a committed artifact is evidence.

Third, it is shareable down to a URL. There is no install, no notebook, no environment to match. The method, the data contract and the result travel together as a page, and the person you send it to sees exactly what you see.

The failure mode of this shape is pretending the two lanes are one: implying a heavy model runs in the browser when it was baked offline, or dressing a replay up as live compute. I have tried to keep that line visible in each tool, because the whole reason browser-native is worth anything is that a visitor can trust what the page says it is doing. Real methods, client-side where they truly run, honestly labelled where they do not, is a more useful thing to hand someone than a demo that hides its server.
