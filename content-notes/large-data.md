# Content Notes: Large Datasets and Structured Databases

## Sources

- **Substack post:** https://paulgp.substack.com/p/large-datasets-and-structured-databases
- **Video:** https://www.youtube.com/watch?v=4uwI1-9DafU (Markus Academy Ep. 162-4)
- **Markus Academy listing:** https://markusacademy.substack.com/p/large-datasets-claude-code-for-economists
- **Repo (PLAN.md reference):** https://github.com/paulgp/hmda-pipeline (**404 as of 2026-07-09**)

## Draft Summary (DRAFT, pending Paul)

Working with large administrative datasets means dealing with messy, multi-format files
that change schema across years. This video walks through turning 70 GB of raw HMDA
mortgage data (291 million records, 2007 to 2024) into a clean, queryable DuckDB
database: downloading and converting CSVs to Parquet, harmonizing schema changes, and
building metadata tables that make the data self-documenting across sessions. The
resulting database supports rapid construction of county-level lending panels and
analysis of trends like the rise of fintech mortgage lenders.

## Timestamps (from Markus Academy listing, unverified against video)

| Time  | Label                                              | Verified? |
|-------|----------------------------------------------------|-----------|
| 00:00 | Intro                                              | unverified |
| 02:59 | Building a mortgage panel from HMDA data           | unverified |
| 07:52 | DuckDB + Parquet for large-scale data work         | unverified |
| 11:47 | Claude Code's planning mode and agent workflow     | unverified |
| 27:55 | Harmonizing 18 years of mortgage data              | unverified |
| 42:01 | Fintech lender classification and market-share trends | unverified |

## What you'll learn (from post's numbered Takeaways section)

Paul lists seven takeaways at the end of the post. The live bullets paraphrase
and compress these. Mapping:

| Paul's # | Takeaway | Live bullet? |
|-----------|----------|--------------|
| 1 | "The cost of doing data engineering properly has collapsed" | Merged into bullet 6 with #7 |
| 2 | "When data doesn't fit in RAM, don't force it" (DuckDB + Parquet) | Bullet 1 |
| 3 | "Metadata tables are context engineering for data" | Bullet 2 |
| 4 | "Plan mode before code" | Bullet 3 |
| 5 | "Ask what's feasible" | Bullet 4 |
| 6 | "Sub-agents are powerful but imperfect" | Bullet 5 |
| 7 | "The big datasets are more accessible than you think" | Merged into bullet 6 with #1 |

Live bullets (6, paraphrased from Paul):
1. Use DuckDB and Parquet instead of CSVs and dataframes when data doesn't fit in RAM, with lazy-loading and fast aggregation
2. Build metadata tables as "context engineering for data": store schema, descriptions, and value labels inside the database so it documents itself across sessions
3. Use plan mode before writing code, so Claude designs the pipeline architecture and creates a persistent reference rather than jumping into premature edits
4. Ask what's feasible first. Inquire about obstacles and missing information before directing Claude to complete a task
5. Deploy parallel sub-agents for research tasks, but verify they inherit your constraints, since they write their own sub-prompts
6. The fixed cost of proper data engineering has collapsed: large administrative datasets (HMDA, Medicare claims, patent filings) are more accessible than the tooling barriers suggest

## High-Level Applications (NOTES ONLY, not published)

- County-by-year mortgage lending panels (originations, dollar volume, lender counts)
- HHI concentration measures across counties and years
- Fintech vs. traditional bank lender classification
- Market share tracking (fintech share rose from 1.1% in 2007 to 16.3% peak in 2021)
- Denial rate analysis
- Median loan amount trends
- Schema harmonization across pre-2018 and post-2018 HMDA formats

## Full Resource Superset (NOTES ONLY)

### Live resources (in videos.yml)
- HMDA Data (CFPB): https://www.consumerfinance.gov/data-research/hmda/
- DuckDB: https://duckdb.org/
- IPEDS Database (example project): https://github.com/paulgp/ipeds-database
- Patent Data (example project): https://github.com/paulgp/patent-data (**404 as of 2026-07-09**)

### Additional references from the post (not live)
- HMDA historic loan data download: https://files.consumerfinance.gov/hmda-historic-loan-data/hmda_{YEAR}_nationwide_all-records_codes.zip
- FFIEC data browser API: https://ffiec.cfpb.gov/v2/data-browser-api/view/nationwide/csv?years={YEAR}
- Fuster, Plosser, Schnabl, and Vickery (2019), "The Role of Technology in Mortgage Lending": https://doi.org/10.1093/rfs/hhz018
- Ian Gow's curated call reports: https://iangow.github.io/notes/published/curate_call_reports.html

## Gaps / Flags for Paul

1. **hmda-pipeline repo does not exist.** PLAN.md references https://github.com/paulgp/hmda-pipeline
   but it returns 404 as of 2026-07-09. Omitted from live resources. Should Paul create it,
   or should the site reference a different repo?
2. **patent-data repo does not exist.** Substack post references https://github.com/paulgp/patent-data
   but it returns 404 as of 2026-07-09. Omitted from live resources.
3. **Video duration** (55:30) extracted from YouTube page metadata, not manually verified.
4. **Timestamps** from Markus Academy Substack listing, not verified against video playback.
   Need someone to scrub through the video to confirm.
5. **Applications not published.** County panels, fintech classification, etc. are parked
   here pending Paul's decision on what to surface.
6. **Video-ID duplicate in list_of_links.rtf.** Both EDGAR (03) and large-data (04)
   listed with `wqLZrKdevHs`. Resolved: that ID is EDGAR (Ep 162-3). Large-data is
   `4uwI1-9DafU` (Ep 162-4), confirmed via Markus Academy YouTube channel search.

## Verification

- **Date:** 2026-07-09
- **Tool:** Claude Code (Opus 4.6)
