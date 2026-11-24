---
title: "Bedah Kritis: Flow Moods: Recommending Music by Moods on Deezer"
author: "Théo Bontempelli et al. (Deezer Research)"
year: 2022
citekey: "bontempelli2022flow"
venue: "ACM Conference on Recommender Systems (RecSys '22), pp. 476–478"
quartile: "Top-Tier Conference in Recommender Systems (Core A)"
dataset: "Deezer Production Catalog (Jutaan Lagu & Jutaan Pengguna Aktif)"
metode: "Collaborative Filtering + Audio Content Embedding + Human Curator Mood Labels"
gap_utama: "Sistem rekomendasi radio industri (Deezer Flow) sebelumnya mengabaikan kondisi suasana hati sesaat (mood) pengguna."
tags:
  - literatur
  - paper-review
  - industri-recsys
  - deezer
  - flow-moods
  - acm-recsys
status: "audited"
---

# 📖 Bedah Kritis: Deezer Flow Moods (Bontempelli et al., 2022)
## *Recommending Music by Moods on Deezer*

> **Objek Bedah:** Paper ACM RecSys '22 (20 KB text)  
> **Kedudukan dalam TA:** **Bukti Urgensi Industri & Masalah Dunia Nyata (Bab I Subbab 1.1)**

---

## 🧭 Step 0: Metadata dan Konteks
* **Penulis & Afiliasi:** Théo Bontempelli, Benjamin Chapus, François Rigaud, Mathieu Morlon, Marin Lorant, Guillaume Salha-Galvan (Deezer Research, Paris, France).
* **Venue & Reputasi:** *ACM RecSys 2022*, konferensi sistem perekomendasi #1 di dunia.
* **Tujuan Membaca:** Mengambil bukti empiris industri streaming musik bahwa pengguna menuntut fitur navigasi berbasis mood, sekaligus mengidentifikasi keterbatasan model diskrit industri.

---

## 📑 Step 1: Abstrak (Bedah 5 Komponen)
1. **Konteks & Masalah:** Deezer mengandalkan algoritma *Flow* untuk membuat radio personalisasi otomatis, namun versi awal *Flow* tidak mempertimbangkan suasana hati pengguna.
2. **Gap yang Diklaim:** Personalisasi murni berbasis riwayat dengar sering gagal saat suasana hati pengguna berubah (misal: butuh fokus belajar tapi sistem menyajikan lagu pesta).
3. **Pendekatan:** Mengembangkan *Flow Moods* yang menggabungkan *Collaborative Filtering*, analisis konten audio, dan anotasi mood dari kurator profesional.
4. **Hasil Kuantitatif Konkret:**
   * Menghasilkan 6 kategori mood utama: *You & Me (Romantis), Motivation, Chill, Focus, Party, Melancholy*.
   * Diuji secara live pada jutaan pengguna Deezer sejak 2021, menghasilkan peningkatan signifikan pada metrik retensi dan *listening time*.
5. **Implikasi:** Pendekatan mood-based recommendation terbukti menjadi pilar utama keterikatan pengguna (*user engagement*) di industri streaming.

---

## ⚠️ Step 7: Limitasi Tersembunyi & Red Flags
> [!WARNING]
> **Limitasi Fundamental Deezer Flow Moods:**
> 1. **Model Kategori Diskrit Tertutup:** Deezer hanya membatasi pengguna pada 6 pilihan tombol mood statis terpisah. Pengguna tidak bisa berpindah secara gradual dari *Melancholy* menuju *Motivation*.
> 2. **Tidak Ada Mood-Arc Transition:** Begitu tombol *Chill* ditekan, seluruh playlist homogen berada di mood tersebut. Tidak ada alur cerita emosi antartrek.

---

## 💡 Step 9: Sintesis Pencapaian 3 Kalimat
1. **Fakta Terbukti:** Integrasi preferensi suasana hati ke dalam sistem rekomendasi radio streaming berskala besar terbukti meningkatkan kepuasan dan retensi jutaan pengguna.
2. **Lompatan SOTA:** Berhasil menyatukan collaborative filtering dengan klasifikasi audio mood pada katalog jutaan lagu berlatensi rendah.
3. **Kegunaan Praktis:** Menjadi bukti tak terbantahkan di latar belakang Bab I bahwa topik Tugas Akhir kita menyentuh kebutuhan riil industri streaming modern.

---

## 🎯 Step 10: Research Gap Tiga Lapis
1. **Lapis 1 (Gap Deezer):** Deezer mengakui perlunya ekspansi kategori mood dan adaptasi real-time.
2. **Lapis 2 (Gap Struktural Diskrit):** Industri masih terjebak pada tombol mood statis; belum mampu menyajikan perjalanan emosional kontinu (*mood trajectory*).
3. **Lapis 3 (Gap Sintesis TA Kita):** Mengembangkan sistem rekomendasi yang melampaui radio diskrit Deezer dengan memungkinkan pengguna menentukan titik awal dan titik akhir emosi (*dynamic mood-arc*).
