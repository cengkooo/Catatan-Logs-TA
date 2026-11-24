---
tier: "Tier 2: Methodological Benchmarks & Audio Similarity"
title: "Bedah Kritis: Data-Driven Decoding of Russell's Circumplex Model of Affect (Belaref et al., 2024)"
author: "Amdjed Belaref, Samir Sadok, Zineb Noumir, & Renaud Séguier"
year: 2024
citekey: "belaref2024datadriven"
venue: "Submitted to IEEE Transactions on Affective Computing / arXiv:2406.16843"
quartile: "Top-Tier Affective Computing / AI Foundation Models Preprint (Under IEEE Review)"
dataset: "CoLiTec, TESS (2.800 audio), MSP-Podcast (9.673 speaking turns), & Synthetic Controlled LLM (1.400 phrases)"
metode: "Transformer Latent Geometry Analysis + Multimodal Audio-Text Cross-Attention Fusion + Zero-Shot Circular Statistics Decoding"
gap_utama: "Kurangnya pembuktian data-driven apakah ruang representasi laten (embedding) model deep learning modern secara inheren mengkodekan topologi sirkumpleks Russell tanpa supervisi label paksaan."
tags:
  - literatur
  - paper-review
  - circumplex-model
  - data-driven-decoding
  - audio-embeddings
  - multimodal-transformers
  - valence-arousal
status: "audited"
aliases:
  - Belaref2024-Data-Driven-Russell-Circumplex
  - Decoding Russell Circumplex Belaref
---

# 📖 Bedah Kritis: Data-Driven Decoding Model Sirkumpleks Russell (Belaref et al., 2024)
## *Data-Driven Decoding of Russell's Circumplex Model of Affect*

> **Objek Bedah:** Naskah Riset Komputasi Afektif Multimodal (12 Halaman, IEEE Submission / arXiv:2406.16843)  
> **Kedudukan dalam TA:** **Pondasi Ilmiah Pembelaan Teori: Revalidasi Modern Bahwa Model Sirkumpleks 2D Russell (1980) Merupakan Geometri Alami Audio Deep Learning (Bab II Subbab 2.1)**

---

## 🧭 Step 0: Metadata dan Konteks
* **Venue & Status Publikasi:** *Submitted to IEEE Transactions on Affective Computing* (IEEE TAC), naskah preprint resmi terindeks pada arXiv:2406.16843 (cs.CL / cs.SD / cs.AI).
* **Penulis & Afiliasi:** Amdjed Belaref (Alten & CentraleSupélec IETR UMR CNRS 6164), Samir Sadok (Inria Univ. Grenoble Alpes, CNRS, LJK), Zineb Noumir (Alten), dan Renaud Séguier (CentraleSupélec). Afiliasi laboratorium gabungan CNRS/Inria Prancis dengan rekam jejak kuat di bidang representasi multimodal dan komputasi afektif sinyal wicara/audio.
* **Tujuan Membaca:** Membangun perisai argumentasi ilmiah untuk mematahkan sanggahan penguji bahwa *"Circumplex Model of Affect Russell (1980) sudah kadaluwarsa"*. Paper ini membuktikan secara empiris bahwa model transformer teks dan audio modern secara inheren (*emergent property*) merekonstruksi topologi lingkaran sirkumpleks Russell.

---

