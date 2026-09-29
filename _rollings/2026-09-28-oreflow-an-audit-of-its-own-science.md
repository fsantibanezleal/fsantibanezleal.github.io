---
title: 'OreFlow 0.06.000: what an audit of its own science found'
date: 2026-09-28
permalink: /rollings/2026/09/oreflow-an-audit-of-its-own-science/
tags:
  - oreflow
  - mineral-processing
  - comminution
  - corrections
---

OreFlow 0.06.000: what an audit of its own science found
======

![OreFlow, an authored case through a closed-circuit engine, a live workbench and baked method records](/images/projects/oreflow_pipeline.svg)

The day after OreFlow 0.05.000 went out, an audit of the engine and the cases found two things that the tests had not. Version 0.06.000, released on 28 September, is the answer to both.

The first was in the grinding energy. The engine gives each mineral a grindability, and in 0.05.000 those grindabilities multiplied the energy-specific breakage selection directly. An ore whose bulk mineral was declared soft therefore broke faster than its own Bond work index allowed: the serpentine of the nickel case, and the clays of the oxide copper, mixed and phosphate cases. Their grinding energy was understated by up to 1.9 times, and the nickel case ground at 1.62 times Bond's efficiency, which is not a thing a ball mill does.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The fix: the work index alone sets the ore's hardness.</strong><br/>
valuable mineral: (S<sup>E</sup><sub>i</sub> / &#7713;) (L<sub>i</sub> g<sub>V</sub> + (1 &minus; L<sub>i</sub>) &#7713;) &nbsp;&nbsp; gangue: (S<sup>E</sup><sub>i</sub> / &#7713;) g<sub>G</sub> &nbsp;&nbsp; with &nbsp; &#7713; = 1 / &Sigma;<sub>k</sub> x<sub>k</sub> / g<sub>k</sub><br/>
<span style="color:#5a9ac0;font-size:13px;">S<sup>E</sup><sub>i</sub> is the energy-specific selection of size class i, L<sub>i</sub> its liberated fraction, g the relative grindabilities and x<sub>k</sub> the mass fraction of mineral k. A mineral's energy for a given reduction goes as 1/g<sub>k</sub> and the work index measures the mass-weighted sum, so the ore breaks like one mineral of grindability &#7713;; dividing by it lets the work index alone set the ore's hardness, while the grindabilities only share the breakage among the minerals. Liberated grains break at their own grindability, composites at the ore's rate. Every nominal case now grinds at 0.83 to 0.91 of Bond's efficiency, and a test holds that ratio.</span>
</div>

The second was in the cases. The audit named three whose results sat outside the ranges their sources give. Checking every case against its own source found seven, and the hard porphyry missed its own 24 percent copper specification. Each was re-authored inside its documented mechanism: the zinc concentrate went from 47.3 to 52.9 percent zinc, inside the 50 to 60 percent of the US EPA's sector profile; the nickel concentrate from 16.0 to 19.8 percent nickel, against about 20 in Mt Keith-type ore; the oxide copper from 29.8 to 20.8 percent copper, inside the 15 to 21 of its source; and the four other copper porphyries from about 24 to about 26 percent, inside the practice band that runs from 25 percent copper to chalcopyrite's stoichiometric 34.6. The plausibility ranges had themselves been written wider than their sources, which is how off-spec cases passed the gate; every range now comes from one table and names its source, or says it is authored.

The manuscript draft still described 0.05.000. It now quotes the new records, and a test parses its tables and formats every quoted number from the records; run against the previous draft, that test fails six of its seven checks. 364 Python tests, 174 frontend tests and a 712-check browser gate, with the bake re-run in a sandbox and compared file by file before it was adopted. The cases remain authored scenarios inside sourced ranges, not calibrated plants.

[Live](https://oreflow.ml.fasl-work.com) · [source](https://github.com/fsantibanezleal/CAOS_OreFlow) · [what changed](https://github.com/fsantibanezleal/CAOS_OreFlow/blob/main/CHANGELOG.md)
