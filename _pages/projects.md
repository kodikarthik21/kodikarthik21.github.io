---
layout: page
title: projects
permalink: /projects/
description: Robotics and machine learning projects. Recent work up top, earlier projects below.
nav: true
nav_order: 3
display_categories: [recent, past]
horizontal: false
---

<style>
  .publications h2.bibliography { display: none; }
  .publications ol.bibliography { margin-top: 0; }
</style>

<div class="projects">

  <!-- RECENT: card grid (existing behavior) -->
  {% assign recent_projects = site.projects | where: "category", "recent" | sort: "importance" %}
  <a id="recent" href=".#recent"><h2 class="category">recent</h2></a>
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in recent_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>

  <!-- PAST: inline accordion list, no separate pages -->
  <a id="past" href=".#past"><h2 class="category">past</h2></a>
  {% assign past_projects = site.projects | where: "category", "past" | sort: "importance" %}
  <div class="past-projects-list">
    {% for project in past_projects %}
    <div class="past-project-entry">
      <div class="past-project-header">
        <div class="past-project-left">
          <div class="past-project-title-row">
            <span class="past-project-title">{{ project.title }}</span>
            {% if project.github %}
              <a href="https://github.com/{{ project.github }}" target="_blank">
                <i class="fab fa-github"></i>
              </a>
            {% endif %}
          </div>
          {% if project.advisor %}
            <div class="past-project-advisor">{{ project.advisor }}</div>
          {% endif %}
          <!-- {% for tag in project.tags %}
            <span class="past-project-tag">{{ tag }}</span>
          {% endfor %} -->
        </div>
        {% if project.date_range %}
          <span class="past-project-date">{{ project.date_range }}</span>
        {% endif %}
      </div>
      <div class="past-project-body">
        {{ project.content }}
      </div>
    </div>
    {% endfor %}
  </div>

</div>
<h2 class="category">publications</h2>
<div class="publications">
  {% bibliography %}
</div>
