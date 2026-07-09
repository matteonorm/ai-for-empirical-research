---
layout: default
title: "New to AI"
track_key: "new-to-ai"
---

{% assign track = site.data.tracks[page.track_key] %}

<p>{{ track.framing }}</p>

<ol class="track-path">
{% for step in track.path %}
<li>
  {% if step.external %}
  <a href="{{ step.url }}" target="_blank" rel="noopener noreferrer">{{ step.title }} ↗</a>
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
