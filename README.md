# AI for Empirical Research

A curated guide to AI tools for empirical researchers, built around Paul
Goldsmith-Pinkham's talks and resources.

**Live**: https://matteonorm.github.io/ai-for-empirical-research/

## Status

V1 content in place. Site live on GitHub Pages.

**Done:**
- Landing page: compression framing, native diagram, econ-lit trend chart with
  journal selector, paper download, closing CTA
- 8 pipeline pages (01-setup through 08-workflow-git) with video embeds,
  takeaways, summaries, and resources
- 3 Start Here tracks (New to AI, Casual User, Power User) with sequential
  paths, further reading, and graduation navigation
- Elsewhere page: 6 external resources in 3 categories
- Navigation: pipeline prev/next, track back-banner with `?track=` param,
  context-swap (one nav at a time)
- Three-tier link policy: internal (same tab), Paul's domains (new tab, no
  marker), third-party (new tab, ↗ marker)
- Monthly review reminder (GitHub Actions workflow)

**Remaining:**
- `talks/nber-hf-2026.md`: stub, awaiting Paul's slides
- `restricted-data.md`: stub, Paul drafts this per the plan
- All editorial copy (pipeline taglines, track framing, landing prose) is
  Matteo's phrasing in Paul's voice, pending Paul's review. See HANDOFF.md
  "Awaiting Paul's review" for the full list.

### Repo layout

```
ai-for-empirical-research/
├── _config.yml            # Jekyll config (site settings, baseurl, paul_domains)
├── index.md               # landing page: framing, diagram, chart, CTA
├── _layouts/              # page templates, adapted from paulgp.github.io
├── _includes/
│   ├── video_page.html    # shared pipeline-page template
│   ├── pipeline_nav.html  # prev/next navigation
│   ├── compression_diagram.html  # native SVG diagram
│   └── econlit_chart.html # vanilla JS canvas chart
├── _data/
│   ├── videos.yml         # one entry per pipeline stage
│   ├── tracks.yml         # three Start Here tracks
│   └── elsewhere.yml      # curated external resources
├── assets/
│   ├── css/styles.css     # Spectral + DM Sans, adapted from paulgp.github.io
│   ├── data/*.csv         # econ-lit snapshot (3 files)
│   └── js/scale.fix.js    # mobile viewport fix
├── start-here/            # new-to-ai.md, casual-user.md, power-user.md
├── pipeline/              # 01-setup … 08-workflow-git (eight stages)
├── restricted-data.md     # stub
├── elsewhere.md           # renders from _data/elsewhere.yml
├── talks/
│   └── nber-hf-2026.md    # stub
├── content-notes/         # repo-only working notes (excluded from build)
├── skills/pgp-writing-style/  # portable voice skill (excluded from build)
├── .github/workflows/
│   ├── jekyll.yml         # build + deploy to GitHub Pages
│   └── monthly-reminder.yml  # monthly review issue
├── docs/PLAN.md           # Paul's spec (repo-only)
├── CLAUDE.md              # repo conventions (repo-only)
├── HANDOFF.md             # decision log (repo-only)
├── changelog.md           # maintenance log (repo-only)
└── README.md              # this file
```

### Internal docs

* `docs/PLAN.md` — Paul's original build plan, verbatim. The source-of-truth spec.
* `CLAUDE.md` — conventions for working in this repo with Claude Code.
* `HANDOFF.md` — decision log: versions, deviations from the plan, migration checklist, and known workarounds. Includes consolidated "Awaiting Paul's review" section.
* `changelog.md` — dated maintenance log.

## Continuing work with Claude Code

Paste this into a fresh Claude Code session:

```
Resuming work on the ai-for-empirical-research Jekyll site (a curated hub of
Paul Goldsmith-Pinkham's AI-in-research content for his NBER Household Finance
2026 talk). This is a continuation, not a fresh start.

Before doing anything:
1. Run `git status` and `git fetch`; if local is behind the remote, `git pull`
   first. Never start on a stale or dirty working copy.
2. Read HANDOFF.md in full — the decision log (build path, versions,
   deviations, migration checklist, known workarounds). Treat its decisions as
   settled unless I say otherwise.
3. Read CLAUDE.md for the site conventions.
4. Read docs/PLAN.md for the full Phase 2+ scope and the definition of done.
5. Confirm the site builds locally: `bundle exec jekyll serve`. If it doesn't,
   fixing that is step one.

Then summarize the current state and the next step you understand it to be, and
wait for my go-ahead before making changes.

Hard rules (do not re-litigate):
- Standalone Jekyll + GitHub Actions. NEVER the github-pages gem.
- Mirror paulgp.github.io styling; don't invent layout.
- Never hand-edit anything that belongs in _data/.
- No content invention — stub with visible TODOs, flag gaps to me.
- changelog.md and docs/PLAN.md are repo-only (excluded from the build); don't
  publish or link them.
- Keep local and GitHub in sync both ways; commit and push, and confirm the
  Actions build deployed before calling a task done.
- Small, reviewable commits; show me the diff or the local site before pushing.
```
