---
layout: default
title: "Changelog"
---

## 2026-07-09 — Phase 2 pilot: 04-large-data

**Format pilot** — populated real content for one topic (large-data) to establish
the Phase 2 workflow before batching the remaining six pipeline pages.

- **`_data/videos.yml`**: filled `04-large-data` entry with real metadata (title,
  youtube_id `4uwI1-9DafU`, duration 55:30, Substack URL, 4 resources)
- **`pipeline/04-large-data.md`**: replaced TODO placeholder with draft 3-sentence
  summary (paraphrased from Substack post; pending Paul's review)
- **`content-notes/large-data.md`**: new repo-only working notes with sources,
  timestamps, application notes, resource superset, and flags for Paul
- **`_config.yml`**: added `content-notes/` to exclude list
- **`CLAUDE.md`**: documented `content-notes/` convention
- **`HANDOFF.md`**: updated with real videos.yml schema, content-notes layer,
  and video-ID resolution

**Video-ID resolution:** list_of_links.rtf listed the same YouTube ID (`wqLZrKdevHs`)
for both EDGAR (03) and large-data (04) — confirmed copy error. Correct large-data
ID is `4uwI1-9DafU` (Markus Academy Ep. 162-4), verified via YouTube search + oembed.

**Flags for Paul:** hmda-pipeline repo (referenced in PLAN.md) returns 404; timestamps
from Markus Academy listing are unverified against video; applications parked in notes only.

**Tool:** Claude Code (Opus 4.6)
