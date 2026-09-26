---
title: 'A fleet promotion, and the eight ways I got it wrong'
date: 2026-09-26
published: true
permalink: /posts/2026/09/a-fleet-promotion-and-the-eight-ways-i-got-it-wrong/
tags:
  - engineering
  - release-engineering
  - honesty
  - documentation
---

A fleet promotion, and the eight ways I got it wrong
======

I keep about eighty repositories under one name. Products with a web surface, research labs that ship an app, the engines those products consume, and a few wikis. They accumulated over a year of building, each promoted when it was done and then left, and by September the fleet had drifted in the ways a fleet drifts: a checkout on a task branch here, a `develop` that had never been merged there, hundreds of branches whose content was already on `main`, a content rule enforced in the newest repositories and absent from the older ones, and versions that agreed in the manifest but not in the footer or the tag.

So I set one floor and took every repository to it, one at a time. The floor is not ambitious. The checkout on `develop`. `develop` equal to `main`. Nothing on origin but the two trunks and the work-in-progress branches that are documented as such. A guard in CI for the content rule I care about (no em-dash, no emoji; both read as a machine wrote the text). Every version source saying the same number as the tag, and the live site serving that number. And a record of all of it, re-read from the repository rather than written from what I meant to do.

![The promotion chain applied to eighty-one repositories, with the counts of the pass](/images/projects/fleet_promotion_chain.svg)

## The chain

The order mattered more than any single step. Read the state first, read-only, before deciding anything: which branch is checked out, what each branch holds against `main` as a tree rather than as a name, whether a stash is sitting there, whether a worktree belongs to another session. Then sweep the content and add the guard. Then align the version sources. Then promote, through `task`, `develop` and `main`, by the REST API rather than by hand, with the continuous integration run required to reach `completed` and to conclude `success` before the next merge. Then tag the release merge, check the live surface, and only then write the row.

Eighty-one repositories in scope once a parked scaffold turned up outside the workspace; eighty promoted clean and one excluded because another session owned it that day. More than two hundred pull requests, forty-two releases tagged, about 1,190 branches pruned (merged or patch-equivalent only, every unique branch compared as a tree before any decision), eight packages published to PyPI through trusted publishing. The counts are real, and they are also the least interesting part.

## The eight errors

![Eight errors of the pass, what each cost, and the gate that now catches it](/images/projects/fleet_errors_gates.svg)

The interesting part is what I got wrong, because every one of these is a shape I will meet again.

**A pipeline that could not stop.** `pytest | tail -1` returns the status of `tail`. So did `python edit.py | grep -v noise`, and `guard.py | tail -1 || exit 1`. One product shipped a failing test and a tag whose version file had not moved; another merged a failing guard. Each got a correcting release, and every chain I run now gates each step on its own exit code, with `set -o pipefail` at the top.

**A version bump by substitution.** Replacing the old version string across the whole tree is fast, and it rewrote the `app_version` field inside thirty-four committed artifacts of a product whose artifacts are the evidence. That is forging provenance without meaning to. They were regenerated under the pinned engine, and the bump tool now moves version sources only: the version file, the manifests, the constant in the footer.

![Fragmenta's engine pin moves from a git tag to a PyPI release and the artifacts stay identical](/images/projects/blastfrag_pin.svg)

The same product gave me the cleanest test of the week. Its engine, blastfrag, had been pinned by git tag because the PyPI project did not exist; I registered it, the release published through a trusted publisher, and the pin changed to the published version. A pin is a claim about numbers, so it was treated as one: re-bake all sixteen cases, diff the committed artifacts. Every published number is identical, and I get to say "identical" because the diff said so, not because nothing should have changed.

**A colon in a YAML step name.** "Guards: content and budget" is a mapping, not a string, and the workflow did not parse. GitHub shows such a workflow under its file path with zero jobs and no error anywhere you would look. Every workflow now goes through `yaml.safe_load` before it is committed, and step names in YAML take the comma form only.

**Footer constants the bump missed.** A version typed into a component is not a version source anybody moves. One site sat at 0.08.000 in its footer for fourteen releases. The bump now sets that constant to the target whatever it read before, and the served bundle is checked after the deploy, not the source.

**An emoji tidy regex.** A strip-and-collapse in one pass ate the newline after seventeen docstrings and joined each to the statement that followed. Restored from `HEAD` and redone on the same line only. The lesson is older than the regex: read the diff before the commit, all of it.

**A pull request head deleted before the merge.** The branch went first and the pull request was stranded with its commits only in the reflog. Recovered; the API now deletes the head only after the merge reports `merged: true`.

**A tag without a release**, created and deleted in the same minute, and **rows written from intent**: a ledger row claiming a version file and a tag that did not exist, two repositories whose rows were never written, an engine repository the pass had skipped entirely.

And a ninth, from the engine extraction the same week: a poll that treated `pending` as a terminal state merged to `main` before the continuous integration had run. It was green afterwards, which is luck, not a process.

## What the record found

![A scaffold whose stages imported a directory the instantiation had dropped, with a tracked sentinel that silenced its own guard](/images/projects/bancoestable_scaffold.svg)

While writing the record I found a repository outside the workspace: a slope-stability product instantiated from my product template in July, given its science a few days later, then parked on one disk with no remote. I would have recorded it as "scaffold with science and tests", which is what the tree says. Before writing the row I made it an environment and ran it. Its test collection stopped at two modules that could not import a directory the instantiation had dropped, so its pipeline had never been able to start, and the template residue guard had been printing "this is the template, check skipped" all along because the sentinel that marks the template was still tracked. No remote, so no CI; no CI, so no gate; a guard that skipped itself. It is fixed and registered as what it is, a parked scaffold, and the cheap rule I kept is to run a repository's tests and entry point before recording its state.

The last error is the one worth a paragraph, because it is the one the others hide behind. The working ledger was written from what each pass intended. When I re-derived every plan's version from its repository instead, the ledger was wrong in four places: a row claiming a version file and a tag that did not exist; a tag placed on sources that still read the previous version; an engine repository with continuous integration red since a lint release two weeks earlier, unremediated; and three products whose version lived only in a manifest. All of it was finished the same day, and none of it would have been found by reading the ledger.

A ledger is a list of intentions with dates. A record is a list of facts with evidence. The rule that survived the pass is that every claim in a record is re-read from the repository before it is written, and that the working ledger is never the record.

## Two rules I am keeping

Read-only state first, and decide per branch with the tree, not with the name. A branch called `promote/final` was merged; a branch called `fix/typo` carried a rewrite nobody else had.

And one repository at a time. The two times I let three chains overlap to go faster, the quality dropped, and the two most expensive errors above, the artifact rewrite and the tag on an unmoved version, both happened inside those windows. Going faster was the failure, not the reason.
