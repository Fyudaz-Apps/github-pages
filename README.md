# IT Software Development Department Portal

A centralized static documentation and service monitoring portal built with [Jekyll](https://jekyllrb.com/) and optimized for deployment on **GitHub Pages**.

---

## 🚀 Key Features

1. **Global SOPs:** A dedicated space in the repository (`_sop/`) to write development team Standard Operating Procedures in Markdown.
2. **App Documentations:** A collection (`_apps/`) that dynamically integrates documentation (e.g. README files) synced from other separate service repositories.
3. **Uptime Kuma Monitoring:** Integrated, responsive status dashboard displaying live microservice availability using a secure borderless iframe.
4. **Developer-First Design:** Fully custom CSS styling featuring a modern dark theme, hover micro-animations, glassmorphism headers, responsive grids, status badges, and syntax-highlighted code blocks.

---

## 📁 Repository Structure

```text
├── .github/
│   └── workflows/
│       └── sync-example.yml         # GitHub Actions template to use in OTHER repos for doc syncing
├── _apps/
│   └── sample-backend-service.md    # Simulates synced backend service README
├── _config.yml                      # Jekyll website configuration (collections, metadata, permalinks)
├── _layouts/
│   └── default.html                 # Main layout template (navbar, footer, logic structures)
├── _sop/
│   └── sop-deployment-flow.md       # Sample deployment Standard Operating Procedure
├── assets/
│   └── css/
│       └── style.css                # Premium vanilla CSS styling variables, layout, typography
├── Gemfile                          # Bundler dependencies for local development
├── index.md                         # Portal Home Dashboard (automated collection loops)
└── monitoring.md                    # Service Status page (Uptime Kuma iframe integration)
```

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
