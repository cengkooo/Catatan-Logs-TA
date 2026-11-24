---
tier: "Tier 2: Methodological Benchmarks & Audio Similarity"
title: "Bedah Kritis: REMAST — Real-Time Emotion-Based Music Arrangement With Soft Transition (Wang et al., 2024)"
author: "Zihao Wang, Le Ma, Chen Zhang, Bo Han, Yunfei Xu, Yikai Wang, Xinyi Chen, Haorong Hong, Wenbo Liu, Xinda Wu, & Kejun Zhang"
year: 2024
citekey: "wang2024remast"
venue: "IEEE Transactions on Affective Computing (IEEE TAC), Vol. 16, No. 2, pp. 1016–1030"
quartile: "Q1 Scopus (Top 5% Affective Computing, Impact Factor: 9.6)"
dataset: "VGMIDI (3.099 MIDI), DEAM (1.680 klip audio), PMEmo, E-GComp, & Pop1K7"
metode: "Emotion Trajectory Direction Correction + Fused Emotion Conditioning + Melody Downsampling + Four Music Theory Features"
gap_utama: "Model pengubah musik afektif konvensional hanya berfokus pada kecocokan emosi seketika (real-time fit) namun mengabaikan kelembutan transisi antarsekuens, memicu sentakan struktural kasar yang merusak koherensi musikal."
tags:
  - literatur
  - paper-review
  - soft-transition
  - music-arrangement
  - circumplex-trajectory
  - boundary-jump
  - ieee-tac
status: "audited"
aliases:
  - Wang2024-REMAST-Soft-Transition
  - REMAST Soft Transition
---

# 📖 Bedah Kritis: REMAST — Soft Emotion Transition (Wang et al., 2024)
## *Real-Time Emotion-Based Music Arrangement With Soft Transition*

> **Objek Bedah:** Naskah Riset Utama IEEE Transactions on Affective Computing (15 Halaman, Vol. 16, No. 2, 2024)  
> **Kedudukan dalam TA:** **Rujukan Otoritatif SOTA Transisi Halus (*Soft Transition*) dan Penalti Lonjakan Batas Emosi (*Boundary Jump Cost*) di Ruang Sirkumpleks V-A (Bab II Subbab 2.2 & Bab III Subbab 3.3)**

---

## 🧭 Step 0: Metadata dan Konteks
* **Venue & Reputasi:** *IEEE Transactions on Affective Computing* (IEEE TAC), jurnal Q1 Scopus peringkat teratas dunia dalam komputasi afektif (CiteScore: 16.4, Impact Factor: 9.6).
* **Penulis & Afiliasi:** Zihao Wang, Le Ma, Kejun Zhang (Corresponding Author), dkk., dari State Key Laboratory of CAD&CG dan College of Computer Science and Technology, Zhejiang University, Hangzhou, China. Laboratorium terkemuka dalam pemrosesan audio kecerdasan buatan dan musik generatif.
* **Tujuan Membaca:** Mengadopsi prinsip dekonstruksi *abrupt emotion transitions* (sentakan emosi kasar) pada sekuens musik di ruang 2D Valence-Arousal Russell, serta memperkuat justifikasi matematis *Boundary Jump Cost* pada Tugas Akhir kita.

---

## 📑 Step 1: Abstrak (Bedah 5 Komponen Inti)
1. **Konteks & Urgensi:** Musik sebagai media intervensi emosi memegang peranan krusial pada terapi musik, video game adaptif, dan platform hiburan. Namun, sistem penataan musik dituntut mampu merespons perubahan emosi target secara dinamis.
2. **Gap Spesifik yang Diklaim:** Penelitian terdahulu hanya berfokus pada pencapaian *emotion real-time fit* (seberapa cepat musik cocok dengan emosi target saat itu), sementara isu **kelembutan transisi emosi (*soft transition*)** sangat diabaikan, sehingga memicu sentakan transisi kasar yang merusak koherensi mendengarkan.
3. **Pendekatan:** Mengajukan kerangka kerja **REMAST** (*Real-Time Emotion-Based Music Arrangement With Soft Transition*) yang:
   * Mengenali emosi musik langkah waktu sebelumnya ($t-1$) dan menggabungkannya (*fused emotion*) dengan emosi target langkah waktu saat ini ($t$).
   * Menggunakan *Melody Downsampling* untuk mengontrol fleksibilitas antara kemiripan melodi asli dan adaptasi emosi baru.
   * Mengekstrak 4 fitur teori musik: *Harmonic Color* (berbasis lingkaran perlima / *circle of fifths*), *Musical Tension*, harmoni, dan melodi.
