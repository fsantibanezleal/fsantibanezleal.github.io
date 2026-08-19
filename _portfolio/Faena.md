---
title: "Faena — Mining-Analytics Hub"
date: 2026-06-28
excerpt: "A single open launcher that catalogues a growing set of independent, in-browser mining-analytics tools across the value chain. Each tool is its own documented product on a named real dataset or a validated synthetic. Three live today, seven in active development, and more on a visible roadmap.<br/><img src='/images/projects/faena_hub.svg'>"
collection: portfolio
tags: [mining, analytics, hub, launcher, astro]
---

The open **hub** for a growing family of independent, in-browser mining-analytics tools. Faena is not an app itself — it is a fast static index that catalogues each tool across the value chain (exploration → drill & blast → load/haul → comminution → processing → tailings → asset health → economics) and links out to its own repo and subdomain. It never bundles or proxies the apps. Live at [faena.fasl-work.com](https://faena.fasl-work.com).

![Faena — value-chain swimlanes with the live tiles lit](/images/projects/faena_hub.svg)

## Honest by construction

Every tile carries a lifecycle status, so the catalogue tells the truth about maturity: **4 live today** (DispatchLab, ChancaDEM, ChargeCascade, RotorVitals), **10 in active development**, and **28 more mapped on the roadmap** — tiles advance *planned → building → live* as each one actually ships. "Live" means brought to the quality bar, not merely deployed. There is no "39 mining apps" claim — a small set that works today, and a visible plan for the rest.

## How it is organized

Two axes: **value-chain stage** as swimlanes and **solution-type** (computer vision, 3D physics, optimization, condition monitoring, geospatial, forecasting) as a colour facet. The whole site is **data-driven** from a registry — adding a tool is a data edit — and built with **Astro** for a static, near-zero-JS surface, bilingual EN/ES with a light/dark theme.

[Live hub](https://faena.fasl-work.com) · [GitHub repository](https://github.com/fsantibanezleal/CAOS_FAENA)
