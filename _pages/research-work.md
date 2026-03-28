---
layout: projects
title: research
permalink: /research-work/
description: A curated selection of my academic and research contributions.
nav: true
nav_order: 3
horizontal: false
---

<div class="projects">
  {% assign visible_projects = site.projects | where_exp: "p", "p.published != false" %}
  {% assign research_projects = visible_projects | where: "research", true | sort: "time_order" | reverse %}

  {% if research_projects.size > 0 %}
    <h2 class="category category-bar mb-3 mt-0">Research Work</h2>
    <div class="row row-cols-1 row-cols-md-2">
      {% for project in research_projects %}
        {% include projects.liquid %}
      {% endfor %}
    </div>
  {% endif %}
</div>