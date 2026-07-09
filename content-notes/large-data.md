# Content Notes: Large Datasets and Structured Databases

## Sources

- **Substack post:** https://paulgp.substack.com/p/large-datasets-and-structured-databases
- **Video:** https://www.youtube.com/watch?v=4uwI1-9DafU (Markus Academy Ep. 162-4)
- **Markus Academy listing:** https://markusacademy.substack.com/p/large-datasets-claude-code-for-economists
- **Repo (PLAN.md reference):** https://github.com/paulgp/hmda-pipeline — **404 as of 2026-07-09**

## Draft Summary (DRAFT — pending Paul)

This video demonstrates how to transform 70 GB of raw HMDA mortgage data — spanning
291 million records from 2007 to 2024 — into a structured, queryable DuckDB database
using Claude Code. The workflow covers downloading and converting CSVs to Parquet format,
harmonizing schema changes across years, and building self-documenting metadata tables
that preserve context across sessions. The resulting database enables rapid construction
of county-level lending panels and analysis of trends such as the rise of fintech
mortgage lenders.

## Timestamps (from Markus Academy listing — unverified against video)

| Time  | Label                                              | Verified? |
|-------|----------------------------------------------------|-----------|
| 00:00 | Intro                                              | unverified |
| 02:59 | Building a mortgage panel from HMDA data           | unverified |
| 07:52 | DuckDB + Parquet for large-scale data work         | unverified |
| 11:47 | Claude Code's planning mode and agent workflow     | unverified |
| 27:55 | Harmonizing 18 years of mortgage data              | unverified |
| 42:01 | Fintech lender classification and market-share trends | unverified |

## What you'll learn (from post)

These are paraphrased from Paul's own framing in the companion Substack post:

1. How to turn a large, messy administrative dataset into a clean, documented, queryable database using Claude Code — post states this as the core demonstration
2. Converting CSVs to Parquet for 15x compression and using DuckDB to query data too large for memory — post describes the technical fundamentals
3. Building metadata tables as "context engineering for data" — post introduces this as the key conceptual contribution, making datasets self-documenting across sessions
4. Using Claude Code's planning mode to design the architecture before writing any code — post emphasizes this as essential for complex pipelines
5. A generalizable pattern (download → convert → harmonize → document → query → analyze) that applies to HMDA, Medicare claims, patent filings, and other large administrative datasets — post states this explicitly as the transferable lesson

## High-Level Applications (NOTES ONLY — not published)

- County-by-year mortgage lending panels (originations, dollar volume, lender counts)
- HHI concentration measures across counties and years
- Fintech vs. traditional bank lender classification
- Market share tracking (fintech share rose from 1.1% in 2007 to 16.3% peak in 2021)
- Denial rate analysis
- Median loan amount trends
- Schema harmonization across pre-2018 and post-2018 HMDA formats

## Full Resource Superset (NOTES ONLY)

### Live resources (in videos.yml)
- HMDA Data — CFPB: https://www.consumerfinance.gov/data-research/hmda/
- DuckDB: https://duckdb.org/
- IPEDS Database (example project): https://github.com/paulgp/ipeds-database
- Patent Data (example project): https://github.com/paulgp/patent-data — **404 as of 2026-07-09**

### Additional references from the post (not live)
- HMDA historic loan data download: https://files.consumerfinance.gov/hmda-historic-loan-data/hmda_{YEAR}_nationwide_all-records_codes.zip
- FFIEC data browser API: https://ffiec.cfpb.gov/v2/data-browser-api/view/nationwide/csv?years={YEAR}
- Fuster, Plosser, Schnabl, and Vickery (2019), "The Role of Technology in Mortgage Lending": https://doi.org/10.1093/rfs/hhz018
- Ian Gow's curated call reports: https://iangow.github.io/notes/published/curate_call_reports.html

## Gaps / Flags for Paul

1. **hmda-pipeline repo does not exist** — PLAN.md references https://github.com/paulgp/hmda-pipeline
   but it returns 404 as of 2026-07-09. Omitted from live resources. Should Paul create it,
   or should the site reference a different repo?
2. **patent-data repo does not exist** — Substack post references https://github.com/paulgp/patent-data
   but it returns 404 as of 2026-07-09. Omitted from live resources.
2. **Video duration** (55:30) extracted from YouTube page metadata — not manually verified.
3. **Timestamps** from Markus Academy Substack listing, not verified against video playback.
   Need someone to scrub through the video to confirm.
4. **Applications not published** — county panels, fintech classification, etc. are parked
   here pending Paul's decision on what to surface.
5. **Video-ID duplicate in list_of_links.rtf** — both EDGAR (03) and large-data (04)
   listed with `wqLZrKdevHs`. Resolved: that ID is EDGAR (Ep 162-3). Large-data is
   `4uwI1-9DafU` (Ep 162-4), confirmed via Markus Academy YouTube channel search.

## Verification

- **Date:** 2026-07-09
- **Tool:** Claude Code (Opus 4.6)
