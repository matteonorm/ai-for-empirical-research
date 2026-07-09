# HANDOFF — Decision Log & Current State

**Date:** 2026-07-09
**Phase:** 2 (content — all 8 pipeline topics populated)
**Canonical spec:** `docs/PLAN.md`
**Repo conventions:** `CLAUDE.md`

## Version choices

- **Ruby:** 3.3.5 locally (via chruby + ruby-install); CI uses 3.2.2 (matches Paul's workflow)
- **Jekyll:** 4.3.4 (resolved from `~> 4.3.3` pin in Gemfile)
- **Bundler:** 2.5.16 (bundled with Ruby 3.3.5)
- **Minima theme:** 2.5.2 (from `~> 2.5` pin)
- **jekyll-feed:** 0.17.0 (from `~> 0.12` pin)

## Build path decision

**Standalone Jekyll 4.3.4 + GitHub Actions deployment** — NOT the `github-pages` gem.

Why: Paul's own repo (`paulgp/paulgp.github.io`) uses this exact setup. The
`github-pages` gem line is commented out in his Gemfile. His CI workflow uses
`ruby/setup-ruby` + `bundle exec jekyll build` + `actions/deploy-pages`. We mirror
this so the two sites build identically and there are no gem-version surprises.

> The plan (`docs/PLAN.md`) mentions "Set up local preview with the `github-pages` gem"
> in Phase 1 step 3. This is outdated — Paul's actual repo does not use that gem. We
> follow the repo, not the plan text, per the instruction to note outdated items here
> rather than editing PLAN.md.

## Baseurl

**Value:** `/ai-for-empirical-research`

This is a GitHub project page at `matteonorm.github.io/ai-for-empirical-research`.
All internal links use `relative_url` so this just works.

### Migration to final subdomain (checklist)

When moving to e.g. `ai.paulgp.com`:

- [ ] In `_config.yml`: change `baseurl` from `"/ai-for-empirical-research"` to `""`
- [ ] In `_config.yml`: change `url` from `"https://matteonorm.github.io"` to `"https://ai.paulgp.com"`
- [ ] Add a `CNAME` file containing `ai.paulgp.com`
- [ ] Set up DNS CNAME record pointing `ai.paulgp.com` to the GitHub Pages domain
- [ ] Transfer or fork the repo to Paul's GitHub account if needed

That's it — all links use `relative_url`, so no other changes needed.

## Files copied/adapted from paulgp.github.io

| File | Source | Changes |
|------|--------|---------|
| `_layouts/default.html` | Paul's `_layouts/default.html` | Removed Google Analytics, PDF gallery scripts, profile image, CV/Papers/Blog nav links. Replaced with site-specific nav (Start Here, Pipeline, Elsewhere, Talks, Changelog). Added `<meta viewport>`. Used `relative_url` for all links. Removed inline accordion CSS (moved to stylesheet). |
| `assets/css/styles.css` | Paul's `assets/css/styles.css` | Kept core typography (Spectral, DM Sans), colors (#faf8f5 bg, #b5451b links), grid layout, and sidenav styling. Removed some media query breakpoints for brevity. Added `.todo-placeholder` class. |
| `assets/js/scale.fix.js` | Paul's `assets/js/scale.fix.js` | Verbatim copy. |
| `.github/workflows/jekyll.yml` | Paul's `.github/workflows/jekyll.yml` | Changed branch from `master` to `main`. Otherwise identical. |
| `Gemfile` | Paul's `Gemfile` | Removed `pdf-reader` gem (not needed — we have no PDF scanner plugin). Otherwise matches. |
| `.gitignore` | Paul's `.gitignore` | Simplified to just Jekyll/vendor/macOS entries. |

**Not copied** (not needed for this site):
- `_layouts/blog.html` — blog-specific layout
- `_includes/analytics.html` — Google Analytics (different property)
- `_includes/cv.html`, `_includes/sidenote.html` — CV/blog-specific
- `_includes/custom_math.html` — MathJax (not needed yet)
- `_plugins/pdf_scanner.rb` — PDF gallery generator
- `assets/css/blog.css`, `assets/css/github-light.css`, `assets/css/jekyll-code-style.css` — blog/code styling

## Writing style

**Voice:** The `pgp-writing-style` skill is used as a voice reference only, not
for its paper-specific machinery (numbered assumptions, propositions, roadmaps,
footnote citations). This is short web/curation copy matching Paul's
Substack/blog register: problem-first, active, concrete, non-overclaiming.

**No em-dashes:** Em-dashes are a common AI-writing tell; we strip them from
AI-drafted copy. Note: Paul uses em-dashes freely in his own writing (the skill
documents this). The rule targets AI-generated prose specifically, not Paul's
style. The no-em-dash rule takes precedence over the skill's em-dash guidance.

The enforceable rules are in `CLAUDE.md` under "Writing style."

## Deviations from docs/PLAN.md

1. **No `github-pages` gem** — plan mentions it in Phase 1 step 3; Paul's actual repo doesn't use it. Noted above.
2. **No CNAME file** — plan lists it in the repo structure; not created yet because no domain is decided. Will add when URL is finalized.
3. **PR-only workflow relaxed** — plan says "all changes via PR"; for this bootstrap phase we commit directly to main. Will enforce PR workflow once the skeleton is live.
4. **Repo hosted on matteonorm's account** — temporary; plan envisions it under Paul's account/domain.
5. **Monthly review implemented as GitHub Actions, not email** — `.github/workflows/monthly-reminder.yml` opens an issue on the 1st of each month with a review checklist. Uses `GITHUB_TOKEN` and `actions/github-script` — no SMTP secrets needed. Notification relies on GitHub's built-in issue-assignment emails.
6. **changelog.md and docs/PLAN.md excluded from site** — the plan lists changelog as a public page; we keep both in the repo as internal maintenance/spec docs but exclude them from the Jekyll build entirely (`_config.yml` exclude list). Neither appears in site navigation, and their URLs (`/changelog/`, `/docs/PLAN/`) will 404 after deploy. They must not be re-published or re-linked.
7. **8 pipeline stages, not 7** — PLAN.md lists 7 stages (01-setup through 07-workflow-git). We added 07-permissions (Permissions, Sandboxes, and Autonomous Agents) based on Paul's Substack post and Markus Academy video (Ep. 162-7), renumbering workflow-git to 08. This is a proposal for Paul's review, not a unilateral change.

## Bold "What you'll learn" heading fix

The `.video-page h3` tags (both "What you'll learn" and "Resources") were
rendering at `font-weight: 400` because the styled h3 rules in `styles.css`
use `section > h3` direct-child selectors, which don't reach inside the
`.video-page` div. Fixed by adding a `.video-page h3` rule that mirrors the
`section > h3:not(:first-of-type)` styling (DM Sans, uppercase, 500-weight,
border-top, #888 color).

## All pipeline content (Phase 2 batch)

All 8 pipeline pages now have real content. Each entry in `_data/videos.yml`
has: title, youtube_id (verified via oembed), duration (from YouTube metadata),
substack_url, takeaways (sourced from Paul's own sections), and resources.
Each `pipeline/*.md` file has a 3-sentence summary and the include. Each topic
has repo-only working notes in `content-notes/`.

All content is DRAFT, pending Paul's review. No em-dashes in any prose.

### Video-ID verification (all confirmed via YouTube oembed)

| Stage | Slug | youtube_id | Markus Academy Ep. |
|-------|------|------------|-------------------|
| 01 | setup | HzgByl5ZsWE | 162-1 |
| 02 | data-analysis | Rp17XUPxa4I | 162-2 |
| 03 | scraping | wqLZrKdevHs | 162-3 |
| 04 | large-data | 4uwI1-9DafU | 162-4 |
| 05 | writing | BxfSiB3Moyo | 162-5 |
| 06 | skills | a03ehomPqMA | 162-6 |
| 07 | permissions | 8Jnx5rL_Gfk | 162-7 |
| 08 | workflow-git | EcloxLPcRsY | 162-8 |

### Repo/URL flags

- **hmda-pipeline** (https://github.com/paulgp/hmda-pipeline): still 404
- **patent-data** (https://github.com/paulgp/patent-data): still 404
- All other referenced repos verified 200 as of 2026-07-09

## Pipeline taglines

The `tagline` field on each `videos.yml` entry is Matteo's editorial phrasing
(written in Paul's voice, not sourced from the companion posts). These are
rendered on `pipeline/index.md` via a data-driven loop. Pending Paul's review.

## Start Here tracks

The three tracks (New to AI, Casual User, Power User) are now data-driven via
`_data/tracks.yml`, with each entry holding `title`, `url`, and `tagline`.
`start-here/index.md` loops over the data file using an explicit slug list
(matching the pipeline pattern). Taglines are Matteo's editorial audience
descriptors, pending Paul's review.

## Local dev setup

### Prerequisites

Your Mac has Ruby 2.6.10 (system Ruby) which is too old for Jekyll 4.3.
Ruby 3.3.5 is installed via `chruby` + `ruby-install` (both from Homebrew).

To activate chruby in your shell (if not already sourced):
```bash
echo 'source /opt/homebrew/share/chruby/chruby.sh' >> ~/.zshrc
echo 'source /opt/homebrew/share/chruby/auto.sh' >> ~/.zshrc
source ~/.zshrc
```

The repo contains a `.ruby-version` file so chruby auto-switches to ruby-3.3.5.

### Building the site

```bash
cd ai-for-empirical-research

# Activate Ruby (if chruby auto.sh isn't sourced)
source /opt/homebrew/share/chruby/chruby.sh && chruby ruby-3.3.5

# Set repo-local gem path (one-time)
bundle config set --local path vendor/bundle

# Install dependencies
bundle install

# Serve locally
bundle exec jekyll serve
# → http://127.0.0.1:4000/ai-for-empirical-research/
```

### Common gotchas

- **eventmachine compilation:** Ruby 3.3.5 was built with `CXX=false` in its
  rbconfig, which prevents the eventmachine native extension from compiling.
  Fixed by patching rbconfig:
  ```bash
  sed -i '' 's/CONFIG\["CXX"\] = "false"/CONFIG["CXX"] = "clang++"/' \
    ~/.rubies/ruby-3.3.5/lib/ruby/3.3.0/arm64-darwin25/rbconfig.rb
  ```
  Also needed `--with-cxxflags` for the correct C++ SDK include path:
  ```bash
  bundle config set --local build.eventmachine \
    "--with-cxxflags='-I/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/c++/v1'"
  ```
  These are persisted in `.bundle/config` and `rbconfig.rb` respectively — they
  only need to be done once per machine.
- If `bundle` still uses system Ruby, ensure chruby is sourced and restart your terminal.
- The local URL includes the baseurl path — don't be surprised by `/ai-for-empirical-research/` in the URL.
- `vendor/` is in `.gitignore` — gems are not committed.
- Sass deprecation warnings from the minima theme are harmless.

## videos.yml schema (live fields)

Each entry in `_data/videos.yml` is keyed by the pipeline page slug and has these fields:

```yaml
04-large-data:
  title: "Large Datasets and Structured Databases"   # video's real title
  youtube_id: "4uwI1-9DafU"                          # ID only, not full URL
  duration: "55:30"                                   # MM:SS
  description: ""                                     # leave empty; summary lives in page .md
  substack_url: "https://paulgp.substack.com/p/..."   # companion post
  resources:                                          # renders as a bullet list
    - title: "HMDA Data (CFPB)"
      url: "https://www.consumerfinance.gov/..."
```

The include (`_includes/video_page.html`) reads: `title`, `youtube_id`, `duration`,
`description`, `substack_url`, `takeaways` (list of strings), and `resources`
(list of `{url, title}`). There is no `timestamps` field; timestamps are captured
in `content-notes/` only (see below).

**`takeaways` (proposed, pending Paul's approval for all pages):** An optional list
of strings rendered as a "What you'll learn" bulleted list after the title and before
the video embed. Renders nothing if absent or empty. Currently populated only for
04-large-data as a pilot. Sourced from the companion post's own framing, not invented.
Do not roll out to other pages until Paul reviews the format.

## content-notes/ layer

`content-notes/` holds repo-only working material for Phase 2 content:
- Sources (post, video, repos)
- Draft summaries marked "DRAFT, pending Paul"
- Timestamps (from Markus Academy listings, marked verified/unverified)
- Application notes (not published)
- Resource superset (including academic refs not in the live resources list)
- Gaps and flags for Paul

Excluded from the Jekyll build via `_config.yml`. Never published or linked from site pages.

## Video-ID resolution (04-large-data)

`list_of_links.rtf` listed the same YouTube ID (`wqLZrKdevHs`) for both:
- 03-scraping (EDGAR): **correct** (Markus Academy Ep. 162-3)
- 04-large-data: **copy error**

The correct large-data ID is `4uwI1-9DafU` (Markus Academy Ep. 162-4), confirmed via:
1. YouTube search for "Markus Academy Paul Goldsmith-Pinkham Large Datasets"
2. YouTube oembed API confirming the title match
3. Markus Academy Substack listing (https://markusacademy.substack.com/p/large-datasets-claude-code-for-economists)

## Current state

| Directory/File | Status |
|----------------|--------|
| `_config.yml` | Done |
| `_layouts/default.html` | Done (adapted from Paul's) |
| `_includes/video_page.html` | Done (template with takeaways, embed, resources) |
| `_data/videos.yml` | All 8 pipeline entries populated |
| `_data/elsewhere.yml` | Stubbed with TODO placeholders |
| `index.md` | All 8 pipeline links with real titles |
| `start-here/index.md` | Stubbed (landing page with track picker) |
| `start-here/*.md` (3 track files) | Stubbed |
| `pipeline/index.md` | All 8 stages listed with real titles |
| `pipeline/*.md` (8 stage files) | All populated with summaries + includes |
| `restricted-data.md` | Stubbed |
| `skills/index.md` | Stubbed |
| `skills/pgp-writing-style/SKILL.md` | Portable voice skill fallback (excluded from build) |
| `elsewhere.md` | Stubbed |
| `changelog.md` | Batch entry added (excluded from site build, git-only) |
| `content-notes/*.md` (8 files) | Repo-only working notes for all 8 topics |
| `talks/nber-hf-2026.md` | Stubbed |
| `assets/css/styles.css` | Done (adapted from Paul's) |
| `assets/js/scale.fix.js` | Done (verbatim from Paul's) |
| `.github/workflows/jekyll.yml` | Done (adapted from Paul's) |
| `Gemfile` | Done |
| `Gemfile.lock` | Done (generated with Ruby 3.3.5) |
| `.ruby-version` | Done (ruby-3.3.5 for chruby auto-switch) |
| `docs/PLAN.md` | Done (verbatim from Paul's PDF) |
| `CLAUDE.md` | Done |
| `HANDOFF.md` | This file |

## Open questions for Paul

(Carried from `docs/PLAN.md` section 7)

1. **URL:** subdomain (`ai.paulgp.com`) vs. subpath (`paulgp.com/ai-research`)
2. **Repo/site name:** keep `ai-for-empirical-research` or something shorter?
3. **Scope of example repos for v1:** all three, or just hmda-pipeline before the talk?
4. **License:** MIT for code, CC-BY for content?

## Assumptions and guesses

- **Default branch is `main`** — Paul's repo uses `master`; we use `main` (GitHub's current default). The workflow is configured for `main`.
- **No Google Analytics** — removed from the layout. Will need a separate tracking ID if Paul wants analytics on this site.
- **Minima theme kept** — Paul's _config.yml references the minima theme even though the custom CSS overrides most of it. We keep the gem dependency for compatibility but the visual styling comes from the custom `styles.css`.
- **No profile image** — Paul's sidebar has his photo; we omit it. Could add a logo or Paul's photo later.
- **Nav structure** — chose Start Here / Pipeline / Elsewhere / Talks / Changelog for the sidebar. This is a guess at the right top-level navigation; may need revision.
