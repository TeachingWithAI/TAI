---
layout: default
title: "Image to noise examples"
parent: "Material for Diffusion"
nav_order: 1
has_children: true
---

Here you find the images and their transformation to noise. 

{% assign pdfs = site.static_files
  | where: "extname", ".pdf"
  | where_exp: "f", "f.path contains '/for-teachers/part-1-ai-arts-humanities/diffusion/'" %}

<ul>
{% for f in pdfs %}
  <li><a href="{{ f.path | relative_url }}">{{ f.name }}</a></li>
{% endfor %}
</ul>
