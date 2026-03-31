---
layout: default
title: "Materials for Art Styles"
parent: "Part 1: AI & Arts and Humanities"
nav_order: 2
has_children: true
---

Here you find the materials for the lesson on art styles and image prompting

{% assign folder = page.dir %}
<ul>
{% for f in site.static_files %}
  {% if f.extname == '.pdf' and f.path contains folder %}
    {% assign rest = f.path | remove_first: folder %}
    {% unless rest contains '/' %}
      <li><a href="{{ f.path | relative_url }}">{{ f.name }}</a></li>
    {% endunless %}
  {% endif %}
{% endfor %}
</ul>
