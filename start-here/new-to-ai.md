---
layout: default
title: "New to AI"
track_key: "new-to-ai"
---

{% assign track = site.data.tracks[page.track_key] %}

<p>{{ track.framing }}</p>

{% assign setup = site.data.videos["01-setup"] %}
### {{ setup.title }}

{% include video_page.html video_key="01-setup" %}

{% assign analysis = site.data.videos["02-data-analysis"] %}
### {{ analysis.title }}

{% include video_page.html video_key="02-data-analysis" %}

{% if track.closing_before %}
<p class="track-closing">{{ track.closing_before }}<a href="{{ '/pipeline/' | relative_url }}">the full pipeline</a>{{ track.closing_after }}</p>
{% endif %}
