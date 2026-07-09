---
layout: default
title: "Large Datasets and Structured Databases"
video_key: "04-large-data"
---

Working with large administrative datasets means dealing with messy, multi-format files that change schema across years. This video walks through turning 70 GB of raw HMDA mortgage data (291 million records, 2007 to 2024) into a clean, queryable DuckDB database: downloading and converting CSVs to Parquet, harmonizing schema changes, and building metadata tables that make the data self-documenting across sessions. The resulting database supports rapid construction of county-level lending panels and analysis of trends like the rise of fintech mortgage lenders.

{% include video_page.html %}
