---
title: "3D Embryo Cell Migration Simulator"
date: 2011-09-01
excerpt: "Interactive 3D simulation of collective cell migration on a spherical zebrafish embryo surface during gastrulation.<br/><img src='/images/projects/sphersim.svg'>"
collection: portfolio
tags: [biophysics, simulation, three-js, fastapi, developmental-biology, python]
---

A **3D simulation of Deep Forming Cell (DFC) collective migration** on the surface of a spherical zebrafish embryo during epiboly — a fundamental process in vertebrate development where cells spread to cover the yolk cell.

![Spherical Model](/images/projects/sphersim.svg)

## Biological context

During zebrafish gastrulation, the Enveloping Layer (EVL) expands from the animal pole toward the vegetal pole. Deep Forming Cells (DFCs) are carried along by the advancing EVL margin, eventually clustering to form the Kupffer's vesicle — an organ critical for establishing left-right body asymmetry. Understanding the mechanics of this collective migration requires modeling how cells move, collide, and respond to tissue-level forces on a curved surface.

## The simulation

Cells move on the surface of a sphere using an **AER (Azimuth-Elevation-Radius) coordinate system** with automatic wrapping at the poles. Each cell is coupled to the EVL margin through a configurable force, with stochastic noise representing biological variability. Pairwise collision detection ensures cells maintain physical separation while migrating collectively.

## Technical highlights

- **Backend**: Python/FastAPI with real-time WebSocket streaming of simulation state
- **Frontend**: Three.js (r128) for interactive 3D visualization with orbit controls
- **Cartesian push collision model**: improved cell-cell interactions using 3D displacement vectors projected back onto the sphere surface
- **Layer-based DFC management**: cells organized by developmental layer with configurable coupling forces
- **Controls**: Play/Pause/Step for continuous or frame-by-frame exploration
- **Configurable**: Cell count, radial size, EVL speed, noise amplitude, collision parameters
- **Legacy**: Preserves the original MATLAB implementation alongside the modern version
- **23+ automated tests** across cell, collision, geometry, and simulation modules

## From SCIAN-Lab

This project originated at the [Laboratory for Scientific Image Analysis (SCIAN-Lab)](http://www.scian.cl/) at the Universidad de Chile, where I worked on computational tools for developmental biology research in collaboration with the NEMO Millennium Nucleus.

[View on GitHub](https://github.com/fsantibanezleal/SCIAN_EVL_SpherSIM)
