# AI for Empirical Research — Platform Build Plan

**For:** Matteo **From:** Paul **Goal:** A public educational site that organizes my existing AI-in-research content (Substack posts, Markus Academy videos, example code) into a single hub I can point people to — including from my NBER Summer Institute Household Finance talk.

---

## 1. What we're building

A Jekyll site, in its own GitHub repo, served through GitHub Pages under my domain (e.g. `ai.paulgp.com` — final URL TBD, see Open Questions). It is primarily an **index and curation layer**, not new content. Almost every page points out to something that already exists: a Substack post, a YouTube video, or an example repo.

Design principle: **every page follows a fixed template, driven by data files, so maintenance is mechanical.** You should be able to update a video timestamp or add a new post by editing one YAML file, not by touching HTML.

The site should visually match paulgp.com — reuse/adapt the layouts, includes, and CSS from that repo rather than picking a new theme.

## 2. Repo structure

```
ai-for-empirical-research/
├── _config.yml              # Jekyll config; pin github-pages gem locally
├── CNAME                    # custom domain (once decided)
├── index.md                 # landing page: one-paragraph pitch + three entry paths
├── _layouts/                # adapted from paulgp.com
├── _includes/
│   └── video_page.html      # renders the standard pipeline-page template
├── _data/
│   ├── videos.yml           # one entry per video: URL, timestamps, companion post, repo
│   └── elsewhere.yml        # curated external resources
├── start-here/
│   ├── new-to-ai.md
│   ├── casual-user.md
│   └── power-user.md
├── pipeline/
│   ├── 01-setup.md
│   ├── 02-data-analysis.md
│   ├── 03-scraping.md
│   ├── 04-large-data.md
│   ├── 05-writing.md
│   ├── 06-skills.md
│   └── 07-workflow-git.md
├── restricted-data.md
├── skills/                  # downloadable skill files + starter CLAUDE.md template
├── elsewhere.md             # renders from _data/elsewhere.yml
├── changelog.md
├── talks/
│   └── nber-hf-2026.md      # landing page for the talk (final-slide URL)
└── CLAUDE.md                # instructions for maintaining this site with Claude Code
```

**Separate repos** (independent, cloneable on their own):

- `hmda-pipeline` — cleaned-up version of the HMDA/DuckDB demo (video 4)
- `edgar-scraper` — cleaned-up version of the EDGAR scraping demo (video 3)
- `hf-project-template` — fork-able starter for an empirical project: folder structure, starter CLAUDE.md, .gitignore for data, Makefile

Each example repo needs a README with: what it does (3 sentences), a 10-minute quickstart, data download size/time expectations, and a link back to the relevant video + post.

## 3. Page template (pipeline pages)

Every page in `pipeline/` renders identically via `_includes/video_page.html`, pulling from `_data/videos.yml`:

1. **Summary** — 3 sentences max, written by Matteo, approved by Paul
2. **Video embed** + timestamp table (from videos.yml)
3. **Companion Substack post** link
4. **Example repo** link (where one exists)
5. **Footer:** "Last verified: [date] with [model/tool version]"

The page's markdown file should contain only front matter (which video key to use) and the summary paragraph. Everything else comes from the include + data file.

**videos.yml schema (per entry)**

```yaml
- key: large-data
  title: "Large Datasets and Structured Databases"
  youtube: "https://www.youtube.com/watch?v=..."
  substack: "https://paulgp.substack.com/p/large-datasets-and-structured-databa"
  repo: "https://github.com/paulgp/hmda-pipeline"
  timestamps:
    - { t: "02:59", label: "Building a mortgage panel from HMDA" }
    - { t: "07:52", label: "DuckDB + Parquet for large-scale data" }
  last_verified: 2026-07-01
  verified_with: "Claude Code x.y / Opus 4.x"
```

## 4. Key pages beyond the pipeline

- **index.md** — pitch + router: "Never used these tools" / "Use them casually" / "Power user" → the three start-here pages, each of which sequences the right videos/posts.
- **restricted-data.md** — the household-finance-specific page: what to do when your data can't go near an agent (RDCs, credit bureau data, IRB/PII). Patterns: develop on synthetic/public analogs then port; containers and sandboxing; what current policies allow. **Paul drafts or heavily edits this one** — it's the highest-stakes page.
- **talks/nber-hf-2026.md** — slides PDF, demo repo link, and an "if you only read three things" list. This is the single URL on the final slide of the talk.
- **changelog.md** — dated entries. Monthly habit: re-check the getting-started path, note model/tool changes, update `last_verified` fields.
- **elsewhere.md** — external resources (Cunningham's series, Sant'Anna's workflow template, Korinek's guides, the ai-econ-wiki, Markus Academy). Positions the site as a hub, not just self-promotion.

## 5. Task sequence

### Phase 1 — skeleton (target: this week)

1. Create repo; copy/adapt layouts + CSS from paulgp.com
2. Get a stub site building on GitHub Pages (all pages exist, mostly empty)
3. Set up local preview with the `github-pages` gem so local matches deployed

### Phase 2 — content plumbing

4. Watch/skim all videos; fill in `_data/videos.yml` with timestamps (the Markus Academy Substack posts already list most timestamps — start there and verify)
5. Build `video_page.html` include; wire up all seven pipeline pages
6. Write 3-sentence summaries per page → Paul reviews in one batch

### Phase 3 — example repos

7. Clean up hmda-pipeline and edgar-scraper: reproducible from a fresh clone, READMEs per spec above
8. Build hf-project-template
9. **Fresh-machine test:** run the full "new-to-ai" path (install → first session → first result) on a clean environment; fix everything that breaks

### Phase 4 — the talk tie-in

10. Stub talks/nber-hf-2026.md; add slides + demo repo when ready
11. Paul drafts restricted-data.md; Matteo formats and links
12. First changelog entry; set the monthly reminder

## 6. Working conventions

- **All changes via PR**, even small ones. Paul reviews; this doubles as the audit trail.
- **Use Claude Code to build the site** — the repo's own CLAUDE.md should describe the site conventions (page template, data-file-driven pages, PR workflow) so the tooling we teach is the tooling we use. Write CLAUDE.md in Phase 1 and keep it current.
- **Don't hand-edit anything that should come from `_data/`.** If you find yourself editing a timestamp in a page file, the architecture is broken — fix the data file or the include.
- **No content invention.** Summaries paraphrase the posts/videos; anything substantive that doesn't exist yet gets flagged to Paul, not written from scratch.
- **Pin gem versions; commit `Gemfile.lock`.**

## 7. Open questions for Paul (decide before Phase 1 ends)

1. **URL:** subdomain (`ai.paulgp.com`, needs a DNS CNAME record) vs. subpath (`paulgp.com/ai-research`, trickier with a separate repo). Subdomain is cleaner for a standalone repo.
2. **Repo/site name:** `ai-for-empirical-research` vs. something shorter.
3. **Scope of example repos for v1:** all three, or just hmda-pipeline (the most HF-relevant) before the talk?
4. **License:** MIT for code repos, CC-BY for site content?

## 8. Definition of done (v1, before the NBER talk)

- Site live at final URL, matching paulgp.com styling
- All seven pipeline pages complete with verified timestamps
- Three start-here paths tested on a fresh machine
- hmda-pipeline repo runs from a fresh clone
- talks/nber-hf-2026.md live with slides
- restricted-data.md live (Paul-approved)
