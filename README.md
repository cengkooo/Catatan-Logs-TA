---
title: "Panduan Master Obsidian Vault — Catatan-Memori-Logs"
tags:
  - obsidian
  - second-brain
  - documentation
  - tugas-akhir
author: "Andryano (123140205)"
updated: 2026-11-24
---

# 🧠 Master Obsidian Vault: Catatan-Memori-Logs
**Second Brain, Manajemen Riset, dan Pusat Kendali Tugas Akhir IF ITERA**

Repositori vault ini merupakan sistem manajemen pengetahuan (*Knowledge Management System*) dan pusat eksekusi teknis untuk penelitian Tugas Akhir Program Studi Teknik Informatika Institut Teknologi Sumatera (ITERA):

> **Topik Penelitian:**  
> *Mood-Arc Playlist Generation Berbasis Dynamic Mood Trajectory (Dataset DEAM, KNN & Trajectory Alignment)*  
> **Dosen Pembimbing:** Hafiz Budi Firmansyah, S.Kom., M.Sc.  
> **Mahasiswa:** Andryano (NIM: 123140205)

---

## 🗺️ Peta Struktur Direktori Vault

```
Catatan-Memori-Logs/
│
├── 00-Dashboard/          ◄── Pusat kendali utama, roadmap sempro, & mode emergency
│   ├── Master-Dashboard.md
│   ├── EMERGENCY-SEMPRO.md
│   └── Roadmap-Sempro.md
│
├── 01-Sprints/            ◄── Perencanaan sprint kerja (Sprint 1 s.d. Sprint 4)
│
├── 02-Daily-Logs/         ◄── Rekam log harian aktivitas, target, dan jurnal kendala
│   ├── 2026-11-16.md s.d. 2026-11-25.md
│
├── 03-Bimbingan/          ◄── Catatan bimbingan dosen, bank Q&A, tracker prasyarat TASYS
│   ├── Notulensi-Bimbingan.md
│   ├── Tracker-Prasyarat-Sempro.md
│   ├── Bank-Pertanyaan-Dosen.md
│   └── Lembar-Diskusi-Skenario-User-Study.md
│
├── 04-Literatur-Review/   ◄── Matriks sintesis 21 paper IEEE/MIR, kamus notasi, spreadsheet
│   ├── Matriks-Sintesis.md
│   └── Kamus-Notasi-Glosarium.md
│
├── 05-Eksperimen/         ◄── Catatan teknis koding, analisis dataset DEAM, baseline Gaur
│   ├── Replikasi-Baseline-KNN.md
│   ├── Dataset-DEAM.md
│   ├── Ekstraksi-Trajectory.md
│   └── Peta-Kode-Code-Walkthrough.md (Persiapan bobot 10% sidang)
│
├── 06-Naskah-Draft/       ◄── Draf naskah proposal Bab I–III format UNESCO & pemantauan Turnitin
│   ├── 01-Skenario-Murni-Komputasional/ (Bab I–III versi metrik matematis objektif)
│   ├── 02-Skenario-Dual-Evaluation-User-Study/ (Bab I–III versi + User Listening Study)
│   ├── Turnitin-Similarity-Ledger.md (Target similarity ≤ 25%, kutipan ≤ 10%)
│   └── README.md
│
├── 07-panduan-ta/         ◄── Pengetahuan regulasi resmi Prodi IF ITERA (Changelog 1.2.0)
│   ├── 00-index-panduan-ta.md
│   ├── 01-kebijakan-ai-dan-integritas.md
│   ├── 02-alur-dan-syarat-sempro.md
│   ├── 04-format-penulisan-unesco.md (Tabel 8.4 Penomoran Halaman)
│   └── pedoman-ta-itera-lengkap.md
│
├── 08-Prompt-History/     ◄── Audit trail penggunaan AI (Lampiran 2 Pedoman TA)
│
├── 09-todolist/           ◄── Mission engine modular fase kerja (Phase 01 s.d. 05)
│   └── 00-Index-Todolist.md
│
├── 10-Slides/             ◄── Blueprint slide sempro 10 menit & amunisi pertahanan 30 menit
│   ├── 02-Master-Blueprint-Slide-Sempro.md (14 Slide presisi waktu)
│   └── 03-Speaker-Notes-Dan-Antisipasi-QnA.md
│
├── 11-Catatan-Belajar/    ◄── Personal study hub: konsep teori & ekstraksi fitur audio
│   ├── 00-Index-Catatan.md
│   ├── Model-Emosi-Sirkumpleks-Russell-1980.md
│   └── Librosa-Audio-Feature-Extraction.md
│
└── 99-Templates/          ◄── Templat standar penulisan note baru (Daily Log, Konsep, Paper)
```

---

## ⚙️ Ekosistem Plugin Obsidian yang Terpasang

Vault ini menggunakan serangkaian *community plugins* untuk otomatisasi riset:

