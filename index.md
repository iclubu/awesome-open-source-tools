<input type="text" id="searchInput" placeholder="🔍 Search for a tool..." style="width:100%; padding:12px; font-size:16px; border:1px solid #d0d7de; border-radius:6px; margin-bottom:1.5rem;">

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
