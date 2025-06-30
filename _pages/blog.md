---
layout: default
permalink: /blog/
title: Articoli
nav: true
nav_order: 1
pagination:
  enabled: true
  collection: posts
  permalink: /page/:num/
  per_page: 5
  sort_field: date
  sort_reverse: true
  trail:
    before: 1
    after: 3
---

<div class="post">

  {% assign blog_name_size = site.blog_name | size %}
  {% assign blog_description_size = site.blog_description | size %}

  {% if blog_name_size > 0 or blog_description_size > 0 %}
    <div class="header-bar">
      <h1>{{ site.blog_name }}</h1>
      <h2>{{ site.blog_description }}</h2>
    </div>
  {% endif %}

  <div class="row">
    <!-- Sidebar sinistra -->
    <div class="col-md-3 mb-4" style="border-right: 1px solid #ddd; padding-right: 1rem;">
      {% if site.display_tags and site.display_tags.size > 0 %}
        <div class="mb-4">
          <h4>Tag</h4>
          <ul class="list-unstyled">
            {% for tag in site.display_tags %}
              <li>
                <i class="fa-solid fa-hashtag fa-sm"></i>
                <a href="{{ tag | slugify | prepend: '/blog/tag/' | relative_url }}">{{ tag }}</a>
              </li>
            {% endfor %}
          </ul>
        </div>
      {% endif %}

      {% if site.display_categories and site.display_categories.size > 0 %}
        <div class="mb-4">
          <h4>Categorie</h4>
          <ul class="list-unstyled">
            {% for category in site.display_categories %}
              <li>
                <i class="fa-solid fa-tag fa-sm"></i>
                <a href="{{ category | slugify | prepend: '/blog/category/' | relative_url }}">{{ category }}</a>
              </li>
            {% endfor %}
          </ul>
        </div>
      {% endif %}
    </div>

    <!-- Contenuto principale: post -->
    <div class="col-md-9">
      <ul class="post-list">
        {% if page.pagination.enabled %}
          {% assign postlist = paginator.posts %}
        {% else %}
          {% assign postlist = site.posts %}
        {% endif %}

        {% for post in postlist %}
          {% unless post.hidden or post.redirect %}
            {% if post.external_source == blank %}
              {% assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 %}
            {% else %}
              {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
            {% endif %}
            {% assign year = post.date | date: "%Y" %}
            {% assign tags = post.tags | join: "" %}
            {% assign categories = post.categories | join: "" %}

            <li>
              {% if post.thumbnail %}
                <div class="row">
                  <div class="col-sm-9">
              {% endif %}

              <h3>
                <a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
              </h3>

              <p>{{ post.description }}</p>
              <p class="post-meta">
                {{ read_time }} min read &nbsp; &middot; &nbsp;
                {{ post.date | date: '%B %d, %Y' }}
                {% if post.external_source %}
                  &nbsp; &middot; &nbsp; {{ post.external_source }}
                {% endif %}
              </p>

              <p class="post-tags">
                <a href="{{ year | prepend: '/blog/' | relative_url }}">
                  <i class="fa-solid fa-calendar fa-sm"></i> {{ year }}
                </a>

                {% if tags != "" %}
                  &nbsp; &middot; &nbsp;
                  {% for tag in post.tags %}
                    <a href="{{ tag | slugify | prepend: '/blog/tag/' | relative_url }}">
                      <i class="fa-solid fa-hashtag fa-sm"></i> {{ tag }}</a>
                    {% unless forloop.last %}&nbsp;{% endunless %}
                  {% endfor %}
                {% endif %}

                {% if categories != "" %}
                  &nbsp; &middot; &nbsp;
                  {% for category in post.categories %}
                    <a href="{{ category | slugify | prepend: '/blog/category/' | relative_url }}">
                      <i class="fa-solid fa-tag fa-sm"></i> {{ category }}</a>
                    {% unless forloop.last %}&nbsp;{% endunless %}
                  {% endfor %}
                {% endif %}
              </p>

              {% if post.thumbnail %}
                  </div>
                  <div class="col-sm-3">
                    <img class="card-img" src="{{ post.thumbnail | relative_url }}" style="object-fit: cover; height: 90%" alt="image">
                  </div>
                </div>
              {% endif %}
            </li>
          {% endunless %}
        {% endfor %}
      </ul>

      {% if page.pagination.enabled %}
        {% include pagination.liquid %}
      {% endif %}
    </div>
  </div>
</div>


