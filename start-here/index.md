---
layout: default
title: "Start Here"
---

### Pick your track

<div class="todo-placeholder">
TODO: Brief framing paragraph — what these tracks are and how to choose.
</div>

{% assign slugs = "new-to-ai,casual-user,power-user" | split: "," %}
{% for slug in slugs %}
{% assign track = site.data.tracks[slug] %}
<div class="track-section">
  <h3><a href="{{ track.url | relative_url }}">{{ track.title }}</a></h3>
  <span class="track-tagline">{{ track.tagline }}</span>
  <p>{{ track.framing }}</p>
  <ol class="track-path">
  {% for step in track.path %}
  <li>
    {% if step.external %}
    <a href="{{ step.url }}">{{ step.title }}</a>
    {% else %}
    <a href="{{ step.url | relative_url }}">{{ step.title }}</a>
    {% endif %}
    <span class="track-why">{{ step.why }}</span>
  </li>
  {% endfor %}
  </ol>
  {% if track.closing_before %}
  <p class="track-closing">{{ track.closing_before }}<a href="{{ '/pipeline/' | relative_url }}">the full pipeline</a>{{ track.closing_after }}</p>
  {% endif %}
</div>
{% endfor %}
