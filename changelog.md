---
layout: default
title: "Changelog"
---

## 2026-07-09 — Re-derive takeaways from Paul's numbered list

- Replaced 5 takeaway bullets with 6 derived directly from Paul's seven numbered
  takeaways at the end of the Substack post. Added sub-agents (#6) and "ask
  what's feasible" (#5), which were missing. Merged cost-collapsed (#1) with
  accessibility (#7). Content-notes updated with full mapping table.

## 2026-07-09 — Remove duplicate title heading from video_page include

- Removed `<h2>{{ video.title }}</h2>` from `_includes/video_page.html`. The page
  already renders its title from the front matter `title:` field, so the include's
  heading was a duplicate. The `title` field stays in `_data/videos.yml` for data use.

## 2026-07-09 — 04-large-data: "What you'll learn" + title fix

- **`_includes/video_page.html`**: added conditional `takeaways` block — renders
  a "What you'll learn" bulleted list when the entry has a non-empty `takeaways`
  list; renders nothing otherwise. Placed after the title, before the video embed.
- **`_data/videos.yml`**: added 5 `takeaways` bullets for 04-large-data, sourced
  from Paul's framing in the companion Substack post.
- **Title fix**: renamed "Large Data & APIs" → "Large Datasets and Structured
  Databases" (the video's real title) in `pipeline/04-large-data.md` front matter,
  `index.md`, and `pipeline/index.md`.
- **`content-notes/large-data.md`**: added "What you'll learn (from post)" section
  with sourcing annotations.

**Note:** the `takeaways` template element is a proposed richer-template addition,
pending Paul's review before rolling out to all pages.

**Tool:** Claude Code (Opus 4.6)

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
