---
title: "Panduan Kebijakan Open Data & Publikasi Riset (Subbab 5.9) IF ITERA"
tags:
  - panduan-ta
  - open-data
  - repositori
  - github
  - publikasi
source_ref: "Pedoman TA IF ITERA Subbab 5.9"
---

# 🌐 Kebijakan Open Data & Keterbukaan Publikasi Riset

> **Kewajiban Mutlak (Subbab 5.9):** Sebagai wujud transparansi ilmiah dan reproduksibilitas riset dalam bidang komputasi, seluruh data penelitian, dataset, kode sumber program (*source code*), model terlatih, dan artefak digital Tugas Akhir **wajib dipublikasikan secara terbuka**.

---

## ⚡ 1. Prinsip Dasar Open Data Riset ITERA

1. **Reproduksibilitas:** Pihak luar atau peneliti lain harus mampu mereplikasi eksperimen dan memverifikasi klaim metrik yang tertulis di naskah laporan.
2. **Keterbukaan Akses (*Open Access*):** Publikasi artefak dilakukan melalui platform repositori publik terpercaya (GitHub, Zenodo, Figshare, HuggingFace, atau Repositori Digital ITERA).
3. **Batas Waktu Wajib:** Seluruh data dan kode sumber wajib diunggah dan dapat diakses publik **paling lambat 30 hari kalender setelah tanggal kelulusan Sidang Akhir**.
4. **Pemberian Lisensi Terbuka:** Repositori kode wajib menyertakan lisensi open-source yang jelas (misal: MIT License, Apache 2.0, atau GNU GPL v3).

---

## 🔒 2. Klasifikasi Data & Penanganan Data Mitra

| Kategori Data | Karakteristik | Mekanisme Publikasi |
| :--- | :--- | :--- |
| **Data Terbuka (*Open*)** | Data publik (e.g. DEAM Dataset, Audio/MIDI publik, data scraping terbuka). | Unggah penuh ke GitHub / Zenodo dengan DOI. |
| **Data Terbatas (*Restricted*)** | Data instansi/mitra dengan batasan privasi sebagian (e.g. data transaksi anonim). | Dilakukan anonimisasi (*data scrubbing/masking*) sebelum dipublikasikan. |
| **Data Tertutup (*Confidential*)** | Rahasia dagang industri, data medis sensitif, kredensial API, atau data pertahanan. | Hanya arsitektur kode dan *dummy sample data* yang diunggah; data asli dienkripsi/disimpan lokal. |

---

## 📝 3. Persetujuan Tertulis Mitra (Lampiran 5)

Jika Tugas Akhir melibatkan mitra eksternal (perusahaan/instansi):
* Mahasiswa **wajib** meminta persetujuan *open data* sejak awal melalui **Surat Kesediaan Mitra (Lampiran 5)**.
* Jika mitra menolak keterbukaan data:
  1. Mahasiswa melakukan negosiasi anonimisasi data (*dummy data / blurred features*).
  2. Mengganti mitra penelitian.
  3. Mengalihkan jalur ke Bentuk 1 (Penelitian Konvensional menggunakan dataset publik independen).

---

## 📦 4. Checklist Repositori Riset (Standar GitHub IF ITERA)

- [ ] `README.md` memuat: Judul riset, identitas mahasiswa/pembimbing, ringkasan abstrak, arsitektur sistem, dan petunjuk instalasi (*quickstart*).
- [ ] Berkas dependensi: `requirements.txt` / `pyproject.toml` / `environment.yml`.
- [ ] Struktur folder rapi: `/data` (petunjuk download dataset), `/src` (kode modular), `/notebooks` (analisis & visualisasi), `/tests` (unit test).
- [ ] Berkas lisensi: `LICENSE` (MIT License / Apache 2.0).
- [ ] Tautan rujukan ke naskah laporan atau draf publikasi ilmiah.
