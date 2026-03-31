---
layout: default
title: "Part 1: AI & Arts and Humanities"
parent: For Students
nav_order: 1
has_children: true
---

# Part 1: AI & Arts and Humanities (Students)

Here you find the material for Part 1: Ai & Arts and Humanities. Note that this material is still under development and will be tested. 

{% comment %}
List immediate subfolders (one level down) as buttons.
Requires each subfolder to have an index.md (or index.html) with a title.
{% endcomment %}
{% assign folder = page.dir %}
{% assign candidates = site.pages | where_exp: "p", "p.dir != folder and p.dir contains folder" %}
{% assign subfolders = "" | split: "" %}

{% for p in candidates %}
  {% assign rest = p.dir | remove_first: folder %}
  {% assign parts = rest | split: '/' %}
  {% if parts.size == 2 and (p.name == 'index.md' or p.name == 'index.html') %}
    {% assign subfolders = subfolders | push: p %}
  {% endif %}
{% endfor %}

{% if subfolders.size > 0 %}
<div class="subfolder-buttons">
  {% for p in subfolders %}
    {% assign rest = p.dir | remove_first: folder %}
    {% assign name = rest | split: '/' | first %}
    {% assign label = p.title | default: name | replace: '-', ' ' | capitalize %}
    <a class="btn btn-primary" href="{{ p.url | relative_url }}">{{ label }}</a>
  {% endfor %}
</div>
{% endif %}



{% assign folder = page.dir %} 
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
