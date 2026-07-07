---
layout: default
title: "Elsewhere"
---

<div class="todo-placeholder">
TODO: Curated links to external resources — Paul's Substack posts,
Markus Academy videos, example GitHub repos, and other relevant materials.
</div>

{% for item in site.data.elsewhere %}
- **{{ item.title }}** — {{ item.description }}
{% endfor %}
