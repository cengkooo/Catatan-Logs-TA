---
title: "Draf Opsi Tambahan User Study: Bab 1 dan Bab 3 (Siap Injeksi Setelah Bimbingan)"
tags:
  - draft
  - opsi-revisi
  - user-study
  - kuesioner
  - sempro
date: 2026-11-24
---

# 📦 Draf Teks Cadangan: Integrasi User Listening Study (Skenario 2)

*Gunakan teks di bawah ini untuk langsung memperbarui `Bab-1-Pendahuluan.md` dan `Bab-3-Metodologi.md` setelah Pak Hafiz menyetujui Skenario 2.*

---

## ✍️ BAGIAN A: Pembaruan Bab 1 (Pendahuluan)

### 1. Tambahan pada Subbab 1.2 Rumusan Masalah (Butir ke-4):
```markdown
4. Bagaimana korelasi antara metrik komputasional objektif dengan tingkat penerimaan perseptual pendengar (perceived transition smoothness dan acoustic continuity) yang diukur melalui pengujian kuesioner pengguna (user listening study) pada segmen transisi antarlagu?
```

### 2. Tambahan pada Subbab 1.3 Tujuan Penelitian (Butir ke-4):
```markdown
4. Mengukur dan memvalidasi penerimaan perseptual pengguna melalui user listening study berskala laboratorium ($N \ge 30$) dengan metode blind A/B testing dan skala Likert 5 poin (indikator keberhasilan: skor Mean Opinion Score (MOS) kelancaran transisi model usulan lebih tinggi secara signifikan dibanding baseline dengan nilai $p < 0.05$ pada uji Wilcoxon Signed-Rank).
```

### 3. Revisi pada Subbab 1.4 Batasan Penelitian (Poin 4):
```markdown
4. Pengujian persepsi manusia (user listening study) dirancang sebagai validasi subjektif komparatif (blind A/B testing) pada skala laboratorium terbatas yang melibatkan minimal 30 responden pendengar aktif musik digital, dievaluasi menggunakan instrumen kuesioner skala Likert 5 poin pada klip sambungan transisi 30 detik dan diuji signifikansinya secara statistik.
```

---

## ✍️ BAGIAN B: Pembaruan Bab 3 (Metodologi)

### Tambahan Subbab 3.6: Metode Pengujian Subjektif (User Listening Study)

```markdown
## 3.6 Metode Pengujian Subjektif (User Listening Study)

Guna melengkapi evaluasi komputasional objektif pada Subbab 3.5, penelitian ini merancang pengujian persepsi subjektif (*User Listening Study*) untuk menguji apakah keunggulan matematis model usulan berbanding lurus dengan kenyamanan mendengar manusia. Protokol ini dirancang pada tahap proposal (TA 1) dan dieksekusi secara penuh pada tahap implementasi (TA 2).

### 3.6.1 Desain Eksperimen Blind A/B Listening Test
Pengujian dilakukan menggunakan metode *blind A/B test* di mana partisipan mendengarkan dua versi sambungan audio untuk pasangan lagu yang sama secara acak tanpa mengetahui algoritma yang menghasilkan masing-masing versi:
- **Versi A (Baseline):** Sambungan transisi yang dihasilkan oleh model *static-point matching* Gaur dan Donnelly (2020).
- **Versi B (Usulan):** Sambungan transisi yang dihasilkan oleh pipeline *Dynamic Mood Trajectory Alignment*.

### 3.6.2 Stimulus Audio Sambungan Batas (Boundary Jump Clip)
Alih-alih memutar keseluruhan lagu yang rentan memicu kelelahan mendengar (*listener fatigue*) dan bias selera musik, stimulus yang diuji difokuskan tepat pada segmen pergantian lagu berdurasi **30 detik**:
$$\text{Clip} = [\text{Audio } s_i \text{ (15 detik akhir)}] + [\text{Audio } s_{i+1} \text{ (15 detik awal)}]$$
Empat pasang transisi lintas kuadran diuji, mencakup pergeseran emosi ekstrem (misal: Kuadran IV Tenang menuju Kuadran I Enerjik, dan Kuadran III Sedih menuju Kuadran I Gembira).

### 3.6.3 Partisipan dan Kriteria Sampling
Pengujian melibatkan minimal $N = 30$ responden (memenuhi batas kecukupan ukuran sampel teorema limit pusat). Responden dipilih menggunakan teknik *purposive sampling* dengan kriteria inklusi:
1. Mahasiswa aktif Program Studi Teknik Informatika ITERA.
2. Pendengar aktif platform penyiaran musik digital (Spotify, Apple Music, YouTube Music) dengan durasi minimal 3 jam per minggu.

### 3.6.4 Instrumen Kuesioner Evaluasi
Setiap responden menilai masing-masing pasangan stimulus audio menggunakan kuesioner berbasis skala Likert 5 poin:
1. **Perceived Transition Smoothness ($Q_1$):** Mengukur derajat kehalusan pergantian antarlagu (1 = Sangat kasar/menyentak, 5 = Sangat mulus/alami).
2. **Acoustic Continuity ($Q_2$):** Mengukur kesinambungan tempo, timbre, dan intensitas audio saat pergantian trek (1 = Sangat terputus, 5 = Sangat berkesinambungan).
3. **Direct Preference ($Q_3$):** Pilihan biner versi mana yang lebih disukai sebagai bagian dari daftar putar suasana hati.

### 3.6.5 Prosedur Analisis Statistik
Data kuesioner dianalisis menggunakan perangkat lunak statistik Python (`scipy.stats`):
1. **Uji Hipotesis Beda Nyata:** Karena data skala ordinal Likert tidak berdistribusi normal, perbedaan skor antara Baseline dan Model Usulan diuji menggunakan uji non-parametrik **Wilcoxon Signed-Rank Test** berpasangan dengan taraf signifikansi $\alpha = 0.05$.
2. **Korelasi Metrik Objektif vs. Subjektif:** Menghitung koefisien korelasi peringkat Spearman ($\rho$) antara nilai penurunan *Smoothness Index* ($\mathcal{S}$) dan peningkatan skor *Mean Opinion Score* (MOS) responden:
$$\rho = 1 - \frac{6 \sum d_i^2}{n(n^2 - 1)}$$
Korelasi negatif yang kuat ($\rho \le -0.6, p < 0.05$) membuktikan bahwa penurunan indeks kekasaran matematis benar-benar dirasakan sebagai peningkatan kelancaran oleh telinga manusia.
```
