---
title: 'Four surfaces, one story — running a personal portfolio like a data pipeline'
date: 2026-04-20
permalink: /posts/2026/04/four-surfaces-one-story/
tags:
  - portfolio
  - management
  - infrastructure
  - runbooks
  - meta
---

Four surfaces, one story
======

For a long time my portfolio was a website I edited when I remembered. This week it became a data pipeline.

This post is about the shift — what changed, why it mattered, and what the finished architecture looks like. The honest version is that I should have done this years ago. The useful version is that the reframing only became possible once I had lived the same reframing in my day job: from writing models to owning their business outcomes, and then to accounting for them quarter after quarter. The same mental model that turns a research script into a production system also turns a personal website into a system. It just took me a while to notice I had not applied it to myself.

## The fragmentation problem

A professional identity online is never one artifact. Mine turned out to be four plus one upstream asset vault.

![Portfolio sync flow — five surfaces, two canonical sources](/images/projects/portfolio_sync_flow.svg)

The **portfolio site** (`FASL_WEB_Portfolio`) is where every project lives in its richest form. Astro, Tailwind, bilingual by construction — the Zod schema refuses to build if any field is missing its English or Spanish twin. KPIs, technical metrics, business context, strategic value, stack, diagrams, screenshots. Twenty-two projects, five tabs each.

The **personal website** (this one, `fsantibanezleal.github.io`) is the first-impression surface. Bio, publications, talks, rollings, posts, a curated subset of the portfolio. Jekyll, English only, academic theme. What you are reading now lives here.

The **online CV** (`online-cv`) is the shareable single-page CV. YAML-driven, Orbit theme, twenty-two project entries compressed to title + link + tagline each. The recruiter link, the LinkedIn bio link, the email signature link.

The **writing-resume** (`FASL_Writing_Resume`) is LaTeX. Four variants — Industry Spanish, Industry English, Research Spanish, Research English — built with `xelatex` through a Makefile, the PDFs committed alongside the sources so anyone cloning gets both without needing a full LaTeX stack.

The upstream vault is **FASL_GTASKS**: logos at three versions (v3 is canonical), favicons at every size a browser might ask for, OG images, a canonical palette, templates for email signatures and slide decks. Every consumer above holds a copy — not a symlink, not a submodule — so deploys stay self-contained.

Four surfaces, five if you count GTASKS. Each with its own repository, its own stack, its own voice.

## Canonical sources and mirrors

The temptation when you have five repos is to think of them as peers. That leads to chaos. The portfolio site's Mine Pile Visualizer entry is worded one way, the online CV's is worded another, the research CV's is worded a third, the personal website's portfolio card is worded a fourth. All four are "correct." None of them is authoritative. Two weeks later you do not remember which one you updated last.

The fix is to pick canonicals. The portfolio site is canonical for product content — it has the richest schema, it enforces bilingual, it is the one place where the challenge paragraph and the KPI table live in full. The writing-resume is canonical for CV text — experience bullets, education entries, honors. GTASKS is canonical for visual identity. Everything else is a mirror.

Once the canonicals are named, the direction of flow becomes obvious.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Direction of flow:</strong><br/>
Product content: portfolio site → personal website card + online CV entry + research CV cventry<br/>
CV text: writing-resume → online CV + personal website CV summary<br/>
Visual identity: GTASKS → every visual consumer (copy, not link)<br/>
<span style="color:#5a9ac0;font-size:13px;">No circular edits. The canonical wins every tie. If the mirror disagrees, the mirror is stale.</span>
</div>

## The runbook layer

Auto-sync was the obvious next step, and I deliberately did not take it.

Each surface has its own voice. The portfolio site is narrative — challenge, approach, strategic value. The personal website portfolio card is reflective — what the product meant, how it evolved. The online CV is terse — title, link, one-line tagline. The research CV is compressed — one bullet that has to earn its two lines by carrying the single most specific technical claim that makes a reader pause.

A template would flatten them. The compression from portfolio excerpt to CV bullet is not a formatting transformation — it is an editorial call about which technical claim survives. You cannot automate that. You can document it.

