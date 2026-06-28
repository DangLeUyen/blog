---
layout: default
title: Categories
permalink: /categories/
---

{% assign sorted_categories = site.categories | sort %}

{% for category in sorted_categories %}
<div class="category-section"
     id="{{ category[0] | slugify }}">
  <h2>{{ category[0] }}</h2>

  <ul>
    {% assign posts = category[1] | sort: "date" | reverse %}
    {% for post in posts %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
    {% endfor %}
  </ul>
</div>
{% endfor %}

<script>
document.addEventListener("DOMContentLoaded", function () {
    const hash = window.location.hash.substring(1);

    if (!hash) return;

    document.querySelectorAll(".category-section").forEach(section => {
        section.style.display = "none";
    });

    const selected = document.getElementById(hash);
    if (selected) {
        selected.style.display = "block";
    }
});
</script>
