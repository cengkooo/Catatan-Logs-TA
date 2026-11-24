---
title: "Draf Naskah Bab 2: Tinjauan Pustaka (Format UNESCO 15,5 x 23 cm)"
tags:
  - draft
  - bab2
  - naskah
  - tinjauan-pustaka
  - state-of-the-art
  - unesco
  - murni-komputasional
status: "READY FOR COMPILATION"
date: 2026-11-24
---

# ✍️ Bab II Tinjauan Pustaka (Skenario 1: Murni Komputasional)

*Dokumen sinkronisasi narasi naskah Bab II mengikuti kaidah Bahasa Peneliti dan standar tata tulis UNESCO ITERA (dilengkapi Tabel 2.1 empat kolom dan kerangka pemikiran).*

---

## 2.1 Landasan Teori

### 2.1.1 Model Emosi Musik Sirkumpleks Russell (1980) dan Revalidasi Modern
Studi komputasi afektif musik bertumpu pada teori psikologi persepsi emosi. James Russell (1980) mengusulkan *Circumplex Model of Affect*, yang mendalilkan bahwa respon afektif manusia tidak terdistribusi dalam kategori kata diskrit yang terpisah, melainkan berakar pada dua dimensi neurofisiologis independen kontinu:
1. **Valence (Kesenangan / Kualitas Afeksi):** Mengukur derajat kebahagiaan atau kepositifan suasana hati, membentang dari kondisi sangat tidak menyenangkan (*negative valence*, seperti sedih dan tertekan) hingga sangat menyenangkan (*positive valence*, seperti gembira dan damai).
2. **Arousal (Aktivasi / Intensitas Fisiologis):** Mengukur tingkat ketergugahan fisiologis dan energi motorik tubuh, membentang dari kondisi pasif atau rendah (*low arousal*, seperti mengantuk dan tenang) hingga sangat bersemangat (*high arousal*, seperti waspada, bersemangat, dan tegang).

Keunggulan utama model dimensional ini dibandingkan model kategorikal Hevner atau Ekman adalah sifatnya yang kontinu dan aljabar. Keadaan afektif dapat diekspresikan sebagai vektor koordinat Cartesian $\mathbf{p} = (v, a) \in [-1.0, +1.0]^2$, sehingga memungkinkan penerapan operasi kalkulus vektor, perhitungan jarak Euclidean, dan interpolasi lintasan mulus yang sangat krusial dalam perancangan kurva *mood arc*.

Meskipun dicetuskan pada tahun 1980, model ini memiliki validitas komputasional kontemporer yang sangat kokoh. Penelitian mutakhir oleh Belaref et al. (2024) yang melakukan *data-driven decoding* terhadap representasi laten jaringan syaraf tiruan multimodal (RoBERTa dan wav2vec 2.0) membuktikan bahwa model Transformer audio secara mandiri (*self-supervised*) mengorganisasikan afeksi manusia mengikuti topologi lingkaran sirkumpleks Russell. Hasil evaluasi membuktikan bahwa 75% dari 28 kata emosi granular terpetakan dalam deviasi sudut sangat presisi ($\Delta \theta < 30^\circ$) terhadap data manusia asli Russell (1980) dengan korelasi angular $r > 0,82$. Kang et al. (2025) kemudian memformulasikan unifikasi matematis antara ruang kontinu dua dimensi ini dengan label kategori afektif modern melalui sudut polar $\theta = \text{atan2}(\Delta a, \Delta v)$, membuktikan bahwa pergerakan sudut vektor emosi merefleksikan pergeseran suasana hati pendengar secara konsisten.

