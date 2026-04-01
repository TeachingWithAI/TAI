---
layout: default
title: "How LLMs work"
parent: "Part 1: AI & Arts and Humanities"
nav_order: 4
has_children: true
---

Here you find the materials for the lesson on how LLMs work. 

{% comment %}
List only PDFs directly in this folder (exclude subfolders).
{% endcomment %}
<ul>
{% for f in site.static_files %}
  {% assign ext = f.extname | downcase %}
  {% if ext == '.pdf' %}
    {% assign p = f.path %}
    {% if p contains folder %}
      {% assign rest = p | remove_first: folder %}
      {% unless rest contains '/' %}
        <li><a href="{{ p | relative_url }}">{{ f.name }}</a></li>
      {% endunless %}
    {% endif %}
  {% endif %}
{% endfor %}
</ul>>
