---
layout: default
title: Awesome Open-Source Tools
---

# 🚀 Awesome Open-Source Tools
A curated list of useful open-source projects for developers, creators, and privacy-conscious users.

<div class="projects-grid">
  {% for project in site.data.projects %}
    <div class="project-card">
      <h3>{{ project.name }}</h3>
      <p>{{ project.description }}</p>
      <p><strong>License:</strong> {{ project.license }}</p>
      <a href="{{ project.url }}" target="_blank" class="btn">View on GitHub →</a>
    </div>
  {% endfor %}
</div>
