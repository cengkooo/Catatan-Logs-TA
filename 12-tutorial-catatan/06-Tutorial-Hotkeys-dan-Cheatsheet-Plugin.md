---
title: "Tutorial 06: Cheatsheet Tombol Pintas (Hotkeys) & Solusi Kendala"
tags:
  - tutorial
  - hotkeys
  - cheatsheet
  - troubleshooting
  - obsidian-plugins
date: 2026-11-24
---

# ⌨️ Tutorial 06: Cheatsheet Tombol Pintas (Hotkeys) & Solusi Kendala

Gunakan halaman ini sebagai kartu contekan cepat untuk seluruh pintasan keyboard (*hotkeys*), fungsi plugin, dan langkah penyelesaian masalah teknis di vault Anda.

---

## 🎯 1. Tabel Master Tombol Pintas (*Hotkeys Cheatsheet*)

Semua tombol pintas berikut sudah aktif secara global di dalam Obsidian Anda:

| Tombol Pintas | Modul / Plugin | Fungsi Utama | Kapan Digunakan? |
| :---: | :--- | :--- | :--- |
| **`Alt + T`** | **Google Tasks** | Menempelkan daftar to-do aktif tepat di posisi kursor Anda. | Di daily log pagi hari pada subbab target harian. |
| **`Alt + C`** | **Google Calendar** | Menempelkan agenda bimbingan/kuliah hari ini ke dalam tabel markdown. | Di daily log pagi hari pada subbab jadwal kalender. |
| **`Alt + S`** | **Google Sheets** | Menampilkan pop-up ringkasan persentase kemajuan Sprint dari Master Sheet Sempro. | Evaluasi progres sore atau malam hari. |
| **`Alt + Y`** | **Sync Tomorrow Macro** | Membaca agenda kalender besok dan otomatis mendaftarkannya ke Google Tasks HP. | Sebelum tidur di malam hari (ritual 21:45). |
| **`Alt + K`** | **Full Calendar** | Membuka antarmuka kalender visual penuh di tab utama Obsidian. | Merencanakan jadwal mingguan / sprint. |
| **`Alt + Shift + K`** | **Calendar Sidebar** | Membuka panel mini kalender di bilah samping kanan. | Navigasi cepat tanggal per tanggal. |
| **`Ctrl + P`** | **Command Palette** | Membuka kotak pencarian seluruh perintah Obsidian. | Mencari perintah apa pun saat lupa tombol pintas. |
| **`Ctrl + O`** | **Quick Switcher** | Mencari dan melompat ke berkas catatan mana pun secara instan. | Navigasi antar-catatan dalam 1 detik. |

---

## 🔄 2. Perintah Penting di Command Palette (`Ctrl + P`)

Jika lupa tombol kombinasi, cukup tekan **`Ctrl + P`**, lalu ketik kata kunci berikut:

1. **`Git: Backup Vault ke GitHub Sekarang`**  
   Melakukan *force commit* dan push instan seluruh catatan ke GitHub tanpa menunggu jeda waktu 15 detik.
2. **`Insert template`**  
   Menempelkan cetakan baku catatan (misal `Template-Paper-Review` atau `Template-Catatan-Konsep`).
3. **`Google: Cek Agenda Hari Ini`**  
   Menjalankan penarikan jadwal Google Calendar secara manual.
4. **`Google: Tarik Daftar Tasks Aktif`**  
   Menjalankan penarikan to-do Google Tasks secara manual.

---

## 🛠️ 3. Solusi Kendala Teknis (*Troubleshooting Guide*)

### Masalah 1: Muncul Peringatan "Google Token Expired / Invalid Grant"
* **Penyebab:** Masa berlaku token otentikasi Google Workspace OAuth telah kedaluwarsa setelah beberapa hari.
* **Solusi Cepat:**  
  1. Buka terminal PowerShell di folder root Tugas Akhir.
  2. Jalankan perintah:
     ```powershell
     python google_workspace/connect_workspace.py
     ```
  3. Browser akan terbuka otomatis. Login kembali dengan akun Google Anda dan klik "Izinkan". Token baru akan langsung tersimpan.

---

### Masalah 2: Tombol `Alt + T` atau `Alt + C` Tiba-tiba Tidak Merespons
* **Penyebab:** Plugin Obsidian belum memuat ulang konfigurasi setelah perubahan setting.
* **Solusi Cepat:**  
  1. Tekan tombol **`Ctrl + R`** di Obsidian untuk me-reload seluruh antarmuka.
  2. Coba tekan kembali `Alt + T`.

---

### Masalah 3: Git Mengeluarkan Pesan "Push Failed / Authentication Required"
* **Penyebab:** Git di laptop Anda belum memiliki hak akses (kredensial) ke akun GitHub Anda.
* **Solusi Cepat:**  
  1. Catatan Anda **tetap aman 100%** di commit lokal.
  2. Buka terminal, pastikan GitHub CLI terinstal atau login menggunakan GitHub Personal Access Token (PAT):
     ```powershell
     git push origin master
     ```
  3. Masukkan username dan token GitHub Anda saat jendela login Windows Credential Manager muncul.