4. **Hasil Kuantitatif Konkret:**
   * **Metrik Objektif Koherensi:** Mereduksi *Pitch Class Transition Entropy* (PCC) menjadi **$3,04 \pm 0,19$** (dibandingkan baseline TG-Muhamed $3,62 \pm 0,29$), mereduksi *Chord Entropy Coherence* (CEC) secara dramatis menjadi **$3,71 \pm 0,31$** (dibandingkan baseline $7,51 \pm 0,66$), serta menurunkan *Musical Chord Tension Coherence* (MCTC) menjadi **$1,04 \pm 0,09$** (dibandingkan baseline $1,77 \pm 0,13$).
   * **Kemiripan Musik:** Meningkatkan skor kesamaan melodi menjadi **$7,60 \pm 0,59$** (dibandingkan MT-Sulun $6,11 \pm 0,04$).
   * **Evaluasi Subjektif Manusia:** Meraih skor kelembutan transisi (*softness score*) tertinggi sebesar **3,79 / 5,00** (baseline hanya 2,66–3,31) dan skor koherensi **4,00 / 5,00** dengan signifikansi statistik valid ($p < 0,03$).
5. **Implikasi:** Membuktikan bahwa intervensi emosi sekuensial yang efektif wajib memperhitungkan inersia afektif keadaan sebelumnya guna meredam lonjakan koordinat yang tajam.
* **Acid Test:** Lulus mutlak. Disertai metrik kuantitatif ganda (PCC, CEC, MCTC, dan skor uji dengar subjektif ber-p-value).

---

## 🎯 Step 2: Pendahuluan (Problem Framing)
* **Spesifisitas Masalah:** Transisi afektif dalam musik yang berubah mendadak dari satu kuadran ke kuadran berlawanan (misal: *Sad/Low Arousal* tiba-tiba melompat ke *Excited/High Arousal*) menimbulkan disonansi pendengaran yang memicu ketidaknyamanan pendengar (*jarring boundary shock*).
* **Motivasi:** Kebutuhan pengguna dalam skenario relaksasi kecemasan (*anxiety relief*) dan interaksi sekuensial membutuhkan kurva transisi halus yang membimbing suasana hati pendengar secara gradual (*gradual emotional guidance*).
* **Gap Statement Audit:** Penulis menegaskan: *"While existing studies predominantly focus on achieving emotion real-time fit, the issue of smooth transition remains understudied, affecting the overall emotional coherence of the music."* Klaim ini faktual dan terverifikasi di kancah MIR modern.
* **Kontribusi Orisinal:**
  1. Metode penataan musik berbasis emosi pertama yang secara eksplisit memprioritaskan *smooth emotion transition*.
  2. Mekanisme koreksi arah trajektori emosi (*trajectory direction correction*) yang memotong jarak lompatan antarlangkah waktu.

---

## 🔍 Step 3: Related Work (Telaah Kritis)
* **Taksonomi Literatur:** Membagi penelitian ke dalam: (1) Pembangkitan musik berbasis emosi (SentiMozart, Music Transformer Sulun), dan (2) Pembangkitan musik real-time (RL-Duet, SongDriver).
* **Fairness of Comparison:** Membandingkan REMAST secara adil terhadap 3 baseline kuat: TG-Muhamed (2021), mL-Ferreira (2022), dan MT-Sulun (2022).
* **Citation Gap:** Meskipun mengulas 11 dataset musik (termasuk DEAM), REMAST memfokuskan pengujian pada domain musik simbolik MIDI, belum menguji pipeline pada seleksi trek rekaman audio utuh (*waveform audio streaming*).

---

