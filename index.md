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
          {% if item.project_url %}
          <a href="{{ item.project_url }}" target="_blank" rel="noopener noreferrer" class="card-link" style="margin-top: 0.25rem; color: var(--accent-secondary, var(--primary)); font-size: 0.85rem;">
            📋 Project Board
            <svg viewBox="0 0 24 24" fill="currentColor" style="width: 14px; height: 14px;">
              <path d="M14 3v2h3.59l-9.83 9.83 1.41 1.41L19 6.41V10h2V3m-2 16H5V5h7V3H5a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7h-2v7z"/>
            </svg>
          </a>
          {% endif %}
        </div>
      {% endfor %}
    {% else %}
      <div class="card" style="grid-column: 1 / -1; align-items: center; justify-content: center; padding: 3rem; text-align: center;">
        <p style="margin: 0; color: var(--text-muted);">No application documents found in the <code>_apps/</code> collection.</p>
      </div>
    {% endif %}
  </div>
</section>

<!-- Project Management Section -->
<section id="projects" style="margin-bottom: 3.5rem; scroll-margin-top: 80px;">
  <h2>Project Management & Task Monitoring</h2>
  <p>Track project progress, task assignments, and team member workload through our centralized GitHub Project board.</p>

  <div class="card-grid" style="grid-template-columns: 1fr;">
    <div class="card" style="padding: 2rem;">
      <div style="display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem;">
        <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="var(--primary)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
          <rect x="3" y="3" width="7" height="7" rx="1"/>
          <rect x="14" y="3" width="7" height="7" rx="1"/>
          <rect x="14" y="14" width="7" height="7" rx="1"/>
          <rect x="3" y="14" width="7" height="7" rx="1"/>
        </svg>
        <div>
          <h3 style="margin: 0; color: var(--text-primary);">Laporan Keuangan — Development Board</h3>
          <p style="margin: 0.25rem 0 0; font-size: 0.9rem; color: var(--text-secondary);">Kanban-style project board tracking all tasks, bugs, and feature requests across Backend & Frontend.</p>
        </div>
      </div>
      <div style="display: flex; flex-wrap: wrap; gap: 0.75rem; margin-bottom: 1.25rem;">
        <span class="badge badge-primary" style="font-size: 0.8rem; padding: 0.35rem 0.75rem;">📌 Task Tracking</span>
        <span class="badge badge-success" style="font-size: 0.8rem; padding: 0.35rem 0.75rem;">👥 Team Assignments</span>
        <span class="badge badge-warning" style="font-size: 0.8rem; padding: 0.35rem 0.75rem;">📊 Sprint Progress</span>
      </div>
      <a href="https://github.com/users/fahmiyuda31/projects/7" target="_blank" rel="noopener noreferrer" class="card-link">
        Open Project Board
        <svg viewBox="0 0 24 24" fill="currentColor" style="width: 16px; height: 16px;">
          <path d="M14 3v2h3.59l-9.83 9.83 1.41 1.41L19 6.41V10h2V3m-2 16H5V5h7V3H5a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7h-2v7z"/>
        </svg>
      </a>
    </div>
  </div>
</section>