### 2.1.2 Dinamika Temporal Emosi Musik dan Jeda Waktu Persepsi
Musik merupakan media temporal berbasis waktu (*time-dependent medium*). Karakteristik perubahan emosional di dalam musik memiliki sifat asimetri yang khas. Mengacu pada meta-analisis komprehensif 144 studi empiris Music Emotion Recognition (MER) oleh Eerola et al. (2026) pada IEEE Transactions on Affective Computing serta temuan Wen et al. (2025), terdapat dua prinsip temporal fundamental:
* **Asimetri Prediktabilitas Arousal vs Valence:** Dimensi Arousal memiliki korelasi yang sangat kuat dengan parameter akustik fisik audio (seperti RMS *energy*, dinamika spektral, dan tempo), sehingga menghasilkan akurasi prediksi model komputasi yang tinggi dan stabil ($r = 0,68 \pm 0,08$). Sebaliknya, dimensi Valence dipengaruhi oleh struktur harmonik, progresi akor, tangga nada mayor-minor, dan asosiasi kognitif yang lebih kompleks, menghasilkan variasi korelasi yang lebih moderat ($r = 0,42 \pm 0,12$).
* **Jeda Waktu Persepsi (*Perceptual Time Lag*):** Telinga dan otak manusia membutuhkan waktu antara 1,5 hingga 3,0 detik untuk mencerna perubahan dinamika akustik dan menginterpretasikannya sebagai pergeseran suasana hati. Oleh karena itu, sinyal anotasi telemetri kontinu berfrekuensi 2 Hz (interval 500 ms) memerlukan pemfilteran peredam derau (*moving average smoothing filter*) dengan ukuran jendela 3 timestamp (1,5 detik) agar variasi mikro sesaat tidak mengaburkan trajektori makro lagu.

### 2.1.3 Representasi Fitur Akustik Audio Tradisional dan Kontemporer
Sistem temu kembali musik mengandalkan ekstraksi deskriptor akustik untuk menilai kesamaan konten audio antarlagu. Fitur akustik konvensional diekstraksi melalui pustaka pemrosesan sinyal seperti Librosa, mencakup:
1. **Timbral dan Tekstur Spektral:** *Mel-Frequency Cepstral Coefficients* (MFCC), *Spectral Centroid*, *Spectral Rolloff*, dan *Spectral Contrast* yang mengukur kecerahan dan warna suara instrumen.
2. **Ritmik dan Energi:** *Tempo (BPM)*, *Beat Strength*, dan *Root Mean Square (RMS) Energy* yang berbanding lurus dengan dimensi Arousal.
3. **Harmoni dan Nada:** *Chroma Feature* dan *Tonnetz* yang merefleksikan progresi tonalitas dan kunci lagu.

Perkembangan mutakhir sistem temu kembali audio telah melahirkan model fondasi berbasis *self-supervised learning* skala besar, seperti MERT (Li et al., 2024) dan adaptasi HuBERT musik (Sun et al., 2025). MERT membuktikan bahwa representasi representasi *masked audio modeling* mampu menangkap ketergantungan harmoni jangka panjang. Namun, untuk kebutuhan sistem perekomendasi playlist berlatensi rendah pada perangkat komputasi terdistribusi, kombinasi fitur akustik kompak Librosa terstandarisasi tetap menjadi pilihan yang sangat efisien dan transparan untuk diinterpretasikan (*explainable features*).

### 2.1.4 Teori Transisi Halus (*Soft Transition*) dan Inersia Afektif
Dalam menyusun urutan stimulus musikal berkesinambungan, transisi mendadak antarsegmen yang memiliki karakter kontras memicu disonansi perseptual yang mengganggu kenyamanan pendengar. Studi mutakhir Wang et al. (2024) pada perancangan sistem penataan musik *REMAST* (IEEE Transactions on Affective Computing) membuktikan bahwa sistem yang hanya memprioritaskan kecocokan emosi seketika (*real-time emotion fit*) tanpa mengontrol laju perubahan antarsegmen selalu menghasilkan sentakan struktural (*jarring boundary transition*).

Wang et al. (2024) membuktikan bahwa dengan memperhitungkan inersia emosi keadaan sebelumnya melalui mekanisme fusi emosi:
$$\mathbf{e}_{\text{fused}, t} = \frac{\mathbf{e}_{\text{music}, t-1} + \mathbf{e}_{\text{target}, t}}{2}$$
kekacauan transisi akor (*Chord Entropy Coherence* / CEC) dapat direduksi hingga 50,6% (turun dari 7,51 menjadi $3,71 \pm 0,31$), serta menghasilkan peningkatan skor kehalusan transisi subjektif (*softness score*) manusia hingga 3,79 dari 5,00 ($p < 0,03$). Prinsip inersia afektif ini menjadi landasan teoretis bahwa transisi antara dua trek rekaman berurutan wajib mengendalikan jarak perbatasan outro ke intro agar lonjakan emosi tidak melampaui toleransi pendengaran.

