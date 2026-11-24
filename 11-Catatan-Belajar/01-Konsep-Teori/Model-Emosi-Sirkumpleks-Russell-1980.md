---
title: "Model Emosi Sirkumpleks Russell (1980) & Representasi Valence-Arousal"
tags:
  - note/konsep
  - teori
  - domain-mir
  - music-psychology
  - valence-arousal
topik: "Music Emotion Recognition (MER)"
status: "solid"
rujukan_paper:
  - "[[Russell1980-Circumplex-Model]]"
  - "[[Aljanaki2017-Developing-Benchmark-DEAM]]"
  - "[[Gaur2020-Mood-Arc]]"
created: 2026-11-23
updated: 2026-11-23
---

# 🧠 Model Emosi Sirkumpleks Russell (1980) & Representasi Valence-Arousal

- **Kategori Topik:** `Music Emotion Recognition (MER)`
- **Tingkat Pemahaman:** `solid`
- **Rujukan Paper Utama:** [[Russell1980-Circumplex-Model]], [[Aljanaki2017-Developing-Benchmark-DEAM]], [[Gaur2020-Mood-Arc]]

---

## 🎯 Inti Konsep (Metode Feynman)
Daripada membatasi emosi musik ke dalam kotak kata-kata kaku seperti "senang", "sedih", atau "marah" (model kategorikal yang sering tumpang-tindih), James Russell (1980) memetakan seluruh respon afektif manusia ke dalam **ruang koordinat 2 dimensi Cartesian kontinu**:
1. **Valence (Sumbu Horizontal $X$):** Menunjukkan polaritas kesenangan (*pleasantness* / kualitas afeksi positif vs negatif). Rentang: $[-1.0, +1.0]$ atau $[1.0, 9.0]$.
2. **Arousal (Sumbu Vertikal $Y$):** Menunjukkan intensitas energi biologis atau ketergugahan psikofisiologis (*activation* / bersemangat vs mengantuk/tenang). Rentang: $[-1.0, +1.0]$ atau $[1.0, 9.0]$.

Setiap keadaan emosi musik merupakan satu titik koordinat $(v, a)$ dalam lingkaran kontinu (*circumplex*) 360 derajat.

---

## 🔍 Pembagian Kuadran Afektif & Peta Emosi

```text
               +Arousal (Tinggi: Energi / Intensitas)
                     |
       Q2: MARAH /   |   Q1: GEMBIRA /
       TEGANG /      |   BERSEMANGAT /
       ALARMED       |   EUPHORIC
                     |
-Valence ------------+------------ +Valence (Positif: Kesenangan)
(Negatif)            |
       Q3: SEDIH /   |   Q4: DAMAI /
       DEPRESI /     |   TENANG /
       GLOOMY        |   RELAXED / SERENE
                     |
               -Arousal (Rendah: Pasif / Tidur)
```

### Karakteristik 4 Kuadran:
1. **Kuadran 1 (Valence+, Arousal+):** Emosi enerjik positif (*Happy, Excited, Triumphant, Danceable*).
2. **Kuadran 2 (Valence-, Arousal+):** Emosi intensitas tinggi namun bertekanan/negatif (*Angry, Frustrated, Tense, Anxious*).
3. **Kuadran 3 (Valence-, Arousal-):** Emosi energi rendah dan muram (*Sad, Depressed, Melancholic, Gloomy*).
4. **Kuadran 4 (Valence+, Arousal-):** Emosi tenang, rileks, dan menenangkan (*Calm, Peaceful, Serene, Meditative*).

---

## 🛠️ Relevansi Kritis pada Tugas Akhir Kita

### 1. Kenapa Model Ini Dipilih Mengalahkan Model Kategorikal?
- **Dataset DEAM ([[01-Dataset-DEAM-dan-Eksplorasi|Dataset-DEAM]]):** Menyediakan anotasi dinamis berbasis time-series (frekuensi 2 Hz, 45 detik) dalam nilai kontinu Valence dan Arousal.
- **Interpolasi Matematika:** Koordinat kontinu memungkinkan perhitungan jarak euclidean/cosine ($L_2$ norm), regresi lereng trajektori dinamis ($m = \Delta y / \Delta x$), serta perancangan busur mood-arc mulus yang tidak dapat diakomodasi oleh label kategori diskrit.

### 2. Akar Masalah Baseline Gaur & Donnelly (2020):
- Model acuan Gaur & Donnelly hanya mengambil **satu nilai rata-rata statis $(\bar{v}, \bar{a})$** untuk seluruh durasi lagu.
- **Fakta di dataset DEAM:** 98,11% lagu mengalami fluktuasi mood dinamis signifikan dari detik ke-15 hingga detik ke-45.
- Akibatnya, lagu yang di awal tenang $(v=0.7, a=0.2)$ namun di akhir menjadi sangat keras/menghentak $(v=0.7, a=0.85)$ akan diwakili oleh titik tengah $(v=0.7, a=0.525)$. Saat disambungkan dengan lagu berikutnya, terjadi *boundary jump shock* yang merusak pengalaman pendengar.

### 3. Solusi Tugas Akhir Kita:
- Kita memodelkan lagu bukan sebagai titik tunggal statis, melainkan **vektor trajektori dinamis** $\mathbf{T} = [(v_1, a_1), (v_2, a_2), \dots, (v_n, a_n)]$.
- Transisi antar-lagu dihitung dengan mencocokkan *exit trajectory* klip $i$ dengan *entry trajectory* klip $i+1$.

---

## 🔗 Catatan Terkait
- [[Matriks-Sintesis]]
- [[Russell1980-Circumplex-Model]]
- [[Aljanaki2017-Developing-Benchmark-DEAM]]
- [[01-Dataset-DEAM-dan-Eksplorasi|Dataset-DEAM]]
- [[02-Formulasi-Ekstraksi-Trajectory|Ekstraksi-Trajectory]]
- [[Bab-2-Tinjauan-Pustaka]]
