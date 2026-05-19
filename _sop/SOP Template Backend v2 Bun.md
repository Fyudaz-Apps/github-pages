---
layout: default
title: Backend Development SOP (Bun & Drizzle)
description: Standard operating procedure for backend development using Bun, ElysiaJS, and Drizzle ORM to ensure code consistency.
category: Backend
author: Backend Team
last_updated: "2026-05-19"
version: 2.0.0
status: active
---

## 1. Tujuan

Menjadi panduan dalam pengembangan backend aplikasi untuk memastikan konsistensi struktur kode, penamaan, manajemen database, penanganan error, logging, dan integrasi dengan sistem lain, sehingga menghasilkan layanan yang aman, terukur, dan mudah dipelihara.

---

## 2. Ruang Lingkup

SOP ini berlaku untuk seluruh Backend Engineer di Divisi Software Development PT Ravelware Technology, mencakup aktivitas sejak inisialisasi proyek hingga deployment dan maintenance.

---

## 3. Definisi & Istilah

| No | Istilah | Deskripsi |
|----|---------|-----------|
| 1 | **Kebab-case** | Penulisan nama dengan pemisah tanda hubung (`-`), contoh: `user-service`. |
| 2 | **CamelCase** | Penulisan tanpa spasi, huruf pertama kata kedua dikapitalisasi, contoh: `getUserById`. |
| 3 | **Snake_case** | Penulisan dengan underscore (`_`) sebagai pemisah, contoh: `user_id`. |
| 4 | **Migration** | File skrip yang merekam perubahan skema database secara terkontrol. |
| 5 | **Artifact** | Hasil build backend (misal: Docker image, executable) yang siap deploy. |
| 6 | **Winston** | Library logging standar tim untuk pencatatan aktivitas sistem. |

---

## 4. Peran & Tanggung Jawab

| Peran | Tanggung Jawab |
|-------|----------------|
| **Backend Engineer** | Membangun layanan backend, menyediakan API, mengimplementasikan logika bisnis, dan mengelola database. Memastikan kode lolos analisis SonarQube sebelum merge serta bertanggung jawab atas keamanan, performa, dan perbaikan bug. |
| **Responsibility Person (RP)** | Memvalidasi kesesuaian implementasi backend dengan PRD dan API Specification. Menyetujui merge ke branch `dev` dan `main`, serta memastikan seluruh deliverables teknis memenuhi standar kualitas dan kebutuhan bisnis — tanpa terlibat dalam coding. |

---

## 5. Prosedur

### 5.1 Requirement & Preparation

| | Detail |
|---|--------|
| **Pelaksana** | Backend |
| **Aktivitas** | Menyiapkan repository dan fondasi proyek |

**Detail Aktivitas:**
- Inisiasi repository GitHub dengan template standar.
- Gunakan struktur folder sesuai SOP.
- Buat branch dari sesuai ticket / sub issue / epic yang terdapat di project tools monitoring.
- Siapkan file `.env.example`, `app.js`, dan `utils/` dasar.

**Deliverables:**
- Repository GitHub Backend
- Struktur folder standar
- Nama branch sesuai dengan ticket / sub issue / epic

---

### 5.2 Desain & Dokumentasi Teknis

| | Detail |
|---|--------|
| **Pelaksana** | Backend |

**Aktivitas:**
- Buat desain database (`snake_case`, tabel plural, kolom singular).
- Susun API Specification (Postman/OpenAPI).
- Koordinasi dengan FE dalam Technical Design Review (TDR).

**Deliverables:**
- Initial Desain database
- API Spec (request/response, error format)
- Notulen / Catatan TDR

---

### 5.3 Implementasi Fitur

| | Detail |
|---|--------|
| **Pelaksana** | Backend |

**Aktivitas:**
- Tulis service, controller, router dalam `kebab-case`.
- Gunakan `camelCase` untuk fungsi & variabel.
- Semua query DB melalui model/migration — tidak ada query langsung.
- Implementasi error response sesuai format array of object.
- Logging menggunakan Winston (level: error=0, info=1, dll).

