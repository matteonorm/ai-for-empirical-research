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
  <a href="{{ item.url }}" target="_blank" rel="noopener noreferrer">{{ item.title }} ↗</a> ({{ item.author }})
  <span class="elsewhere-desc">{{ item.description }}</span>
  {% if item.sessions %}
  <ul class="session-list">
  {% for session in item.sessions %}
  <li>
    <a href="{{ session.url }}" target="_blank" rel="noopener noreferrer">{{ session.title }} ↗</a> ({{ session.speaker }})
    <span class="elsewhere-desc">{{ session.description }}</span>
  </li>
  {% endfor %}
  </ul>
  {% endif %}
</li>
{% endfor %}
</ul>

{% endfor %}
