---
title: 'Standardizing versioning across the workspace, including the tagging bug I caused'
date: 2026-07-17
permalink: /rollings/2026/07/versioning-and-the-bug-i-shipped/
tags:
  - engineering
  - tooling
  - process
  - honesty
---

Standardizing versioning across the workspace, including the tagging bug I caused
======

I spent a stretch bringing every repo in the workspace onto one versioning scheme (`X.XX.XXX`: a single version constant in code, plus CHANGELOG, UI string, README badge and a `vX.XX.XXX` git tag). The tidy outcome is at the bottom. The part worth leading with is the bug I introduced while doing it, because a batch mutation across many repos is exactly where I have burned myself before.

Re-tagging 22 SAP accelerators at once, the first batch used an unbracketed regex to read the release version from each CHANGELOG. It matched the "Keep a Changelog 1.1.0" line in the file's intro instead of the `## [X.XX.XXX]` release heading, and briefly created bogus `v1.1.0` and `v1.0.0` tags on about 16 repos.

<div style="background:#0d1b2a;padding:16px 20px;border-radius:8px;margin:16px 0;font-family:Georgia,serif;color:#e0e0e0;font-size:15px;line-height:1.8;">
<strong style="color:#e07830;">The mistake, and the recovery:</strong><br/>
a regex matched "Keep a Changelog <strong>1.1.0</strong>", not the release heading, tagging bogus <strong>v1.1.0</strong> on ~16 repos<br/>
caught on the output, deleted every bogus tag (local and remote), re-tagged with the bracketed <strong>[X.XX.XXX]</strong> pattern<br/>
<span style="color:#5a9ac0;font-size:13px;">Verified 0 remaining v1.x tags and 0 tag-vs-CHANGELOG mismatches across all 22. Tags are additive and reversible, so it was recoverable; the real lesson is the one I skipped, which is to test the batch on one repo and verify the value before fanning out.</span>
</div>

There was a quieter measurement error in the same audit that is worth recording too. The first pass read tags with `git describe --tags` from the `develop` checkout. Releases are tagged on `main`, and `develop` sits behind main, so `describe` returned the nearest ancestor tag reachable from develop and under-reported almost every tag. Re-scanning with `git tag --sort=-v:refname` (all tags, branch-independent) corrected the picture. An audit's own tooling can lie to it, so I re-scanned rather than trusting the first read.

The other systemic finding was that `X.XX.XXX` carries leading zeros (`0.12.003`), which are invalid in a semver `package.json` or `pyproject.toml`. The working rule is now explicit: manifests hold the semver form (`0.12.3`) while the CHANGELOG, git tag, UI string and any `VERSION` file hold the display form; they are the same version, one padded. Several repos had literally put the padded string into `package.json` as invalid semver, and the deeper problem in many was that the sources disagreed beyond the padding.

After reconciling the splits (Atalaya, Lidar3D, RotorVitals, where the CHANGELOG lagged tags that had really shipped) and adopting the scheme on the flagships and legacy apps, the final workspace check was 71 repos versioned with tag and CHANGELOG, 10 explicitly exempt, and 0 gaps. The honest version of this note is not the clean count. It is that the count came with a self-inflicted bug in the middle, caught and fixed, and recorded here rather than smoothed over.