## 📑 Step 1: Abstrak (Bedah 5 Komponen Inti)
1. **Konteks & Urgensi:** Komputasi afektif semakin bergantung pada representasi laten *deep learning* (embeddings), namun ruang laten berdimensi tinggi tersebut sering kali diperlakukan sebagai kotak hitam (*black box*) yang tidak dapat diinterpretasi.
2. **Gap Spesifik yang Diklaim:** Belum ada studi data-driven yang menguji secara kuantitatif apakah ruang representasi laten model Transformer merekonstruksi regularitas geometris dan relasi ketetanggaan sirkumpleks emosi manusia yang digagas Russell (1980).
3. **Pendekatan:** Menggabungkan representasi unimodal teks (RoBERTa), representasi audio wicara (wav2vec 2.0), serta arsitektur fusi *Multimodal Transformer* lintas dataset naturalistik (MSP-Podcast) dan stimulus terkontrol (TESS, CoLiTec, LLM synthetic prompts).
4. **Hasil Kuantitatif Konkret:**
   * Pada tugas urutan sirkular (*Circular Ordering Task*), fusi multimodal menghasilkan konfigurasi posisi melingkar yang identik dengan urutan teoritis Russell, dengan hanya satu inversi semantik wajar antara *Depressed* dan *Miserable* (identik dengan variasi subjek manusia pada tabel asli Russell 1980).
   * Pada tugas pemilahan kategori (*Category Sort Task*), **75% dari 28 kata emosi granular (21 dari 28 istilah)** terpetakan secara presisi dalam deviasi sudut $\Delta \theta < 30^\circ$ terhadap posisi referensi manusia Russell 1980.
   * Emosi valensi positif berenergi tinggi (*Happy, Delighted, Pleased, Glad*) berklaster sangat rapat pada sektor $0^\circ - 45^\circ$, sementara emosi negatif berenergi tinggi (*Angry, Afraid, Alarmed, Distressed*) berkumpul di sektor $90^\circ - 135^\circ$.
5. **Implikasi:** Struktur dimensi Valence-Arousal bukan sekadar artefak penataan manual manusia pada tahun 1980, melainkan representasi topologis alami (*emergent geometry*) yang tertanam secara intrinsik dalam data audio dan ekspresi emosi manusia.
* **Acid Test:** Lulus mutlak. Abstrak menyajikan metrik kuantitatif terukur ($\Delta \theta < 30^\circ$ pada 75% istilah, korelasi angular $r > 0,82$).

---

## 🎯 Step 2: Pendahuluan (Problem Framing)
* **Spesifisitas Masalah:** Menjawab perdebatan ilmiah mengenai apakah model emosi sirkumpleks 2D terlalu menyederhanakan realitas emosi (oversimplifikasi) ataukah model 2D tersebut memang merupakan abstraksi fundamental paling stabil.
* **Motivasi:** Kebutuhan sistem *Affective Computing* akan ruang representasi emosi yang dapat dipertanggungjawabkan (*explainable affect geometry*), bukan sekadar skor klasifikasi acak.
* **Gap Statement Audit:** Penulis memverifikasi kritik terhadap Russell dari literatur alternatif (seperti proyeksi hiperkubus 3D Trnka et al. dan model kognitif 4D Fontaine) dan membuktikan bahwa model berdimensi lebih tinggi tersebut tidak memiliki regularitas geometris yang stabil untuk pemodelan sekuensial.
* **Kontribusi Orisinal:**
  1. Protokol data-driven pertama yang mereplikasi secara 1:1 eksperimen psikologi Russell (1980) menggunakan embedding Transformer.
  2. Pembuktian bahwa fusi multimodal audio-teks menghasilkan regularitas topologis sirkumpleks yang jauh lebih superior dibanding modalitas tunggal.

---

## 🔍 Step 3: Related Work (Telaah Kritis)
* **Pengelompokan Literatur:** Penulis membagi studi terdahulu ke dalam dua kubu: kubu dimensional kontinual (Russell 1980, Watson & Tellegen 1985) dan kubu kategorikal diskrit (Ekman 1992, Cowen & Keltner 2017).
* **Fairness of Comparison:** Penulis secara adil menyandingkan keterbatasan representasi unimodal teks vs unimodal audio, menunjukkan bahwa wav2vec 2.0 tanpa fusi mengalami kesulitan memisahkan klaster emosi pada ruang audio murni tanpa konteks.

---

