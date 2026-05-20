---
layout: default
title: Github Pages
description: Technical specifications and developer guide for github-pages.
repo_name: github-pages
status: active
version: 1.0.0
author: Automated Sync
last_updated: "2026-05-20"
---

# IT Software Development Department Portal

A centralized static documentation and service monitoring portal built with [Jekyll](https://jekyllrb.com/) and optimized for deployment on **GitHub Pages**.

---

## 🚀 Key Features

1. **Global SOPs:** A dedicated space in the repository (`_sop/`) to write development team Standard Operating Procedures in Markdown.
2. **App Documentations:** A collection (`_apps/`) that dynamically integrates documentation (e.g. README files) synced from other separate service repositories.
3. **Uptime Kuma Monitoring:** Integrated status page link to access live microservice availability dashboard.
4. **Project Task Monitoring:** Quick access links to the GitHub Projects task board directly from individual application cards and homepage.
5. **Developer-First Design:** Fully custom CSS styling featuring a modern dark theme, hover micro-animations, glassmorphism headers, responsive grids, status badges, and syntax-highlighted code blocks.

---

## 📁 Repository Structure

```text
├── .github/
│   └── workflows/
│       ├── deploy.yml               # Automatic deployment to GitHub Pages
│       └── sync-example.yml         # GitHub Actions template to use in OTHER repos for doc syncing
├── _apps/
│   ├── laporan-keuangan-backend.md  # Synced backend bot documentation
│   ├── laporan-keuangan-webserver.md# Synced react dashboard documentation
│   └── v0-karate-var-app.md         # Synced v0 app deployment documentation
├── _config.yml                      # Jekyll website configuration (collections, metadata, permalinks)
├── _layouts/
│   └── default.html                 # Main layout template (navbar, footer, logic structures)
├── _sop/
│   ├── SOP Software Development Life Cycle.md
│   ├── SOP Template Backend v2 Bun.md
│   └── SOP Template Frontend v2.md
├── assets/
│   └── css/
│       └── style.css                # Premium vanilla CSS styling variables, layout, typography
├── index.md                         # Portal Home Dashboard (automated collection loops)
├── monitoring.md                    # Service Status monitoring page
├── setup-portal.ps1                 # Windows setup wizard (PowerShell)
└── setup-portal.sh                  # Linux/Mac setup wizard (Bash)
```

---

## ⚙️ Setup on Other GitHub Accounts

We provide interactive setup scripts to quickly configure and deploy this portal on another GitHub account:

### On Windows (PowerShell)
```powershell
.\setup-portal.ps1
```

### On Linux / macOS (Bash)
```bash
chmod +x setup-portal.sh
./setup-portal.sh
```

These scripts will guide you through updating the configuration files (`_config.yml`), updating repository links, and setting up the Uptime Kuma and Project Board targets.

---

## 🛠️ Local Development

### Prerequisites
* **Ruby** (v3.0 or higher recommended)
* **Bundler** (`gem install bundler`)

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/your-org/portal-repo.git
   cd portal-repo
   ```

2. Install dependencies:
   ```bash
   bundle install
   ```

3. Start the local Jekyll server:
   ```bash
   bundle exec jekyll serve
   ```

4. Open your browser and navigate to:
   [http://localhost:4000](http://localhost:4000)

---

## 🔄 Automated Multi-Repo Synchronization

The directory contains an example workflow at `.github/workflows/sync-example.yml`. 

To enable dynamic syncing from an external repository (e.g., `payment-service`):
1. **Copy the sync workflow:** Move `.github/workflows/sync-example.yml` to the external repository under `.github/workflows/sync-documentation.yml`.
2. **Create a GitHub Token:** Create a GitHub Personal Access Token (PAT) with write access to this portal repository.
3. **Save Token in Source Repo:** Save the PAT in the secrets of the source (external) repository named `SYNC_PORTAL_TOKEN`.
4. **Modify Destination:** Open the workflow file in the source repository and update the `destination_repo` to target this portal repository.
5. **Merge/Push:** Any changes pushed to the default branch will automatically prepare the source README with Jekyll Front Matter headers and push it to this portal's `_apps/` folder.
