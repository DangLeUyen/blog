---
layout: default
title: Categories
permalink: /categories/
---
<ul class="blog-list">
  {% assign sorted_categories = site.categories | sort %}

  {% assign excerpt_length = site.excerpt_length | default: 180 %}
  {% for category in sorted_categories %}
    <section id="{{ category[0] | slugify }}" class="category-section">
      <h2>{{ category[0] }}</h2>
      {% assign posts = category[1] | sort: "date" | reverse %}
      {% for post in posts %}
        <li class="blog-item">
          <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
          <p class="blog-meta">
          <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time>
          </p>
          <p class="blog-excerpt">{{ post.excerpt | strip_html }}</p>
          <a href="{{ post.url | relative_url }}" class="read-more">Read more<span class="visually-hidden"> about {{ post.title }}</span> &rarr;</a>
        </li>
      {% endfor %}
  {% endfor %}
</ul>

<script>
document.addEventListener("DOMContentLoaded", function () {
    const hash = window.location.hash.substring(1);
    const sections = document.querySelectorAll(".category-section");

    if (hash) {
        sections.forEach(s => s.style.display = "none");

        const selected = document.getElementById(hash);
        if (selected) {
            selected.style.display = "block";
        }
    }
});
</script>
