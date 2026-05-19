---
layout: default
title: Frontend Development SOP
description: Standard operating procedure for frontend development detailing folder structure, component naming, and API integration.
category: Frontend
author: Frontend Team
last_updated: "2026-05-19"
version: 2.0.0
status: active
---

## 1. Tujuan

Menjadi panduan dalam pengembangan aplikasi frontend untuk memastikan konsistensi struktur proyek, penamaan komponen, integrasi API, manajemen state, dan kualitas kode — sehingga menghasilkan antarmuka yang responsif, teruji, dan mudah dipelihara.

---

## 2. Ruang Lingkup

SOP ini berlaku untuk seluruh Frontend Engineer di Divisi Software Development PT Ravelware Technology, mencakup aktivitas sejak inisialisasi proyek hingga deployment dan maintenance.

---

## 3. Definisi & Istilah

| No | Istilah | Deskripsi |
|----|---------|-----------|
| 1 | **Kebab-case** | Penulisan nama file/folder dengan tanda hubung (`-`), contoh: `user-profile.tsx`. |
| 2 | **PascalCase** | Penulisan nama komponen React, contoh: `UserProfile`, `DataTable`. |
| 3 | **CamelCase** | Penulisan fungsi, variabel, dan properti objek, contoh: `handleSubmit`, `isLoggedIn`. |
| 4 | **Shadcn/UI** | Library UI berbasis Radix UI + Tailwind CSS yang digunakan sebagai standar komponen. |
| 5 | **Jira** | Alat pelacakan tugas berbasis kolom (To Do → In Progress → Done). |
| 6 | **Branch Feature** | Branch pribadi berdasarkan nama developer (misal: `fahmi/fix-login-ui`). |
| 7 | **API Spec** | Dokumen teknis dari Backend yang menjadi acuan integrasi (Postman/OpenAPI). |
| 8 | **Responsibility Person (RP)** | Individu yang bertanggung jawab terhadap hasil pekerjaan developer. |
| 9 | **Developer** | Individu yang bertanggung jawab menghasilkan kode. |

---

## 4. Peran & Tanggung Jawab

| Peran | Tanggung Jawab |
|-------|----------------|
| **Frontend Developer** | Mengembangkan tampilan dan interaksi pengguna sesuai desain dan arahan RP, serta mengintegrasikan dengan API backend. Boleh memberi saran desain, tapi keputusan akhir ada di RP. Juga bertanggung jawab atas performa, aksesibilitas, validasi form, dan error boundary. |
| **Responsibility Person** | Memvalidasi kesesuaian implementasi backend dengan PRD dan API Specification. Menyetujui merge ke branch `dev` dan `main`, serta memastikan seluruh deliverables teknis memenuhi standar kualitas dan kebutuhan bisnis — tanpa terlibat dalam coding. |

---

## 5. Prosedur

### 5.1 Requirement & Preparation

| | Detail |
|---|--------|
| **Pelaksana** | Frontend |

**Aktivitas:**
- Inisialisasi repository GitHub dengan template standar.
- Gunakan struktur folder sesuai SOP.
- Buat branch untuk tiap fitur yang dikembangkan.
- Siapkan `.env.example`, `vite.config.js`, dan struktur folder dasar.

**Deliverables:**
- Repository GitHub Frontend
- Struktur folder standar
- Branch feature

---

### 5.2 Desain

| | Detail |
|---|--------|
| **Pelaksana** | Frontend |

**Aktivitas:**
- Koordinasi dengan BE dalam TDR.
- Pastikan API Spec lengkap (request/response, error format).

**Deliverables:**
- API Spec terkonfirmasi
- Notulen TDR
- Koleksi Postman

---

### 5.3 Implementasi Fitur

| | Detail |
|---|--------|
| **Pelaksana** | Frontend |

**Aktivitas:**
- Komponen: PascalCase (misal: `LoginForm.tsx`)
- File & folder: kebab-case (misal: `auth/login-form.tsx`)
- Gunakan Shadcn/ui untuk UI konsisten
- State management: React Context / Zustand
- Validasi form & error handling user-friendly
- Error boundary untuk proteksi UI

**Deliverables:**
- Kode terstruktur sesuai SOP
- UI sesuai desain
- Integrasi API berjalan

---

### 5.4 Code Review & Integrasi

| | Detail |
|---|--------|
| **Pelaksana** | Backend, Frontend, & Responsibility Person |

**Aktivitas:**
- Push ke branch pribadi → buat PR ke `dev`.
- Setiap PR wajib lolos SonarQube (Quality Gate PASSED).
- Pastikan tidak ada broken UI atau console error.

**Deliverables:**
- Laporan SonarQube
- PR merged ke `dev`

---

### 5.5 Testing & Deployment

| | Detail |
|---|--------|
| **Pelaksana** | Frontend & Responsibility Person |

**Aktivitas:**
- Perbaiki bug berdasarkan laporan Responsibility Person.
- Setelah approval, merge `dev` → `main`.
- Build artifact (`npm run build`).
- Deploy ke production (On-Premise/Cloud).
- Jalankan smoke test pasca-deploy.

**Deliverables:**
- Aplikasi running di production
- Tag rilis GitHub (SemVer)
- Status task "Done" di GitHub Project

---

