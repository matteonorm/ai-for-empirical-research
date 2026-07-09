# Content Notes: Integration and Collaboration in AI Research Work

## Sources

- **Substack post:** https://paulgp.substack.com/p/integration-and-collaboration-in
- **Video:** https://www.youtube.com/watch?v=EcloxLPcRsY (Markus Academy Ep. 162-8)
- **Duration:** 65:14 (from YouTube metadata)

## Draft Summary (DRAFT, pending Paul)

AI tools make it cheap to produce code, but verifying that code is correct
remains expensive. This video tackles the "verification debt" problem head-on,
using an IPO event study (built from Jay Ritter's data and CRSP returns) as a
worked example. It walks through git fundamentals for research (commits as audit
trail, branches for experiments), code review practices, routing feedback through
GitHub issues, and wiring results directly into LaTeX drafts via Overleaf so no
number is ever hand-typed.

## What you'll learn (from post's numbered recommendations)

Paul provides five numbered recommendations at the end. All preserved, with
one bullet added from the body's emphasis on verification debt.

Live bullets (5):
1. Ask for the audit trail before the work happens: commit messages, issue references, and documentation should be part of the workflow, not an afterthought
2. Review commits, not full codebases; the unit of verification is a bounded diff, not thousands of lines
3. Treat documentation as a map, not a verdict: LLMs will claim results are done that are not, so verify and consider having another AI review
4. Route feedback through GitHub issues to keep the paper trail useful for both humans and agents
5. No hand-typed numbers: code emits results, the draft ingests them, and git connects the two; review the method before you wire it in

## High-Level Applications (NOTES ONLY, not published)

- IPO event study: three-year buy-and-hold abnormal returns
- Git workflow for research collaboration
- Code review practices for AI-generated code
- Overleaf/GitHub integration for LaTeX papers
- Verification debt management

## Full Resource Superset (NOTES ONLY)

### Live resources (in videos.yml)
- ipo-bump project repo: https://github.com/paulgp/ipo-bump
- Jay Ritter's IPO data: https://site.warrington.ufl.edu/ritter/ipo-data/

### Additional references from the post (not live)
- Financial event studies paper: https://paulgp.com/papers/financial_event_studies_dec282025.pdf
- WRDS/CRSP (institutional access required, no direct link)
- Overleaf (general platform, no project-specific link)

## Gaps / Flags for Paul

1. **Video duration** (65:14) from YouTube metadata, not manually verified.
2. **ipo-bump repo** is public and returns 200; included in live resources.
3. **WRDS access** is required for CRSP data; not something we can link to directly.
4. **IPO results** (three-year BHAR of -19.7%, 70.5% underperformance) are from the demo, not published findings; noted in content-notes only.

## Verification

- **Date:** 2026-07-09
- **Tool:** Claude Code (Opus 4.6)
