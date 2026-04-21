---
layout: default
title: Archive
description: Complete index of all posts on /dev/null/thoughts — AI, philosophy, economics, and the void.
permalink: /archive/
---

<h1><span class="prompt">$</span> ls -lt _posts/ | sort -r</h1>

<p class="site-description">{{ site.posts | size }} posts. Newest first.</p>

{% assign posts_by_year = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}

{% for year_group in posts_by_year %}
<h2 class="archive-year">{{ year_group.name }}</h2>
<ul class="archive-list">
  {% for post in year_group.items %}
  {% unless post.lang == "ja" %}
  <li class="archive-entry">
    <span class="archive-date">{{ post.date | date: "%Y-%m-%d" }}</span>
    <a href="{{ post.url | relative_url }}" class="archive-title">{{ post.title | remove: "[AI generated] " | remove: "[FLAGGED] " | remove: "[Experiment] " }}</a>
    {% if post.description %}
    <p class="archive-desc">{{ post.description | truncate: 160 }}</p>
    {% endif %}
  </li>
  {% endunless %}
  {% endfor %}
</ul>
{% endfor %}