**Deliverables:**
- Kode terstruktur sesuai SOP
- Error handling standard
- Log terklasifikasi

---

### 5.4 Manajemen Database

| | Detail |
|---|--------|
| **Pelaksana** | Backend |

**Aktivitas:**
- Setiap perubahan skema → buat file migration.
- Nama database: singular `snake_case`.
- Tidak ada folder query.

**Deliverables:**
- Migration files
- Skema DB konsisten

---

### 5.5 Code Review & Integrasi

| | Detail |
|---|--------|
| **Pelaksana** | Backend, Frontend, & Responsibility Person |

**Aktivitas:**
- Push ke branch pribadi → buat Pull Request ke `dev`.
- Setiap PR wajib melewati SonarQube (Quality Gate PASSED).
- Pastikan integrasi dengan frontend berjalan lancar.

**Deliverables:**
- Laporan SonarQube
- PR merged ke `dev`

---

### 5.6 Testing & Deployment

| | Detail |
|---|--------|
| **Pelaksana** | Backend Engineer & Responsibility Person |

**Aktivitas:**
- Perbaiki bug berdasarkan laporan Responsibility Person.
- Setelah approval, merge `dev` → `main`.
- Build artifact dari `main`.
- Deploy production (on-premise/cloud).

**Deliverables:**
- Aplikasi running di production
- Tag release GitHub (SemVer)
- Status task "Done" di GitHub Project

---

### 5.7 Maintenance & Dokumentasi

| | Detail |
|---|--------|
| **Pelaksana** | Backend & Responsibility Person |

**Aktivitas:**
- Simpan log & storage di luar repo (terpusat, auto-purge).
- Buat dokumentasi teknis (arsitektur, env setup, endpoint).

**Deliverables:**
- Dokumentasi teknis
- Sistem logging & storage terkelola

---

## 6. Diagram Alir

> *Diagram alir Backend Development Flow tersedia di dokumen SOP internal.*

---

## 7. Struktur dan Layout (Feature Based)

Bagian ini merinci fungsi dan tanggung jawab dari setiap direktori utama dalam proyek untuk memastikan konsistensi pengembangan.

