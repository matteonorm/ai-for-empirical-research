---
layout: default
title: "Casual User"
track_key: "casual-user"
---

{% assign track = site.data.tracks[page.track_key] %}

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
