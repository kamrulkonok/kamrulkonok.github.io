---
layout: projects
title: publications
permalink: /research-work/
description: Selected publications and research preprints in machine learning, retrieval-augmented generation, and applied AI.
nav: true
nav_order: 3
horizontal: false
---

<div class="projects">
  {% assign visible_projects = site.projects | where_exp: "p", "p.published != false" %}
  {% assign research_projects = visible_projects | where: "research", true | sort: "time_order" | reverse %}
  {% assign published_projects = research_projects | where: "publication_status", "published" %}
  {% assign preprint_projects = research_projects | where: "publication_status", "preprint" %}

  {% if published_projects.size > 0 %}
    <h2 class="category category-bar mb-3 mt-0">Selected Publications</h2>
    <div class="row row-cols-1 row-cols-md-2">
      {% for project in published_projects %}
        {% include projects.liquid %}
      {% endfor %}
    </div>
  {% endif %}

  {% if preprint_projects.size > 0 %}
    <h2 class="category category-bar mb-3 mt-5">Preprints</h2>
    <div class="row row-cols-1 row-cols-md-2">
      {% for project in preprint_projects %}
        {% include projects.liquid %}
      {% endfor %}
    </div>
  {% endif %}
</div>