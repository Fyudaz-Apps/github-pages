---
layout: default
title: Laporan Keuangan Backend
description: Fast and efficient multimodal financial tracking bot built with Bun, ElysiaJS, and grammY.
repo_name: laporan-keuangan-backend
status: active
version: 1.0.0
author: Fyudaz-Apps
last_updated: "2026-05-19"
project_url: https://github.com/users/fahmiyuda31/projects/7
---

# Laporan Keuangan - Multimodal Finance Bot

A fast and efficient financial tracking bot built with **Bun**, **ElysiaJS**, and **grammY**.

## Features

* **Multimodal Input:** Record transactions via text, voice notes (STT), or photos of receipts (OCR/Vision).
* **Interactive Confirmations:** Data is parsed by AI and sent to your Telegram for verification before being saved permanently.
* **Local Database:** Fast and lightweight storage using **SQLite** and **Drizzle ORM**.
* **Modern Stack:** Built on the cutting-edge Bun runtime for maximum performance.

## Tech Stack

* **Runtime:** [Bun](https://bun.sh)
* **Framework:** [ElysiaJS](https://elysiajs.com/)
* **Bot Lib:** [grammY](https://grammy.dev/)
* **ORM:** [Drizzle ORM](https://orm.drizzle.team/)
* **Database:** SQLite

## Getting Started

### Prerequisites

* [Bun](https://bun.sh/docs/installation) installed.
* A Telegram Bot Token from [@BotFather](https://t.me/botfather).

### Installation

1. Clone the repository.
2. Install dependencies:
   ```bash
   bun install
   ```
3. Configure environment variables in `.env`:
   ```env
   TELEGRAM_TOKEN=your_bot_token
   DATABASE_URL=sqlite.db
   ```

### Development

Run the server with hot-reload:
```bash
bun dev
```

### Database Management

* Push schema changes to database:
  ```bash
  bun db:push
  ```
* Open Drizzle Studio to explore data:
  ```bash
  bun db:studio
  ```

### Process Management (PM2)

The application is configured to run in the background using PM2.

* Start application:
  ```bash
  pm2 start ecosystem.config.cjs
  ```
* List processes:
  ```bash
  pm2 status
  ```
* View logs:
  ```bash
  pm2 logs laporan-keuangan
  ```
* Stop/Restart:
  ```bash
  pm2 stop laporan-keuangan
  pm2 restart laporan-keuangan
  ```

## Documentation

For more detailed information, see the documentation in the source repository:
* [Architecture Overview](https://github.com/Fyudaz-Apps/laporan-keuangan-backend/blob/main/doc/architecture.md)
* [API Reference](https://github.com/Fyudaz-Apps/laporan-keuangan-backend/blob/main/doc/api.md)
* [Database Schema](https://github.com/Fyudaz-Apps/laporan-keuangan-backend/blob/main/doc/database.md)
* [Source Repository](https://github.com/Fyudaz-Apps/laporan-keuangan-backend)
