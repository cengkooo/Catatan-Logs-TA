---
title: "Turnitin Similarity Ledger & Log Parafrase"
tags:
  - turnitin
  - similarity
  - integritas-akademik
  - anti-plagiasi
  - etika-ta
created: 2026-11-23
updated: 2026-11-23
---

# 🛡️ Turnitin Similarity Ledger & Log Parafrase

Dokumen ini memantau secara berkala hasil uji kemiripan (*similarity index*) naskah Tugas Akhir menggunakan Turnitin/iThenticate sesuai batas keras etika akademik Program Studi Teknik Informatika ITERA:
* **Batas Maksimum Similarity Index:** $\le \mathbf{25\%}$ (setelah filter eksklusi daftar pustaka dan kecocokan kecil $<1\%$).
* **Batas Maksimum Kutipan Langsung:** $\le \mathbf{10\%}$ dari total panjang naskah.
* **Prinsip:** Dilarang keras fabrikasi teks atau menyalin mentah paragraf paper/web. Seluruh rujukan diolah melalui parafrase kritis berbahasa Indonesia ilmiah baku.

---

## 📊 Riwayat Pengecekan Turnitin

| Iterasi Uji | Tanggal | Bagian Naskah yang Diuji | Similarity (%) | Direct Quotes (%) | Status Regulasi | Tautan Berkas Laporan |
| :-: | :---: | :--- | :-: | :-: | :---: | :--- |
| **Run 1** | 2026-11-20 | Bab 1 Pendahuluan (Draft Awal) | *~18%* | *2%* | `LOLOS BAB 1` | `arsip/turnitin_bab1_v1.pdf` |
| **Run 2** | 2026-11-22 | Bab 1 + Bab 2 (Tinjauan Pustaka) | *~22%* | *4%* | `PERLU PARAFRASE` | `arsip/turnitin_bab1_bab2.pdf` |
| **Run Final** | 2026-11-23 | Draf Lengkap Bab 1–3 (`laporan-ta.pdf`) | **Target $\le 15\%$** | **$\le 5\%$** | `SIAP DAFTAR` | `arsip/Turnitin_Sempro_Final.pdf` |

---

## ✍️ Log Catatan Parafrase Kritis

Gunakan bagian ini untuk mencatat kalimat/paragraf yang terdeteksi kecocokan tinggi oleh Turnitin beserta versi perbaikannya.

### 📌 Kasus Parafrase #1: Definisi Model Emosi Sirkumpleks Russell (1980)
* **Sumber Terdeteksi:** Jurnal terjemahan / paper psikologi emosi musik.
* **Teks Asli Terdeteksi ($>70\%$ kemiripan):**
  > *"Model sirkumpleks afek mengusulkan bahwa semua kondisi afektif muncul dari dua sistem neurofisiologis independen, satu terkait dengan kenikmatan dan yang lain dengan aktivasi."*
* **Hasil Parafrase Akademik Baru (Bebas Plagiasi):**
  > *"Russell (1980) mempostulatkan bahwa respon afektif manusia dapat dipetakan secara terpadu ke dalam dua dimensi ortogonal kontinu, yaitu polaritas kesenangan (valence) dan tingkat intensitas energi fisiologis (arousal), sehingga memungkinkan representasi keadaan emosi sebagai koordinat Cartesian aljabar."*

---

### 📌 Kasus Parafrase #2: Kelemahan Baseline Gaur & Donnelly (2020)
* **Sumber Terdeteksi:** Repositori publik / draf lama.
* **Teks Asli Terdeteksi:**
  > *"Algoritma Gaur dan Donnelly memiliki kelemahan karena lagu yang mereka hasilkan sering kali melompat-lompat dan tidak konsisten energinya."*
* **Hasil Parafrase Akademik Baru (Bebas Plagiasi):**
  > *"Keterbatasan pendekatan interpolasi lintasan emosi Gaur dan Donnelly (2020) berakar pada penggunaan titik rerata statis per lagu pada korpus DMDD, yang mengabaikan dinamika afektif internal sehingga menimbulkan fenomena boundary jump problem pada saat pergantian antarlagu berturutan."*

---

### 📌 Kasus Parafrase #3: Metrik Evaluasi Smoothness & Evenness
* **Sumber Terdeteksi:** Publikasi EvoMUSART 2024.
* **Teks Asli Terdeteksi:**
  > *"Smoothness dihitung dari jarak euclidean antarlagu dan evenness dihitung dari varians jaraknya."*
* **Hasil Parafrase Akademik Baru (Bebas Plagiasi):**
  > *"Evaluasi kehalusan sekuensial playlist diukur melalui metrik Smoothness ($\mathcal{S}$) yang menghitung deviasi jarak Euclidean pada titik perbatasan antartrek berturutan, sementara metrik Evenness ($\mathcal{E}$) mengkuantifikasi homogenitas laju transisi emosi di sepanjang kurva target."*

---

## 📋 Checklist Kepatuhan Sebelum Submit Berkas
- [ ] Pengaturan filter Turnitin sudah mengaktifkan **Exclude Bibliography / Daftar Pustaka**
- [ ] Pengaturan filter Turnitin mengaktifkan **Exclude Matches $< 1\%$ atau $< 8$ kata berturut-turut**
- [ ] Total skor kemiripan tidak melampaui **25%**
- [ ] Tidak ada satu sumber tunggal yang menyumbang kemiripan $> 5\%$
- [ ] File PDF ringkasan hasil Turnitin telah disimpan di folder arsip dan siap dicetak / dilampirkan

---

## 🔗 Tautan Terkait
- 📜 **Regulasi Akademik:** [[01-kebijakan-ai-dan-integritas]]
- 📝 **Naskah Draf:** [[Bab-1-Pendahuluan]] | [[Bab-2-Tinjauan-Pustaka]] | [[Bab-3-Metodologi]]
- 📋 **Checklist Sempro:** [[Tracker-Prasyarat-Sempro]]
