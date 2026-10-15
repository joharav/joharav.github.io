---
layout: archive
title: "Sitemap"
permalink: /sitemap/
author_profile: true
sitemap: false
noindex: true
---

{% include base_path %}

A list of the published pages on this site. An [XML version]({{ base_path }}/sitemap.xml) is also available.

<h2>Pages</h2>
{% assign published_pages = site.html_pages | where_exp: 'item', 'item.sitemap != false' | where_exp: 'item', 'item.noindex != true' %}
<ul>
{% for item in published_pages %}
  <li><a href="{{ item.url | relative_url }}">{{ item.title | default: site.title | escape }}</a></li>
{% endfor %}
</ul>
