---
title: 'CentralIA: the version-control provider is the backend'
date: 2026-07-21
permalink: /rollings/2026/07/centralia-repos-are-the-backend/
tags:
  - developer-tools
  - project-management
  - honesty
---

CentralIA: the version-control provider is the backend
======

![CentralIA: connect to a provider, read a management repo, render a portfolio with 5-axis status and a hub graph](/images/projects/centralia_pipeline.svg)

Once you run more than a handful of initiatives across many repos, the state of the whole portfolio lives nowhere: scattered across READMEs, plan files, issue trackers and your own head. A static dashboard goes stale the moment a repo moves. [CentralIA](https://centralia.fasl-work.com) fixes that by making the version-control provider itself the backend of the console.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Connect, then it reads the repos live:</strong><br/>
GitHub / GitLab / offline emulator to a management repo via its structure map<br/>
<span style="color:#5a9ac0;font-size:13px;">A filterable portfolio grid, per-initiative 5-axis status (development, design, implementation, deployment, value), live open issues, and a hub growth graph. Never staler than the last commit.</span>
</div>

It is a real tool, not a mockup: the connectors are genuinely implemented and the offline emulator is a self-contained backend with a bundled fake management repo, so it runs with no credentials. The access token lives in the server environment only, never the browser or a database, and a server-side anonymize toggle redacts client info for screen-sharing. Single-user auth; the public instance is private, the offline emulator is how to see it. [Live](https://centralia.fasl-work.com) · [source](https://github.com/fsantibanezleal/CentralIA).
