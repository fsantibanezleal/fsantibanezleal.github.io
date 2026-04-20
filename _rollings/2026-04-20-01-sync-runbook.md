---
title: 'The Sync Runbook'
date: 2026-04-20
permalink: /rollings/2026/04/sync-runbook/
tags:
  - Portfolio
  - Management
  - Meta
  - Runbooks
  - CAOS
---

The Sync Runbook
======

Spent the afternoon carving out a new folder in my private management repo: `portfolio/`. Not a product — a flow. Four public surfaces (this website, the online CV, the portfolio site, the LaTeX resumes) plus one upstream brand vault (GTASKS) that every visual consumer quietly depends on. They each have their own voice, their own cadence, their own schema. What they did not have, until today, was a map describing how content moves between them when something changes.

![Portfolio sync flow — five surfaces, two canonical sources](/images/projects/portfolio_sync_flow.svg)

For a long time I treated my portfolio like content. A new project? Paste it into whichever surface I was editing at the moment, remember to update the others later. That "later" was doing a lot of work. The online CV lagged the portfolio site. The research CV trailed both. Something would always be a little bit out of date, and the only person noticing was me.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Five runbooks under one folder:</strong><br/>
sync-portfolio-web · sync-personal-website · sync-online-cv · sync-writing-resume · sync-branding-gtasks<br/>
<span style="color:#5a9ac0;font-size:13px;">Plus surfaces.md, content-model.md, cadence.md — the vocabulary, the schema, and the beat.</span>
</div>

The shift in framing was from "content management" to "data pipeline." Portfolio site is the canonical source for product content; writing-resume is canonical for CV text; GTASKS is canonical for visual identity. Everything else is a mirror. Each mirror has its own runbook that explains exactly which file, which field, which convention. No auto-sync — I want to keep each surface's voice, and flattening them into one template would lose what makes them useful. Manual, but documented. That's the difference.

The code at my day job has the same shape: canonical tables, derived marts, explicit ownership, drift checks. It felt strange not to have the same discipline for the website I had been running for ten years. Now I do. The runbooks are in [CAOS_MANAGE#17](https://github.com/fsantibanezleal/CAOS_MANAGE/pull/17), along with a cadence doc that says when to sync what.
