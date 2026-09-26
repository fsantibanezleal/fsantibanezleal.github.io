---
title: 'A scaffold that never ran'
date: 2026-09-26
permalink: /rollings/2026/09/a-scaffold-that-never-ran/
tags:
  - engineering
  - honesty
  - testing
  - bancoestable
---

A scaffold that never ran
======

![A scaffold whose stages imported a directory the instantiation had dropped, with a tracked sentinel that silenced its own guard](/images/projects/bancoestable_scaffold.svg)

While promoting the fleet I found a repository outside the workspace: BancoEstable, a slope-stability product instantiated from my product template on 2026-07-12, given its science on 2026-07-17 (limit-equilibrium factors of safety, the Hoek-Brown 2002 criterion, a Monte-Carlo reliability layer), and then parked on one disk with no remote. I would have recorded it as "scaffold with science and tests", which is what the tree says. So before writing the row I made it a venv and ran it.

`pytest` stopped at collection: two test modules could not import `engine.model.sir`. The template's stages and its live entry import an example model, and the instantiation had dropped that directory while leaving every import that pointed at it. The three science modules and their tests were fine, because they never touched the pipeline; the pipeline itself had not been able to start since the day it was created. And the template residue guard, whose job is to fail an instantiated product that still carries example cases, had been printing "this is the template, check skipped" and exiting zero all along, because the sentinel file that marks the template was still tracked.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">Nothing surfaced for two months because nothing ever ran it.</strong><br/>
No remote, so no CI. No CI, so no gate. A guard that skipped itself. The state I was about to record was a claim read from the tree, not a state measured by running anything.<br/>
<span style="color:#5a9ac0;font-size:13px;">Same family as the checkout that was twenty-eight commits behind the shipped artifact: the record must be re-read from the running thing, not from what the files look like.</span>
</div>

Fixed the same day, without pretending the product exists: the example model restored from the template so the pipeline bakes and every test collects, the sentinel removed so the guard now reports the example cases on every run, no declared package (the offline code is invoked by path, as my conventions require), a version file, the content sweep, CI in the cheap trunk-only shape, published as a private repository and registered as what it is: a parked scaffold whose build still waits for research dossiers, a plan and a validation.

The rule I am keeping is small and cheap: before recording any repository's state, create its environment and run its tests, its lint and its entry point, and write down what they printed. A scaffold that has never run is not a scaffold; it is a directory.

[BancoEstable is private for now; the product page lives in the management record.]
