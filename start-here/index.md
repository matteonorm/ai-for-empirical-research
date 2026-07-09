---
layout: default
title: "Start Here"
---

### Pick your track

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
