---
layout: default
title: Awesome Open-Source Tools
---

<style>
  /* ===== CSS Variables for Light/Dark Mode ===== */
  :root {
    --bg-color: #ffffff;
    --text-color: #24292f;
    --card-bg: #f6f8fa;
    --card-border: #d0d7de;
    --footer-color: #57606a;
    --input-border: #d0d7de;
    --header-border: #d0d7de;
    --shadow-color: rgba(0,0,0,0.1);
  }

  /* Dark Mode Variables */
  body.dark-mode {
    --bg-color: #0d1117;
    --text-color: #c9d1d9;
    --card-bg: #161b22;
    --card-border: #30363d;
    --footer-color: #8b949e;
    --input-border: #30363d;
    --header-border: #30363d;
    --shadow-color: rgba(0,0,0,0.4);
  }

  /* Apply variables to elements */
  body {
    background-color: var(--bg-color);
    color: var(--text-color);
    transition: background-color 0.3s ease, color 0.3s ease;
  }

  .project-card {
    background: var(--card-bg);
    border-color: var(--card-border);
    transition: background-color 0.3s ease, border-color 0.3s ease, transform 0.2s ease, box-shadow 0.2s ease;
  }

  /* Force card text to use the dynamic color */
  .project-card h3,
  .project-card p {
    color: var(--text-color);
  }

  .project-card:hover {
    box-shadow: 0 8px 24px var(--shadow-color);
  }

  footer {
    border-top-color: var(--card-border) !important;
    color: var(--footer-color) !important;
  }

  #searchInput {
    background: var(--card-bg);
    color: var(--text-color);
    border-color: var(--input-border) !important;
  }

  .category-header {
    border-bottom-color: var(--card-border) !important;
  }

  .anchor-link {
    color: var(--footer-color) !important;
  }

  .anchor-link:hover {
    color: #2da44e !important;
  }

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

  /* Back to Top Button Styles */
  #backToTopBtn {
    position: fixed;
    bottom: 30px;
    right: 30px;
    z-index: 99;
    background: #2da44e;
    color: white;
    border: none;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    font-size: 24px;
    cursor: pointer;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    transition: opacity 0.3s ease, transform 0.3s ease;
    opacity: 0;
    transform: translateY(20px);
    pointer-events: none;
  }

  #backToTopBtn.show {
    opacity: 1;
    transform: translateY(0);
    pointer-events: auto;
  }

  #backToTopBtn:hover {
    background: #1c7e3a;
    transform: scale(1.1);
  }

  /* Clickable Category Link Styles */
  .category-header {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    margin-top: 2rem;
    margin-bottom: 1rem;
    border-bottom: 2px solid #d0d7de;
    padding-bottom: 0.5rem;
  }

  .category-header h2 {
    margin: 0;
    border-bottom: none;
    padding-bottom: 0;
  }

  .anchor-link {
    color: #8b949e;
    text-decoration: none;
    font-size: 1.2rem;
    transition: color 0.2s ease;
    opacity: 0.5;
  }

  .anchor-link:hover {
    color: #2da44e;
    opacity: 1;
  }

  /* ===== Dark Mode Toggle Switch ===== */
  .theme-toggle-wrapper {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    gap: 10px;
    margin-bottom: 1rem;
    font-size: 0.9rem;
    color: var(--footer-color);
  }

  .toggle-switch {
    position: relative;
    width: 50px;
    height: 26px;
    background: #d0d7de;
    border-radius: 50px;
    cursor: pointer;
    transition: background 0.3s ease;
    flex-shrink: 0;
  }

  body.dark-mode .toggle-switch {
    background: #30363d;
  }

  .toggle-switch::after {
    content: '';
    position: absolute;
    top: 3px;
    left: 3px;
    width: 20px;
    height: 20px;
    background: white;
    border-radius: 50%;
    transition: transform 0.3s ease;
    box-shadow: 0 2px 4px rgba(0,0,0,0.2);
  }

  body.dark-mode .toggle-switch::after {
    transform: translateX(24px);
    background: #f0f6fc;
  }

  .theme-icon {
    font-size: 1.1rem;
    line-height: 1;
  }
</style>

<!-- ===== Dark Mode Toggle ===== -->
<div class="theme-toggle-wrapper">
  <span class="theme-icon">☀️</span>
  <div class="toggle-switch" id="themeToggle" role="button" aria-label="Toggle dark mode"></div>
  <span class="theme-icon">🌙</span>
</div>

<input type="text" id="searchInput" placeholder="🔍 Search for a tool..." style="width:100%; padding:12px; font-size:16px; border:1px solid #d0d7de; border-radius:6px; margin-bottom:1.5rem;">

<div style="text-align: center; margin-bottom: 1.5rem;">
  <span style="display: inline-block; background: #2da44e; color: white; padding: 6px 16px; border-radius: 20px; font-size: 0.9rem; font-weight: 500;">
    ⭐ {{ site.data.projects | size }} awesome tools
  </span>
</div>

{% assign categories = site.data.projects | group_by: "category" | sort: "name" %}

{% for category in categories %}
  {% assign category_id = category.name | slugify %}
  <div class="category-header">
    <h2 id="{{ category_id }}">{{ category.name }}</h2>
    <a href="#{{ category_id }}" class="anchor-link" title="Copy link to this category">🔗</a>
  </div>
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

<footer style="margin-top: 3rem; padding-top: 1.5rem; border-top: 1px solid #d0d7de; text-align: center; color: #57606a; font-size: 0.9rem;">
  <p>
    Have a suggestion for another awesome open-source tool?
    <a href="https://github.com/iclubu/awesome-open-source-tools/issues" target="_blank" style="color: #2da44e; text-decoration: none; font-weight: 500;">
      Submit it here →
    </a>
  </p>
  <p style="margin-top: 0.5rem; font-size: 0.8rem;">
    Built with ❤️ on GitHub Pages
  </p>
</footer>

<!-- Back to Top Button HTML -->
<button id="backToTopBtn" title="Back to top">↑</button>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    const searchInput = document.getElementById('searchInput');
    const cards = document.querySelectorAll('.project-card');
    const backToTopBtn = document.getElementById('backToTopBtn');
    const themeToggle = document.getElementById('themeToggle');

    // === Dark Mode Toggle ===
    // Check for saved preference
    const currentTheme = localStorage.getItem('theme');
    if (currentTheme === 'dark') {
      document.body.classList.add('dark-mode');
    }

    // Toggle on click
    themeToggle.addEventListener('click', function() {
      document.body.classList.toggle('dark-mode');
      // Save preference
      if (document.body.classList.contains('dark-mode')) {
        localStorage.setItem('theme', 'dark');
      } else {
        localStorage.setItem('theme', 'light');
      }
    });

    // === Search functionality ===
    searchInput.addEventListener('keyup', function() {
      const query = this.value.toLowerCase();
      cards.forEach(card => {
        const text = card.textContent.toLowerCase();
        card.style.display = text.includes(query) ? '' : 'none';
      });
    });

    // === Back to Top functionality ===
    window.addEventListener('scroll', function() {
      if (window.scrollY > 300) {
        backToTopBtn.classList.add('show');
      } else {
        backToTopBtn.classList.remove('show');
      }
    });

    backToTopBtn.addEventListener('click', function() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth'
      });
    });
  });
</script>
