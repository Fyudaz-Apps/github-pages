---
layout: default
title: Software Development Life Cycle (SDLC) SOP
description: Standard operating procedure defining the lifecycle stages of software development, roles, and deployment workflows.
category: Development
author: Responsibility Person
last_updated: "2026-05-19"
version: 1.0.0
status: active
---

## 1. Tujuan

Menjadi pedoman baku pelaksanaan Software Development Life Cycle (SDLC) agar proses pengembangan perangkat lunak berjalan terstruktur, terkontrol, terdokumentasi, dan menghasilkan produk berkualitas sesuai kebutuhan bisnis.

---

## 2. Ruang Lingkup

SOP ini berlaku untuk seluruh aktivitas pengembangan perangkat lunak di divisi Software Development, mulai dari tahap requirement gathering hingga maintenance.

---

## 3. Definisi & Istilah

| No | Istilah | Deskripsi |
|----|---------|-----------|
| 1 | **PRD** (Product Requirements Document) | Dokumen yang menjelaskan tujuan, fitur, dan kebutuhan fungsional produk dari sisi bisnis; menjadi acuan utama pengembangan. |
| 2 | **GitHub Project** | Alat manajemen tugas di GitHub berbasis kolom (To Do, In Progress, Done) untuk melacak progres fitur dan issue. |
| 3 | **Branch `main`** | Branch utama yang berisi kode stabil dan siap produksi. |
| 4 | **Branch `dev`** | Branch integrasi tempat fitur-fitur digabung dan diuji sebelum masuk ke `main`. |
| 5 | **SonarQube** | Platform untuk analisis kualitas kode, termasuk deteksi bug, code smell, dan kerentanan. |
| 6 | **API Specification** (API Spec) | Dokumen teknis yang menjelaskan endpoint, metode, parameter, contoh request/response, dan penanganan error API. |
| 7 | **Technical Design Review** (TDR) | Diskusi teknis antara Frontend dan Backend Engineer yang difasilitasi Responsibility Person untuk menyepakati arsitektur, spesifikasi API, dan desain database sebelum development. |
| 8 | **Semantic Versioning** (SemVer) | Sistem penomoran versi perangkat lunak dalam format `MAJOR.MINOR.PATCH` (misal: `v1.2.0`). |
| 9 | **Artifact** | Hasil build aplikasi — seperti bundle JavaScript, Docker image, atau executable — yang siap di-deploy ke lingkungan produksi. |
| 10 | **On-Premise** | Deployment aplikasi ke server internal yang dikelola oleh organisasi sendiri. |
| 11 | **Cloud** | Deployment aplikasi ke infrastruktur cloud publik seperti AWS, Google Cloud Platform (GCP), atau Microsoft Azure. |

---

## 4. Peran & Tanggung Jawab

| Peran | Tanggung Jawab |
|-------|----------------|
| **Responsibility Person (RP)** | Menetapkan kebutuhan proyek, mengatur jadwal, dan menentukan standar teknis. RP memantau progres, mereview hasil kerja tim, dan memastikan produk sesuai requirement — tanpa terlibat dalam coding. |
| **Frontend** | Mengembangkan tampilan dan interaksi pengguna sesuai desain dan arahan RP, serta mengintegrasikan dengan API backend. Boleh memberi saran desain, tapi keputusan akhir ada di RP. |
| **Backend** | Membangun layanan backend, menyediakan API, mengimplementasikan logika bisnis, dan mengelola database. Juga bertanggung jawab atas keamanan, performa, dan perbaikan bug. |

---

## 5. Prosedur

### 5.1 Requirement Gathering & Preparation

| | Detail |
|---|--------|
| **Pelaksana** | Responsibility Person, Frontend, Backend |
| **Aktivitas** | Membuat breakdown list fitur berdasarkan PRD yang diterima dari tim project |

**Detail Aktivitas (Responsibility Person):**
- Membuat daftar fitur berdasarkan kebutuhan proyek dan memecahnya menjadi task/issue.
- Menyiapkan struktur awal repositori untuk frontend dan backend sesuai standar tim.
- Buat project Jenkins di server development.
- Mengkoordinasikan Technical Design Review (TDR) antara FE & BE untuk menyepakati arsitektur, API Spek.

**Deliverables:**
- GitHub Project / Open Project
- GitHub repository Frontend
- GitHub repository Backend
- Workspace Jenkins di server development.

**Detail Aktivitas (Frontend):**
- Menginisialisasi project frontend
- Slicing User Interface sesuai dengan kebutuhan fitur

**Deliverables:**
- Setup GitHub Repository Frontend (dengan template siap pakai)
- Gunakan branch (nama developer)