So the `portfolio/` folder in my management repo holds five runbooks, one per target surface (plus one for branding). Each runbook explains the exact file, the exact field, the exact convention for adding or updating content in that specific surface. When I add a new project, I follow them in sequence: portfolio site first (canonical), then three mirrors. Two hours of work. Four separate pull requests across four separate repositories, because they are separate git histories and batching them would hide what changed where.

The runbooks are manual by design but surface-by-surface explicit. Future me — or anyone coming in fresh — follows them step by step and nothing is left to memory.

## The drift audit

The point of naming canonicals is to make drift detectable. The point of writing runbooks is to make drift correctable on a schedule.

The first audit, run as soon as the folder existed, found three projects present in the portfolio site and personal website but missing from either the online CV, the research CV, or both. This is exactly the kind of drift that accumulates silently when there is no defined flow.

![Drift matrix — three projects before the sync](/images/projects/portfolio_drift_matrix.svg)

Mine Pile Visualizer and FeelIT 2.0 — both shipped in the last two months — had landed everywhere except the LaTeX research CV. The PhD thesis itself had slipped out of the online CV at some point and was never copied into the LaTeX research variants, even though it was sitting right there in the portfolio site and on the personal website's `_portfolio/` folder. Three projects, five missing entries total.

Closing the drift took an afternoon. Six new `\cventry` blocks in the LaTeX Research variants (three each in EN and ES), both PDFs rebuilt at the same six-page length without overflow. One YAML entry added to the online CV, positioned next to its algorithmic companion so the narrative flowed. Two pull requests, two merges, and the matrix went green.

The interesting part was not the work. It was that the audit surfaced the gaps in minutes. Before this week, I would have noticed the LaTeX CV was out of date the next time I sent it to a recruiter — weeks or months later, and probably in a rush. Having a defined flow means the fix belongs to a regular cadence instead of a crisis.

## The shift in framing

Ten years ago the same work would have looked different. I would have treated each surface as a separate task, edited them directly without a plan, and trusted memory to keep track. The Windows Forms / OpenGL version of my portfolio management, if you will. It worked. Kind of. The surfaces drifted, the branding was stale in two of them, and the research CV was a year behind.

Then a decade of building production systems happened. Canonical tables. Derived marts. Explicit ownership. Drift checks in CI. The habit of asking "where does this come from, and what depends on it?" before editing anything. That habit is obvious in a data team. It is less obvious when the "data" is your own career narrative scattered across five repositories you own alone.

The runbooks are not the artifact that matters. The artifact is the reframing: my portfolio is five repositories, not one website, and the connections between them are a pipeline that needs the same discipline as any other pipeline I would design professionally. Canonicals, mirrors, runbooks, drift audits, cadence. The only difference from a production data stack is that I am both the engineer and the user, and the audience is whoever reads the link.

![Mining optimization — the business-impact lens applied to technical work](/images/projects/mining_optimization.svg)

## What comes next

The current runbooks cover adding and updating content. Retirement is covered too — archive in place, never delete the slug, because the URL is permanent history.

What is not yet covered is the surface that does not exist yet. LinkedIn, for example, is a manual paste of a PDF from the writing-resume plus a summary written fresh. That is a surface without a runbook. Eventually it will get one. The same goes for the occasional outbound PDF sent to a specific recruiter with tailored project selection — today that is a judgment call, tomorrow maybe a Flow G in the writing-resume runbook.

For now the five that exist are synchronized, the runbooks are committed, and the cadence is defined. The next drift audit is scheduled for the next heavy cycle. If the matrix is green, good. If not, the flow is obvious: pick the stalest surface, follow the runbook, merge the PR, move on.

The whole thing, including the runbook folder, is in [CAOS_MANAGE#17](https://github.com/fsantibanezleal/CAOS_MANAGE/pull/17). The two content-sync pull requests are [FASL_Writing_Resume#37](https://github.com/fsantibanezleal/FASL_Writing_Resume/pull/37) and [online-cv#24](https://github.com/fsantibanezleal/online-cv/pull/24). The two rollings from today are the short version of this post: [The Sync Runbook](/rollings/2026/04/sync-runbook/) and [Two Lines](/rollings/2026/04/two-lines/).
