---
layout: page
title: researchs
header_title: Research Projects and Explorations
permalink: /projects/
description: A selection of the astronomy work, analysis tools, and side experiments I have been building.
nav: true
nav_order: 2
display_categories: [Astronomy, Fun]
horizontal: false
social: true
---

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <div class="category-nav" aria-label="Project categories">
    {% for category in page.display_categories %}
      {% assign section_id = category | slugify %}
      <a href="#{{ section_id }}">{{ category }}</a>
    {% endfor %}
  </div>

  <!-- Display categorized projects -->

{% for category in page.display_categories %}
{% assign section_id = category | slugify %}
<a id="{{ section_id }}" href="#{{ section_id }}">

<h2 class="category">{{ category }}</h2>
</a>
{% assign categorized_projects = site.projects | where: "category", category %}
{% assign sorted_projects = categorized_projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% if sorted_projects.size == 0 %}
  <p class="category-empty">Projects in this category will appear here soon.</p>
  {% endif %}
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
