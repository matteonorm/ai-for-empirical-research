# AI for Empirical Research

Public hub for materials on using AI tools in empirical research.

**Live**: https://matteonorm.github.io/ai-for-empirical-research/

## Status

Phase 1 complete: skeleton live, content still TODO.

### Repo layout

```
ai-for-empirical-research/
├── _config.yml            # Jekyll config (site settings, baseurl, excludes)
├── index.md               # landing page: pitch + router to the three tracks
├── _layouts/              # page templates, adapted from paulgp.github.io
├── _includes/
│   └── video_page.html    # the shared pipeline-page template
├── _data/
│   ├── videos.yml         # one entry per video: URL, timestamps, links
│   └── elsewhere.yml      # curated external resources
├── start-here/            # new-to-ai.md, casual-user.md, power-user.md
├── pipeline/              # 01-setup … 07-workflow-git (seven stages)
├── restricted-data.md     # working with data an agent can't touch (RDCs, PII)
├── skills/                # downloadable skill files + starter CLAUDE.md
├── elsewhere.md           # renders from _data/elsewhere.yml
├── talks/
│   └── nber-hf-2026.md    # landing page for the talk (the final-slide URL)
├── .github/workflows/
│   └── jekyll.yml         # build + deploy to GitHub Pages
├── docs/PLAN.md           # Paul's spec (repo-only, excluded from build)
├── CLAUDE.md              # repo conventions (repo-only)
├── HANDOFF.md             # decision log (repo-only)
├── changelog.md           # maintenance log (repo-only, excluded from build)
└── README.md              # this file
```

### Internal docs

* `docs/PLAN.md` — Paul's original build plan, verbatim. The source-of-truth spec.
* `CLAUDE.md` — conventions for working in this repo with Claude Code.
* `HANDOFF.md` — decision log: versions, deviations from the plan, migration checklist, and known workarounds.
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
### Append this to each prompt

```
Also: keep local and the GitHub repo in sync in both directions. Before starting,
run git fetch / git status and pull if behind. After creating the workflow,
commit and push, then confirm the workflow appears in the repo's Actions tab.
Record in CLAUDE.md and HANDOFF.md that a monthly review reminder exists and how
it works. Show me the diff before pushing.
```


