---
layout: default
title: "Power User"
track_key: "power-user"
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