## 📐 Step 4: Metodologi (Komponen Paling Kritis)
* **Formulasi Masalah Matematis:**
  1. **Pemetaan Ruang Afektif 2D Russell:**
     Emosi dipetakan ke dalam bidang kontinu Valence-Arousal $[-1.0, +1.0]^2$. 16 label emosi diskrit diposisikan mengikuti distribusi normal di sekeliling bidang sirkumpleks Russell.
  2. **Mekanisme Fusi Emosi Transisi (*Fused Emotion*):**
     Daripada langsung melompat ke emosi target $\mathbf{e}_{\text{target}, t}$, REMAST membentuk emosi perantara yang mengoreksi arah trajektori:
     $$\mathbf{e}_{\text{fused}, t} = \frac{\mathbf{e}_{\text{music}, t-1} + \mathbf{e}_{\text{target}, t}}{2}$$
     Di mana $\mathbf{e}_{\text{music}, t-1}$ adalah posisi afektif aktual segmen musik sebelumnya dan $\mathbf{e}_{\text{target}, t}$ adalah koordinat target baru. Formulasi ini menjamin vektor transisi mengarah ke target namun memangkas jarak perpindahan instan menjadi setengahnya ($\Delta \mathbf{e} / 2$).
  3. **Ekstraksi Fitur Teori Musik *Harmonic Color*:**
     Dihitung berdasarkan *circle of fifths*, mengkuantifikasi derajat kesegaran progresi akor antar-segmen:
     $$H_{\text{color}}(c_1, c_2) = \min(|idx(c_1) - idx(c_2)|, 12 - |idx(c_1) - idx(c_2)|)$$
* **Arsitektur Model:**
  * Tahap 1: *Music Emotion Recognition Phase* (menggunakan arsitektur konvolusional untuk mengekstrak vektor emosi aktual trek).
  * Tahap 2: *Music Generation Phase* (menggunakan Transformer berbasis kondisi fusi emosi dan melodi ter-downsample).
* **Kompleksitas Komputasi:** Operasi inferensi fusi emosi bersifat aljabar skalar berlatensi rendah ($<10 \text{ ms}$), memungkinkan penerapan real-time.

---

## 🧪 Step 5: Setup Eksperimen (Audit Forensik Cacat Riset)
* **Karakteristik Korpus Dataset (Tabel I Paper):**
  * Mensurvei 11 dataset musik terbuka: DEAM (1.680 klip, anotasi kontinu V-A $[-1, 1]$), PMEmo (2.881 klip), EmoMusic (704 klip), VGMIDI (3.099 trek MIDI dengan V-A kontinu), EMOPIA (1.078 klip 4 kuadran), dan Nottingham.
  * Eksperimen pelatihan dilakukan pada dataset gabungan yang diselaraskan ke dalam resolusi birama (*bar resolution*).
* **Audit Data Split & Leakage:** Memisahkan data berbasis identitas lagu (*song-level split*), mencegah kebocoran motif melodi antar set latih dan uji.
* **Metrik Evaluasi Objektif yang Presisi:**
  * *Pitch Class Transition Entropy (PCC):* Mengukur ketidakteraturan perpindahan nada pitch.
  * *Chord Entropy Coherence (CEC):* Mengukur kekacauan transisi akor.
  * *Musical Chord Tension Coherence (MCTC):* Mengukur kontinuitas tegangan musikal.
  * *Real-Time Emotion Fit:* Jarak Euclidean $\|\mathbf{e}_{\text{output}} - \mathbf{e}_{\text{target}}\|_2$.

---

## 📊 Step 6: Hasil (Klaim vs Bukti Empiris)
* **Tabel Hasil Komparasi Objektif (Tabel II Paper):**
  * *REMAST* meraih PCC $3,04 \pm 0,19$ (Terbaik), CEC $3,71 \pm 0,31$ (Terbaik, reduksi entropi transisi akor sebesar **50,6%** dibanding baseline TG-Muhamed 7,51), dan MCTC $1,04 \pm 0,09$ (Terbaik).
  * Skor kemiripan melodi asli mencapai $7,60 \pm 0,59$ (unggul mutlak dibanding seluruh metode acuan).
* **Tabel Hasil Subjektif Uji Dengar Manusia (Tabel III Paper, $p < 0,03$):**
  * *Softness (Kehalusan Transisi):* REMAST meraih skor **3,79**, jauh melampaui TG-Muhamed (3,03) dan MT-Sulun (2,66).
  * *Music Coherence:* REMAST meraih skor tertinggi **4,00** (baseline hanya 2,66–3,86).
* **Ablation Study (Tabel IV Paper):**
  * Menguji 6 variasi: kombinasi *Downsampling vs w/o Downsampling* dan 3 metode fusi (*Feature Concat, Median Emotion, Emotion Concat*).
  * Pengaturan #1 (*Downsampling + Feature Concat*) terbukti paling unggul di seluruh metrik subjektif ($p < 0,012$).

