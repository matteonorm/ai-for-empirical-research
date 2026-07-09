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
  <a href="{{ item.url }}">{{ item.title }}</a> ({{ item.author }})
  <span class="elsewhere-desc">{{ item.description }}</span>
</li>
{% endfor %}
</ul>

{% endfor %}