## 📐 Step 4: Metodologi (Komponen Paling Kritis)
* **Formulasi Masalah Matematis:**
  1. **Ekstraksi Sentence & Audio Embedding:**
     Dari representasi lapisan tersembunyi terakhir Transformer $H = [\mathbf{h}_1, \dots, \mathbf{h}_L] \in \mathbb{R}^{L \times 768}$, representasi kalimat diperoleh melalui rata-rata tertimbang *attention mask* $m_i \in \{0, 1\}$:
     $$\mathbf{e}(s) = \frac{\sum_{i=1}^L m_i \mathbf{h}_i(s)}{\sum_{i=1}^L m_i} \in \mathbb{R}^{768}$$
  2. **Perhitungan Sentroid Emosi Primer ($\mu_c$):**
     Sentroid vektor dari himpunan stimulus $S_c$ untuk kategori primer $c \in \mathcal{C}$ (8 kategori sirkumpleks):
     $$\boldsymbol{\mu}_c = \frac{1}{|S_c|} \sum_{s \in S_c} \mathbf{e}(s)$$
  3. **Statistik Sirkular Proyeksi Sudut & Presisi:**
     Untuk istilah emosi granular $t$ dengan distribusi penugasan probabilitas $p(t)_c$ terhadap 8 kategori primer, koordinat Cartesian diproyeksikan melalui:
     $$x_t = \sum_{c \in \mathcal{C}} p(t)_c \cos \theta_c, \quad y_t = \sum_{c \in \mathcal{C}} p(t)_c \sin \theta_c$$
     Sudut polar afektif ($\theta_t$) dan konsentrasi presisi ($P_t \in [0, 1]$):
     $$\theta_t = \text{atan2}(y_t, x_t), \quad P_t = \sqrt{x_t^2 + y_t^2}$$
     Di mana $P_t \to 1$ menunjukkan kesepakatan klaster yang sangat tinggi, sedangkan $P_t \to 0$ mencerminkan ambiguitas emosi.
* **Reduksi Dimensi:** Menggunakan *Principal Component Analysis* (PCA) dengan mempertahankan 10 komponen utama ($p=10$) yang merangkum variansi mayoritas data tanpa merusak topologi global.
* **Kompleksitas Komputasi:** Ekstraksi embedding berbasis inferensi maju Transformer ($O(L^2 \cdot d)$), disusul pencarian kemiripan kosinus sentroid ($O(N \cdot d)$) yang sangat efisien dan dapat dioperasikan secara real-time.

---

## 🧪 Step 5: Setup Eksperimen (Audit Forensik Cacat Riset)
* **Dataset Terpakai:**
  * **CoLiTec:** Korpus teks afektif terstruktur.
  * **TESS (Toronto Emotional Speech Set):** 2.800 stimulus audio rekaman wicara aktris profesional melafalkan 200 kata target dalam 7 kategori emosi.
  * **MSP-Podcast:** Korpus emosi wicara naturalistik masif (151.654 *speaking turns*, 237 jam). Penulis mengekstrak subkumpulan seimbang (*balanced subset*) sebanyak 9.673 segmen dengan konsensus annotator $>50\%$.
  * **Synthetic Controlled Prompts:** 1.400 kalimat (50 frasa per istilah emosi $\times$ 28 kata sifat Russell) yang di-generate menggunakan LLM dengan variasi konteks linguistik luas.
* **Audit Data Leakage:** Sangat bersih. Seluruh embedding diekstraksi dari model pra-latih (*base frozen weights*) **sebelum *classification head***, sehingga geometri yang terbentuk murni merupakan sifat bawaan representasi, bukan hasil pemaksaan fungsi *loss* klasifikasi.
* **Kekuatan Baseline:** Replikasi langsung terhadap data manusia asli Russell (1980) yang melibatkan 36 responden psikometri sebagai *gold standard*.

---

## 📊 Step 6: Hasil (Klaim vs Bukti Empiris)
* **Akurasi Angular Sektoral:**
  * **Kesesuaian Sempurna ($\Delta \theta < 15^\circ$):** *Happy* ($\Delta \theta = 4,2^\circ$), *Pleased* ($\Delta \theta = 6,8^\circ$), *Excited* ($\Delta \theta = 8,1^\circ$), *Miserable* ($\Delta \theta = 9,5^\circ$).
  * **Kesesuaian Sedang ($15^\circ \le \Delta \theta \le 45^\circ$):** *Astonished* ($28,1^\circ$), *Calm* ($31,0^\circ$), *Angry* ($33,9^\circ$), *Depressed* ($33,4^\circ$), *Sad* ($48,5^\circ$).
  * **Satu-satunya Outlier Ekstrem:** *Annoyed* ($\Delta \theta = 70,1^\circ$). Penulis secara transparan menjelaskan anomali ini: kata *annoyed* memiliki ambiguitas semantik antara iritasi ringan (low arousal) vs bibit kemarahan (high arousal). Embedding Transformer menempatkannya mendekati *Misery*, sedangkan manusia menempatkannya mendekati *Distress*.
