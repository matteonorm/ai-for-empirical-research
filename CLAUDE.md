# AI for Empirical Research: Site Conventions

This is a Jekyll 4.3 site for Paul Goldsmith-Pinkham's AI-in-research content.
The canonical spec is `docs/PLAN.md`. This file describes how to work in the repo.

## Build system

- Standalone Jekyll 4.3.3, NOT the `github-pages` gem (see HANDOFF.md for why).
- Deployed via GitHub Actions (`.github/workflows/jekyll.yml`).
- Local dev: `bundle exec jekyll serve` (uses `baseurl` from `_config.yml`).

## Data-driven pages

Pipeline pages (`pipeline/*.md`) render via `_includes/video_page.html`,
pulling all video metadata from `_data/videos.yml`. Each pipeline `.md` file
contains ONLY:
1. Front matter with `video_key`
2. A 3-sentence summary (or TODO placeholder)
3. `{% include video_page.html %}`

Never hand-edit timestamps, video URLs, or Substack links in a page file.
If you need to change video metadata, edit `_data/videos.yml`.

The `elsewhere.md` page renders from `_data/elsewhere.yml` (grouped by category;
each group has `label` and `items`, each item has `title`, `url`, `author`,
`description`). This is an external-ecosystem page, not Paul's own content.

The `start-here/index.md` page renders tracks from `_data/tracks.yml`.
Each track entry has `title`, `url`, and `tagline`.

## Links and URLs

Use Jekyll's `relative_url` and `link` filters for ALL internal links and assets.
The site may be served from a subpath (`/ai-for-empirical-research`) or a root
subdomain; hardcoded leading-slash paths will break one of these.

Example: `{{ '/assets/css/styles.css' | relative_url }}`

**Three-tier external link rule:**

| Destination | Tab | ↗ marker |
|---|---|---|
| This site's own pages | Same tab | No |
| Paul's own domains (`paulgp.com`, `paulgp.substack.com`) | New tab | **No** |
| Third-party domains (everything else) | New tab | Yes |

Paul's content should not read as "leaving to an external site." All off-site
links still open in a new tab (`target="_blank" rel="noopener noreferrer"`);
the only difference is whether the ↗ glyph appears.

The list of Paul's domains lives in `_config.yml` under `paul_domains`. Data-driven
templates (track pages, elsewhere) check `site.paul_domains` with a Liquid loop to
decide the marker. Hardcoded links in includes and pages apply the rule manually.
This is kept separate from "this site" so it behaves correctly after migration to
`ai.paulgp.com`.

## Writing style

**Voice:** Site content and content-notes prose should read in Paul
Goldsmith-Pinkham's voice. Use the `pgp-writing-style` skill as a voice
reference only, not its paper-specific machinery. This is short web/curation
copy, not an academic paper. If the installed/global `pgp-writing-style` skill
is available, use it. Otherwise, read and follow the repo-local fallback at
`skills/pgp-writing-style/SKILL.md`. Never skip the voice check just because
the global skill isn't found.

- YES: problem/practical-first framing; active, direct sentences ("shows",
  "builds", not "it is shown that"); concrete specifics; generous credit;
  careful, non-overclaiming statements.
- NO: numbered/named assumptions, propositions, roadmaps, footnote citations,
  section scaffolding. None of that belongs in a video summary.
- Register: match Paul's Substack/blog voice (the source posts), which is more
  casual than his papers. Paraphrase closely from his own phrasing in the post.

**Curly quotes:** Use curly/typographic quotes uniformly in all rendered content.
kramdown curls straight quotes in Markdown prose automatically, but strings in
`_data/videos.yml` (titles, takeaways, resource labels) are printed verbatim by
the include, so type curly quotes directly in those files. No straight quotes
should appear in rendered page text. Do not alter quotes in code blocks,
filenames, URLs, or YAML syntax itself.

**No em-dashes:** Never use the em-dash in site content or content-notes prose.
Em-dashes are a common AI-writing tell; we strip them from AI-drafted copy.
Rewrite with commas, colons, parentheses, or separate sentences. Applies to
prose only, not to hyphens in compound words, filenames, or numeric ranges.
This rule OVERRIDES the `pgp-writing-style` skill's em-dash guidance. Paul
uses em-dashes in his own writing, but they read as an AI tell in our
AI-drafted copy.

## No content invention

Stub pages use a visible `<div class="todo-placeholder">` with a TODO message.
Never write fake video summaries, descriptions, or timestamps. Content is
written by Matteo, approved by Paul.

## Styling

Adapted from paulgp.github.io. Key files:
- `_layouts/default.html`: main layout with sidebar nav
- `assets/css/styles.css`: Spectral + DM Sans fonts, warm background (#faf8f5)
- `assets/js/scale.fix.js`: mobile viewport fix

## Gem management

Pin versions in Gemfile. Always commit `Gemfile.lock`.
Use `bundle config set --local path vendor/bundle` to keep gems repo-local.

## Excluded from the site (but tracked in git)

These files are in the repo but excluded from Jekyll processing via `_config.yml`.
They must NOT be re-published or re-linked from any site page.
- `changelog.md`: internal change log, repo-only
- `docs/PLAN.md`: Paul's canonical spec, repo-only
- `HANDOFF.md`, `CLAUDE.md`, `README.md`
- `content-notes/`: repo-only working material for Phase 2 content drafts (sources, timestamps, application notes, flags for Paul); never published or linked from site pages
- `skills/pgp-writing-style/`: portable fallback copy of the writing-voice skill; used by Claude Code, not a site page

## Key files

- `docs/PLAN.md`: Paul's canonical spec (do not edit; repo-only, not on the site)
- `HANDOFF.md`: decision log and current state
- `CLAUDE.md`: this file; how to work in the repo
- `changelog.md`: internal change log (repo-only, not on the site)

## Monthly review reminder

A scheduled GitHub Actions workflow (`.github/workflows/monthly-reminder.yml`)
opens a new issue on the 1st of each month with a review checklist: re-run
getting-started path, verify video links/timestamps, note model/tool version
changes, update `changelog.md`, confirm the site deploys. Uses the built-in
`GITHUB_TOKEN` (no secrets or SMTP needed). Can also be triggered manually via
workflow_dispatch.

## Keeping local and remote in sync

- **Before starting work:** run `git status` and `git fetch`, then check whether
  local is behind the remote. If there are un-pulled remote commits, `git pull`
  first. If there are uncommitted local changes, resolve them before starting.
  Never begin edits on a stale or dirty working copy.
- **After any change:** commit and push so the deployed site and local working
  copy never drift. A change isn't "done" until it's pushed AND the Actions
  build has deployed it. Confirm the build succeeded (Actions tab shows a
  green check) before considering the task complete.