**Detail Aktivitas (Backend):**
- Menginisialisasi project backend
- Membuat spesifikasi awal API (koordinasi dengan FE)
- Membuat desain database awal

**Deliverables:**
- Setup GitHub Repository Backend (dengan template siap pakai)
- Gunakan branch (nama developer)
- API spec (tools: Postman)
- Desain database awal.

---

### 5.2 Development / Implementation

#### Frontend

**Implementasi Fitur Frontend:**
- Mengembangkan tampilan & interaksi sesuai desain/requirement
- Membuat komponen UI
- Integrasi dengan API backend
- State management
- Form validation
- Error boundary / user feedback

**Deliverables:**
- Push kode frontend ke GitHub
- Semua fitur sesuai task di GitHub Project
- Merge ke branch `dev` dan siap review

#### Backend

**Implementasi Fitur Backend:**
- Mengembangkan logika bisnis & API
- Membuat endpoint sesuai spesifikasi
- Validasi input
- Custom error handling (Sesuaikan)
- Logging aktivitas penting (Winston)

**Deliverables:**
- Push kode backend ke GitHub
- Endpoint berfungsi penuh, dokumentasi minimal (contoh request/response)
- Semua fitur sesuai task di GitHub Project
- Merge ke branch `dev` dan siap review

---

### 5.3 Code Review & Integrasi

| | Detail |
|---|--------|
| **Pelaksana** | Responsibility Person, Frontend Engineer & Backend Engineer |

**Aktivitas:**
- Memastikan kualitas kode sesuai standar tim
- Setiap PR melewati analisis SonarQube sebelum merge ke `dev`.
- Integrasi antara frontend dan backend.

**Deliverables:**
- Laporan SonarQube yang menunjukkan report Quality Gate **PASSED**, Warning level high = 0.
- Fitur terintegrasi penuh antara Frontend & Backend Engineer.
- Laporan GitHub Project

---

### 5.4 Testing & Quality Assurance

| | Detail |
|---|--------|
| **Pelaksana** | Responsibility Person, Frontend & Backend |

**Aktivitas (Responsibility Person):**
- Susun test case berdasarkan requirement
- Uji semua fitur di branch `dev`

**Deliverables:**
- Merge branch `dev` ke `main` ketika testing sudah selesai

**Aktivitas (Frontend & Backend):**
- Fixing bug → push ke `dev` → retest
- Saat commit, inputkan issue GitHub Project dan tambahkan prefix `bug`. Example: `bug: message #{id_issue github project}`

**Deliverables:**
- Bug resolved
- Informasi bug tercatat di GitHub Project
- Merge ke `dev`

---

### 5.5 Deployment & Release

#### Persiapan Rilis (Responsibility Person)

- Pastikan semua fitur telah diuji dan merged ke branch `main`
- Terapkan Semantic Versioning (misal: `v1.2.0`)
- Update status semua task di GitHub Project menjadi "Done"

**Deliverables:**
- GitHub Project: semua status "Done"
- Tag rilis di GitHub

#### Deployment Production (On-Premise)

- Lakukan build aplikasi dari branch `main` dalam mode production
- Deploy artifact ke server fisik/virtual
- Jalankan migrasi database jika diperlukan
- Web Server: running via nginx
- Backend Application: buat service dengan nssm (windows) atau linux service, tergantung server client

#### Deployment ke Production (Cloud)

- Buat atau pastikan tersedia Jenkins Project/Workspace yang terhubung ke repository GitHub
- Jenkins menarik kode dari branch `main`
- Lakukan build otomatis di dalam workspace Jenkins
- Jalankan migrasi database jika diperlukan

**Pelaksana:** Frontend & Backend

**Deliverables:**
- Aplikasi berhasil di-deploy ke server production

#### Post Deployment Smoke Test

- Akses aplikasi
- Login sukses
- Fitur inti berjalan
- Tidak ada error 500

**Pelaksana:** Responsibility Person

**Deliverables:**
- Aplikasi running normal tanpa error

---

### 5.6 Handover & Maintenance

| | Detail |
|---|--------|
| **Pelaksana** | Responsibility Person |

**Aktivitas:**
- Buat panduan teknis & user guide untuk operasional & maintenance
- Rekap actual pengerjaan fitur

**Deliverables:**
- Dokumentasi teknis dan user guide (jika dibutuhkan)
- Dokumentasi Actual pengerjaan fitur

---

## 6. Development Lifecycle Flow

> *Diagram alir Development Lifecycle Flow tersedia di dokumen SOP internal.*

---

## 7. Change Request Flow

> *Diagram alir Change Request Flow tersedia di dokumen SOP internal.*
