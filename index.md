---
layout: default
title: Home Dashboard
permalink: /
---

<!-- Welcoming Hero Section -->
<section class="hero">
  <h1 class="hero-title">IT Software Development Portal</h1>
  <p class="hero-subtitle">
    Welcome to the centralized internal portal for our engineering department. Here you can find standard operating procedures, dynamically aggregated microservices and system documentations, and real-time environment health dashboards.
  </p>
</section>

<!-- Introduction and Overview -->
<section style="margin-bottom: 3.5rem;">
  <h2>About the Portal</h2>
  <p>
    This portal is built as a static site generated via Jekyll and hosted on GitHub Pages. It acts as a single source of truth for the software development department by integrating multiple sources of information:
  </p>
  <div class="card-grid" style="grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));">
    <div class="card" style="padding: 1.25rem;">
      <h3 style="margin-top: 0; color: var(--primary);">Standard Operating Procedures</h3>
      <p style="font-size: 0.9rem; margin-bottom: 0;">Maintained directly in this repository to define release workflows, coding standards, environment access protocols, and incident response guidelines.</p>
    </div>
    <div class="card" style="padding: 1.25rem;">
      <h3 style="margin-top: 0; color: var(--success);">Repository Documentation Sync</h3>
      <p style="font-size: 0.9rem; margin-bottom: 0;">Dynamically pulled from autonomous repositories. GitHub Actions in external repos automatically compile, prepend front-matter metadata, and sync updates directly to this site.</p>
    </div>
    <div class="card" style="padding: 1.25rem;">
      <h3 style="margin-top: 0; color: var(--warning);">Continuous Health Checks</h3>
      <p style="font-size: 0.9rem; margin-bottom: 0;">Embeds active service level monitoring dashboards (Uptime Kuma) for transparent engineering reporting on system availability and uptime stats.</p>
    </div>
  </div>
</section>

<!-- Global SOPs Section -->
<section id="sops" style="margin-bottom: 3.5rem; scroll-margin-top: 80px;">
  <h2>Global Standard Operating Procedures (SOPs)</h2>
  <p>Department-wide standards and step-by-step guides for deployment, system architecture, security guidelines, and development guidelines.</p>

  <div class="card-grid">
    {% if site.sop.size > 0 %}
      {% for item in site.sop %}
        <div class="card">
          <div class="card-title">
            {{ item.title }}
            {% if item.category %}
              <span class="badge badge-primary">{{ item.category }}</span>
            {% endif %}
          </div>
          <div class="card-meta">
            {% if item.author %}
              <span>By: {{ item.author }}</span>
            {% endif %}
            {% if item.last_updated %}
              <span>Updated: {{ item.last_updated }}</span>
            {% endif %}
          </div>
          <p class="card-desc">
            {% if item.description %}
              {{ item.description }}
            {% else %}
              {{ item.content | strip_html | truncatewords: 25 }}
            {% endif %}
          </p>
          <a href="{{ item.url | relative_url }}" class="card-link">
            Read SOP
            <svg viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 4l-1.41 1.41L16.17 11H4v2h12.17l-5.58 5.59L12 20l8-8z"/>
            </svg>
          </a>
        </div>
      {% endfor %}
    {% else %}
      <div class="card" style="grid-column: 1 / -1; align-items: center; justify-content: center; padding: 3rem; text-align: center;">
        <p style="margin: 0; color: var(--text-muted);">No SOP documents found in the <code>_sop/</code> collection.</p>
      </div>
    {% endif %}
  </div>
</section>

<!-- App Documentations Section -->
<section id="apps" style="margin-bottom: 3.5rem; scroll-margin-top: 80px;">
  <h2>Application Documentations</h2>
  <p>Technical specifications, README files, and architecture overviews synced from various microservices, backend apps, and frontend repositories.</p>

  <div class="card-grid">
    {% if site.apps.size > 0 %}
      {% for item in site.apps %}
        <div class="card">
          <div class="card-title">
            {{ item.title }}
            {% if item.status %}
              <span class="badge {% if item.status == 'active' or item.status == 'stable' %}badge-success{% elsif item.status == 'deprecated' %}badge-danger{% else %}badge-warning{% endif %}">
                {{ item.status }}
              </span>
            {% endif %}
          </div>
          <div class="card-meta">
            {% if item.repo_name %}
              <span>Repo: <code>{{ item.repo_name }}</code></span>
            {% endif %}
            {% if item.version %}
              <span>v{{ item.version }}</span>
            {% endif %}
          </div>
          <p class="card-desc">
            {% if item.description %}
              {{ item.description }}
            {% else %}
              {{ item.content | strip_html | truncatewords: 25 }}
            {% endif %}
          </p>
          <a href="{{ item.url | relative_url }}" class="card-link">
            View Docs
            <svg viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 4l-1.41 1.41L16.17 11H4v2h12.17l-5.58 5.59L12 20l8-8z"/>
            </svg>
          </a>
        </div>
      {% endfor %}
    {% else %}
      <div class="card" style="grid-column: 1 / -1; align-items: center; justify-content: center; padding: 3rem; text-align: center;">
        <p style="margin: 0; color: var(--text-muted);">No application documents found in the <code>_apps/</code> collection.</p>
      </div>
    {% endif %}
  </div>
</section>
