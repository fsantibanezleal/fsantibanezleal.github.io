---
title: "Inverse Earth Studio, a Geophysical Inversion Workbench on Original Synthetic Earths"
date: 2026-09-24
excerpt: "3D potential fields, layered magnetotellurics, acoustic full-waveform inversion, learned inverses and joint cross-gradient inversion on twenty geological constructors with six computed conditions each: 120 artifacts and 348 method results replayed in the browser with an inversion scrubber and a 3D scene. Numerics checked against Choclo, SimPEG and an executed Deepwave adjoint. Synthetic, not field validation; version 2 replaced a rejected first version.<br/><img src='/images/projects/geophysics_pipeline.svg'>"
collection: portfolio
tags: [geophysics, inversion, gravity, magnetotellurics, fwi, simpeg, deepwave, scientific-ml]
---

Geophysical inversion is taught one method at a time on one example each, and every method hides its non-uniqueness in its own way. **Inverse Earth Studio** holds several physics on the same synthetic earths, runs every method on every case under the same conditions, and lets the reader watch the inversion converge instead of reading that it did.

![Inverse Earth Studio, twenty synthetic earths through several physics, baked on a GPU and replayed with a scrubber and a 3D scene](/images/projects/geophysics_pipeline.svg)

## Several physics, the same earths

Twenty distinct geological constructors under six conditions each produce 120 artifacts and 348 method results, baked locally on an RTX 4070 and never in CI. Gravity with SimPEG integral kernels, checked against independent Choclo and SimPEG prism computations; layered magnetotellurics with complex parity tests and a live browser solve; acoustic full-waveform inversion with an executed Deepwave CUDA adjoint derivative; learned inverses (a CNN and an autoencoder on 800, 160 and 160 independent realizations, the inverse CNN estimating column density rather than a 3D volume); and joint cross-gradient inversion coupling two physics on one earth.

## One case at a time

![Inverse Earth Studio, the App on an offset intrusive stock: known geology in 3D, the survey plane and the inversion replay](/images/projects/geophysics_app_dark.png)

The App selects a case with its hypothesis, an experiment and an inverse method (sparse IRLS among them), scrubs the inversion over its computed states, shows the known and the recovered geology in a 3D scene with survey plane, cut, threshold and rotation, and exports the run. Fifteen numerical and fifteen frontend tests; both public hosts match the local build byte for byte (120 experiment hashes, six route documents, three model files).

## A rejected version, withdrawn

The first version, with a bespoke look and a course's material it had no permission to redistribute, was rejected; the whole-project complete claim was retracted, the 0.03.000 correction gave the visual layer back to the shared shell and rewrote the science in both languages, and every case was regenerated on refined grids. Not claimed: field validation, posterior uncertainty, algorithmic novelty; Devito, MTpy/MTH5 and PGI were surveyed and are not implemented, and EDI, PGI and ensemble uncertainty stay open in a public issue. Apache-2.0 code, CC-BY-4.0 content; the lifecycle is building. On 2026-09-27 a replacement plan and a thirteen-method product design were approved; version 0.04.001 stays online as the legacy release while the product is rebuilt.

[Live](https://geophysics.ml.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_Geophysics)
