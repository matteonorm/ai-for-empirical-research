# AI for Empirical Research — Site Conventions

This is a Jekyll 4.3 site for Paul Goldsmith-Pinkham's AI-in-research content.
The canonical spec is `docs/PLAN.md`. This file describes how to work in the repo.

## Build system

- Standalone Jekyll 4.3.3 — NOT the `github-pages` gem (see HANDOFF.md for why).
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

The `elsewhere.md` page renders from `_data/elsewhere.yml`.

## Links and URLs

Use Jekyll's `relative_url` and `link` filters for ALL internal links and assets.
The site may be served from a subpath (`/ai-for-empirical-research`) or a root
subdomain — hardcoded leading-slash paths will break one of these.

Example: `{{ '/assets/css/styles.css' | relative_url }}`

## No content invention

Stub pages use a visible `<div class="todo-placeholder">` with a TODO message.
Never write fake video summaries, descriptions, or timestamps. Content is
written by Matteo, approved by Paul.

## Styling

Adapted from paulgp.github.io. Key files:
- `_layouts/default.html` — main layout with sidebar nav
- `assets/css/styles.css` — Spectral + DM Sans fonts, warm background (#faf8f5)
- `assets/js/scale.fix.js` — mobile viewport fix

## Gem management

Pin versions in Gemfile. Always commit `Gemfile.lock`.
Use `bundle config set --local path vendor/bundle` to keep gems repo-local.

## Key files

- `docs/PLAN.md` — Paul's canonical spec (do not edit)
- `HANDOFF.md` — decision log and current state
- `CLAUDE.md` — this file; how to work in the repo
