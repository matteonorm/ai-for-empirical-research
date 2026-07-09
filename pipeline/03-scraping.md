---
layout: default
title: "From EDGAR Filings to a Structured Database"
video_key: "03-scraping"
---

Scraping structured data from messy HTML is a common research bottleneck. This video builds a complete pipeline that pulls 10-K filings from SEC EDGAR for roughly 30 trade-exposed firms, extracts tariff-related paragraphs using BeautifulSoup, and loads everything into a queryable DuckDB database. The workflow uses Claude Code's plan mode for upfront architecture, handles EDGAR's rate limits, and includes quality reports that catch parsing failures early (119 of 120 filings parsed after one fix cycle).

{% include video_page.html %}
