---
title: "CentralIA — Initiative-Management Console over a Version-Control Provider"
date: 2026-07-21
excerpt: "A connection-first web console that connects to GitHub, GitLab or an offline emulator, reads a management repo through its structure map, and renders a whole portfolio of repo-mapped initiatives: a filterable grid, per-initiative 5-axis status, live open issues, and a hub growth graph. A real tool, not a mockup; the token lives server-side, with a server-side anonymize toggle for screen-sharing.<br/><img src='/images/projects/centralia_pipeline.svg'>"
collection: portfolio
tags: [developer-tools, project-management, github, gitlab, dashboard, connectors]
---

A **connection-first** web console that turns a version-control provider into the backend of a management dashboard, so the state of a whole portfolio of initiatives is never staler than the last commit.

![CentralIA — connect to a provider, read a management repo, render a portfolio with 5-axis status and a hub growth graph](/images/projects/centralia_pipeline.svg)

## Read the state live from the repos

Connect to a provider (**GitHub, GitLab, or an offline emulator**), point it at a management repo, declare the structure file, and CentralIA renders every repo-mapped initiative: a grid filterable by group, line, hub, lifecycle, deploy class and kind; per-initiative **5-axis status** (development, design, implementation, deployment, value, each 0 to 5); the implementation backlog; **live open issues** pulled from the provider; plans, findings, history; and a hub drill-down with a **growth graph** where nodes are coloured by component type, ringed by lifecycle, and connected by directed consumes edges.

## A real tool, not a mockup

The connectors are genuinely implemented and the offline emulator is a self-contained backend with a bundled fake management repo, so it runs with no credentials. The access token lives in the server environment only, never in the browser or a database, and a server-side **anonymize** toggle redacts client info for screen-sharing. Single-user auth; the public instance is private, the offline emulator is how to see it. [Source on GitHub](https://github.com/fsantibanezleal/CentralIA).
