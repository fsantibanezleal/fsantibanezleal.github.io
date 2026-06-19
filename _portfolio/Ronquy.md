---
title: "Ronquy — On-Device Snore Detection"
date: 2026-06-14
excerpt: "A private mobile app that detects snoring on-device, overnight, with no audio ever leaving the phone — a YAMNet + TFLite model runs an 8-hour native audio-and-inference loop locally."
collection: portfolio
tags: [mobile, audio-ml, on-device, yamnet, tflite, private]
---

> **Private product.** This is proprietary work; the app is private. This page describes the architecture and intent without exposing internal logic.

**Ronquy** detects snoring **on-device, all night, with no audio ever leaving the phone**. A real YAMNet model runs through TFLite (react-native-fast-tflite) inside a native overnight loop that captures audio and runs inference locally for ~8 hours. The heavy, time-critical path is **native**, not a JavaScript shim. Only derived events are stored; the audio itself never leaves the device.

## Why it matters

Privacy is the product. A snore tracker that never uploads your sleep audio is fundamentally more trustworthy than one that does — and doing the inference on-device also means it works offline and costs nothing per night to run. An optional cloud mode (FastAPI + Postgres + own auth) lets a user register and sync results across devices, but the detection itself is fully local.

## What it demonstrates

- A hard mobile-ML pattern end to end: a native, battery-aware, all-night audio + inference loop with a **real model on-device** (no mock).
- A privacy-first design where the sensitive data never leaves the phone.
- A cross-platform app shipped as a **standalone build**, with an optional own-auth cloud backend.