---

## ⚖️ Step 7: Diskusi & Limitasi
* **Limitasi Tertulis:** Ketergantungan pada representasi simbolik MIDI; belum mampu mengontrol dinamika ekspresi instrumen rekaman hidup secara penuh.
* **Limitasi Tersembunyi (Audit Forensik Kita):**
  * Model REMAST bekerja dengan **mengaransemen ulang atau menyintesis nada musik baru**, bukan memilih lagu yang sudah ada (*track retrieval*). Pada platform streaming komersial, penyedia layanan tidak boleh merekayasa ulang rekaman asli musisi; sistem harus **memilih trek rekaman asli yang memiliki trajektori paling selaras**.
* **Threats to Validity:**
  * *External Validity:* Diuji pada skenario musik terapi kecemasan berdurasi pendek; validitas pada sesi mendengarkan playlist panjang ($>30 \text{ menit}$) memerlukan pengujian sekuensial lebih lanjut.

---

## 🏁 Step 8: Kesimpulan & Future Work
* **Kesimpulan:** Integrasi inersia emosi masa lalu terbukti secara ilmiah merupakan kunci fundamental untuk mencapai transisi musik yang mulus tanpa mengorbankan ketepatan suasana hati target.
* **Petunjuk Arah Masa Depan:** Menjelajahi penerapan transisi emosi halus pada kurasi katalog audio riil berskala industri.

---

## 💡 Step 9: Sintesis Pencapaian (3 Kalimat Kunci)
1. **Fakta Terbukti:** Menerapkan pembatasan pergeseran emosi instan melalui penggabungan kondisi afektif sebelumnya terbukti mereduksi entropi kekacauan transisi akor (CEC) hingga 50,6% dan meningkatkan kehalusan perseptual dengar (*softness score*) ke 3,79/5,00 ($p < 0,03$).
2. **Lompatan SOTA:** Membuktikan bahwa mengejar *target emotion fit* secara membabi buta tanpa peredam inersia selalu menghasilkan sentakan transisi kasar yang merusak koherensi musikal.
3. **Kegunaan Praktis:** Memberikan justifikasi matematis dan empiris terkuat bagi Tugas Akhir ITERA dalam merumuskan fungsi penalti *Boundary Jump Cost* $\mathcal{BJC}$ pada perankingan playlist audio DEAM.

---

## 🎯 Step 10: Research Gap Tiga Lapis (Three-Tier Gap)
1. **Lapis 1 (Gap Klaim Penulis):** Model REMAST berfokus pada aransemen musik simbolik (MIDI generation), menyisakan tantangan transisi halus pada audio mentah.
2. **Lapis 2 (Gap Temuan Audit Kritis Kita):** Wang et al. menyelesaikan sentakan transisi dengan *men-generate* transisi sintetis, yang tidak dapat diterapkan pada katalog penyiaran musik digital resmi (Spotify/Deezer) di mana lagu rekaman asli tidak boleh dimodifikasi.
3. **Lapis 3 (Gap Riset Tugas Akhir Kita):**
   * *Formula Gap Naskah Proposal Bab II:*  
     > *"Kendati Wang et al. (2024) membuktikan bahwa sentakan transisi emosi kasar dapat diredam melalui formulasi inersia afektif pada musik simbolik generatif, belum ada penelitian yang mengadaptasi prinsip soft transition tersebut ke dalam mekanisme perankingan lagu katalog audio riil (seperti korpus DEAM) untuk menyelesaikan The Boundary Jump Problem pada penyusunan mood-arc playlist."*

---

## 🚩 Radar Red Flags Audit
* [x] **Hasil Multi-Seed & Standar Deviasi:** Terpenuhi (seluruh metrik objektif menyertakan nilai $\pm \sigma$).
* [x] **Signifikansi Statistik:** Terpenuhi ketat (seluruh metrik subjektif memiliki $p < 0,03$).
* [x] **Ablation Study Komprehensif:** Terpenuhi (Tabel IV membedah 6 kombinasi arsitektur).
* [x] **Kekuatan Baseline:** Kuat (membandingkan dengan 3 model SOTA: TG-Muhamed, mL-Ferreira, MT-Sulun).
* [x] **Bebas Data Leakage:** Terpenuhi (*song-level dataset split*).