### 5.6 Maintenance & Dokumentasi

| | Detail |
|---|--------|
| **Pelaksana** | Frontend & Responsibility Person |

**Aktivitas:**
- Buat dokumentasi teknis: env setup, routing, komponen utama.

**Deliverables:**
- Dokumentasi teknis

---

## 6. Diagram Alir

> *Diagram alir Frontend Development Flow tersedia di dokumen SOP internal.*

---

## 7. Tech Stack

Aplikasi ini menggunakan teknologi web modern untuk performa dan skalabilitas tinggi:

| Komponen | Teknologi | Versi |
|----------|-----------|-------|
| **Framework** | React + TypeScript | 19.2.3 + 5.9.3 |
| **Build Tool** | Vite | 7.3.0 |
| **Routing** | TanStack Router | 1.144.0 |
| **State Management** | Zustand (Global) + TanStack Query (Server) | 5.0.9 + 5.90.16 |
| **UI Framework** | Tailwind CSS + Shadcn UI | 4.1.18 |
| **Form & Validation** | React Hook Form + Zod | 7.70.0 + 4.3.5 |
| **API Client** | Axios | 1.13.2 |
| **Real-time** | Socket.IO + MQTT | 4.8.3 + 5.14.1 |
| **Data Table** | TanStack React Table | 8.21.3 |

---

## 8. Setup dan Menjalankan Aplikasi

### Prasyarat

- Node.js v20.x atau lebih tinggi
- Npm v9.x atau pnpm v8.x

### Langkah-langkah

#### 8.1 Instalasi Dependencies

Gunakan salah satu perintah:
```bash
npm install
# atau
pnpm install
```

#### 8.2 Konfigurasi Environment

1. Salin `.env-example` menjadi `.env` dan sesuaikan nilainya.
2. Proyek ini mendukung dua tipe konfigurasi:
   - **`.env`**: Untuk konfigurasi saat build-time (lokal/development).
   - **`public/runtime-env.js`**: Untuk Build Once, Deploy Anywhere (runtime configuration). Jika deployment dilakukan on cloud, tidak perlu update file ini.

#### 8.3 Menjalankan Development Server

```bash
npm run dev
```

#### 8.4 Build untuk Production

```bash
npm run build
```

Untuk melihat hasil build:
```bash
npm run preview
```

---

## 9. Struktur dan Layout

### 9.1 High-Level Structure

Dalam pengaturan ini, direktori `src/features` adalah inti dari aplikasi. Setiap folder di dalamnya mewakili domain atau area fungsional tertentu.

```
src/
├── assets/                # Global static files (images, fonts)
├── components/            # Global, reusable UI components (Button, Input, Modal)
├── config/                # Global config, env variables, API clients
├── features/              # The "Meat": Feature-specific logic (see below)
├── hooks/                 # Global reusable hooks (useDebounce, useLocalStorage)
├── layouts/               # Page wrappers/templates (AdminLayout, AuthLayout)
├── pages/                 # Route components that compose features together
├── services/              # Global API services or SDK initializations
├── store/                 # Global state management (Redux/Zustand)
├── utils/                 # Global helper functions (formatDate, validation)
└── App.tsx                # Main entry component & Providers
```

### 9.2 Dalam "features" folder

Setiap fitur harus menjadi aplikasi mini tersendiri.

```
features/auth/
├── api/                    # Fetching data khusus fitur ini (e.g., login.ts, register.ts)
├── components/             # Komponen yang hanya dipakai di fitur ini (e.g., login-form.tsx, register-dialog.tsx)
├── hooks/                  # Logika/state khusus fitur ini (e.g., use-auth-session.ts)
├── types/                  # Definisi TypeScript untuk fitur ini (e.g., auth-schema.ts)
├── utils/                  # Helper khusus fitur ini (e.g., token-validator.ts)
└── index.ts                # "Gerbang" fitur (Public API)
```

---

## 10. Alur Pengembangan (Development Workflow)

### 10.1 Menambahkan Route dan Halaman Baru

Gunakan `src/configs/menu-config.ts` sebagai *single source of truth*.

1. Buat komponen halaman di `src/pages/`.
2. Daftarkan halaman tersebut di `MENU_LIST` pada `menu-config.ts`.
3. Router akan secara otomatis membuat route berdasarkan konfigurasi tersebut.

### 10.2 Menambahkan Komponen UI

Gunakan Shadcn CLI untuk konsistensi:
```bash
npx shadcn@latest add [nama-komponen]
```

### 10.3 Integrasi API

Ikuti pola **Service Controller**:

1. Definisikan tipe data di `src/types/`.
2. Buat fungsi API di `src/services/api/`.
3. Gunakan custom hooks dengan **TanStack Query** untuk fetching data di komponen.

### 10.4 Implementasi ACL

Gunakan utility `hasPermission` untuk kontrol akses:

- Cek permission di UI: `hasCreatePermission("User")`, `hasUpdatePermission("Role")`, dll.
- Menu di sidebar akan otomatis disaring berdasarkan hak akses user yang didapat dari backend.

---

## 11. Catatan

> **Link Repository Frontend:** [https://github.com/PT-Ravelware-Technology-Indonesia/shadcn-template-webserver](https://github.com/PT-Ravelware-Technology-Indonesia/shadcn-template-webserver)
