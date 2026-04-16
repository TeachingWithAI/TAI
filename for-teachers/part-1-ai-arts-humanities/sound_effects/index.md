---
layout: default
title: "Materials for Sound Effects"
parent: "Part 1: AI & Arts and Humanities (Teachers)"
nav_order: 3
has_children: true
---

Here you find download links to the mp4 files that can be used as videos in the lesson.

<p>
  <a href="{{ '/for-teachers/part-1-ai-arts-humanities/sound_effects/Big_Buck_Bunny_apple_30.mp4' | relative_url }}"
     download="Big_Buck_Bunny_apple_30.mp4">
    Big Buck Bunny Apple 30s Download video (MP4) 
  </a>
</p>


{% raw %}{% assign vids = site.static_files | where_exp: 'f', "f.path contains '/for-teachers/part-1-ai-arts-humanities/sound_effects/'" | where_exp: 'f', "f.extname == '.mp4'" %}{% endraw %} {% raw %}{% for v in vids %}{% endraw %}

<p><a href="{{ {% raw %}v.path{% endraw %} | relative_url }}" download>Download {{ {% raw %}v.name{% endraw %} }}</a></p> {% raw %}{% endfor %}{% endraw %}

{% comment %}
Immediate subfolder buttons (one level down), Pages-compatible.
{% endcomment %}
{% assign folder = page.dir %}
{% assign folder_parts = folder | split: '/' %}
{% assign folder_len = folder_parts | size %}

{%- assign dirs_concat = "" -%}
{%- for p in site.pages -%}
  {%- if p.dir != folder and p.dir contains folder -%}
    {%- assign p_parts = p.dir | split: '/' -%}
    {%- assign p_len = p_parts | size -%}
    {%- assign depth = p_len | minus: folder_len -%}
    {%- if depth == 1 -%}
      {%- if p.name == 'index.md' or p.name == 'index.html' -%}
        {%- assign dirs_concat = dirs_concat | append: p.dir | append: '||' -%}
      {%- endif -%}
    {%- endif -%}
  {%- endif -%}
{%- endfor -%}

{%- assign dir_list = dirs_concat | split: '||' | uniq | sort -%}
{%- if dir_list.size > 0 -%}
<div class="subfolder-buttons">
  {%- for d in dir_list -%}
    {%- if d != "" -%}
      {%- assign index_page = nil -%}
      {%- for pg in site.pages -%}
        {%- if pg.dir == d -%}
          {%- if pg.name == 'index.md' or pg.name == 'index.html' -%}
            {%- assign index_page = pg -%}
            {%- break -%}
          {%- endif -%}
        {%- endif -%}
      {%- endfor -%}
      {%- if index_page -%}
        {%- assign label = index_page.title | default: d | replace: folder, '' | replace: '/', '' | replace: '-', ' ' | capitalize -%}
        <a class="btn btn-primary" href="{{ index_page.url | relative_url }}">{{ label }}</a>
      {%- endif -%}
    {%- endif -%}
  {%- endfor -%}
</div>
{%- endif -%}


<ul>
{% for f in site.static_files %}
  {% assign ext = f.extname | downcase %}
  {% if ext == '.pdf' %}
    {% assign p = f.path %}
    {% if p contains folder %}
      {% assign rest = p | remove_first: folder %}
      {% unless rest contains '/' %}
        <li><a href="{{ p | relative_url }}">{{ f.name }}</a></li>
      {% endunless %}
    {% endif %}
  {% endif %}
{% endfor %}
</ul>



