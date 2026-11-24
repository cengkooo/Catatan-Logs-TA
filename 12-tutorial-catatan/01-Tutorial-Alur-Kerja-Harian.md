---
title: "Tutorial 01: Alur Kerja Harian Mahasiswa (The Daily Loop)"
tags:
  - tutorial
  - daily-workflow
  - productivity
  - google-workspace
date: 2026-11-24
---

# ☀️ Tutorial 01: Alur Kerja Harian Mahasiswa (*The Daily Loop*)

Tutorial ini memandu Anda menjalani siklus kerja harian dari pagi hingga malam agar waktu Anda fokus menghasilkan luaran naskah dan eksperimen, bukan habis mengurus sistem.

---

## 🌅 Fase 1: Ritual Pagi (06:00 – 07:00 WIB)

### Langkah 1: Buka Catatan Hari Ini
1. Buka aplikasi **Obsidian**.
2. Di bilah samping kanan (*right sidebar*), perhatikan widget **Calendar**.
3. Klik pada tanggal hari ini. Catatan baru otomatis dibuat di folder `02-Daily-Logs/YYYY-MM-DD.md` menggunakan cetakan baku `Template-Daily-Log.md`.

### Langkah 2: Tarik Agenda Kuliah/Bimbingan Hari Ini
1. Arahkan kursor Anda tepat di bawah judul `## 🕒 Agenda Kalender (Google Calendar)`.
2. Tekan tombol kombinasi: **`Alt + C`**.
3. *Hasil:* Seluruh jadwal kuliah, asistensi praktikum (ASPRAK), dan slot bimbingan dari Google Calendar Anda akan tertempel otomatis dalam bentuk tabel markdown rapi.

### Langkah 3: Tarik Daftar Tugas Aktif (Google Tasks)
1. Arahkan kursor di bawah judul `## 🎯 Target Utama Hari Ini`.
2. Tekan tombol kombinasi: **`Alt + T`**.
3. *Hasil:* Daftar to-do prioritas dari Google Tasks HP Anda langsung muncul di catatan dengan kotak checklist `[ ]`.

---

## 💻 Fase 2: Eksekusi Siang & Sore (13:00 – 18:30 WIB)

### Jika Sedang Membaca Literatur / Paper Baru:
1. Jangan mencatat acak di sembarang tempat.
2. Buka folder `04-Literatur-Review/Papers/`, buat note baru: `NamaPenulisTahun-Topik.md`.
3. Terapkan template `Template-Paper-Review.md` (tekan `Ctrl + P` $\rightarrow$ ketik `Insert template`).
4. Isi ringkasan metode, dataset, dan keterbatasannya. Begitu disimpan dengan tag `#paper-review`, catatan tersebut **otomatis masuk ke tabel komparasi** di `04-Literatur-Review/Matriks-Sintesis.md`.

### Jika Sedang Menulis Naskah Proposal:
1. Buka folder `06-Naskah-Draft/`.
2. Tulis substansi bab pada file draf (misal `01-Skenario-Murni-Komputasional/Bab-1-Pendahuluan.md`).
3. Anda tidak perlu takut data hilang: setiap ketikan Anda otomatis di-commit dan di-push ke GitHub setiap 15 detik.

### Jika Sedang Menjalankan Eksperimen Koding:
1. Buka `05-Eksperimen/Peta-Kode-Code-Walkthrough.md` untuk melihat arsitektur modul yang sedang Anda uji.
2. Catat temuan metrik (misal nilai *Smoothness* $\mathcal{S}$ atau grafik traversal) pada subbab `## 🔬 Log Riset & Eksperimen Hari Ini` di daily log Anda.

---

## 🌙 Fase 3: Evaluasi Malam & Persiapan Esok Hari (21:45 WIB)

Aturan utama: **Maksimal 15 menit untuk evaluasi harian**. Jangan berlama-lama di dashboard.

1. **Centang Target yang Selesai:** Buka kembali catatan `02-Daily-Logs/YYYY-MM-DD.md`, ubah `[ ]` menjadi `[x]` pada target yang berhasil dicapai.
2. **Cek Status Sprint Master Sheets:**  
   Tekan **`Alt + S`**. Kotak notifikasi akan muncul di layar menampilkan ringkasan persentase kemajuan Sprint dari Google Sheets tanpa mengotori naskah Anda.
3. **Pindahkan Jadwal Besok ke To-Do Tasks:**  
   Tekan **`Alt + Y`**. Sistem akan membaca jadwal Google Calendar untuk besok pagi dan otomatis mendaftarkannya sebagai to-do di Google Tasks Anda, sehingga saat bangun tidur Anda sudah tahu apa yang harus dikerjakan!
