---
layout: default
title: Categories
permalink: /categories/
---

Browse all posts by category.

<ul class="category-post-list">
{% assign posts = category[0] | sort: "date" | reverse %}
{% for post in posts %}
  <li>
    <a href="{{ post.url | relative_url }}">
      {{ post.title }}
    </a>
    <small style="color:#777;">
      {{ post.date | date: "%b %d, %Y" }}
    </small>
  </li>
{% endfor %}
</ul>
