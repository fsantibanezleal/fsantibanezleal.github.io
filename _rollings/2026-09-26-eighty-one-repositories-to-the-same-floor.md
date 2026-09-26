---
title: 'Eighty-one repositories to the same floor'
date: 2026-09-26
permalink: /rollings/2026/09/eighty-one-repositories-to-the-same-floor/
tags:
  - engineering
  - release-engineering
  - honesty
  - fleet
---

Eighty-one repositories to the same floor
======

![The promotion chain applied to eighty-one repositories, with the counts of the pass](/images/projects/fleet_promotion_chain.svg)

Over the last days I took every CAOS repository I own, eighty-one of them once a parked scaffold turned up outside the workspace, to one floor: the checkout on `develop`, `develop` equal to `main`, nothing on origin but the two trunks and the work-in-progress branches that are documented as such, a content guard in CI, every version source saying the same number as the tag, and the live site serving that number. One repository at a time, in the same order every time: read the state before deciding anything, sweep the content, add the guard, align the versions, promote through `task`, `develop` and `main` by API with CI required to reach `completed` and not merely to exist, tag the release merge, check the live surface, then write the row.

The counts are not the point but they are real: more than two hundred pull requests opened and merged through the REST API, forty-two releases tagged (patch releases carrying the sweep, plus tags for releases that had shipped untagged), about 1,190 branches pruned, every one of them merged or patch-equivalent and every unique branch compared as a tree before a decision, and eight packages published to PyPI through trusted publishing: copela, minehaulsim, oreblocks, pygeotypes, preqts, and today blastfrag, geocond and fracpta.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The record found what the work had not.</strong><br/>
Writing the fleet ledger from what each pass intended, then re-deriving every plan's version from its repository, exposed a row that claimed a VERSION file and a tag that did not exist, a tag placed on sources that still read the previous version, an engine repository the pass had skipped with CI red since a lint release two weeks earlier, and three products whose version lived only in a manifest.<br/>
<span style="color:#5a9ac0;font-size:13px;">All finished the same day. The rule that survived: a claim in a record is re-read from the repository before it is written, and a working ledger is never the record.</span>
</div>

I made eight errors of my own along the way and each has its correction and the gate that catches it next time. A pipeline of the form `pytest | tail -1` returns the last command's status, so a product shipped a failing test and a tag whose version had not moved; every later chain gates on its own exit code. A version bump done by substitution across the tree rewrote the `app_version` inside thirty-four committed artifacts; the bump tool now moves version sources only. A colon inside a YAML step name made a workflow unparseable, silently. A poll that treated `pending` as terminal merged to `main` before CI had run. The rest are in the record, with the same shape: the mistake, the cost, the correction, the check.

Two things I will keep. Read-only state first, and decide per branch with the tree, not with the branch name. And one repository at a time: the two times I let three chains overlap, the quality dropped, and both of the errors above happened in those windows.