1. **Dataview:** Menampilkan rekap otomatis to-do list, tabel literatur, dan status sprint melalui query markdown.
2. **Omnisearch:** Pencarian teks semantik super-cepat di seluruh isi catatan dan PDF literatur.
3. **LaTeX Suite:** Pengetikan rumus matematika LaTeX berkecepatan tinggi dengan tab-trigger snippets.
4. **Calendar & Full Calendar:** Visualisasi time-blocking jadwal harian dan tenggat akademik.
5. **Obsidian Shell Commands:** Eksekusi skrip kompilasi LaTeX, Typst, dan sinkronisasi Git langsung dari dalam vault.

---

## 🛡️ Aturan Gitignore & Sinkronisasi Version Control

Untuk mencegah *merge conflict*, bloat repositori, dan kebocoran file sementara, berkas `.gitignore` telah dikonfigurasi dengan aturan berikut:

### 🚫 Berkas yang Wajib Diabaikan (`.gitignore`):
* `.obsidian/workspace.json` & `workspace-mobile.json`  
  *(Layout jendela dan tab aktif yang selalu berubah setiap kali note diklik).*
* `.obsidian/cache/` & `.trash/`  
  *(Cache internal Obsidian dan tong sampah lokal).*
* `.obsidian/plugins/omnisearch/index/` & `*.db`  
  *(Basis data indeks pencarian Omnisearch yang membesar hingga puluhan MB).*
* `.obsidian/plugins/**/data-backup*.json`  
  *(Berkas backup otomatis plugin).*

### ✅ Berkas Konfigurasi yang Tetap Dilacak Git:
* Seluruh berkas catatan Markdown (`*.md`) di semua subfolder.
* Setelan plugin inti & tema: `app.json`, `appearance.json`, `community-plugins.json`, `core-plugins.json`, `hotkeys.json`.
* Kode sumber plugin lokal: `.obsidian/plugins/*/{main.js,manifest.json,styles.css}`.

---

## 🔄 Otomatisasi Backup GitHub Setiap Perubahan (CRUD)

Vault ini telah dilengkapi dengan sistem pencadangan otomatis ke GitHub setiap kali terjadi aksi **Create, Read/Update, Delete, atau Rename (CRUD)** terhadap berkas catatan:

### 1. Cara Kerja Otomatis di Dalam Obsidian (Native Event Trigger)
Plugin `obsidian-shellcommands` telah dikonfigurasi untuk menangani event:
* `file-created` (Saat membuat note baru)
* `file-modified` (Saat menyunting atau mengetik isi note)
* `file-deleted` (Saat menghapus note)
* `file-renamed` (Saat mengganti nama note)

> **Mekanisme Debounce (15 Detik):**  
> Sistem akan menunggu selama 15 detik setelah Anda selesai mengetik/berhenti mengedit, lalu otomatis mengeksekusi skrip `scripts/sync_vault_now.ps1` (`git add -A`, `git commit`, dan `git push`) secara hening di latar belakang serta memunculkan notifikasi di pojok kanan bawah.

### 2. Pemicu Manual Lewat Obsidian Command Palette
Anda dapat melakukan sinkronisasi instan kapan saja:
1. Tekan `Ctrl + P` di Obsidian.
2. Ketik: **`Git: Backup Vault ke GitHub Sekarang`** lalu tekan `Enter`.

### 3. Background Watcher Eksternal (PowerShell)
Bila Anda sering menyunting berkas Markdown dari luar Obsidian (misal via VS Code atau terminal), jalankan background watcher:
```powershell
powershell -ExecutionPolicy Bypass -File "D:\Kuliah\Semester 7\Tugas Akhir\Proposal Tugas Akhir\scripts\watch_vault_git_sync.ps1"
```

### 4. Menghubungkan ke Repositori GitHub Anda (Sekali Saja)
Vault lokal sudah diinisialisasi sebagai repositori Git. Untuk menghubungkannya ke GitHub:
```powershell
cd "D:\Kuliah\Semester 7\Tugas Akhir\Proposal Tugas Akhir\Catatan-Memori\Catatan-Memori-Logs"
git remote add origin https://github.com/<USERNAME-ANDA>/<NAMA-REPO-VAULT>.git
git push -u origin master
```

---

## 🚀 Panduan Alur Kerja Harian Mahasiswa

1. **Pagi (06:00–07:00):** Buka `02-Daily-Logs/YYYY-MM-DD.md`, cek target prioritas hari ini.
2. **Bimbingan Dosen:** Buka `03-Bimbingan/Notulensi-Bimbingan.md` dan `Tracker-Prasyarat-Sempro.md` untuk mencatat arahan dan memantau status TASYS.
3. **Eksperimen & Koding:** Rujuk ke `05-Eksperimen/Peta-Kode-Code-Walkthrough.md` saat menguji modul Python.
4. **Malam (21:45):** Perbarui checklist deliverable harian dan catat kendala sebelum menutup hari.