```
├── .agents
│   └── workflows
│       ├── generate-backend-docs.md
│       └── generate-backend-structure.md
│
├── docs
│   ├── API_DOC.md
│   ├── ARCHITECTURE.md
│   ├── CODE_STRUCTURE.md
│   ├── ERD.md
│   └── FLOW.md
│
├── drizzle
│   ├── meta
│   │   ├── _journal.json
│   │   └── 0000_snapshot.json
│   └── 0000_grey_nocturne.sql
│
├── src
│   ├── app.ts
│   ├── server.ts
│   ├── migrate.ts
│   ├── reset.ts
│   ├── seed.ts
│   │
│   ├── config
│   │   └── database.ts
│   │
│   ├── shared
│   │   ├── middleware
│   │   │   └── auth.guard.ts
│   │   ├── utils
│   │   │   ├── logger.ts
│   │   │   ├── mqtt.ts
│   │   │   ├── hash.ts
│   │   │   └── uuid.ts
│   │   ├── constants
│   │   │   └── index.ts          # FOR CONSTANTS VARIABLE
│   │   └── types
│   │       └── index.ts          # AS TYPE DATA
│   │
│   ├── database
│   │   ├── schema
│   │   │   ├── user.schema.ts
│   │   │   ├── role.schema.ts
│   │   │   └── auth.schema.ts
│   │   ├── migrations
│   │   │   ├── 0001_create_user.sql
│   │   │   └── 0002_create_role.sql
│   │   └── seed
│   │       ├── 001-user.ts
│   │       └── 002-role.ts
│   │
│   ├── features
│   │   ├── auth
│   │   │   ├── auth.route.ts
│   │   │   ├── auth.controller.ts
│   │   │   ├── services
│   │   │   │   ├── login.ts
│   │   │   │   ├── register.ts
│   │   │   │   ├── validate-token.ts
│   │   │   │   └── refresh-token.ts
│   │   │   ├── repositories
│   │   │   │   ├── find-user-by-email.ts
│   │   │   │   ├── find-user-by-username.ts
│   │   │   │   ├── create-auth-user.ts
│   │   │   │   └── save-refresh-token.ts
│   │   │   └── types
│   │   │       └── auth.type.ts
│   │   │
│   │   ├── user
│   │   │   ├── user.route.ts
│   │   │   ├── user.controller.ts
│   │   │   ├── services
│   │   │   │   ├── create-user.ts
│   │   │   │   ├── get-user.ts
│   │   │   │   ├── get-users.ts
│   │   │   │   ├── update-user.ts
│   │   │   │   ├── delete-user.ts
│   │   │   │   └── get-profile.ts
│   │   │   ├── repositories
│   │   │   │   ├── create-user.ts
│   │   │   │   ├── find-user-by-id.ts
│   │   │   │   ├── find-users.ts
│   │   │   │   ├── update-user.ts
│   │   │   │   └── delete-user.ts
│   │   │   └── types
│   │   │       └── user.type.ts
│   │   │
│   │   └── mqtt
│   │       ├── mqtt.route.ts
│   │       ├── mqtt.controller.ts
│   │       ├── services
│   │       │   └── handle-message.ts
│   │       └── repositories
│   │           ├── publish-message.ts
│   │           └── subscribe-topic.ts
│   │
│   └── routes
│       └── index.ts
│
├── tests
│   ├── user
│   │   ├── create-user.test.ts
│   │   ├── get-user.test.ts
│   │   └── update-user.test.ts
│   └── auth
│       ├── login.test.ts
│       └── register.test.ts
│
├── .env
├── .env.example
├── .gitattributes
├── .gitignore
├── bun.lock
├── drizzle.config.ts
├── package-lock.json
├── package.json
├── pm2.config.cjs
├── README.md
├── setup.ps1
├── sonar-project.properties
└── tsconfig.json
```

---

### 7.1 Direktori Konfigurasi & Pendukung (`.agents/`, `docs/`, `drizzle/`)

- **`.agents/workflows/`**: Menyimpan skrip, konfigurasi, atau alur kerja (workflow) otomatisasi AI untuk membantu pengembangan, seperti generator dokumentasi backend secara otomatis.
- **`docs/`**: Direktori terpusat untuk dokumentasi teknis proyek. Mencakup spesifikasi API (`API_DOC.md`), Arsitektur Sistem (`ARCHITECTURE.md`), aturan penulisan kode (`CODE_STRUCTURE.md`), relasi database (`ERD.md`), dan alur sistem (`FLOW.md`).
- **`drizzle/`**: Direktori yang dihasilkan dan dikelola oleh Drizzle ORM. Folder ini berisi file snapshot dan journal (format `.json` dan `.sql`) yang berfungsi untuk melacak riwayat perubahan dan versi skema database (migrasi).

---

### 7.2 Direktori Kode Sumber Utama (`src/`)

Folder ini merupakan inti dari aplikasi backend.

- **`app.ts` & `server.ts`**: Merupakan entry point (titik awal) aplikasi. `app.ts` biasanya berisi konfigurasi framework (seperti Express/Fastify) beserta inisialisasi middleware global, sedangkan `server.ts` bertugas untuk menjalankan server di port tertentu.
- **Database Scripts (`migrate.ts`, `reset.ts`, `seed.ts`)**: Skrip utilitas khusus untuk mengeksekusi migrasi tabel, mengosongkan/mereset database, dan memasukkan data awal (seeding).

---

### 7.3 Komponen Bersama & Database (`src/shared/`, `src/database/`)

