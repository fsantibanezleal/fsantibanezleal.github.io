---
title: "Cellular Potts Model Simulator"
date: 2013-06-01
excerpt: "Interactive simulator for zebrafish embryonic cell migration using deformable cell bodies and filopodia-driven motility.<br/><img src='/images/projects/cpm_simulator.svg'>"
collection: portfolio
tags: [biophysics, cellular-potts-model, simulation, computational-biology, fastapi, python]
---

A **Cellular Potts Model (CPM) simulator** for modeling collective migration of Dorsal Forerunner Cells (DFCs) during zebrafish Kupffer's vesicle formation. Unlike particle-based models, the CPM represents cells as **deformable bodies** on a lattice, capturing shape changes, area constraints, and contact interactions naturally.

![CPM Model](/images/projects/cpm_simulator.svg)

## Why a Cellular Potts Model?

Real cells are not point particles. They have area, they deform when they push against neighbors, and they extend structures (filopodia) that generate directional forces. The CPM captures all of this on a lattice where each cell occupies multiple pixels, and the system evolves by minimizing a Hamiltonian that balances:

- **Area constraint**: cells resist compression and expansion
- **Perimeter constraint**: cells resist excessive deformation
- **Adhesion energy**: cells stick to neighbors with type-dependent strength
- **Motility**: Gaussian filopodia generate directed forces toward migration targets

## Key features

- **Deformable cell model** with configurable Gaussian filopodia
- **Durotaxis mechanics**: cells respond to stiffness gradients in the tissue, biasing migration toward stiffer regions — a key mechanism in developmental biology
- **Real-time 2D Canvas visualization** at 10-50 FPS
- **Per-cell color coding** for tracking individual cells
- **Tissue boundary dynamics**: EVL epiboly front and DEB convergence margin
- **Cell proliferation** with configurable 8-stage schedule
- **Two-pass collision resolution** (soft + hard pass)
- **REST API** with Swagger/ReDoc documentation
- **~30 automated tests** covering cells, agents, and simulation logic

## Technical stack

- **Backend**: Python/FastAPI with NumPy for lattice operations
- **Frontend**: HTML5 Canvas 2D rendering with interactive slider controls
- **Communication**: REST API + WebSocket for live simulation streaming
- **Legacy**: Previous C++/CLI codebase (2014-2024) preserved for reference

## Research context

Developed during my work at [SCIAN-Lab](http://www.scian.cl/) and the [BNI](https://www.bni.cl/) at the Universidad de Chile, this simulator supported research in developmental biology, helping understand the physical mechanisms behind collective cell migration in vertebrate embryos.

[View on GitHub](https://github.com/fsantibanezleal/SCIAN_LEO_CPM)
