---
layout: page
title: Podcast
permalink: /podcast/
description: Collection of podcast
nav: true
nav_order: 4
display_categories: [work, fun]
horizontal: false
---

<style>
.card {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.card:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
}

.card-img-top {
  object-fit: cover;
  height: 180px;
  border-bottom: 1px solid #eee;
}
</style>


<div class="projects">
{% assign sorted_podcasts = site.podcast | where_exp: "item", "item.hidden != true" %}

{% if site.enable_project_categories and page.display_categories %}
  {% for category in page.display_categories %}
    <a id="{{ category | downcase }}" href=".#{{ category | downcase }}">
      <h2 class="category">{{ category }}</h2>
    </a>
    {% assign categorized_podcasts = sorted_podcasts | where: "category", category %}
    {% assign sorted_projects = categorized_podcasts | sort: "importance" %}

    {% if page.horizontal %}
      <div class="container">
        <div class="row row-cols-1 row-cols-md-2">
          {% for project in sorted_projects %}
            {% include podcast_card_horizontal.liquid post=project %}
          {% endfor %}
        </div>
      </div>
    {% else %}
      <div class="row row-cols-1 row-cols-md-3">
        {% for project in sorted_projects %}
          {% include podcast_card.liquid post=project %}
        {% endfor %}
      </div>
    {% endif %}
  {% endfor %}
{% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% assign sorted_projects = sorted_podcasts | sort: "importance" %}
    {% for project in sorted_projects %}
      {% include podcast_card.liquid post=project %}
    {% endfor %}
  </div>
{% endif %}
</div>
