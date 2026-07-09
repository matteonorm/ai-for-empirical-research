---
layout: default
title: "Start Here"
---

### Pick your track

<div class="todo-placeholder">
TODO: Brief framing paragraph — what these tracks are and how to choose.
</div>

{% assign slugs = "new-to-ai,casual-user,power-user" | split: "," %}
<ul class="track-list">
{% for slug in slugs %}
{% assign track = site.data.tracks[slug] %}
<li>
  <a href="{{ track.url | relative_url }}">{{ track.title }}</a>
  <span class="track-tagline">{{ track.tagline }}</span>
</li>
{% endfor %}
</ul>
