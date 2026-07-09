---
layout: default
title: "Changelog"
---

## 2026-07-09 — Landing: add applications-everywhere beat

- Added a bridging paragraph between the compression diagram and the econ-lit
  chart: "And it helps everywhere along the way..." Sourced from the stage-by-stage
  section of Paul's "Research in the Time of AI" post. Matteo's editorial phrasing,
  pending Paul.

## 2026-07-09 — Simplify compression diagram caption

- Replaced the two-line caption (grey "After Paul Goldsmith-Pinkham," prefix +
  separate linked title) with a cleaner layout: the sentence on its own line,
  then the post title as a single orange link. No grey prefix.

## 2026-07-09 — Landing page: compression framing, native diagram, econ-lit evidence

- Rewrote landing page framing around the "timeline compression" thesis (drawn
  from Paul's "Research in the Time of AI" post): AI compresses the distance
  between research stages without removing the researcher.
- Added a native inline SVG compression diagram showing the research pipeline
  (Ideation → Design → Data → Analysis → Writing → Paper) in two rows:
  "Traditional" with wide gaps, "With AI" compressed. Built in site style
  (Spectral, DM Sans, rust #b5451b), no external dependencies. Attributed to
  Paul's original figure.
- Relabeled chart selector from "All economics papers" to "Top economics
  journals" to match the data scope.
- Removed the redundant "Explore the live tool here" line (the chart caption
  already links to Paul's pipeline).
- All framing, captions, diagram caption, and closing are Matteo's editorial
  (pending Paul). The compression diagram is a native rebuild inspired by
  Paul's figure (attributed). The econ-lit chart + data are Paul's research
  artifact featured on the front page (flagged for Paul's review).

## 2026-07-09 — Build landing page: econ-lit chart, paper download, start-here CTA

- Added econ-lit trend chart (vanilla JS canvas) and three data CSVs under
  `assets/data/`. Aggregate curve (2011 to 2025) as default, journal selector
  dropdown for per-journal view. No external dependencies.
- Data: dated snapshot from July 2026, refreshed monthly.

## 2026-07-09 — Add Practical Guide as New-to-AI further reading

- Added "Using AI in Research and Teaching: A Practical Guide" (Paul's 2024
  talk page) as a `further_reading` item on the New-to-AI track. Opens in a
  new tab with the external marker. Not part of the sequential path or the
  `?track=` chain. Flagged as pre-Claude-Code background, pending Paul's
  view on whether to keep it.

## 2026-07-09 — Per-track closing lines matching the graduation ladder

- Each track page now ends with a closing line pointing to the next track up
  the ladder and the full pipeline: New to AI → Casual User, Casual → Power
  User, Power → full pipeline + Elsewhere. Replaces the old `closing_before`/
  `closing_after` YAML fields with inline template closings. All links internal.

## 2026-07-09 — Navigation fixes: context-swap, banner layout, Further reading

Two commits:

1. **Banner OR prev/next, never both**: when `?track=` is present, the track
   banner shows and the static pipeline prev/next is hidden via JS. Without
   the param, prev/next shows normally (no banner). Banner layout fixed: back
   link and forward action now stack on separate lines instead of running
   together on one line.

2. **External links become Further reading**: track `path` arrays now contain
   only internal pipeline pages. External links (O-Ring, llms.txt, One-Shot)
   moved to a `further_reading` list in `tracks.yml`, rendered as a separate
   "Further reading" subsection on each track page (new tab, ↗ marker). They
   are not numbered steps and never appear as "next in track" targets.
   Graduation fires after the last internal item.

## 2026-07-09 — Remove pipeline and Start Here TODO placeholders

- Removed the yellow TODO framing-paragraph placeholders from
  `pipeline/index.md` and `start-here/index.md`. The subtitle and list
  follow the heading directly.

## 2026-07-09 — New-to-AI linked path + track graduation end-states

Two commits:

1. **New-to-AI as a linked path**: reverted the inline video embeds. New-to-AI
   now renders as a link-based path identical to Casual and Power (framing,
   ordered links with `?track=new-to-ai`, closing). All three tracks are
   structurally consistent.

2. **Track graduation end-states**: the `?track=` back-banner's last-item state
   now points to the next track up the ladder instead of a generic "finished"
   message. New to AI graduates to Casual User, Casual to Power User. Power
   User (top of the ladder) shows only the back link. Driven by a `next_track`
   field in `tracks.yml`.

3. **Banner bug fixes** (two commits): the banner JS was silently broken by two
   issues. First, pipeline pages render as `.html` files but `tracks.yml` URLs
   omit the extension, so the path comparison never matched; fixed with a
   `normPath` function that strips `.html` before comparing. Second, kramdown
   was converting straight quotes inside `<script>` to curly (smart) quotes,
   breaking all JS string literals; fixed by wrapping the script in
   `{% raw %}` and passing dynamic data (tracks JSON, baseUrl) via `data-`
   attributes on a hidden div.

## 2026-07-09 — Elsewhere: update Sant'Anna URL/description and Blattman title

- Sant'Anna: changed URL from GitHub repo to `psantanna.com/claude-code-my-workflow/`;
  rewrote description to reflect the full academic workflow system (not just a
  slides template).
- Blattman: changed display title from "claudeblattman.com" to
  "Claude Blattman · AI for Professionals Who Don't Code." Description unchanged.

## 2026-07-09 — UX/path navigation (4 commits)

Four navigation mechanisms, each in its own commit:

1. **Pipeline prev/next** (`_includes/pipeline_nav.html`): auto-included via
   `video_page.html`. Stage 01 shows next only, stage 08 shows prev only,
   middle stages show both. Labels display the destination title with arrows.

2. **External links open in new tab**: all off-site links get
   `target="_blank" rel="noopener noreferrer"` and a ↗ glyph. Applied to
   track path items (casual-user, power-user) and all Elsewhere links.

3. **Track back-banner** (`?track=` param): client-side JS reads the param
   and renders a banner ("← Back to Track" / "Next in this track → " /
   "You've finished the track ↩"). Triggers "finished" after the last
   internal item, skipping external links. No banner without the param;
   static pages work fully without it. Script guarded to `page.video_key`
   pages only.

4. **New-to-AI inline videos**: embeds 01-setup and 02-data-analysis inline
   via `include.video_key` override. No out-links, no pipeline nav. Closing
   links to the full pipeline.

CSS additions: `.pipeline-nav`, `.pipeline-nav-next`, `.track-banner`.

## 2026-07-09 — Elsewhere: notable sessions + neutral pgp-voice descriptions

- Added four Markus' Academy sessions as a `sessions` sub-list (Bryan, Golub,
  Correia, Talamas), each fetched and described from its event page.
- Removed "Paul's video series lives here" from the Markus' Academy entry.
- Rewrote all descriptions in pgp voice: direct, concrete, no filler or
  marketing adjectives. All external links open in new tabs.

## 2026-07-09 — Fill Elsewhere: external ecosystem resources

- Populated `_data/elsewhere.yml` with 6 verified resources in 3 categories
  (Guides and writing, Workflow systems, Video series).
- Rewrote `elsewhere.md` to render grouped data from the YAML file.
- Added `.elsewhere-desc` CSS rule. Removed TODO placeholder.
- All URLs fetched and confirmed live. Descriptions written from actual page
  content, not from memory.

## 2026-07-09 — Restructure Start Here: router index + per-track pages

- `start-here/index.md` is now a short router: heading, TODO framing paragraph,
  three track links with taglines only.
- Each track page (`new-to-ai.md`, `casual-user.md`, `power-user.md`) renders
  its own framing, ordered path, and closing from `_data/tracks.yml` via
  `track_key` front matter. TODO placeholders removed.
- No new content; all data was already in `tracks.yml` from the previous commit.

## 2026-07-09 — Populate Start Here tracks (data-driven)

- Extended `_data/tracks.yml` with `framing`, `path` (ordered list of
  `{title, url, why}`), and `closing` fields for each track.
- `start-here/index.md` renders each track as: heading, tagline, framing
  paragraph, numbered path with links and why-lines, closing (new-to-ai only).
- Three external links added: AI and the Research O-Ring (Substack), llms.txt
  for Academic Papers (paulgp.com), AI One-Shot Papers (paulgp.com).
- Added `.track-section`, `.track-why`, `.track-closing` CSS rules.
- O-Ring why-line ("Why it's worth going deeper") flagged for Paul: the post
  actually argues a bottleneck warning, not encouragement.
- All framing paragraphs and why-lines are Matteo's editorial phrasing, pending
  Paul's review.

## 2026-07-09 — Dictated pipeline taglines

- Replaced auto-sourced taglines with Matteo's editorial one-liners (in Paul's
  voice). Placed verbatim in `_data/videos.yml`; rendered via the existing
  data-driven loop in `pipeline/index.md`. Noted in HANDOFF.md as pending
  Paul's review.

## 2026-07-09 — Sourced pipeline taglines

- Added `tagline` field to each of the 8 entries in `_data/videos.yml`.
- `pipeline/index.md` now loops over video data to render title + tagline for
  each stage (no hand-written list).
- Added `.pipeline-tagline` CSS rule for muted styling beneath each link.
- Each tagline mirrored into `content-notes/<slug>.md` with its source
  (post first sentence, takeaway, or summary compression).

## 2026-07-09 — Batch content, 8-stage restructure, heading fix

### Branch rename
- Renamed `content/large-data` to `content`. Closed PR #2 (git ref conflict);
  new PR opened from `content`.

### Bold "What you'll learn" heading (Phase B)
- Added `.video-page h3` CSS rule to match `section > h3:not(:first-of-type)`
  styling (DM Sans, uppercase, 500-weight, border-top). The h3 tags inside
  `.video-page` were getting base h3 style (font-weight 400) because the styled
  rules use direct-child selectors. Affects both "What you'll learn" and
  "Resources" headings on all pipeline pages.

### 8-stage restructure (Phase C, proposal for Paul)
- Added `pipeline/07-permissions.md` (Permissions, Sandboxes, and Autonomous Agents).
- Renamed `pipeline/07-workflow-git.md` to `pipeline/08-workflow-git.md`.
- Updated stage listings in `pipeline/index.md`, `index.md`, `README.md`,
  and `_data/videos.yml`.

### Content for all 7 remaining topics (Phase D)
Each topic: videos.yml entry (title, youtube_id, duration, substack_url,
takeaways, resources), pipeline page (summary + include), content-notes
(repo-only rich notes). All takeaways sourced from Paul's own sections.

| # | Slug | Video ID | Duration | Takeaway source |
|---|------|----------|----------|-----------------|
| 01 | setup | HzgByl5ZsWE | 36:31 | "Tips for Getting Started" (4 tips, expanded to 5 bullets) |
| 02 | data-analysis | Rp17XUPxa4I | 37:30 | "Summing up" (5 numbered points) |
| 03 | scraping | wqLZrKdevHs | 27:46 | "A few things I've learned" (7 points, compressed to 6) |
| 05 | writing | BxfSiB3Moyo | 46:39 | "Key takeaways" (6 numbered points) |
| 06 | skills | a03ehomPqMA | 31:04 | Takeaways section (6 numbered points) |
| 07 | permissions | 8Jnx5rL_Gfk | 47:47 | Takeaways section (6 numbered points) |
| 08 | workflow-git | EcloxLPcRsY | 65:14 | Numbered recommendations (5 points) |

All video IDs verified via YouTube oembed API. No em-dashes in any content.
Page titles updated to match actual video titles in index.md and pipeline/index.md.

### Flags for Paul
- 8-stage restructure (permissions added as stage 7) is a proposal
- hmda-pipeline and patent-data repos still 404
- All summaries and takeaways are DRAFT, pending review
- Video durations from YouTube metadata, not manually verified
- Subscription pricing in 01-setup ($20/$100/$200) may be stale
- Skills documentation URL may change as Anthropic updates docs

**Tool:** Claude Code (Opus 4.6)

## 2026-07-09 — Portable pgp-writing-style skill fallback

- Copied `pgp-writing-style` skill into the repo at `skills/pgp-writing-style/SKILL.md`
  so collaborators without the global skill installed can still follow the voice rule.
- Updated CLAUDE.md: use global skill if available, otherwise read the repo-local copy.
- Added `skills/pgp-writing-style/` to `_config.yml` exclude list and CLAUDE.md
  "Excluded from the site" section.

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
