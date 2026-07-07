# AI for Empirical Research

Public hub for materials on using AI tools in empirical research.

**Live**: https://matteonorm.github.io/ai-for-empirical-research/

## Status

Phase 1 complete: skeleton live, content still TODO.

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
