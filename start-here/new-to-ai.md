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
  {% assign is_paul = false %}{% for d in site.paul_domains %}{% if item.url contains d %}{% assign is_paul = true %}{% endif %}{% endfor %}<a href="{{ item.url }}" target="_blank" rel="noopener noreferrer">{{ item.title }}{% unless is_paul %} ↗{% endunless %}</a>
  <span class="track-why">{{ item.why }}</span>
</li>
{% endfor %}
</ul>
{% endif %}

<p class="track-closing">Once these feel natural, try the <a href="{{ '/start-here/casual-user' | relative_url }}">Casual User track</a>, or browse the <a href="{{ '/pipeline/' | relative_url }}">full pipeline</a> for AI in empirical research.</p>
