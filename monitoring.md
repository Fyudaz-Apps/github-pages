---
layout: default
title: Service Status Monitoring
permalink: /monitoring/
---

<div class="monitoring-container">
  <div>
    <h1>System Status &amp; Service Monitoring</h1>
    <p style="color: var(--text-secondary); margin-bottom: 1.5rem;">
      Real-time availability monitoring dashboard for IT department applications and infrastructure services. Powered by Uptime Kuma.
    </p>
  </div>

  <div class="iframe-wrapper">
    <!-- Loading spinner placeholder behind iframe -->
    <div class="loading-indicator">
      Connecting to status monitor...
    </div>
    
    <!-- Responsive Uptime Kuma Status Page Iframe -->
    <iframe 
      src="https://kuma.ravelware.cloud/" 
      title="Uptime Kuma Status Page"
      loading="lazy"
      allowtransparency="true"
      scrolling="yes"
      style="width: 100%; height: 100%; border: none;">
    </iframe>
  </div>
  
  <div style="margin-top: 1rem; padding: 1rem; background-color: var(--bg-secondary); border: 1px solid var(--border-color); border-radius: 8px; font-size: 0.9rem; color: var(--text-muted);">
    <strong>Note:</strong> Status updates are polled every 60 seconds automatically. If the panel fails to load, please verify VPN connection settings or contact the Infrastructure Operations team.
  </div>
</div>
