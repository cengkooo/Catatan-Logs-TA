---
title: Master Dashboard Tugas Akhir
tags:
  - dashboard
  - overview
  - tugas-akhir
---

# 🎯 Master Dashboard Tugas Akhir

> **Topik TA (LOCKED 16 Nov):** *Mood-Arc Playlist Generation Berbasis Dynamic Mood Trajectory (Dataset DEAM, KNN & Trajectory Alignment)*  
> **Target Utama:** Seminar Proposal (Sempro) & Ujian TA IF ITERA  
> **Spreadsheet Rujukan:** [Master Dashboard Sempro (Google Sheets)](https://docs.google.com/spreadsheets/d/1Iu5A5hGb0ZI4K9G48n8dv2W-SpkjMajS5go47I5D1cI)

> [!danger] 🚨 STATUS 16 NOV 2026 — EMERGENCY RECOVERY
> Progres riil: **0 dari 17 task (0.0%)**, 15 hari terpakai tanpa output naskah. Sprint 1 & 2 sudah overdue.
> Batas pendaftaran sempro: **25 Nov** → submit berkas **24 Nov 13:00** · naskah utuh v1 ke pembimbing **20 Nov 21:45** · ACC/TTD **23 Nov**.
> **Baca dan patuhi: [[EMERGENCY-SEMPRO]]** (satu-satunya sumber jadwal yang berlaku).

---

## ⚡ Navigasi Cepat Sprints

| Sprint | Fokus Utama | Target Luaran | Window | Status Dokumen |
| :--- | :--- | :--- | :--- | :--- |
| **[[Sprint-1-Bab1-EDA]]** | Bab 1 & Eksplorasi Data | Latar belakang + EDA DEAM | 16–18 Nov | `IN PROGRESS` (overdue) |
| **[[Sprint-2-Bab2-Baseline]]** | Bab 2 & Baseline PoC | Matriks 15 paper + baseline 1 run | 18–23 Nov | `IN PROGRESS` (overdue) |
| **[[Sprint-3-Bab3-Metodologi]]** | Bab 3 & Desain Pipeline | Diagram + metrik + PoC GPU | 19–22 Nov | `IN PROGRESS` |
| **[[Sprint-4-Final-Sidang]]** | Integrasi, Slide & Sidang | Naskah utuh + slide + berkas daftar | 20–27 Nov | `IN PROGRESS` |

---

## 📌 To-Do List yang Belum Selesai (Otomatis via Dataview)

```dataview
TASK
WHERE !completed AND file.path != this.file.path
GROUP BY file.link
```

---

## 📚 Literatur Terbaru yang Selesai Direview

```dataview
TABLE author AS "Penulis", year AS "Tahun", dataset AS "Dataset", metode AS "Metode"
FROM #paper-review
SORT year DESC
LIMIT 5
```

---

## 🔗 Pusat Kendali & Folder Penting
- 🚨 **Rencana Aktif:** [[EMERGENCY-SEMPRO]] ← **baca ini dulu**
- 📋 **Sistem Eksekusi Modular:** [[00-Index-Todolist|09-Todolist (Panduan 5 Fase)]]
- 🌐 **Arsitektur Cloud Drive:** [[fix_gdrive|SOP & Struktur Google Drive]]
- 📊 **Roadmap:** [[Roadmap-Sempro]]
- 💬 **Bimbingan Dosen:** [[Notulensi-Bimbingan]] | [[Bank-Pertanyaan-Dosen]] | [[Tracker-Prasyarat-Sempro|Tracker Prasyarat Sempro & TASYS]]
- 📖 **Literatur:** [[Matriks-Sintesis]] | [[Spreadsheet-Studi-Literatur]] | [[Spreadsheet-Penjelasan-Dataset]] | [[Kamus-Notasi-Glosarium]]
- 💡 **Catatan Belajar & Tech Stack:** [[00-Index-Catatan|11-Catatan-Belajar (Konsep, Tools, & Sintesis)]]
- 🔬 **Eksperimen:** [[01-Dataset-DEAM-dan-Eksplorasi|Dataset-DEAM]] | [[02-Formulasi-Ekstraksi-Trajectory|Ekstraksi-Trajectory]] | [[03-Replikasi-Baseline-KNN-Gaur|Replikasi-Baseline-KNN]] | [[06-Log-Training-Baseline-Gaur|Analisis Baseline Gaur]] | [[08-Blueprint-Arah-Penelitian-TA|Blueprint Arah TA]] | [[09-Peta-Kode-Code-Walkthrough|Peta Kode Walkthrough (Lampiran 4)]]
- ✍️ **Draf Naskah:** [[Bab-1-Pendahuluan]] | [[Bab-2-Tinjauan-Pustaka]] | [[Bab-3-Metodologi]] | [[Turnitin-Similarity-Ledger|Turnitin Similarity & Parafrase]]
- 💬 **Riwayat Prompt AI:** [[README|08-Prompt-History]] | [[Prompt-2026-11-23]]
- 📜 **Pedoman Resmi IF ITERA:** [[pedoman-ta-itera-lengkap|Buku Pedoman Lengkap]] | [[format-isi-ta]] | [[format-penulisan-unesco]] | [[dokumen-wajib]]
- 📖 **Pusat Panduan & Tutorial:** [[00-Index-Tutorial|12-Tutorial-Catatan (Indeks Master Tutorial Vault)]]
- 🛠️ **Panduan Sistem & Tooling:** [[tutorial-catatan|Panduan Vault & Hotkeys]] | [[obsidian-connect-google|Integrasi Google Workspace]]

---

## ☁️ Google Drive Direct Hub
- 👨‍🏫 [Portal Khusus Dosen Pembimbing (View Only - Siap Kirim)](https://drive.google.com/drive/folders/1whfbLHNvW9IOjwj5CHuFqsYg13P3FhNq)
- 🌐 [Buka Folder Master Tugas Akhir di Google Drive](https://drive.google.com/drive/folders/13i2Ww16FTgukID1djcfh5oTRfBqN7kb8)
- 📊 [Master Dashboard Sempro (Google Sheets)](https://docs.google.com/spreadsheets/d/1Iu5A5hGb0ZI4K9G48n8dv2W-SpkjMajS5go47I5D1cI)
- 📚 [Spreadsheet Studi Literatur (20 Paper)](https://docs.google.com/spreadsheets/d/1rLIr500lLbXeltTCZLF58RETTJvEALd6SFic8OUHtUY)
- 📦 [Spreadsheet Penjelasan Dataset DEAM](https://docs.google.com/spreadsheets/d/1ydH6Cnd-DG08dG2ix7CgPogitx_rmPxgzt0NudJbRHk)
