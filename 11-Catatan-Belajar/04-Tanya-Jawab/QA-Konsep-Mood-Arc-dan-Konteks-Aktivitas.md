---
title: "Fungsi Konteks Aktivitas vs. Mood Dasar pada Mood-Arc Playlist"
tags:
  - note/tanya-jawab
  - learning-qa
  - mood-arc
  - bab-1
topik: "Konsep Mood-Arc dan Konteks Aktivitas"
status: "berkembang"
rujukan_paper:
  - "[[01-Gaur2023-Mood-Dynamic]]"
  - "[[06-Bontempelli2022-Flow-Moods-Deezer]]"
  - "[[03-Russell1980-Circumplex-Model]]"
created: 2026-11-28
updated: 2026-11-28
---

# 💬 Fungsi Konteks Aktivitas vs. Mood Dasar pada Mood-Arc Playlist

- **Topik:** `Konsep Mood-Arc dan Konteks Aktivitas`
- **Status Pemahaman:** `berkembang`

---

## ❓ Pertanyaan #1
> Pada `chapter-1.tex` tertulis: *"Kebutuhan pendengar modern bergeser ke arah daftar putar berbasis konteks dan aktivitas, seperti belajar, berolahraga, meditasi, dan tidur, yang menuntut perubahan suasana hati (mood) mengikuti lintasan afektif terkontrol."* Mengapa yang disebut adalah konteks aktivitas, bukan mood seperti senang, bahagia, sedih, atau marah seperti pada paper yang membahas mood? Apa fungsi aktivitas tersebut?

### 💡 Jawaban

Penyebutan **aktivitas** (belajar, berolahraga, meditasi, tidur) bukanlah pengganti konsep *mood* (senang, sedih, marah, tenang), melainkan **lapisan konteks dunia nyata** yang menjelaskan *mengapa* manusia membutuhkan **perubahan mood secara bertahap (*mood arc*)**, bukan sekadar satu *mood* diam.

#### 1. Mengapa Aktivitas, Bukan Sekadar "Senang / Sedih / Marah"?
- **Mood tunggal bersifat statis:** Jika pendengar hanya ingin mendengarkan lagu "sedih" atau "senang", sistem cukup mengambil lagu dari satu kuadran emosi yang sama dari awal sampai akhir (seperti 6 tombol kategori statis pada *Deezer Flow Moods*).
- **Aktivitas memiliki fase waktu (*awal -> tengah -> akhir*) yang menuntut *mood regulation*:** Sebagaimana dijelaskan dalam motivasi riil paper acuan **Gaur & Donnelly (2023)**, kebutuhan utama *mood-arc* adalah *mood regulation*:
  - **Tidur:** Pendengar sering memulai dalam kondisi masih terjaga/gelisah (*Arousal* tinggi), lalu membutuhkan musik yang menurunkan ketegangan secara bertahap menuju kondisi rileks/mengantuk (*Arousal* rendah, Kuadran 4) agar transisi tidurnya alami.
  - **Berolahraga:** Dimulai dari pemanasan (*Arousal* sedang), naik ke puncak intensitas latihan (*Arousal* tinggi, Kuadran 1), lalu turun saat pendinginan (*cool-down*).
  - **Belajar / Meditasi:** Berpindah dari pikiran yang ramai atau terdistraksi menuju kondisi fokus dan tenang yang stabil.

#### 2. Hubungan Aktivitas dengan Ruang Emosi (Senang, Sedih, Marah, Tenang)
Keduanya bekerja di lapisan yang berbeda namun saling terhubung:
- **Lapisan Konteks Pengguna (Bab 1 - Urgensi Dunia Nyata):** Aktivitas (*belajar, olahraga, tidur*) menjelaskan **untuk apa** *mood arc* dipakai oleh pengguna aplikasi streaming.
- **Lapisan Representasi Matematis (Bab 2 & Bab 3):** Di dalam sistem, aktivitas tersebut diterjemahkan menjadi titik awal dan titik tujuan ($\mathbf{p}_{\text{start}} \to \mathbf{p}_{\text{target}}$) pada **Model Sirkumpleks Russell (Valence-Arousal)** yang memang memetakan emosi dasar seperti *Marah/Tegang* (Q2), *Senang/Bersemangat* (Q1), *Sedih* (Q3), dan *Tenang/Damai* (Q4).

#### 3. Tiga Fungsi Utama Kalimat Aktivitas di Bab 1 Proposal
1. **Membedakan sistem Anda dari rekomendasi berbasis riwayat biasa:** Seperti dicatat pada paper **Bontempelli et al. (2022)** (Deezer *Flow Moods*), rekomendasi yang hanya mengandalkan riwayat dengar sering gagal ketika konteks pengguna berubah (misalnya pengguna sedang ingin *fokus belajar*, tetapi sistem malah memutar lagu *pesta* karena kemarin ia sering memutar lagu pesta).
2. **Menjustifikasi bentuk "lintasan" (*arc*), bukan titik tunggal:** Aktivitas membuktikan bahwa emosi pendengar dalam satu sesi mendengarkan bersifat dinamis dan terarah dari satu titik emosi ke titik emosi lain.
3. **Menjawab pertanyaan penguji soal manfaat praktis:** Tanpa contoh aktivitas nyata, topik *Valence-Arousal trajectory* bisa terdengar terlalu abstrak. Dengan adanya contoh tidur, olahraga, dan belajar, dosen penguji langsung menangkap dampak praktisnya di industri streaming.

### 📚 Referensi
- [[01-Gaur2023-Mood-Dynamic]] — Motivasi *mood regulation* (terapi musik, pengantar tidur dari gelisah ke rileks, dan musik olahraga dari pemanasan ke intensitas tinggi).
- [[06-Bontempelli2022-Flow-Moods-Deezer]] — Contoh kegagalan personalisasi historis saat konteks aktivitas pengguna berubah (*belajar* vs. *pesta*).
- [[03-Russell1980-Circumplex-Model]] — Pemetaan emosi dasar (senang, marah, sedih, tenang) ke koordinat kontinu *Valence-Arousal*.
- `proposal-penelitian-andryano-123140205/chapters/chapter-1.tex` (Latar Belakang, baris 7–9).

### 🔗 Catatan Terkait
- [[00-Index-Catatan]]
- [[Model-Emosi-Sirkumpleks-Russell-1980]]
- [[QA-Algoritma-Rekomendasi-Platform-Streaming]]
