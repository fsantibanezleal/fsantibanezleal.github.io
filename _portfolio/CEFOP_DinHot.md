---
title: "Dynamic Holographic Optical Tweezers"
date: 2010-04-01
excerpt: "Real-time holographic phase mask computation for optical particle trapping using the Gerchberg-Saxton algorithm.<br/><img src='/images/projects/cefop_dinhot.svg'>"
collection: portfolio
tags: [optics, holography, computational-physics, fastapi, python]
---

A web application for **real-time computation and visualization of holographic phase masks** used in optical tweezers systems. Originally developed during my time at the [Center for Optics and Photonics (CEFOP)](http://cefop.udec.cl/), Universidad de Concepcion, this project bridges computational optics with interactive visualization.

![Architecture](/images/projects/cefop_dinhot.svg)

## The problem

Holographic optical tweezers (HOT) use a Spatial Light Modulator (SLM) to shape a laser beam into multiple focused traps capable of holding and manipulating microscopic particles. Computing the required phase mask in real time is the core challenge: given desired trap positions in 3D space, determine the phase pattern that produces the correct intensity distribution at the focal plane.

## The approach

The system implements the **weighted Gerchberg-Saxton (GS) algorithm**, an iterative Fourier-transform method that alternates between the SLM plane and the focal plane. At each iteration: (1) the current phase mask is Fourier-transformed to the focal plane, (2) the resulting amplitude is replaced with the desired trap amplitudes while preserving the computed phase, (3) the inverse FFT returns to the SLM plane, and (4) the amplitude is replaced with the uniform illumination profile while preserving the phase. Per-trap weights are adjusted at each iteration to equalize intensities across all targets -- traps receiving too much light have their weights reduced, and vice versa. The algorithm converges when the intensity uniformity across traps falls below a threshold, typically within 20-50 iterations.

## Technical highlights

- **Backend**: Python/FastAPI serving the GS computation with NumPy for FFT operations
- **Improved phase scaling**: corrected phase mask normalization for accurate multi-trap intensity distribution
- **Frontend**: HTML5 Canvas for dual visualization — interactive trap placement and real-time phase mask rendering
- **Communication**: REST API + WebSocket for streaming convergence data
- **Legacy preservation**: The original C++/.NET version (2010) is preserved alongside the modern rewrite
- **Testing**: 59 automated tests covering optical computation, API endpoints, and frontend interactions

## From the lab to the browser

The original implementation ran on lab hardware controlling a physical SLM. The modern version recreates the full computational pipeline as an interactive web tool, making it accessible for teaching and exploration without specialized equipment.

[View on GitHub](https://github.com/fsantibanezleal/CEFOP_DinHot)
