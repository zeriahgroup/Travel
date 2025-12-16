---
layout: default
title: Travel Journal
permalink: /travels/
---

# Travel Journal

A growing archive of trips.

<ul>
{% assign travel_pages = site.pages
  | where_exp: "p", "p.path contains 'travels/'"
  | where_exp: "p", "p.title"
  | sort: "date"
  | reverse %}

{% assign current_year = nil %}

{% for p in travel_pages %}
  {% if p.url != page.url %}
    {% assign year = p.date | date: "%Y" %}
    {% if year != current_year %}

## {{ year }}

      {% assign current_year = year %}
    {% endif %}

<div style="display:flex; gap:20px; margin:20px 0; padding:18px; border:1px solid #eee; border-radius:16px; background:#fff;">
  
  {% if p.cover %}
  <img 
    src="{{ p.cover }}" 
    alt="{{ p.title }}"
    style="width:220px; height:140px; object-fit:cover; border-radius:12px;"
  >
  {% endif %}

  <div style="flex:1;">
    <div style="font-size:1.2rem; font-weight:700; margin-bottom:6px;">
      <a href="{{ p.url }}" style="text-decoration:none;">
        {{ p.title }}
      </a>
    </div>

    <div style="color:#777; font-size:0.9rem; margin-bottom:8px;">
      {{ p.date | date: "%b %Y" }}
    </div>

    {% if p.excerpt %}
    <div style="color:#444; line-height:1.5;">
      {{ p.excerpt }}
    </div>
    {% endif %}
  </div>

</div>

  {% endif %}
{% endfor %}

</ul>
