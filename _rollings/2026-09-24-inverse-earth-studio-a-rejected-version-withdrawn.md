---
title: 'Inverse Earth Studio: several physics on the same synthetic earths, after a version I rejected'
date: 2026-09-24
permalink: /rollings/2026/09/inverse-earth-studio-a-rejected-version-withdrawn/
tags:
  - geophysics
  - inversion
  - scientific-ml
  - honesty
---

Inverse Earth Studio: several physics on the same synthetic earths, after a version I rejected
======

![Inverse Earth Studio, twenty synthetic earths through several physics, baked on a GPU and replayed with a scrubber and a 3D scene](/images/projects/geophysics_pipeline.svg)

The 0.03.000 correction of Inverse Earth Studio is deployed on both hosts today. The first version of this geophysics workbench had a bespoke look, a course's material it had no permission to redistribute, and a whole-project complete claim; I rejected it. Version 2 replaced it on original synthetic earths and the shared shell, the complete claim was retracted, and today's correction removed the custom palette, fonts and slogan headings, rewrote the scientific explanations in English and Spanish, and regenerated every case on refined grids.

What it does: twenty distinct geological constructors, each computed under six conditions, give 120 artifacts and 324 method results, baked locally on an RTX 4070 and never in CI. Gravity with SimPEG integral kernels; layered magnetotellurics with a live browser solve; acoustic full-waveform inversion with an executed Deepwave CUDA adjoint derivative; learned inverses, a CNN and an autoencoder on 800, 160 and 160 independent realizations; and joint cross-gradient inversion coupling two physics on one earth. The App takes one case at a time, with an inversion scrubber over the computed states and a 3D scene of the known and the recovered geology.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The numerics answer to codes I do not own.</strong><br/>
Independent Choclo and SimPEG prism checks, complex MT parity, checkpoint reload and split uniqueness among fifteen numerical tests; both public hosts match the local build byte for byte (120 experiment hashes, six route documents, three model files).<br/>
<span style="color:#5a9ac0;font-size:13px;">Not claimed: field validation, posterior uncertainty, algorithmic novelty, a 3D volume from the inverse CNN (it estimates column density). Devito, MTpy/MTH5 and PGI were surveyed and are not implemented; EDI, PGI and ensemble uncertainty stay open in a public issue. My acceptance of the new design is not inferred, and the plan says building.</span>
</div>

[Live](https://geophysics.ml.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_Geophysics)
