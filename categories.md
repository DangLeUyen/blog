---
layout: default
title: Categories
permalink: /categories/
---

{% assign sorted_categories = site.categories | sort %}

{% for category in sorted_categories %}
<section id="{{ category[0] | slugify }}" class="category-section">
  <h2>{{ category[0] }}</h2>

  {% assign posts = category[1] | sort: "date" | reverse %}

  {% for post in posts %}
    <article class="post-preview">
      <h3>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h3>

      <p class="post-meta">
        {{ post.date | date: "%B %-d, %Y" }}
      </p>

      {{ post.excerpt }}
    </article>
  {% endfor %}
</section>
{% endfor %}

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
