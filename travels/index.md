---
layout: default
title: Travel Journal
permalink: /travels/
---

# Travel Journal

A growing archive of trips.

<ul>
{% assign travel_pages = site.pages | where_exp: "p", "p.path contains 'travels/'" %}
{% for p in travel_pages %}
  {% if p.title and p.url != page.url %}
  • <a href="{{ p.url }}">{{ p.title }}</a>
    {% if p.date %} — {{ p.date | date: "%Y" }}{% endif %}
  {% endif %}
{% endfor %}

</ul>