### 2.1.5 Sistem Pembangkitan Playlist Berbasis Lintasan Emosi dan The Boundary Jump Problem
Pembangkitan playlist berbasis suasana hati bertujuan menyusun barisan trek musik $P = [s_1, s_2, \dots, s_M]$ yang mengarahkan pendengar dari kondisi awal $P_{\text{start}}$ menuju kondisi akhir $P_{\text{target}}$ melalui serangkaian titik acuan perantara (*waypoints*) $W = [\mathbf{w}_1, \dots, \mathbf{w}_M]$ pada ruang koordinat Valence-Arousal.

Model acuan Gaur dan Donnelly (2020, 2023, 2024) menggunakan pendekatan dua tahap: mengambil $K$ kandidat terdekat di sekitar waypoint menggunakan KNN, lalu melakukan perankingan berdasarkan jarak fitur akustik Spotify pada dataset DMDD. Namun, karena DMDD hanya menyediakan label rata-rata skalar statis ($\bar{v}, \bar{a}$), model Gaur mengabaikan dinamika internal lagu. Ketika lagu pertama yang berkarakter tenang di bagian akhirnya bersambung dengan lagu kedua yang berkarakter enerjik di bagian awalnya, timbul fenomena **The Boundary Jump Problem**. Kondisi ini dibuktikan secara empiris oleh Schweiger et al. (2025), di mana diskontinuitas transisi antartrek berturutan yang melompat melebihi ambang batas ($\Delta > 0,25$) menjadi pemicu utama pendengar melakukan *skip* pada platform penyiaran streaming.

---

## 2.2 Penelitian Terdahulu (*State of the Art*)

Penelitian mengenai sistem pembangkitan playlist dan analisis afektif musik telah berkembang melalui berbagai tonggak penting yang dipetakan secara komprehensif pada Tabel 2.1.

\begin{center}
\textbf{Tabel 2.1 Perbandingan Penelitian Terdahulu}
\end{center}

