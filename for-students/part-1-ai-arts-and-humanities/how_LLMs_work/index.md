---
layout: default
title: "How LLMs work"
parent: "Part 1: AI & Arts and Humanities"
nav_order: 4
has_children: true
---

Here you find the materials for the lesson on how LLMs work. 


{% assign folder = page.dir %}
{%- assign dirs_concat = "" -%}
{%- for p in site.pages -%}
  {%- if p.dir != folder and p.dir contains folder -%}
    {%- assign rest = p.dir | remove_first: folder -%}
    {%- assign parts = rest | split: '/' -%}
    {%- if parts.size == 2 -%}
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

{% comment %}
List only PDFs directly in this folder (exclude subfolders).
{% endcomment %}
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

{% comment %}
Links for How_LLMs_work_presentation.pptx in this folder.
Preview uses Office Web Viewer and needs an absolute URL.
Make sure _config.yml has:
  url: "https://YOUR-USER.github.io"
  baseurl: "/YOUR-REPO"   # for project pages
{% endcomment %}

{% assign file = 'How_LLMs_work_presentation.pptx' %}
{% assign rel = page.dir | append: file %}

{%- comment -%} Absolute URL for viewer {%- endcomment -%}
{% assign abs = rel | absolute_url %}

{%- comment -%} Office Web Viewer preview link {%- endcomment -%}
{% assign preview = 'https://view.officeapps.live.com/op/view.aspx?src=' | append: abs | uri_escape %}

<p>
  <a class="btn btn-primary" href="{{ preview }}" target="_blank" rel="noopener">
    Preview presentation (opens in new tab)
  </a>
</p>

<p>
  <a class="btn" href="{{ rel | relative_url }}" download>
    Download presentation (.pptx)
  </a>
</p>
