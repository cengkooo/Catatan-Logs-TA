---
title: "Panduan Standar Format Penulisan Naskah UNESCO (BAB 8) IF ITERA"
tags:
  - panduan-ta
  - unesco
  - format-penulisan
  - tabel-8-4
  - margin
  - font-11pt
source_ref: "Pedoman TA IF ITERA Bab 8 (Changelog 1.2.0)"
---

# 📐 Format Penulisan Naskah Standar UNESCO (BAB 8)

> **Regulasi Resmi (Changelog 1.2.0 & Subbab 8.4):** Seluruh naskah Tugas Akhir Program Studi Teknik Informatika ITERA (baik draf seminar proposal maupun laporan akhir) wajib disusun menggunakan **Format Buku UNESCO (15,5 cm $\times$ 23 cm)**.

---

## ⚡ 1. Spesifikasi Fisik Kertas & Margin (Tabel 8.2)

```text
               ┌─────────────────────── 15,5 cm ────────────────────────┐
               │                                                        │
               │                   Margin Atas: 2,0 cm                  │
               │         ┌────────────────────────────────────┐         │
               │         │                                    │         │
               │  Sisi   │                                    │  Sisi   │
               │  Dalam  │        Times New Roman 11 pt       │  Luar   │
  Tinggi 23 cm │ (Jilid) │             Spasi 1,5              │ (Outer) │
               │ 2,5 cm  │                                    │ 2,0 cm  │
               │         │                                    │         │
               │         └────────────────────────────────────┘         │
               │                  Margin Bawah: 2,0 cm                  │
               │                                                        │
               └────────────────────────────────────────────────────────┘
```

| Parameter Layout | Aturan Baku ITERA (Changelog 1.2.0) |
| :--- | :--- |
| **Ukuran Kertas** | **UNESCO (Lebar 15,5 cm $\times$ Tinggi 23,0 cm)** |
| **Jenis / Berat Kertas** | Kertas HVS Putih tebal **75 gsm** |
| **Pencetakan Versi Final** | **Wajib Bolak-balik (*Double-sided / Mirror Margins*)** |
| **Pencetakan Versi Draf** | **Boleh Satu Sisi (*Single-sided*)** untuk draf Seminar Proposal dan Sidang Akhir |
| **Margin Atas (*Top*)** | **2,0 cm** |
| **Margin Bawah (*Bottom*)** | **2,0 cm** |
| **Margin Sisi Luar (*Outer*)** | **2,0 cm** |
| **Margin Sisi Dalam (*Inner / Gutter*)** | **2,5 cm** (space untuk penjilidan) |

---

## 🔢 2. Aturan Baku Penomoran Halaman (Tabel 8.4)

> [!IMPORTANT]
> Changelog [1.2.0] menetapkan penomoran halaman yang seragam untuk menyesuaikan cetak bolak-balik format UNESCO:

| Bagian Dokumen | Format Nomor | Posisi Nomor Halaman |
| :--- | :--- | :--- |
| **Bagian Awal (*Front Matter*)** | Angka Romawi kecil (`i, ii, iii, iv, …`) | **Tengah bawah halaman (*center-footer*)** |
| **Halaman Sampul (*Cover*)** | Tidak diberi nomor fisik | — *(tetap dihitung sebagai halaman i)* |
| **Bagian Isi & Akhir (*Main & Back*)** | Angka Arab (`1, 2, 3, …`) | **Pojok atas sisi luar**: **Kanan atas** pada halaman ganjil, **Kiri atas** pada halaman genap (*cetak bolak-balik*) |
| **Halaman Awal Bab (*Chapter Head*)** | Angka Arab (`1, 2, 3, …`) | **Tengah bawah halaman (*center-footer*)** *(tidak di pojok atas)* |

*Penomoran halaman dimulai ulang dari angka 1 saat memasuki Bagian Isi (Bab I). Daftar Pustaka dan Lampiran melanjutkan nomor halaman bagian isi.*

---

## 🔤 3. Tipografi & Tata Letak Paragraf (Tabel 8.3 & Changelog 1.1.1)

* **Jenis Huruf Utama:** **Times New Roman**
* **Ukuran Font:**
  * **Judul BAB:** **14 pt**, **BOLD**, KAPITAL SEMUA, Rata Tengah (*Center*).
  * **Sub-bab:** **11 pt**, **BOLD**, Title Case, Rata Kiri.
  * **Sub-sub-bab:** **11 pt**, **BOLD**, Title Case, Rata Kiri.
  * **Isi Teks Paragraf:** **11 pt**, Regular, Rata Kiri-Kanan (*Justify*).
  * **Label Tabel & Gambar:** **10–11 pt** (label *"Tabel X.X"* / *"Gambar X.X"* dicetak **bold**).
  * **Potongan Kode (*Code Snippet*):** Monospace (Consolas / Courier New), **10–11 pt**.
* **Spasi Baris (*Line Spacing*):**
  * **1,5 spasi:** Untuk seluruh teks isi naskah bab.
  * **1,0 spasi (Tunggal):** Untuk abstrak, kutipan langsung panjang ($>4$ baris), isi dalam tabel, potongan kode program, dan daftar pustaka.
* **Indentasi Paragraf Baru:** Menjorok ke dalam **1,0 cm** (atau 1 tab konsisten).
* **Jarak Antar-paragraf:** **0 pt** (dilarang menggunakan spasi ganda antar-paragraf).

---

## 🖼️ 4. Aturan Elemen Naskah: Tabel, Gambar & Persamaan

### A. Tabel
* Nomor & Judul diletakkan di **ATAS** tabel, rata tengah (*center*), *bold*, Title Case.
* Contoh: **Tabel 3.1 Parameter Eksperimen KNN Gaur**
* Sumber data diletakkan di **bawah** tabel, ukuran 10 pt, *italic* (contoh: *Sumber: Gaur & Donnelly (2020)*).

### B. Gambar & Diagram
* Nomor & Judul diletakkan di **BAWAH** gambar, rata tengah (*center*), *bold*, Title Case.
* Contoh: **Gambar 2.1 Visualisasi Trajectory 2D Valence-Arousal**
* Resolusi gambar minimal **300 dpi** agar tajam saat dicetak fisik.

### C. Persamaan Matematis (*Equation*)
* Wajib diketik menggunakan Equation Editor / LaTeX formula.
* Diberi nomor di **sisi kanan** dengan tanda kurung per bab:
  $$ \text{Smoothness} = \frac{1}{N-1} \sum_{i=1}^{N-1} \|\vec{\mathbf{v}}_{i+1} - \vec{\mathbf{v}}_i\|_2 \tag{3.2} $$
* Wajib dirujuk secara eksplisit dalam teks narasi sebelum atau sesudahnya.

---

## 📚 5. Standar Sitasi & Daftar Pustaka (Subbab 8.7)

* **Gaya Sitasi:** Format **IEEE Style** (menggunakan tanda kurung siku berangka numerik `[1]`, `[2]`).
* **Kuantitas Pustaka:** **Minimal 15 sumber pustaka primer** (artikel jurnal ilmiah atau prosiding konferensi bereputasi).
* **Kebaruan Literatur:** **Minimal 70% referensi berasal dari 3 tahun terakhir**.
* Sangat disarankan mengelola referensi menggunakan Zotero / Mendeley dan disinkronkan ke `references.bib`.
