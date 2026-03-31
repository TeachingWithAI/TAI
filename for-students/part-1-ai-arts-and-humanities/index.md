---
layout: default
title: "Part 1: AI & Arts and Humanities"
parent: For Students
nav_order: 1
has_children: true
---

# Part 1: AI & Arts and Humanities (Students)

Here you find the material for Part 1: Ai & Arts and Humanities. Note that this material is still under development and will be tested. 

{% assign folder = page.dir %}  {# e.g., "/for-students/part-1-ai-arts-and-humanities/" #}
{% assign pdfs = site.static_files
  | where: "extname", ".pdf"
  | where_exp: "f", "f.path contains folder" %}

<ul>
{% for f in pdfs %}
  {% assign rest = f.path | remove_first: folder %}
  {% unless rest contains '/' %}
    <li><a href="{{ f.path | relative_url }}">{{ f.name }}</a></li>
  {% endunless %}
{% endfor %}
</ul>