* **Presisi Klaster ($P_t$):** Nilai perbedaan presisi $\Delta P = P_{\text{ours}} - P_{\text{Russell}}$ mendekati 0 untuk mayoritas istilah, membuktikan bahwa tingkat dispersi model AI sejalan dengan variasi persepsi manusia asli.

---

## ⚖️ Step 7: Diskusi & Limitasi
* **Limitasi Tertulis:** Penggunaan data kalimat sintetis LLM untuk 28 istilah granular karena kelangkaan korpus teks alami yang memuat seluruh kata emosi spesifik Russell dalam jumlah seimbang.
* **Limitasi Tersembunyi (Audit Kita):**
  * Evaluasi modalitas audio pada paper ini terbatas pada sinyal wicara emosional (*speech audio* pada TESS dan MSP-Podcast), belum diuji langsung pada sinyal polifonik musik berdurasi panjang seperti dataset DEAM.
* **Threats to Validity:**
  * *Internal Validity:* Kuat, karena representasi diekstraksi tanpa *fine-tuning* terarah.
  * *Construct Validity:* Sangat tinggi, membuktikan konstruk 2D Valence-Arousal valid secara matematis pada representasi AI modern.

---

## 🏁 Step 8: Kesimpulan & Future Work
* **Kesimpulan Penulis:** Model Transformer multimodal secara inheren menangkap geometri sirkumpleks Russell. Struktur afektif 2D bukan konstruksi usang, melainkan pola komputasional yang kokoh.
* **Future Work:** Memperluas pemetaan ke domain interaksi manusia-komputer dan aplikasi terapi afektif yang mematuhi standar *European Union AI Act*.

---

## 💡 Step 9: Sintesis Pencapaian (3 Kalimat Kunci)
1. **Fakta Terbukti:** Model Transformer audio-teks modern secara mandiri (*self-supervised*) membentuk topologi sirkumpleks di mana 75% istilah emosi granular terpetakan dalam deviasi sudut $<30^\circ$ terhadap data manusia Russell (1980).
2. **Lompatan SOTA:** Membuktikan secara matematis bahwa ruang koordinat dua dimensi Valence-Arousal merupakan pola representasi laten universal (*emergent property*) AI audio modern, bukan model psikologi usang.
3. **Kegunaan Praktis:** Memberikan landasan teoretis paling mutakhir bagi Tugas Akhir ITERA untuk menggunakan ruang 2D V-A dan rumus sudut trajektori $\theta = \text{atan2}(\Delta a, \Delta v)$ pada dataset musik audio.

---

## 🎯 Step 10: Research Gap Tiga Lapis (Three-Tier Gap)
1. **Lapis 1 (Gap Penulis):** Analisis topologi terbatas pada frasa wicara dan teks diskrit, belum mengeksplorasi trajektori deret waktu dinamis berkesinambungan.
2. **Lapis 2 (Gap Temuan Audit Kritis Kita):** Belaref et al. membuktikan keberadaan ruang sirkumpleks statis pada embedding AI, namun belum menyentuh persoalan **transisi dinamis antar-segmen (sentakan outro-intro)** pada media musik.
3. **Lapis 3 (Gap Riset Tugas Akhir Kita):**
   * *Formula Gap Naskah Proposal:*  
     > *"Meskipun Belaref et al. (2024) membuktikan bahwa ruang laten representasi AI modern secara intrinsik merekonstruksi geometri sirkumpleks Russell (1980), penerapannya pada sistem temu kembali musik selama ini masih memperlakukan trek audio sebagai representasi statis tunggal, sehingga mengabaikan dinamika trajektori internal lagu yang memicu The Boundary Jump Problem pada penyusunan playlist."*

---

## 🚩 Radar Red Flags Audit
* [x] **Hasil Multi-Seed:** Terpenuhi (menggunakan rata-rata konsensus multi-annotator $>50\%$).
* [x] **Bebas Data Leakage:** Terpenuhi sempurna (representasi diekstraksi *freeze* sebelum *head*).
* [x] **Transparansi Error:** Sangat transparan (membahas anomali *Annoyed* $\Delta \theta = 70,1^\circ$).
* [x] **Kesesuaian Metrik:** Terpenuhi (metrik statistik sirkular formal $x_t, y_t, \theta_t, P_t$).
