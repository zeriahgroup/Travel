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

### {{ year }}
<hr>

      {% assign current_year = year %}
    {% endif %}

<div style="margin-bottom:1.2rem;">
  <strong>
    <a href="{{ p.url }}">{{ p.title }}</a>
  </strong><br>
  <span style="color:#666; font-size:0.9rem;">
    {{ p.date | date: "%b %Y" }}
  </span>
</div>

  {% endif %}
{% endfor %}

</ul>
