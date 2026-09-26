---
title: 'Laminario 0.01.000: the data model and both contracts before any interface'
date: 2026-09-25
permalink: /rollings/2026/09/laminario-the-data-model-before-any-interface/
tags:
  - laminario
  - microscopy
  - iiif
  - contracts
---

Laminario 0.01.000: the data model and both contracts before any interface
======

![Laminario, a slide case enters through an ingestion contract into the catalog and a durable job queue; the imaging engine writes pyramidal planes served over IIIF to a deep-zoom stage](/images/projects/laminario_pipeline.svg)

Laminario is an open collection of microscope slides in the spirit of iNaturalist: every case a real slide shown as the glass object it is, with its format, the specimen under the coverslip and a label whose QR opens the slide's page, and behind the glass the micro imagery in deep zoom, from one photomicrograph to a whole-slide scan with focal planes and polarised pairs. Three realms, 18 collections and 129 sub-collections with their own iconography. Visitors browse without an account, invited contributors add slides, and the community agrees on identifications by a two-thirds rule.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">What 0.01.000 is, and what it is not.</strong><br/>
The repository base and the data model: the slide-case ingestion contract (Pydantic), the catalog and IIIF artifact contract, the SQLite schema with migrations, the JSON Schemas mirrored as TypeScript types, and an API that validates a slide case, stores it and serves the catalog record. Contract tests run on malformed input in CI.<br/>
<span style="color:#5a9ac0;font-size:13px;">Not yet: the imaging engine (libvips with OpenSlide, one pyramidal BigTIFF per plane, PPL and XPL pairs, the extended-depth-of-field composite with parity against the EPFL reference), the IIIF delivery, the worker, the uploads, the accounts, the collection tree, the base collection of at least 300 openly licensed slides, the design system and the interface. Nothing is deployed. The 100 GB volume is mounted on the ML box and waits.</span>
</div>

The order is the point. Seven research dossiers came first, then an architecture decision (ADR-0077) and a design document with a named verification gate per requirement, then the plan, validated on 2026-09-24, and only then the first unit. The product will carry its own design system rather than the shared shell, by Felipe's instruction, which is why the interface is the last unit and not the first: the stage viewer, the object renderer with a true-scale mount that prints at 1:1, and the collection browser are designed against contracts that already exist.

[Repository](https://github.com/fsantibanezleal/CAOS_Laminario)