| Peneliti (Tahun) | Metode dan Dataset | Hasil Utama | Keterbatasan |
| :--- | :--- | :--- | :--- |
| **Cardoso et al. (2011)** | Prototipe *MOODetector* berbasis antarmuka grafis ruang Thayer 2D; dataset audio kecil (~500 lagu). | Pengguna dapat menarik garis lintasan mood secara interaktif untuk mengambil lagu yang sesuai. | Tidak memiliki metrik evaluasi kehalusan formal; fitur audio sangat terbatas dan mengabaikan transisi sekuensial. |
| **Aljanaki et al. (2017)** | Anotasi crowdsourcing kontinu frekuensi 2 Hz pada 1.802 klip musik (45s); dataset benchmark DEAM. | Menghasilkan standar emas dataset MIR pertama dengan anotasi deret waktu Valence-Arousal dinamis. | Hanya mempublikasikan dataset dan model regresi ekstraksi; tidak merancang algoritma optimasi playlist. |
| **Delbouys et al. (2018)** | Fusi multimodal deep learning audio dan teks lirik pada dataset DMDD (18.644 lagu). | Peningkatan akurasi estimasi Valence-Arousal global melalui integrasi fitur multimodal audio-lirik. | Anotasi hanya menyediakan satu nilai rata-rata statis per lagu; kehilangan seluruh dinamika pergeseran internal. |
| **Gaur & Donnelly (2020, 2023)** | Two-Stage Pipeline: interpolasi waypoint KNN + penyaringan kemiripan akustik pada DMDD. | Menghasilkan algoritma pembangkitan mood-arc playlist terarah dengan metrik *Smoothness* dan *Evenness*. | **Static-point matching**: Mengabaikan dinamika intra-lagu sehingga memicu *The Boundary Jump Problem* pada rute lintas kuadran. |
| **Gaur & Donnelly (2024)** | Formalisasi metrik matematis *Smoothness Index* ($\mathcal{S}$) dan *Evenness Index* ($\mathcal{E}$) di forum evaluasi MIREX. | Menyediakan landasan metrik terstandarisasi untuk mengukur kehalusan transisi antartrek berurutan. | Pengujian masih berbasis representasi statis; nilai kehalusan tinggi pada rute diagonal adalah artefak penataan buatan. |
| **Bontempelli et al. (2022)** | Sistem rekomendasi industri *Flow Moods* pada platform Deezer berbasis radio suasana hati. | Mengimplementasikan pengelompokan katalog jutaan lagu ke dalam kuadran emosi komersial berskala masif. | Playlist terkunci pada kategori suasana hati tunggal yang seragam; belum mendukung lintasan dinamis kontinu (*mood arc*). |
| **Tomasi et al. (2023)** | *Reinforcement Learning* (RL) untuk kelanjutan playlist sekuensial otomatis pada katalog Spotify. | Agen RL mampu mengoptimalkan urutan trek sekuensial berdasarkan umpan balik koherensi sekuens. | Komputasi pelatihan RL sangat berat dan sulit diinterpretasikan; mengabaikan kurva koordinat emosi eksplisit. |
| **Thome et al. (2022)** | Analisis korelasi jarak kemiripan audio *self-supervised* CNN terhadap transisi persepsi emosi. | Menemukan bahwa jarak emosi dan jarak akustik tidak berkorelasi linier, menuntut integrasi fusi skor. | Tidak menguji pada perancangan algoritma sekuensial playlist; fokus murni pada analisis representasi audio. |
| **Belaref et al. (2024)** | *Data-driven decoding* model sirkumpleks Russell menggunakan Transformer audio-teks (MSP-Podcast & TESS). | Membuktikan 75% istilah emosi sirkumpleks terpetakan dalam $\Delta \theta < 30^\circ$ ($r > 0,82$) secara alami pada representasi AI. | Evaluasi terbatas pada sinyal audio wicara pendek, belum diuji pada data polifonik musik berdurasi penuh. |
| **Wang et al. (2024)** | Model *REMAST* (IEEE TAC): Fusi inersia emosi masa lalu dan koreksi trajektori pada musik simbolik. | Mereduksi kekacauan transisi akor (CEC) hingga 50,6% dan meraih skor kelembutan transisi tertinggi 3,79/5,00. | Diterapkan pada sintesis musik simbolik MIDI generatif, tidak dapat diaplikasikan langsung pada trek rekaman audio utuh. |
| **Wen et al. (2025)** | Audit kebocoran data (*leakage audit*) pada regresi Arousal dinamis dataset DEAM (IEEE TAC). | Membuktikan pemisahan frame acak memicu inflasi $R^2$ semu 28%–45%; mewajibkan *Song-Level Holdout Split*. | Berfokus pada perbaikan metodologi prediksi deret waktu audio; tidak merancang sistem rekomendasi playlist. |
| **Schweiger et al. (2025)** | Analisis empiris jutaan playlist kurasi manusia Spotify/Deezer terhadap retensi pengguna. | Membuktikan transisi emosi antartrek $\Delta \le 0,25$ adalah syarat retensi dengar (*skip rate* naik 37% jika melompat kasar). | Kajian analitis retrospektif murni; tidak menyediakan algoritma optimasi kurasi playlist otomatis. |
| **Kang et al. (2025)** | Arsitektur multi-task unifikasi model dimensi V-A dan emosi kategorikal (IEEE/ACM TASLP). | Memformulasikan sudut polar $\theta = \text{atan2}(\Delta a, \Delta v)$ sebagai jembatan matematis kontinu-kategori. | Tidak menerapkan pemodelan trajektori untuk penyusunan playlist sekuensial antarlagu. |
| **Eerola et al. (2026)** | Meta-analisis 144 studi empiris Music Emotion Recognition pada IEEE Transactions on Affective Computing. | Mengukuhkan asimetri Arousal ($r = 0,68$) vs Valence ($r = 0,42$) serta jeda persepsi manusia 1,5–3,0 detik. | Berupa studi meta-regresi literatur sintesis; tidak merancang algoritma komputasi playlist baru. |
| **Penelitian Ini (2026)** | Two-stage pipeline: KNN retrieval + **Dynamic Trajectory Alignment Reranker** pada korpus DEAM. | Menyelesaikan *The Boundary Jump Problem* melalui penalti sambungan outro-intro; reduksi Smoothness Index $\ge 15\%$. | Evaluasi berbasis metrik komputasional objektif pada GPU; belum mencakup pengujian usabilitas responden manusia. |

---

