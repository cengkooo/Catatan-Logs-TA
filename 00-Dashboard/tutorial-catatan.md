---
title: Panduan & Tutorial Penggunaan Vault Catatan-Memori-Logs
author: Andryano
tags:
  - tutorial
  - obsidian
  - workflow
  - tugas-akhir
  - hotkeys
created: 2026-11-16
updated: 2026-11-16
---

# 📚 Panduan & Tutorial Penggunaan Vault Catatan-Memori-Logs

Selamat datang di pusat komando (*Mission Control*) Tugas Akhir Anda! 

Vault ini telah dirancang khusus untuk menyelaraskan **Google Sheets SEMPRO** (`1Iu5A5hGb...`), **Google Tasks & Calendar**, draf naskah **LaTeX**, serta plugin cerdas di Obsidian.

---

## 🗺️ 1. Peta & Fungsi Struktur Folder

| Folder | Isi & Fungsinya |
| :--- | :--- |
| **`00-Dashboard/`** | **Pusat Navigasi:** Berisi `Master-Dashboard.md` (menampilkan to-do yang belum selesai via Dataview) dan `Roadmap-Sempro.md` (peta milestone Sprint 1-4). |
| **`01-Sprints/`** | **Target Per Bab:** Memuat target checklist per sprint (`Sprint-1-Bab1-EDA` s/d `Sprint-4-Final-Sidang`). |
| **`02-Daily-Logs/`** | **Catatan Harian:** Tempat log harian tanggal per tanggal yang otomatis terbuat saat Anda mengklik kalender widget. |
| **`03-Bimbingan/`** | **Interaksi Dosen:** `Notulensi-Bimbingan.md` untuk arahan dosen dan `Bank-Pertanyaan-Dosen.md` untuk persiapan sidang Sempro. |
| **`04-Literatur-Review/`** | **Manajemen Paper:** `Matriks-Sintesis.md` (tabel komparasi otomatis Dataview) dan subfolder `Papers/` untuk catatan ringkasan jurnal. |
| **`05-Eksperimen/`** | **Log Teknis:** Eksplorasi dataset `DEAM`, formulasi matematika `Ekstraksi-Trajectory`, dan replikasi model `Gaur & Donnelly`. |
| **`06-Naskah-Draft/`** | **Draf Mentah Bab:** Tempat menulis draf Bab 1, 2, dan 3 sebelum disalin ke template LaTeX (`chapters/babX.tex`). |
| **`07-panduan-ta/`** | **Regulasi & Pedoman:** Penyelarasan pedoman TA IF ITERA versi Changelog 1.2.0 (format UNESCO, etika AI, alur Sempro/Sidang). |
| **`08-Prompt-History/`** | **Riwayat Interaksi AI:** Arsip transkrip prompt harian untuk deklarasi integritas Lampiran 2 ITERA. |
| **`09-todolist/`** | **Sistem Eksekusi Modular:** Panduan fase kerja mikro (Bab 1-3, koding DEAM, administrasi Sempro). |
| **`10-Slides/`** | **Materi Presentasi:** Bahan slide Sempro (Typst Touying / PPTX) alokasi 10 menit. |
| **`11-Catatan-Belajar/`** | **Second Brain & Tech Stack:** Catatan pembelajaran mandiri (Konsep Teori, Tech Stack, & Sintesis Ide) dengan indexing Dataview otomatis. |
| **`99-Templates/`** | **Cetakan Otomatis:** Template untuk Daily Log, Paper Review, Catatan Konsep, dan Tech Stack. |

---

## ⌨️ 2. Tombol Pintas (*Hotkeys*) Siap Pakai

Semua tombol di bawah ini sudah aktif secara otomatis:

| Tombol Pintas | Fungsi | Hasil Kerja |
| :--- | :--- | :--- |
| **`Alt + T`** | **Google Tasks** | Menempelkan daftar to-do aktif tepat di posisi kursor Anda. |
| **`Alt + C`** | **Google Calendar** | Menempelkan agenda bimbingan/kuliah hari ini ke catatan Anda. |
| **`Alt + S`** | **Status Sprint Sheets** | Menampilkan pop-up ringkasan progres Master Dashboard Sempro tanpa mengotori teks catatan. |
| **`Alt + Y`** | **Sync Tomorrow Macro** | Memindahkan otomatis jadwal kalender besok menjadi to-do Google Tasks. |
| **`Alt + K`** | **Buka Kalender Penuh** | Membuka tampilan Full Calendar di tab utama Obsidian. |
| **`Alt + Shift + K`** | **Kalender Sidebar** | Membuka kalender di bilah samping kanan Obsidian. |

> [!TIP]
> **Lupa Tombol?** Tekan **`Ctrl + P`**, lalu ketik kata kunci **`Google:`** atau **`Open Calendar`**.

---

## ☀️ 3. Alur Kerja Harian Anda (*The Daily Loop*)

### Langkah 1: Buka Catatan Hari Ini (Pagi Hari)
1. Buka Obsidian.
2. Di sidebar sebelah kanan, ada widget **Calendar**. Klik tanggal hari ini (atau buka folder `02-Daily-Logs/`).
3. File catatan harian otomatis terbuat menggunakan `Template-Daily-Log.md`.

### Langkah 2: Tarik Agenda & To-Do
1. Klik di bawah judul `## 🕒 Agenda Kalender`, tekan **`Alt + C`** $\rightarrow$ jadwal hari ini langsung tertempel.
2. Klik di bawah judul `## 📋 To-Do Aktif`, tekan **`Alt + T`** $\rightarrow$ daftar tugas dari Google Tasks langsung tertempel.

### Langkah 3: Menulis Draf / Membaca Paper (Siang & Sore)
* **Kalau lagi baca paper:** Buat catatan baru di `04-Literatur-Review/Papers/` pakai `Template-Paper-Review.md`. Begitu disimpan, tabel di `Matriks-Sintesis.md` langsung bertambah otomatis!
* **Kalau lagi merancang draf TA:** Buka `06-Naskah-Draft/Bab-X.md`, tulis ide Anda dengan cepat memakai wikilinks `[[Gaur2020-Mood-Arc]]` atau rumus matematis.

### Langkah 4: Evaluasi Progres (Malam Hari)
* Tekan **`Alt + S`** untuk melihat status kemajuan sprint.
* Tekan **`Alt + Y`** agar agenda besok otomatis masuk ke Google Tasks HP Anda.

---

## ⚠️ Catatan Pemeliharaan Penting

1. **Reload Obsidian Sekali Saja:**
   Jika baru menyalakan Obsidian, tekan `Ctrl + R` agar seluruh plugin dan hotkey sinkron.
2. **Jika Token Google Expired:**
   Jika muncul peringatan token expired saat menekan `Alt + T` atau `Alt + C`, jalankan perintah berikut di terminal:
   ```powershell
   python google_workspace/connect_workspace.py
   ```
