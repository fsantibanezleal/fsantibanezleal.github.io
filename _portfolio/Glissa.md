---
title: "Glissa — Expressive Glissando Instrument"
date: 2026-06-15
excerpt: "A private mobile musical instrument whose signature is continuous glissando — slide smoothly between notes — backed by an FX rack, instrument morphing, sampled packs, and a Pro tier with cloud sync.<br/><img src='/images/projects/glissa_architecture.svg'>"
collection: portfolio
tags: [mobile, audio, music, synthesis, private]
---

> **Private product.** This is proprietary work; the app is private. This page describes the architecture and intent without exposing internal logic.

Touchscreen instruments mostly imitate piano keys — discrete, quantized, expressively flat. **Glissa**'s signature is the hard, interesting thing: **continuous glissando**, letting a finger slide between pitches the way a voice or a slide guitar does, in real time, on a phone, with three modes — Keys, Glide, and Auto.

![Glissa — expressive glissando instrument](/images/projects/glissa_architecture.svg)

## What it demonstrates

- A real-time audio engine with a **distinctive expressive feature** rather than a keyboard clone.
- An FX rack, instrument morphing, and a sampled-pack path for richer timbres; a two-finger octave pan and an options sheet round out the playing surface.
- A full consumer-app ladder: a **Pro suite** with local recording, account management, cloud sync, and billing (own-JWT auth + RevenueCat) over a FastAPI + Postgres backend.
- Shipped as a cross-platform **standalone build**.

Expressive control is what separates a toy from an instrument — and the Pro tier turns that expressiveness into a sustainable product.
