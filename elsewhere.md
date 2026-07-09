---
layout: default
title: "Elsewhere"
---

### AI for research, beyond this site

{% assign groups = "guides,workflows,video" | split: "," %}
{% for key in groups %}
{% assign group = site.data.elsewhere[key] %}

#### {{ group.label }}

<ul class="elsewhere-list">
{% for item in group.items %}
<li>
  {% assign is_paul = false %}{% for d in site.paul_domains %}{% if item.url contains d %}{% assign is_paul = true %}{% endif %}{% endfor %}<a href="{{ item.url }}" target="_blank" rel="noopener noreferrer">{{ item.title }}{% unless is_paul %} ↗{% endunless %}</a> ({{ item.author }})
  <span class="elsewhere-desc">{{ item.description }}</span>
  {% if item.sessions %}
  <ul class="session-list">
  {% for session in item.sessions %}
  <li>
    {% assign is_paul = false %}{% for d in site.paul_domains %}{% if session.url contains d %}{% assign is_paul = true %}{% endif %}{% endfor %}<a href="{{ session.url }}" target="_blank" rel="noopener noreferrer">{{ session.title }}{% unless is_paul %} ↗{% endunless %}</a> ({{ session.speaker }})
    <span class="elsewhere-desc">{{ session.description }}</span>
  </li>
  {% endfor %}
  </ul>
  {% endif %}
</li>
{% endfor %}
</ul>

{% endfor %}
