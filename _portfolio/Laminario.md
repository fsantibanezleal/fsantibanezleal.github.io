---
title: "Laminario, an Open Collection of Microscope Slides in the Spirit of iNaturalist"
date: 2026-09-25
excerpt: "A public collection where every case is a real microscope slide shown as the glass object it is, its format, the specimen under the coverslip, a label with a scannable QR, and behind the glass the micro imagery in deep zoom over IIIF, from one photomicrograph to a whole-slide scan with focal planes and polarised pairs. Three realms, 18 collections, 129 sub-collections; visitors browse without an account, invited contributors add slides, the community agrees on identifications. Version 0.01.000: the data model and both contracts; nothing deployed yet.<br/><img src='/images/projects/laminario_pipeline.svg'>"
collection: portfolio
tags: [microscopy, slides, natural-history, iiif, deep-zoom, openslide, community, education]
---

Microscope slides are among the most numerous objects in natural-history and teaching collections; the Natural History Museum in London alone holds about 2.5 million. A growing share is digitised and openly licensed, but it is published as records in portals or files in deposits: nobody can browse slides as slides, across plants, animals, microbes, rocks, minerals and crystals, or add their own. **Laminario** is built to do both.

![Laminario, a slide case enters through an ingestion contract into the catalog and a durable job queue; the imaging engine writes pyramidal planes served over IIIF to a deep-zoom stage](/images/projects/laminario_pipeline.svg)

## A slide as an object, standards on the way out

Every case is shown as the glass object it is: true format and size, the macro image under the coverslip, a printed label with a QR that opens the slide's page; behind the glass, the micro assets, single images, deep-zoom pyramids, focal planes and polarisation states. The collection tree has three realms (life, earth, matter), 18 collections and 129 sub-collections with 185 designed icons, anchored on GBIF, the IMA mineral list, the crystal systems and the materials. Imagery is written by libvips with OpenSlide as one pyramidal BigTIFF per plane and served over the IIIF Image API 3 at level 2, with a IIIF Presentation 3 manifest per slide, so any IIIF viewer can open it; multi-gigabyte scanner files (NDPI, SVS, MRXS, DICOM) arrive through resumable tus uploads with quarantine, sniffing, checksum and quotas. Source, author and licence are recorded per asset, and a base collection of at least 300 openly licensed slides enters through the same pipeline as a contributor's upload.

## Built in the mandatory order, and described as it is

Seven research dossiers, an architecture decision (ADR-0077), a design document with a named verification gate per requirement, the plan validated on 2026-09-24, then the units. Version 0.01.000 (2026-09-25) is the repository base and the data model: the slide-case ingestion contract, the catalog and IIIF artifact contract, the SQLite schema with migrations, the JSON Schemas mirrored as TypeScript types, and an API that validates, stores and serves a slide case. The 100 GB data volume is mounted on the ML VPS. The imaging engine, the delivery, the worker, the uploads, the accounts, the collection tree, the base collection, the design system and the interface follow; nothing is deployed, the lifecycle is planned, and the product carries its own design system rather than the shared shell, by Felipe's instruction.

[GitHub repository](https://github.com/fsantibanezleal/CAOS_Laminario)
