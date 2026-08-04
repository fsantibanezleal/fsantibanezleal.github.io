---
title: "Mineral Tracking Models: five years of Codelco experience"
collection: talks
type: "Conference presentation"
permalink: /talks/2026-08-05-talk-mineria-digital-mineral-tracking
venue: "Minería Digital 2026"
date: 2026-08-05
location: "Hotel Sheraton, Santiago, Chile"
---

![Minería Digital 2026 — Modelos de Mineral Tracking: cinco años de experiencia en Codelco](/images/mineria-digital-2026.png)

Presented at **Minería Digital 2026** (Hotel Sheraton, Santiago, Chile, 5-7 August 2026), co-presented with **Magdalena Ribbeck**, Directora of Codelco MinCo-Hidro. I gave this talk in my role as Ind&Func Decision Science Associate Manager at Accenture (Industry X).

The talk draws on five years of mineral tracking work across Codelco's divisions and the challenges each of them raised. Tracking a tonne of ore from the pit to the plant sounds like bookkeeping and is not: it forces a decision about what the "truth" of a parcel of material even is, and that truth has to be assembled from sources that disagree and arrive at different times. The block model, the dispatch system and the laboratory each describe the same material differently, at different resolutions, with different latency, and reconciling them requires explicit choices about time windows and mass aggregation before any number can be trusted.

The harder part is that the material does not stay where the model says it is. Between the shovel and the mill it is diluted, advected, segregated and remobilised, and a stockpile in particular mixes and re-orders material in ways a static inventory cannot represent. Tracking that credibly needs a realistic simulation of the physical processes involved, dilution, advection, ratholing and size segregation on stockpiles, rather than a ledger that assumes material teleports intact.

The throughline of the talk is the case for a general mineral tracking engine: a common substrate that unifies these sources and simulations and powers the mineral tracking capability across the corporation, instead of a separate ad-hoc solution rebuilt per division.

The open, synthetic counterpart to this line of work is [StockTwin](https://stocktwin.fasl-work.com), a public research workbench that builds a run-of-mine stockpile truck by truck and measures how it homogenises the feed, where each reclaimed tonne came from, and how size segregation biases the cut, entirely on synthetic and public data. No Codelco data is used or shown; StockTwin is the research reflection of the same questions.
