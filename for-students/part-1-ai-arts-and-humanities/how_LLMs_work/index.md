
---
layout: default
title: "How LLMs work"
parent: "Part 1: AI & Arts and Humanities"
nav_order: 4
has_children: true
---

Here you find the materials for the lesson on how LLMs work. 

{% assign pdfs = site.static_files
  | where: "extname", ".pdf"
  | where_exp: "f", "f.path contains '/for-students/part-1-ai-arts-and-humanities/how_LLMs_work/'" %}

<ul>
{% for f in pdfs %}
  <li><a href="{{ f.path | relative_url }}">{{ f.name }}</a></li>
{% endfor %}
</ul>
