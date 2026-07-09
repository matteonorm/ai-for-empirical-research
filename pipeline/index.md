---
layout: default
title: "The Pipeline"
---

### Video walkthroughs for every stage of an empirical project

{% assign slugs = "01-setup,02-data-analysis,03-scraping,04-large-data,05-writing,06-skills,07-permissions,08-workflow-git" | split: "," %}
<ol class="pipeline-list">
{% for slug in slugs %}
{% assign video = site.data.videos[slug] %}
<li>
  <a href="{{ '/pipeline/' | append: slug | relative_url }}">{{ video.title }}</a>
  <span class="pipeline-tagline">{{ video.tagline }}</span>
</li>
{% endfor %}
</ol>