- **`src/config/`**: Menyimpan konfigurasi tingkat aplikasi (environment/konfigurasi infrastruktur), seperti pengaturan koneksi database (`database.ts`).
- **`src/shared/`**: Menyimpan kode utilitas yang digunakan secara universal melintasi berbagai fitur untuk menghindari duplikasi kode (Prinsip DRY).
  - **`middleware/`**: Lapisan penyaring request HTTP, seperti pembatasan akses (`auth.guard.ts`).
  - **`utils/`**: Kumpulan fungsi pembantu (helper) seperti logger (pencatat aktivitas), konfigurasi client MQTT, generator Hash/UUID.
  - **`constants/` & `types/`**: Deklarasi variabel statis/tetap dan tipe data global (TypeScript).
- **`src/database/`**: Area khusus untuk interaksi struktural database.
  - **`schema/`**: Definisi tabel Drizzle ORM (seperti tabel user, role, auth).
  - **`migrations/` & `seed/`**: Rekaman script SQL untuk membentuk tabel dan mengisi data (dummy/default).

---

### 7.4 Inti Arsitektur: Direktori Fitur (`src/features/`)

Ini adalah bagian terpenting dari arsitektur. Setiap folder merepresentasikan satu domain/fitur yang bisa berdiri sendiri secara fungsional. Struktur standar setiap fitur (misal: `auth` dan `user`) dibagi menjadi:

- **`*.route.ts`**: Bertanggung jawab untuk mendefinisikan endpoint API (URL) dan mengarahkannya ke controller yang tepat.
- **`*.controller.ts`**: Menangani request dan response HTTP. Lapisan ini bertugas melakukan validasi input dari pengguna sebelum meneruskannya ke service.
- **`services/`**: Menyimpan **Business Logic** (aturan bisnis) inti. Lapisan ini mengambil data dari controller, memproses alur logika algoritma aplikasi, dan memanggil repository untuk interaksi database. (Setiap aksi dipisah menjadi satu file untuk menjaga Clean Code).
- **`repositories/`**: **Data Access Layer**. Lapisan ini secara eksklusif menangani komunikasi ke database (Query Drizzle ORM). Controller atau service tidak boleh melakukan query langsung, melainkan harus memanggil repository.
- **`types/`**: Mendefinisikan tipe data, interface, atau DTO (Data Transfer Object) spesifik yang hanya digunakan oleh fitur tersebut.

---

### 7.5 Router Utama & Pengujian (`src/routes/`, `tests/`)

- **`src/routes/index.ts`**: Berfungsi sebagai kolektor. File ini mengimpor semua `*.route.ts` dari direktori `features/` dan mendaftarkannya ke dalam satu rute global di aplikasi.
- **`tests/`**: Direktori untuk pengujian otomasi (Unit Test / Integration Test). Strukturnya sengaja dibuat mirror (berkaca) dengan struktur fitur untuk memudahkan developer mencari file test untuk fungsionalitas tertentu (contoh: test untuk `create-user` disimpan di `tests/user/`).

---

### 7.6 File Root (Konfigurasi Proyek)

File-file di luar folder seperti `.env`, `package.json`, `bun.lock`, `drizzle.config.ts`, `pm2.config.cjs`, dan `tsconfig.json` adalah file standar pengaturan ekosistem Node.js/Bun yang mengelola dependencies, environment variables, konfigurasi TypeScript, dan deployment server.

---

## 8. Tech Stack

| Kategori | Teknologi |
|----------|-----------|
| **Runtime** | Bun |
| **Framework** | ElysiaJS |
| **ORM** | Drizzle |
| **Authentication** | JSON Web Token (JWT) |
| **API Documentation** | OpenAPI |
| **Logging** | Winston |
| **Architecture** | Feature-Based / Vertical Slicing |

---

## 9. Catatan

> **Link Repository Backend:** [https://github.com/PT-Ravelware-Technology-Indonesia/bun-template-drizzle](https://github.com/PT-Ravelware-Technology-Indonesia/bun-template-drizzle)
