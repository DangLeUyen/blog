---
layout: default
title: Categories
permalink: /categories/
---

Browse all posts by category.

{% assign sorted_categories = site.categories | sort %}

{% for category in sorted_categories %}
  <h2 id="{{ category[0] | slugify }}">
    {{ category[0] }}
  </h2>

  <ul class="category-post-list">
    {% assign posts = category[1] | sort: "date" | reverse %}
    {% for post in posts %}
      <li>
        <a href="{{ post.url | relative_url }}">
          {{ post.title }}
        </a>
        <small>{{ post.date | date: "%b %d, %Y" }}</small>
      </li>
    {% endfor %}
  </ul>
{% endfor %}
