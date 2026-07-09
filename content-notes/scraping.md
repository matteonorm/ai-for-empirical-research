# Content Notes: From EDGAR Filings to a Structured Database

## Sources

- **Substack post:** https://paulgp.substack.com/p/from-edgar-filings-to-a-structured
- **Video:** https://www.youtube.com/watch?v=wqLZrKdevHs (Markus Academy Ep. 162-3)
- **Duration:** 27:46 (from YouTube metadata)

## Draft Summary (DRAFT, pending Paul)

Scraping structured data from messy HTML is a common research bottleneck.
This video builds a complete pipeline that pulls 10-K filings from SEC EDGAR
for roughly 30 trade-exposed firms, extracts tariff-related paragraphs using
BeautifulSoup, and loads everything into a queryable DuckDB database. The
workflow uses Claude Code's plan mode for upfront architecture, handles EDGAR's
rate limits, and includes quality reports that catch parsing failures early
(119 of 120 filings parsed after one fix cycle).

## Tagline

"Front-load context for scraping; let Claude ask you the design questions."

**Source:** Compressed from takeaways 1 ("Front-load context for scraping tasks")
and 2 ("Let Claude ask you questions about design decisions").

## What you'll learn (from post's "A few things I've learned")

Paul provides seven numbered points. Live bullets compress to 6.

| Paul's # | Takeaway | Live bullet? |
|-----------|----------|--------------|
| 1 | Front-load context for scraping (rate limits, API structure) | Bullet 1 |
| 2 | Let Claude ask you questions about design decisions | Bullet 2 |
| 3 | Build the database schema yourself or approve it | Bullet 3 |
| 4 | Resume capability is essential for network-dependent tasks | Bullet 4 |
| 5 | Quality reports catch data issues early | Bullet 5 |
| 6 | DuckDB or SQLite works well for research projects | Merged into bullet 3 |
| 7 | The finding matters: descriptive analysis validates the pipeline | Bullet 6 |

Live bullets (6):
1. Front-load context for scraping tasks: tell Claude about rate limits, API structure, and expected response formats before it starts writing code
2. Let Claude ask you questions about design decisions rather than specifying everything upfront; the interactive back-and-forth produces better architecture
3. Build or approve the database schema yourself, and use DuckDB or SQLite for research-scale projects where a full database server is overkill
4. Build resume capability into network-dependent pipelines so a dropped connection doesn't mean starting over
5. Add quality reports that run after each stage; they catch parsing failures early (in this case, surfacing that 1 of 120 filings failed)
6. Run a real descriptive analysis on the output: if the finding makes sense (tariff mentions rising in the expected years), it validates the whole pipeline

## High-Level Applications (NOTES ONLY, not published)

- Scraping SEC EDGAR for 10-K filings
- Extracting tariff-related paragraphs from filings
- Building structured databases from unstructured HTML
- Tracking tariff discussion trends across years (2010 vs. 2022-2025)
- Policy uncertainty research using corporate filings

## Full Resource Superset (NOTES ONLY)

### Live resources (in videos.yml)
- SEC EDGAR Full-Text Search: https://efts.sec.gov/LATEST/
- DuckDB: https://duckdb.org/
- Economic Policy Uncertainty Index: https://www.policyuncertainty.com/

### Additional references from the post (not live)
- Loughran & McDonald (2013) on 10-K parsing: https://link.springer.com/article/10.1007/s11142-013-9258-3
- Compound Engineering plugin: https://github.com/EveryInc/compound-engineering-plugin

## Gaps / Flags for Paul

1. **Video duration** (27:46) from YouTube metadata, not manually verified.
2. **edgar-scraper repo** mentioned in PLAN.md as a separate repo to be cleaned up, but not referenced in the post. Not included in live resources.
3. **Roughly 30 firms** is approximate from the post; actual count is "~30 trade-exposed firms."

## Verification

- **Date:** 2026-07-09
- **Tool:** Claude Code (Opus 4.6)
