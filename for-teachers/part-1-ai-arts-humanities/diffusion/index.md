---
layout: default
title: "Materials for Diffusion"
parent: "Part 1: AI & Arts and Humanities (Teachers)"
nav_order: 2
has_children: true
---

Here you find the supplementary teaching material on diffusion models.

The following pdf can best be printed on A3. It contains 8 different half-noisy images, with the corresponding prompt. If printed on A3, the little circular pixels are rougly 8mm in diameter, which means you can use black and white sticker marker points to cover them in Assignment 1. 

{% assign pdfs = site.static_files
  | where: "extname", ".pdf"
  | where_exp: "f", "f.path contains '/for-teachers/part-1-ai-arts-humanities/diffusion/'" %}

<ul>
{% for f in pdfs %}
  <li><a href="{{ f.path | relative_url }}">{{ f.name }}</a></li>
{% endfor %}
</ul>
