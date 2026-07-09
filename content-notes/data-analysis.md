# Content Notes: From an Empty Folder to a Figure

## Sources

- **Substack post:** https://paulgp.substack.com/p/from-an-empty-folder-to-a-figure
- **Video:** https://www.youtube.com/watch?v=Rp17XUPxa4I (Markus Academy Ep. 162-2)
- **Duration:** 37:30 (from YouTube metadata)

## Draft Summary (DRAFT, pending Paul)

Starting from an empty folder, this video shows how to go from a research
question ("how has U.S. homeownership changed over 50 years?") to a
publication-quality figure in a single Claude Code session. Claude navigates the
Census Bureau's housing data, downloads the right tables, and produces an R
script with ggplot2. The key lessons: let Claude handle data acquisition, cite
style guides you like (such as Kieran Healy's) instead of specifying every
parameter, iterate in small steps, and always generate reproducible scripts
rather than one-off outputs.

## What you'll learn (from post's "Summing up" section)

Paul provides five numbered points in his "Summing up" section. Live bullets
paraphrase these directly.

Live bullets (5):
1. Let Claude handle data acquisition: point it at the source (Census, FRED) and let it navigate the download, rather than spending 20 minutes finding the right table yourself
2. Reference style guides you like (such as Kieran Healy's data visualization work) instead of specifying individual plot parameters one at a time
3. Iterate in small steps rather than writing one comprehensive specification; refine the figure incrementally
4. Always generate scripts, not just outputs: the code is the reproducible artifact, not the chart
5. The judgment is still yours: Claude accelerates implementation, but choosing what to plot and how to interpret it remains your job

## High-Level Applications (NOTES ONLY, not published)

- Downloading and cleaning Census/FRED data
- Building publication-quality ggplot2 figures
- Comparing Claude Code vs. Cowork for the same task
- Homeownership rate trends (2004 peak, post-financial-crisis recovery)

## Full Resource Superset (NOTES ONLY)

### Live resources (in videos.yml)
- Kieran Healy, Data Visualization (book): https://socviz.co/
- Census Bureau Housing Vacancies Survey: https://www.census.gov/housing/hvs/

### Additional references from the post (not live)
- Goldsmith-Pinkham & Shue housing returns paper: https://paulgp.github.io/papers/GoldsmithPinkham_Shue_HousingReturns.pdf
- Kieran Healy's website: https://kieranhealy.org/
- Research on politeness to LLMs: https://arxiv.org/abs/2402.14531

## Gaps / Flags for Paul

1. **No YouTube embed in the post.** The RTF lists `Rp17XUPxa4I`, confirmed via oembed as "Data Analysis: Claude Code for Economists... Ep. 162-2."
2. **Video duration** (37:30) from YouTube metadata, not manually verified.
3. **Census data URLs** may shift over time; the Census Housing Vacancies Survey page is the most stable link.
4. **Sub-agents discussion** in the post (context window, delegation) is interesting but not surfaced in takeaways since Paul's "Summing up" section doesn't emphasize it.

## Verification

- **Date:** 2026-07-09
- **Tool:** Claude Code (Opus 4.6)
