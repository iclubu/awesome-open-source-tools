---
layout: default
title: Awesome Open-Source Tools
---

<style>
  /* Fix header title and subtitle sizes */
  .project-name {
    font-size: 3rem !important;
    margin-bottom: 0.1rem !important;
  }
  .project-tagline {
    font-size: 1.25rem !important;
    font-weight: 300 !important;
    opacity: 0.8 !important;
    margin-top: 0 !important;
  }
</style>

<input type="text" id="searchInput" placeholder="🔍 Search for a tool..." style="width:100%; padding:12px; font-size:16px; border:1px solid #d0d7de; border-radius:6px; margin-bottom:1.5rem;">

{% assign categories = site.data.projects | group_by: "category" | sort: "name" %}

{% for category in categories %}
  <h2 style="margin-top: 2rem; margin-bottom: 1rem; border-bottom: 2px solid #d0d7de; padding-bottom: 0.5rem;">
    {{ category.name }}
  </h2>
  <div class="projects-grid">
    {% for project in category.items %}
      <div class="project-card">
        <h3>{{ project.name }}</h3>
        <p>{{ project.description }}</p>
        <p><strong>License:</strong> {{ project.license }}</p>
        <a href="{{ project.url }}" target="_blank" class="btn">View on GitHub →</a>
      </div>
    {% endfor %}
  </div>
{% endfor %}

<script>
  document.addEventListener('DOMContentLoaded', function() {
    const searchInput = document.getElementById('searchInput');
    const cards = document.querySelectorAll('.project-card');

    searchInput.addEventListener('keyup', function() {
      const query = this.value.toLowerCase();
      cards.forEach(card => {
        const text = card.textContent.toLowerCase();
        card.style.display = text.includes(query) ? '' : 'none';
      });
    });
  });
</script>
