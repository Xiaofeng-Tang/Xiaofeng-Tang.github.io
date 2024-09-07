---
page_id: profiles
layout: page
title: people
permalink: /profiles/
description: Members of out group.
nav: true
nav_order: 7
display_categories: [staff, phd, master,alumni]
horizontal: false
---

<div class="projects">
  {% if site.enable_project_categories and page.display_categories %}
    <!-- Display categorized projects -->
    {% for category in page.display_categories %}
      <a id="{{ site.data[site.active_lang].strings.categories[category] }}" href=".#{{ site.data[site.active_lang].strings.categories[category] }}">
        <h2 class="category">{{ site.data[site.active_lang].strings.categories[category] }}</h2>
      </a>
      {% assign categorized_profiles = site.profiles | where: "category", category %}
      {% assign sorted_profiles = categorized_profiles | sort: "importance" %}
      <!-- Generate cards for each project -->
      {% if page.horizontal %}
        <div class="container">
          <div class="row row-cols-1 row-cols-md-2">
            {% for profile in sorted_profiles %}
              {% include profiles_horizontal.liquid %}
            {% endfor %}
          </div>
        </div>
      {% else %}
        <div class="row row-cols-1 row-cols-md-3">
          {% for profile in sorted_profiles %}
            {% include profiles.liquid %}
          {% endfor %}
        </div>
      {% endif %}
    {% endfor %}
  {% else %}
    <!-- Display projects without categories -->
    {% assign sorted_profiles = site.profiles | sort: "importance" %}
    <!-- Generate cards for each project -->
    {% if page.horizontal %}
      <div class="container">
        <div class="row row-cols-1 row-cols-md-2">
          {% for profile in sorted_profiles %}
            {% include profiles_horizontal.liquid %}
          {% endfor %}
        </div>
      </div>
    {% else %}
      <div class="row row-cols-1 row-cols-md-3">
        {% for profile in sorted_profiles %}
          {% include profiles.liquid %}
        {% endfor %}
      </div>
    {% endif %}
  {% endif %}
</div>