### 2.2.1 Sintesis Kesenjangan Riset (*Three-Tier Research Gap*)
Berdasarkan telaah komprehensif pada Tabel 2.1, sintesis kesenjangan penelitian dirumuskan ke dalam tiga lapis:
1. **Lapis 1 (Celah Teoretis dan Desain Baseline):** Model acuan pembangkitan mood-arc Gaur dan Donnelly (2020, 2023) bertumpu pada dataset DMDD yang hanya menyediakan label statis tunggal per lagu. Akibatnya, sistem mengasumsikan suasana hati lagu bersifat konstan, mengabaikan fakta empiris DEAM bahwa 98,11% lagu mengalami pergeseran afektif internal nyata.
2. **Lapis 2 (Celah Metodologis Komparasi):** Penelitian terkini seperti REMAST (Wang et al., 2024) telah membuktikan pentingnya meredam sentakan transisi (*soft transition*) dengan memanfaatkan inersia emosi masa lalu, namun metodenya bekerja dengan menyintesis komposisi simbolik baru (MIDI). Di sisi lain, layanan penyiaran musik digital komersial (Spotify, Deezer) bekerja dengan mengurasi rekaman audio gelombang utuh yang tidak boleh diubah strukturnya.
3. **Lapis 3 (Posisi Kebaruan Tugas Akhir):** Belum ada penelitian yang mengadaptasi prinsip transisi halus (*soft transition*) ke dalam mekanisme perankingan trek rekaman audio utuh menggunakan representasi trajektori dinamis 2 Hz pada korpus benchmark DEAM. Tugas Akhir ini mengisi celah tersebut dengan merumuskan penalti *Boundary Jump Cost* $\mathcal{BJC}$ guna menjamin kontinuitas transisi antarlagu pada penyusunan mood-arc playlist.

---

## 2.3 Kerangka Pemikiran

Alur logika yang menghubungkan identifikasi kesenjangan literatur dengan perancangan metodologi penelitian dipetakan melalui diagram kerangka pemikiran berikut:

```mermaid
flowchart TD
    Masalah["Kelemahan Struktural Model Acuan (Gaur & Donnelly, 2020):<br/>Pencocokan titik statis (static-point matching) mengabaikan dinamika internal lagu,<br/>memicu The Boundary Jump Problem pada sambungan outro-intro trek."] --> Bukti["Bukti Empiris SOTA:<br/>1. DEAM: 98,11% trek mengalami pergeseran emosi internal (Delta = 0,1937 - 0,5950).<br/>2. Schweiger et al. (2025): Lompatan transisi Delta > 0,25 menaikkan skip rate hingga 37%.<br/>3. Wang et al. (2024 / REMAST): Soft transition mereduksi kekacauan transisi harmoni hingga 50,6%."]
    
    Bukti --> Teori["Landasan Teoretis & Validitas Representasi:<br/>1. Russell (1980) & Belaref et al. (2024): Ruang 2D Valence-Arousal terbukti sebagai geometri alami AI.<br/>2. Eerola et al. (2026): Arousal r=0,68 vs Valence r=0,42, serta perceptual lag 1,5-3,0s.<br/>3. Kang et al. (2025): Formulasi sudut arah trajektori polar theta = atan2(Delta A, Delta V)."]
    
    Teori --> Solusi["Solusi yang Diusulkan (Tugas Akhir):<br/>Pipeline Dua Tahap Berbasis Dynamic Mood Trajectory Alignment pada Korpus DEAM:<br/>- Tahap 1: KNN Waypoint Candidate Retrieval di ruang V-A kontinu.<br/>- Tahap 2: Trajectory Alignment Reranker dengan pembobotan Boundary Jump Cost (BJC)."]
    
    Solusi --> Evaluasi["Evaluasi Kuantitatif Terstandarisasi (GPU Benchmark):<br/>- 540 Playlist Batch Run (Rute Diagonal vs Rute Lintas Kuadran).<br/>- Metrik: Smoothness Index (S), Evenness Index (E), dan Boundary Jump Cost.<br/>- Uji Signifikansi Statistik Non-Parametrik Wilcoxon Signed-Rank Test (p < 0,05)."]
    
    Evaluasi --> Luaran["Target Luaran:<br/>Sistem pembangkitan playlist mood-arc yang koheren, mulus, dan terbebas dari sentakan emosi kasar."]
```

Diagram kerangka pemikiran di atas menjembatani pemahaman bahwa kelemahan baseline Gaur diatasi bukan dengan mengganti algoritma retrieval secara radikal, melainkan dengan memperkaya representasi data dari titik statis menjadi vektor trajektori temporal kontinu yang dikendalikan oleh penalti diskontinuitas perbatasan.
