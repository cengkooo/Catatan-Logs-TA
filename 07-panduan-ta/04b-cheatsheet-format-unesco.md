---
title: "Cheat Sheet Visual: Spesifikasi Format Penulisan Naskah UNESCO (BAB 8)"
tags:
  - panduan-ta
  - unesco
  - format-penulisan
aliases:
  - format-penulisan-unesco
  - Cheat Sheet Format UNESCO
---
# 📐 Format Penulisan UNESCO (BAB 8) — Cheat Sheet Praktis

> **Aturan Wajib Perpustakaan & FTI ITERA:** Seluruh draf naskah LaTeX (`thesis.tex`) wajib mengikuti spesifikasi ukuran buku UNESCO.

---

## ⚡ 1. Cheat Sheet Spesifikasi Kertas & Margin

```text
               ┌─────────────────────── 15,5 cm ────────────────────────┐
               │                                                        │
               │                   Margin Atas: 2 cm                    │
               │         ┌────────────────────────────────────┐         │
               │         │                                    │         │
               │  Sisi   │                                    │  Sisi   │
               │  Dalam  │        Times New Roman 11 pt       │  Luar   │
  Tinggi 23 cm │ (Jilid) │             Spasi 1,5              │ (Outer) │
               │ 2,5 cm  │                                    │  2 cm   │
               │         │                                    │         │
               │         └────────────────────────────────────┘         │
               │                  Margin Bawah: 2 cm                    │
               │                                                        │
               └────────────────────────────────────────────────────────┘
```

| Parameter | Aturan Baku ITERA |
| :--- | :--- |
| **Ukuran Kertas** | **UNESCO (Lebar 15,5 cm $\times$ Tinggi 23 cm)** |
| **Jenis Kertas** | Putih, tebal 75 gsm |
| **Pencetakan** | Versi final wajib bolak-balik (*Mirror Margins*); **draf Sempro/Sidang boleh dicetak satu sisi (*single-sided*)** (Tabel 8.2) |
| **Margin Atas** | **2,0 cm** |
| **Margin Bawah** | **2,0 cm** |
| **Margin Luar (*Outer*)** | **2,0 cm** |
| **Margin Dalam (*Gutter / Jilid*)** | **2,5 cm** |

---

## 🔤 2. Tipografi & Tata Huruf

* **Font Utama:** **Times New Roman**
* **Ukuran Font:**
  * **Judul BAB:** **14 pt**, **BOLD**, KAPITAL, Rata Tengah (*Center*).
  * **Sub-bab:** **11 pt**, **BOLD**, Title Case, Rata Kiri.
  * **Sub-sub-bab:** **11 pt**, **BOLD**, Title Case, Rata Kiri.
  * **Isi Paragraf:** **11 pt**, Normal, Rata Kiri-Kanan (*Justify*).
  * **Keterangan Tabel & Gambar:** **10–11 pt** (label *"Tabel X.X"* dicetak **bold**).
* **Spasi Baris:**
  * **1,5 spasi:** Untuk seluruh teks isi bab.
  * **1,0 spasi (Tunggal):** Untuk abstrak, kutipan langsung panjang ($>4$ baris), isi dalam tabel, dan daftar pustaka.
* **Indentasi Paragraf Baru:** Menjorok ke dalam **1 cm** (atau 1 tab konsisten).
* **Jarak Antar-paragraf:** **0 pt** (jangan diberi enter dobel antar-paragraf).

---

## 🖼️ 3. Aturan Elemen Visual & Rumus

### A. Tabel
* Nomor & Judul diletakkan di **ATAS** tabel, rata tengah (*center*), *bold*.
* Contoh: **Tabel 3.1 Parameter Eksperimen KNN**
* Sumber data ditulis di **bawah** tabel, font 10 pt, *italic* (misal: *Sumber: Aljanaki et al. (2017)*).

### B. Gambar & Diagram
* Nomor & Judul diletakkan di **BAWAH** gambar, rata tengah (*center*), *bold*.
* Contoh: **Gambar 3.2 Diagram Alur Sistem Playlist Generation**
* Resolusi minimal **300 dpi** (supaya tidak pecah saat dicetak).

### C. Persamaan Matematis (Equation)
* Wajib diketik menggunakan formula LaTeX / Equation editor.
* Nomor persamaan diletakkan di **ujung kanan** dalam tanda kurung:
  $$ \text{Sim}(\vec{\mathbf{v}}_i, \vec{\mathbf{u}}_k) = \frac{\vec{\mathbf{v}}_i \cdot \vec{\mathbf{u}}_k}{\|\vec{\mathbf{v}}_i\| \|\vec{\mathbf{u}}_k\|} \tag{3.1} $$
* Wajib dirujuk di paragraf sebelumnya: *"Perhitungan kemiripan sudut dihitung dengan Persamaan (3.1)."*

---

## 🔢 4. Penomoran Halaman (Tabel 8.4)

| Bagian Dokumen | Jenis / Format Nomor | Posisi Nomor Halaman |
| :--- | :--- | :--- |
| **Bagian Awal (*Front Matter*)** (Kata Pengantar, Daftar Isi, Abstrak) | Romawi kecil (`i, ii, iii...`) | **Tengah bawah** halaman (*center-footer*) |
| **Halaman Sampul (*Cover*)** | Tidak diberi nomor fisik | — *(tetap dihitung sebagai halaman i)* |
| **Halaman Pertama Tiap Bab Baru** | Angka Arab (`1, 2, ...`) | **Tengah bawah** halaman (*center-footer*) |
| **Halaman Lanjutan Isi & Akhir Bab** | Angka Arab (`2, 3, ...`) | **Pojok atas sisi luar** (kanan atas di halaman ganjil, kiri atas di halaman genap pada cetak bolak-balik) |

---

## 📚 5. Sitasi & Referensi (Wajib Standar IEEE)

* **Gaya Sitasi:** Format **IEEE** dengan nomor dalam kurung siku `[1]`, `[2]`.
* **Kuantitas Referensi:** **Minimal 15 sumber pustaka primer** (jurnal / prosiding konferensi).
* **Kebaruan:** **Minimal 70% referensi berasal dari 3 tahun terakhir**.
* Di LaTeX: cukup ketik `\cite{citekey}` yang tersinkron otomatis dari Zotero!
