---
layout: default
title: "Part 1: AI & Arts and Humanities"
parent: For Students
nav_order: 1
has_children: true
---

# Part 1: AI & Arts and Humanities (Students)

Here you find the material for Part 1: Ai & Arts and Humanities. 

{% assign pdfs = site.static_files
  | where: "extname", ".pdf"
  | where_exp: "f", "f.path contains '/for-students/part-1-ai-arts-and-humanities/'" %}

<ul>
{% for f in pdfs %}
  <li><a href="{{ f.path | relative_url }}">{{ f.name }}</a></li>
{% endfor %}
</ul>
