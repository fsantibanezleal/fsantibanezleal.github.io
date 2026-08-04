---
title: 'A stockpile is inventory nobody has opened'
date: 2026-08-04
published: true
permalink: /posts/2026/08/a-stockpile-is-inventory-nobody-has-opened/
tags:
  - mining
  - stockpiles
  - grade-control
  - simulation
---

A stockpile is inventory nobody has opened
======

A run-of-mine stockpile is inventory on the balance sheet, and its value rests on an estimated grade and recovery for material nobody has opened. That is an uncomfortable position, and the accounts show it. Newmont reported around 3.9 billion dollars in stockpiles and leach pads at the end of 2015, and roughly 2.2 billion in write-downs over the following three years, with lower grade and lower recovery named among the drivers. At Coeur, the auditor raised stockpile grade and tonnage estimation as a Critical Audit Matter and asked for the daily tonnage, the laboratory procedures and the ounces roll-forward. At Katanga, a restatement covered concentrate booked as produced that was not physically in the storage locations. The stockpile is where grade-control error and blending benefit both hide, and both eventually surface as money.

Characterizing what is in the pile rests on two streams a site already records. From the truck and the shovel: which unit, which bench and phase each load came from, GPS position and movements, and where it tipped against the plan. From quality estimation: the source block grade, from the block model, from dispatch, and from the lab. With those two streams you can begin to defend what is going to the plant, how much it varies between cuts, and how far traceability still reaches once the dozer has moved the material and the built sequence has drifted from the planned one.

The sampling density to do this already exists. A per-truck record is one sample per 100 to 400 tonnes, where conventional practice is closer to one per 175,000. What has been missing is not data, it is a build model honest enough to trust the answer, because a stockpile does not hold material the way a spreadsheet does. It is built by trucks that cannot stand on fresh material, so tips follow a dump plan and a tip the pile has grown past is refused rather than teleported into place. Material segregates down the face it runs out on, so the toe ends up coarser than the crest. A reclaim campaign then cuts through the layers, and how well it blends depends entirely on how the pile was built.

I put together a workspace to look at exactly this. [StockTwin](https://stocktwin.fasl-work.com) fills a pile truck by truck and draws it down in campaigns, and it reports the three things that decide whether the exercise was worth anything: how much the pile homogenised the feed, measured against the bound a set of independent layers would give rather than against nothing; where each reclaimed tonne actually came from, as a ledger that has to sum to one; and how much size segregation biased the cut, solved down a real face rather than a nominal slope. It is honest about its own scope: the cases are synthetic and public, there is no plant measurement in it, and it does not solve blending or emit a setpoint. It is the open research reflection of a question I have spent years on in industry, not a substitute for the operation's own reconciliation.

The point of building it in the open is the same one the write-downs make in the other direction. A stockpile that is only a number on the balance sheet is a number waiting to be corrected. A stockpile you can rebuild, cut open and account for is one you can defend before the assay does it for you.
