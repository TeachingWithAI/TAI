---
layout: default
title: "Materials for Diffusion"
parent: "Part 1: AI & Arts and Humanities (Teachers)"
nav_order: 2
has_children: true
---

Here you find the supplementary teaching material on diffusion models. 

{% assign pdfs = site.static_files
  | where: "extname", ".pdf"
  | where_exp: "f", "f.path contains '/for-teachers/part-1-ai-arts-humanities/diffusion/'" %}

<ul>
{% for f in pdfs %}
  <li><a href="{{ f.path | relative_url }}">{{ f.name }}</a></li>
{% endfor %}
</ul>
