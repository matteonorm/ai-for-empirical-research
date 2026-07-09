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
  <a href="{{ step.url | relative_url }}?track={{ page.track_key }}">{{ step.title }}</a>
  <span class="track-why">{{ step.why }}</span>
</li>
{% endfor %}
</ol>

{% if track.further_reading.size > 0 %}
### Further reading

<ul class="track-further-reading">
{% for item in track.further_reading %}
<li>
  <a href="{{ item.url }}" target="_blank" rel="noopener noreferrer">{{ item.title }} ↗</a>
  <span class="track-why">{{ item.why }}</span>
</li>
{% endfor %}
</ul>
{% endif %}

<p class="track-closing">That's the frontier. Browse the <a href="{{ '/pipeline/' | relative_url }}">full pipeline</a>, or explore further resources <a href="{{ '/elsewhere' | relative_url }}">elsewhere</a>.</p>
