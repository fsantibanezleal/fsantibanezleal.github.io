---
title: "Atalaya — A Watchtower over Chile's Open Data"
date: 2026-07-01
excerpt: "Atalaya harvests Chile's Data Observatory open catalog, profiles every downloadable table, and mines five kinds of cross-dataset relation — same-source, semantic similarity, spatial overlap, joinability and statistical correlation — into an explorable knowledge graph, with client-side semantic search. Honest about evidence strength, never causal.<br/><img src='/images/projects/atalaya_graph.svg'>"
collection: portfolio
tags: [data-engineering, knowledge-graph, information-retrieval, embeddings, open-data]
---

A **watchtower over Chile's open data**. Atalaya harvests the [Data Observatory](https://catalogo.dataobservatory.net) catalog, profiles every downloadable table, and mines **five kinds of cross-dataset relation** into an explorable knowledge graph — turning a flat list of a thousand-plus datasets into a map of which ones join, overlap, correlate or share a source. Live at [atalaya.fasl-work.com](https://atalaya.fasl-work.com).

![Atalaya — harvest → profile → relate → knowledge graph](/images/projects/atalaya_graph.svg)

## Five relations, mined with care

Over 1,017 real datasets: **same-source**, **semantic similarity** (a MiniLM model exported to ONNX), **spatial overlap**, **joinability** (MinHash containment) and **statistical correlation** (Spearman with a permutation null, Benjamini-Hochberg FDR control and a partial-correlation guard). A novel calibrated **affinity** score fuses the signals against null-distribution percentiles and can be re-weighted live. It ships as a static React SPA with the graph baked in and **semantic search running client-side** — no backend.

## Honest about the graph

The number that matters is not "~14,000 relationships" — most of those are cheap priors. The **hard evidence** is a few hundred joinable pairs and a handful of FDR-controlled correlations, and Atalaya labels that strength rather than hiding it. It never implies causation (some small-n correlations are flagged fragile), and the modern embedding model beats the classical TF-IDF baseline only **modestly** (~+1.4 points). A relation *explorer*, reported at the confidence the data supports.

[Live demo](https://atalaya.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_ATALAYA)
