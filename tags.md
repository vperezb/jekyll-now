﻿---
layout: default
title: Tags
permalink: /tags/
---

<h2>Tags</h2>
<ul>
{% assign categories_list = site.tags %}
  {% if categories_list.first[0] == null %}
    {% for category in categories_list %}
		{% unless site.tags[tags] contains 'cooking' %}
      <li><a href="#{{ category }}">{{ category | capitalize }} ({{ site.tags[tags].size }})</a></li>
		{% endunless %}
    {% endfor %}
  {% else %}
    {% for category in categories_list %}
      <li><a href="#{{ tag[0] }}">{{ category[0] | capitalize }} ({{ category[1].size }})</a></li>
    {% endfor %}
  {% endif %}
{% assign categories_list = nil %}
</ul>

{% for tag in site.tags %}
  <h3 id="{{ tag[0] }}">{{ tag[0] | capitalize }}</h3>
  <ul>
    {% assign pages_list = tag[1] %}
    {% for post in pages_list %}
      {% if post.title != null %}
      {% if group == null or group == post.group %}
      <li><a href="{{ site.url }}{{ post.url }}">{{ post.title }}<span class="entry-date"> - <time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%B %d, %Y" }}</time></span></a></li>
      {% endif %}
      {% endif %}
    {% endfor %}
    {% assign pages_list = nil %}
    {% assign group = nil %}
  </ul>
{% endfor %}