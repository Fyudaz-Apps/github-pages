---
layout: default
title: Service Status Monitoring
permalink: /monitoring/
---

<div class="monitoring-container">
  <div>
    <h1>System Status & Service Monitoring</h1>
    <p style="color: var(--text-secondary); margin-bottom: 1.5rem;">
      Real-time availability monitoring dashboard for IT department applications and infrastructure services. Powered by Uptime Kuma.
    </p>
  </div>

  <div style="display: flex; flex-direction: column; align-items: center; gap: 1.5rem; padding: 3rem 2rem; background: var(--bg-secondary); border: 1px solid var(--border-color); border-radius: 12px; text-align: center;">
    <svg xmlns="http://www.w3.org/2000/svg" width="64" height="64" viewBox="0 0 24 24" fill="none" stroke="var(--accent-primary)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
      <path d="M22 12h-4l-3 9L9 3l-3 9H2"/>
    </svg>
    <h2 style="margin: 0; color: var(--text-primary);">Uptime Kuma Dashboard</h2>
    <p style="margin: 0; color: var(--text-secondary); max-width: 500px;">
      Click the button below to access the full monitoring dashboard with real-time service status, uptime history, and incident logs.
    </p>
    <a href="https://kuma.ravelware.cloud/" target="_blank" rel="noopener noreferrer" 
       style="display: inline-flex; align-items: center; gap: 0.5rem; padding: 0.85rem 2rem; background: var(--accent-primary); color: #fff; text-decoration: none; border-radius: 8px; font-weight: 600; font-size: 1.05rem; transition: all 0.2s ease;">
      Open Monitoring Dashboard
      <svg viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
        <path d="M14 3v2h3.59l-9.83 9.83 1.41 1.41L19 6.41V10h2V3m-2 16H5V5h7V3H5a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7h-2v7z"/>
      </svg>
    </a>
  </div>

  <div style="margin-top: 1rem; padding: 1rem; background-color: var(--bg-secondary); border: 1px solid var(--border-color); border-radius: 8px; font-size: 0.9rem; color: var(--text-muted);">
    <strong>Note:</strong> The monitoring dashboard requires authentication. Contact the Infrastructure Operations team if you need access credentials.
  </div>
</div>
