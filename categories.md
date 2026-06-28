---
layout: default
title: Categories
permalink: /categories/
---

{% assign sorted_categories = site.categories | sort %}

{% for category in sorted_categories %}
<section class="category-section"
         id="{{ category[0] | slugify }}">

  <h2>{{ category[0] }}</h2>

  {% assign posts = category[1] | sort: "date" | reverse %}

  {% for post in posts %}
    <article class="post-card">
      <h3>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h3>
    </article>
  {% endfor %}

</section>
{% endfor %}
