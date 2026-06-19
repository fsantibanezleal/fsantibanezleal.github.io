---
title: 'A Quiet Week of Dual-Target Deploys'
date: 2026-06-18
permalink: /rollings/2026/06/azure-deploy-wave/
tags:
  - DevOps
  - Azure
  - Containers
  - Security
---

A Quiet Week of Dual-Target Deploys
======

Not every productive week produces a demo you can fly through. This one was infrastructure: I took a batch of my private apps and gave them a second home on Azure Container Apps, alongside the VPS they already run on — dual-target, same image, two destinations. The interesting part was doing it without a single long-lived secret anywhere in the pipeline.

The pattern I converged on, repeated across every service:

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:'Courier New',monospace;color:#e0e0e0;font-size:13.5px;line-height:1.9;">
GitHub Actions ──(OIDC federated identity)──▶ Azure&nbsp;&nbsp;<span style="color:#5a9ac0;"># no stored AZURE_CREDENTIALS</span><br/>
&nbsp;&nbsp;build image ─▶ push ACR ─▶ deploy Container App (Bicep)<br/>
Container App ──(user-assigned managed identity + AcrPull)──▶ ACR&nbsp;&nbsp;<span style="color:#5a9ac0;"># no admin creds</span><br/>
0.75 vCPU / 1.5 GiB · scale-to-zero · /healthz probe
</div>

Two things earn their keep here. **OIDC federated identity** means the CI job exchanges a short-lived GitHub token for an Azure one at run time — there is no client secret to leak or rotate. And the running container pulls its own image from the registry via a **user-assigned managed identity** with just the `AcrPull` role, so there are no registry admin credentials in the loop either. Bicep describes the whole thing declaratively; scale-to-zero keeps idle cost near nothing.

It was not all clean. I hit an RBAC propagation race (the deploy runs before the role assignment is visible, so it needs a retry), an ARM read-lag when fetching the live URL, and — embarrassingly — a version-bump script that opened a file for writing *before* reading it and truncated a `pyproject.toml`. Caught and restored, then noted so I never do it again. Secrets, of course, never live in these repos: they come from my private vault and are injected at deploy time as container-app secrets.
