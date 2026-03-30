---
layout: default
title: "Part 1: AI & Arts and Humanities"
parent: For Teachers
nav_order: 1
has_children: true
---

# Part 1: AI & Arts and Humanities (Teachers)

Here you find supporting teaching material for the lessons that you find in the student's folder. 


{% assign pdfs = site.static_files
  | where: "extname", ".pdf"
  | where_exp: "f", "f.path contains '/for-teachers/part-1-ai-arts-humanities/'" %}

<ul>
{% for f in pdfs %}
  <li><a href="{{ f.path | relative_url }}">{{ f.name }}</a></li>
{% endfor %}
</ul>
