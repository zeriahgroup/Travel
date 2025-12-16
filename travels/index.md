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
<div style="height:1px;background:#eee;margin:8px 0 16px 0;"></div>

      {% assign current_year = year %}
    {% endif %}

<div style="padding:14px 16px; border:1px solid #eee; border-radius:12px; margin:12px 0; background:#fff;">
  <div style="font-size:1.05rem; font-weight:700;">
    <a href="{{ p.url }}" style="text-decoration:none;">{{ p.title }}</a>
  </div>
  <div style="color:#666; font-size:0.9rem; margin-top:4px;">
    {{ p.date | date: "%b %Y" }}
  </div>
  {% if p.tags %}
  <div style="margin-top:8px;">
    {% for t in p.tags %}
      <span style="display:inline-block; padding:2px 10px; margin-right:6px; border:1px solid #eee; border-radius:999px; font-size:0.8rem; color:#555;">
        {{ t }}
      </span>
    {% endfor %}
  </div>
  {% endif %}
</div>

  {% endif %}
{% endfor %}
</ul>
