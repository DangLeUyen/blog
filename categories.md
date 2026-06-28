---
layout: default
title: Categories
permalink: /categories/
---

{% assign category_name = page.category %}

{% for post in site.categories[category_name] %}
<article class="post-card">
  <h2>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
  </h2>

  <p class="post-meta">
    {{ post.date | date: "%B %-d, %Y" }}
  </p>

  <p>{{ post.excerpt | strip_html | truncate: 180 }}</p>

  <a href="{{ post.url | relative_url }}">Read more →</a>
</article>
{% endfor %}
