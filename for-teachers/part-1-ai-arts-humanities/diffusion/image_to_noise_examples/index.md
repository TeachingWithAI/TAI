---
layout: default
title: "Image to noise examples"
parent: "Material for Diffusion"
nav_order: 1
has_children: true
---

Here you find the images and their transformation to noise. 

{% assign pngs = site.static_files
  | where: "extname", ".png"
  | where_exp: "f", "f.path contains '/for-teachers/part-1-ai-arts-humanities/diffusion/image_to_noise_examples/'" %}

<ul>
{% for f in pngs %}
  <li><a href="{{ f.path | relative_url }}">{{ f.name }}</a></li>
{% endfor %}
</ul>
