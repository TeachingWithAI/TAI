
---
layout: default
title: "Prompting LLMs"
parent: "Part 1: AI & Arts and Humanities"
nav_order: 1
has_children: true
---

Here you find the materials for the art exhibition. 

{% assign pdfs = site.static_files
  | where: "extname", ".pdf"
  | where_exp: "f", "f.path contains '/for-students/part-1-ai-arts-and-humanities/Prompting-LLMs/'" %}

<ul>
{% for f in pdfs %}
  <li><a href="{{ f.path | relative_url }}">{{ f.name }}</a></li>
{% endfor %}
</ul>
