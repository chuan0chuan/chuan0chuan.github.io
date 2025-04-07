---
layout: page
title: AI-Design
permalink: /projects/
description: 
nav: true
nav_order: 6
display_categories: [work, fun]
horizontal: True
---

<!-- pages/projects.md -->
<div class="projects">
  {% if site.enable_project_categories and page.display_categories %}
    {% for category in page.display_categories %}
      {% if category == "work" %}
        {% assign limit = 2 %}
      {% elsif category == "fun" %}
        {% assign limit = 0 %}
      {% else %}
        {% assign limit = 100 %}
      {% endif %}

      {% if limit > 0 %}
        <a id="{{ category }}" href=".#{{ category }}">
          <h2 class="category">{{ category }}</h2>
        </a>

        {% assign categorized_projects = site.projects | where: "category", category | sort: "importance" | slice: 0, limit %}

        <!-- Generate cards for each project -->
        {% if page.horizontal %}
          <div class="container">
            <div class="row row-cols-1 row-cols-md-2">
              {% for project in categorized_projects %}
                {% include projects_horizontal.liquid %}
              {% endfor %}
            </div>
          </div>
        {% else %}
          <div class="row row-cols-1 row-cols-md-3">
            {% for project in categorized_projects %}
               {% include projects.liquid show_description=false %}
            {% endfor %}
          </div>
        {% endif %}
      {% endif %}
    {% endfor %}
  {% endif %}
</div>
