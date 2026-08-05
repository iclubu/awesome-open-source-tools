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
</style>

<input type="text" id="searchInput" placeholder="🔍 Search for a tool..." style="width:100%; padding:12px; font-size:16px; border:1px solid #d0d7de; border-radius:6px; margin-bottom:1.5rem;">

<div style="text-align: center; margin-bottom: 1.5rem;">
  <span style="display: inline-block; background: #2da44e; color: white; padding: 6px 16px; border-radius: 20px; font-size: 0.9rem; font-weight: 500;">
    ⭐ {{ site.data.projects | size }} awesome tools
  </span>
</div>

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

    // Search functionality
    searchInput.addEventListener('keyup', function() {
      const query = this.value.toLowerCase();
      cards.forEach(card => {
        const text = card.textContent.toLowerCase();
        card.style.display = text.includes(query) ? '' : 'none';
      });
    });

    // Back to Top functionality
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
