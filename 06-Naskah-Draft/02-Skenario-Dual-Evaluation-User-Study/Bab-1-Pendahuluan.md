---
title: "Draf Naskah Bab 1: Pendahuluan (Skenario 2 - Dual Evaluation: Objektif & User Study)"
tags:
  - draft
  - skenario-2
  - bab1
  - pendahuluan
  - user-study
  - deam
  - unesco
status: "SYNCED WITH LATEX"
date: 2026-11-25
---

# Bab I Pendahuluan

## 1.1 Latar Belakang

Platform penyiaran musik digital (*music streaming services*) seperti Spotify, Apple Music, dan Deezer telah menggeser pola konsumsi musik ke arah daftar putar (*playlist*) otomatis yang dikurasi sesuai konteks dan aktivitas pendengar (Bontempelli et al., 2022; Schweiger et al., 2025). Dalam kajian sistem temu kembali informasi musik (*Music Information Retrieval* / MIR), sebagian besar sistem rekomendasi konvensional masih bertumpu pada penyaringan kolaboratif (*collaborative filtering*) dan pencocokan kemiripan statis yang memperlakukan preferensi pengguna secara terpisah per lagu. Pendekatan tersebut belum memperhitungkan kesinambungan alur emosional di sepanjang sesi mendengarkan.

Kebutuhan pendengar modern bergeser ke arah daftar putar berbasis konteks dan aktivitas, seperti belajar, berolahraga, meditasi, dan tidur, yang menuntut perubahan suasana hati (*mood*) mengikuti lintasan afektif terkontrol (*mood arc*). Layanan penyiaran komersial merespons kebutuhan ini melalui fitur *Flow Moods* pada Deezer (Bontempelli et al., 2022) serta pengembangan model sekuensial berbasis pembelajaran penguatan (*reinforcement learning*) (Tomasi et al., 2023). Studi empiris berskala besar oleh Schweiger et al. (2025) pada jutaan daftar putar kurasi pengguna membuktikan bahwa koherensi sekuensial dan kehalusan transisi antartrek berturutan (*sequential transition coherence*) berkorelasi langsung dengan kenyamanan serta retensi pendengar. Transisi antarlagu yang melompat kasar di ruang emosi ($\Delta > 0{,}25$) meningkatkan tingkat pembatalan dengar (*skip rate*) hingga 37%.

Penyusunan daftar putar berbasis kurva emosi telah dirintis sejak prototipe MOODetector (Cardoso et al., 2011) melalui pemetaan lagu ke dalam ruang afektif dua dimensi *Valence-Arousal* pada model sirkumpleks Russell (1980). Model dimensional ini memiliki landasan komputasional yang kuat. Penelitian mutakhir oleh Belaref et al. (2024) melalui dekode berbasis data (*data-driven decoding*) membuktikan bahwa representasi laten jaringan saraf tiruan modern (*Transformer embeddings*) secara alami merekonstruksi topologi lingkaran sirkumpleks Russell dengan korelasi keteraturan angular $r > 0{,}82$, serta memetakan 75% konsep emosi dalam deviasi sudut presisi ($\Delta \theta < 30^\circ$). Temuan tersebut menegaskan bahwa ruang *Valence-Arousal* merupakan geometri representasi alami untuk pemodelan afektif komputasional.

Penelitian acuan oleh Gaur dan Donnelly (2023, 2024) mengusulkan algoritma pembangkitan daftar putar *mood-arc* dua tahap. Tahap pertama menggunakan *K-Nearest Neighbors* (KNN) untuk menginterpolasi dan mengambil kandidat lagu di sekitar titik acuan (*waypoint*) lintasan emosi, lalu tahap kedua menyaring kandidat berdasarkan kemiripan fitur akustik. Model tersebut diuji pada dataset DMDD (Delbouys et al., 2018) dan menjadi rujukan utama pengukuran metrik kelurusan lintasan (*Linearity Smoothness* berbasis korelasi Pearson) serta keseragaman (*Evenness Index*).

Meskipun model Gaur dan Donnelly (2023, 2024) menghasilkan penelusuran kandidat yang terarah, pendekatan tersebut memiliki kelemahan struktural berupa pencocokan titik statis (*static-point matching*). Pada dataset DMDD, setiap lagu direpresentasikan oleh satu nilai rata-rata skalar *Valence* dan *Arousal* ($\bar{v}, \bar{a}$) untuk keseluruhan durasi audio. Representasi statis ini mengasumsikan suasana hati lagu bersifat konstan dari awal hingga akhir. Penelitian Wang et al. (2024) pada sistem penataan musik afektif REMAST membuktikan bahwa pencocokan emosi seketika tanpa memperhitungkan inersia dan kontinuitas transisi antarsegmen memicu sentakan struktural yang merusak koherensi dengar. Analisis empiris pada korpus DEAM (*Database for Emotion Analysis in Music*, Aljanaki et al., 2017) yang memuat anotasi dinamis 2 Hz pada 1.802 klip musik menunjukkan bahwa 98,11% lagu mengalami pergeseran emosi internal sepanjang durasinya, dengan jarak pergeseran rata-rata awal ke akhir $\Delta = 0{,}1937$ dan rentang dinamis intra-lagu mencapai $0{,}5950$. Studi Pyrovolakis et al. (2022) mengonfirmasi bahwa reduksi lagu menjadi titik rata-rata statis menghilangkan 15% hingga 35% variansi informasi afektif audio.

Ketiadaan representasi dinamika internal memicu kegagalan perseptual yang disebut *The Boundary Jump Problem*, yaitu diskontinuitas emosi tajam ketika bagian penutup (*outro*) lagu $i$ bersambung langsung dengan bagian pembuka (*intro*) lagu $i+1$, meskipun kedua lagu memiliki nilai rata-rata statis yang berdekatan. Kondisi tersebut menyebabkan daftar putar yang tampak halus pada tingkat rata-rata trek tetap memicu sentakan emosi kasar saat didengarkan secara berurutan. Hasil replikasi awal pada 540 pengujian beruntun (*batch run*) menunjukkan bahwa skor *Linearity Smoothness* berbasis korelasi Pearson ($|\rho|$) yang tinggi pada model Gaur ($0{,}9950$) hanya muncul sebagai artefak rute diagonal buatan (Q3 ke Q1), sedangkan pada rute lintas kuadran realistis (Q1 ke Q2 dan Q1 ke Q4), korelasi kelurusan tersebut turun ke rentang $0{,}6628$ hingga $0{,}7189$. Selain itu, metrik korelasi titik statis tersebut tidak mengukur jarak lompatan emosi pada sambungan *outro-intro*.

Kelemahan tersebut diperparah oleh ketiadaan validasi perseptual pendengar manusia pada penelitian terdahulu. Evaluasi MIR berbasis metrik komputasional murni sering kali tidak sejalan sepenuhnya dengan pengalaman mendengar nyata. Studi Daikoku et al. (2022) menemukan bahwa tingkat keselarasan (*agreement rate*) antara metrik matematis otomatis MIR dan persepsi subjektif manusia hanya berada pada tingkat moderat ($r = 0{,}42$ hingga $0{,}58$). Penurunan matematis pada jarak lompatan batas (*Boundary Smoothness*) belum cukup menjamin kenyamanan transisi di telinga pendengar. Pembuktian efektivitas algoritma *mood-arc* menuntut kerangka evaluasi ganda (*Dual Evaluation Framework*) yang memadukan pengujian komputasional berskala besar dengan pengujian psikoakustik langsung terhadap pendengar manusia.

Belum ada studi yang menguji apakah pemanfaatan trajektori dinamis *mood* internal lagu menghasilkan transisi daftar putar *mood-arc* yang lebih koheren dibandingkan pendekatan *static-point matching*, sekaligus mengukur dampaknya terhadap kenyamanan dengar manusia. Penelitian ini mengusulkan pengembangan *pipeline* pembangkitan daftar putar *mood-arc* dua tahap berbasis *Dynamic Mood Trajectory Alignment* pada korpus DEAM dengan kerangka evaluasi ganda yang menggabungkan metrik komputasional GPU dan pengujian persepsi subjektif (*user listening study*).

---

## 1.2 Rumusan Masalah

Berdasarkan latar belakang yang telah diuraikan, rumusan masalah dalam penelitian ini disusun sebagai berikut:
1. Bagaimana merancang dan mengimplementasikan arsitektur *pipeline* pembangkitan daftar putar *mood-arc* dua tahap pada korpus DEAM yang memadukan penelusuran kandidat KNN dengan penyelarasan vektor trajektori dinamis serta penalti lompatan batas (*Boundary Jump Cost*)?
2. Bagaimana kinerja kelancaran transisi (*Boundary Smoothness*), keseragaman sebaran (*Evenness Index*), dan akumulasi penalti lompatan batas model usulan dibandingkan dengan model acuan *static-point matching* pada pengujian rute diagonal maupun lintas kuadran?
3. Bagaimana tingkat penerimaan perseptual pendengar (*perceived smoothness*, *acoustic continuity*, dan *emotional naturalness*) terhadap transisi antarlagu yang dihasilkan model usulan, serta seberapa kuat korelasinya dengan metrik komputasional objektif?

---

## 1.3 Tujuan Penelitian

Tujuan yang dicapai melalui penelitian ini meliputi:
1. Merancang dan mengimplementasikan arsitektur *pipeline* komputasional dua tahap berbasis *KNN candidate retrieval*, ekstraksi vektor trajektori internal lagu, dan penalti *Boundary Jump Cost* pada korpus audio DEAM, dengan indikator keberhasilan berupa modul kode Python berbasis PyTorch yang mengeksekusi penelusuran daftar putar secara deterministik dan dapat direproduksi.
2. Mengevaluasi performa kelancaran transisi, keseragaman sebaran, dan reduksi lompatan batas model usulan terhadap model acuan *static-point matching* melalui pengujian komparatif 540 *batch run* pada rute diagonal dan lintas kuadran, dengan indikator keberhasilan berupa penurunan nilai jarak lompatan batas (*Boundary Smoothness*) minimal 15% tanpa menurunkan *Evenness Index* secara nyata berdasarkan uji statistik non-parametrik *Wilcoxon Signed-Rank Test* ($p < 0{,}05$).
3. Mengukur dan memvalidasi tingkat penerimaan perseptual pendengar melalui pengujian dengar buta (*Blind A/B Listening Test*) skala laboratorium terhadap minimal 30 responden manusia menggunakan stimulus sambungan transisi 30 detik dan kuesioner skala Likert 5 poin, serta menganalisis korelasinya terhadap metrik objektif melalui korelasi peringkat Spearman, dengan indikator keberhasilan berupa skor preferensi model usulan yang lebih tinggi ($p < 0{,}05$) dan reliabilitas instrumen *Cronbach's Alpha* minimal $0{,}70$.

---

## 1.4 Batasan Penelitian

Ruang lingkup dan batasan operasional penelitian ini ditetapkan sebagai berikut:
1. Dataset terbatas pada korpus audio terbuka DEAM yang mencakup 1.802 klip musik berdurasi 45 detik dengan anotasi emosi kontinu berfrekuensi 2 Hz.
2. Sesuai protokol resmi anotasi DEAM, 15 detik pertama dari setiap klip audio diabaikan sebagai fase adaptasi anotator, sehingga analisis dinamika internal bertumpu pada 30 detik segmen stabil (90 *timestamp* per lagu).
3. Ruang koordinat afektif dibatasi pada model sirkumpleks dua dimensi ortogonal Russell yang mencakup dimensi *Valence* dan *Arousal* dalam rentang ternormalisasi $[-1{,}0, +1{,}0]$.
4. Pengujian persepsi manusia dirancang sebagai validasi subjektif komparatif skala laboratorium dengan melibatkan minimal 30 responden mahasiswa atau dewasa muda pendengar aktif musik digital (minimal 1 jam per hari) yang memiliki fungsi pendengaran normal. Stimulus difokuskan pada klip sambungan transisi terisolasi berdurasi 30 detik (15 detik *outro* lagu pertama disambung 15 detik *intro* lagu kedua) untuk mencegah kelelahan pendengar dan bias preferensi genre.
5. Pelaksanaan pengujian pengguna mematuhi etika penelitian, prosedur persetujuan sadar (*informed consent*), serta perlindungan data pribadi responden sesuai Undang-Undang Nomor 27 Tahun 2022 tentang Perlindungan Data Pribadi.
6. Algoritma penelusuran kandidat tahap pertama dibatasi pada KNN deterministik guna menjaga kesetaraan pembandingan terhadap model acuan *static-point matching*.
7. Penelitian ini tidak mencakup perancangan atau pengembangan aplikasi dan tidak membahas implementasi sistem dalam skenario *real-time*.

---

## 1.5 Manfaat Penelitian

Penelitian ini memberikan kontribusi pada dua aspek utama:
1. Manfaat teoretis: memperkaya kajian MIR dan psikoakustik komputasional melalui bukti empiris mengenai pemodelan audio sebagai trajektori temporal kontinu, serta memformalkan keterkaitan antara metrik matematis algoritmik dan persepsi kenyamanan afektif manusia.
2. Manfaat praktis: menyediakan cetak biru arsitektur sistem perekomendasi daftar putar yang teruji secara komputasional dan tervalidasi secara perseptual, sehingga siap diterapkan pada layanan penyiaran musik digital untuk meningkatkan retensi pendengar.

---

## 1.6 Sistematika Penulisan

Laporan tugas akhir ini disusun dalam lima bab yang saling berkaitan. Bab I menguraikan latar belakang masalah industri penyiaran musik, identifikasi *The Boundary Jump Problem*, justifikasi empiris korpus DEAM, kebutuhan evaluasi ganda, rumusan masalah, tujuan, batasan, manfaat, dan sistematika penulisan. Bab II memaparkan landasan teori model sirkumpleks Russell beserta revalidasi modernnya, dinamika temporal emosi musik, representasi fitur audio, teori transisi halus, psikoakustik evaluasi dengar, perbandingan penelitian terdahulu, sintesis kesenjangan riset, dan kerangka pemikiran. Bab III merinci alur penelitian tujuh tahap, prapemrosesan dataset DEAM bebas kebocoran data, perancangan *pipeline* dua tahap dan formulasi penalti *Boundary Jump Cost*, lingkungan eksperimen GPU, protokol pengujian 540 *batch run*, serta desain pengujian dengar pengguna. Bab IV menyajikan hasil eksperimen komputasional pada GPU, hasil pengujian dengar manusia, analisis korelasi metrik dengan persepsi, serta pembahasan teknis fenomena *boundary jump*. Bab V merangkum jawaban atas rumusan masalah berdasarkan temuan kuantitatif dan perseptual serta menguraikan saran pengembangan lanjutan.


---

# 📝 Catatan Belajar, Konsep Dasar, Glosarium Teknis & Poin Inti Slide/Asistensi

> [!tip] Tujuan Catatan Ini
> Bagian ini merupakan panduan internal untuk persiapan **presentasi Sempro (10 menit)** dan **asistensi/bimbingan dengan Pak Hafiz**. Bagian teks **di atas garis pemisah** adalah naskah murni yang sinkron dengan LaTeX, sedangkan bagian **di bawah ini** adalah bekal pemahaman konseptual dan poin bicara (*talking points*).

---

## 🎯 1. Poin-Poin Inti Wajib untuk Slide & Asistensi (Sorotan Tebal)

Saat presentasi atau ditanya dosen, pastikan poin-poin berikut tersampaikan dengan tegas:

1. **Urgensi Masalah Industri:**
   - **Lebih dari 60% waktu mendengarkan musik di layanan streaming berasal dari playlist**, bukan memutar lagu satu per satu.
   - **Transisi emosi antarlagu yang melompat kasar ($\Delta > 0{,}25$) menaikkan tingkat *skip rate* pendengar hingga 37%** ([[05-Schweiger2025-Playlist-Coherence|Schweiger et al., 2025]]). Jadi kehalusan transisi bukan sekadar estetika, melainkan berdampak langsung pada retensi pengguna.

2. **Kenapa Pakai Ruang Emosi Russell (1980) Meski Sudah Tua?**
   - Ruang 2D **Valence–Arousal** bukan konstruksi subjektif kuno, melainkan **tervalidasi ulang oleh AI modern ([[23-Belaref2024-Data-Driven-Russell-Circumplex|Belaref et al., 2024]])**: representasi laten *Transformer* secara alami membentuk lingkaran sirkumpleks Russell dengan **korelasi angular $r > 0{,}82$** (75% konsep emosi akurat dalam $\Delta\theta < 30^\circ$).

3. **Kritik Tajam ke Model Acuan (Gaur & Donnelly, 2023/2024):**
   - Kelemahan baseline Gaur bukan karena algoritma KNN-nya salah, melainkan **keterbatasan data DMDD yang hanya punya satu titik rata-rata statis per lagu (*static-point matching*)**.
   - **Fakta empiris di korpus DEAM: 98,11% lagu mengalami pergeseran emosi internal** (rata-rata $\Delta = 0{,}1937$, rentang hingga $0{,}5950$). Mereduksi lagu menjadi satu titik menghilangkan **15%–35% variansi emosi audio** ([[16-Pyrovolakis2022-Multimodal-Song-Mood|Pyrovolakis et al., 2022]]).

4. **Masalah Utama yang Dipecahkan (*The Boundary Jump Problem*):**
   - Dua lagu bisa punya nilai rata-rata yang mirip, tetapi **bagian akhir (*outro*) lagu 1 bertolak belakang dengan bagian awal (*intro*) lagu 2**, sehingga saat disambung terdengar menyentak.
   - **Bukti replikasi awal 540 *batch run*: skor kehalusan tinggi Gaur ($0{,}9950$) hanyalah artefak rute diagonal buatan (Q3 $\to$ Q1)**; saat diuji pada rute lintas kuadran realistis (Q1 $\to$ Q2 atau Q1 $\to$ Q4), skornya anjlok ke **$0{,}6628$–$0{,}7189$**.

5. **Kenapa Harus *Dual Evaluation* (GPU + *User Listening Study*)?**
   - **Metrik matematis MIR saja hanya berkorelasi moderat dengan telinga manusia ($r = 0{,}42$–$0{,}58$)** ([[11-Daikoku2022-Human-Automated-Similarity|Daikoku et al., 2022]]).
   - **Solusi Tugas Akhir ini:** menggabungkan **pengujian komputasional objektif (540 *batch run*, target reduksi *Smoothness Index* $\ge 15\%$)** dengan **validasi subjektif *Blind A/B Listening Test* ($N \ge 30$ responden, klip sambungan 30 detik, Likert 5 poin, uji Wilcoxon $p < 0{,}05$)**.

6. **Tiga Pilar Kontribusi (Sesuai 3 Rumusan Masalah & Tujuan):**
   - **Pilar 1 (Desain):** *Pipeline* 2 tahap (**KNN *Candidate Retrieval*** + ***Dynamic Trajectory Alignment Reranker*** dengan penalti ***Boundary Jump Cost***).
   - **Pilar 2 (Uji Objektif):** Mengalahkan *static-point matching* pada 540 *batch run* rute diagonal & lintas kuadran.
   - **Pilar 3 (Uji Subjektif & Korelasi):** Membuktikan bahwa transisi yang lebih halus secara matematis benar-benar terasa lebih nyaman oleh pendengar manusia.

---

## 🧠 2. Penjelasan Konsep Dasar & Referensi Rujukan

1. **Ruang Afektif Dua Dimensi (*Circumplex Model of Affect*):**
   - **Konsep:** Emosi musik tidak dikotak-kotakkan secara kaku (misal: hanya "sedih" atau "senang"), melainkan dipetakan sebagai titik koordinat kontinu $(v, a)$ dalam bidang 2D: sumbu horizontal **Valence** (negatif/sedih $\leftrightarrow$ positif/gembira) dan sumbu vertikal **Arousal** (energi rendah/tenang $\leftrightarrow$ energi tinggi/bersemangat). Karena berupa angka koordinat, kita bisa menghitung jarak, sudut, dan membuat lintasan garis lurus atau kurva antarlagu.
   - **Referensi:** [[03-Russell1980-Circumplex-Model|Russell (1980)]] dan validasi modern oleh [[23-Belaref2024-Data-Driven-Russell-Circumplex|Belaref et al. (2024)]].

2. **Dinamika Intra-Lagu (*Intra-Song Mood Dynamics*) & Anotasi 2 Hz:**
   - **Konsep:** Suasana hati sebuah lagu berubah seiring waktu (misal: *intro* pelan, *reff* meledak, *outro* mereda). Dataset DEAM merekam penilaian emosi manusia setiap **0,5 detik (frekuensi 2 Hz)** selama 45 detik klip lagu (15 detik pertama dibuang karena fase adaptasi pendengar, tersisa 30 detik stabil = 90 *timestamp*).
   - **Referensi:** [[02-Aljanaki2017-Developing-Benchmark-DEAM|Aljanaki et al. (2017)]] dan [[16-Pyrovolakis2022-Multimodal-Song-Mood|Pyrovolakis et al. (2022)]].

3. ***Static-Point Matching* vs *Dynamic Trajectory Alignment*:**
   - **Konsep:** *Static-point matching* menganggap satu lagu sebagai **satu titik rata-rata** $(\bar{v}, \bar{a})$. Sebaliknya, *Dynamic Trajectory Alignment* memodelkan lagu sebagai **vektor panah berarah** dari segmen pembuka (*intro*) menuju segmen penutup (*outro*), sehingga sistem memilih lagu yang arah pergeseran emosinya searah dengan alur *mood arc* playlist dan titik sambungan *outro*-nya dekat dengan *intro* lagu berikutnya.
   - **Referensi:** Model acuan [[01-Gaur2023-Mood-Dynamic|Gaur & Donnelly (2023, 2024)]] vs konsep *Soft Transition* dan inersia afektif dari [[22-Wang2024-REMAST-Soft-Transition|Wang et al. (2024 - REMAST)]].

4. ***The Boundary Jump Problem* & Penalti *Boundary Jump Cost* ($\mathcal{BJC}$):**
   - **Konsep:** Fenomena "sentakan" emosi ketika detik terakhir lagu A (misal tenang) bertemu detik pertama lagu B (misal keras/enerjik) meski rata-rata kedua lagu berdekatan. $\mathcal{BJC}$ mengukur jarak Euclidean langsung antara posisi *outro* lagu sebelumnya dan posisi *intro* lagu kandidat berikutnya, lalu menjadikannya penalti dalam pemilihan lagu.
   - **Referensi:** Terinspirasi inersia afektif [[22-Wang2024-REMAST-Soft-Transition|Wang et al. (2024)]] dan ambang *skip rate* $\Delta > 0{,}25$ dari [[05-Schweiger2025-Playlist-Coherence|Schweiger et al. (2025)]].

5. **Kerangka Evaluasi Ganda (*Dual Evaluation Framework*):**
   - **Konsep:** Menggabungkan dua jenis pembuktian: (1) pembuktian **komputasional objektif** pada GPU menggunakan metrik matematis otomatis, dan (2) pembuktian **perseptual subjektif** melalui telinga manusia (*User Listening Study*). Hal ini wajib dilakukan karena metrik matematis sering tidak sepenuhnya mewakili rasa nyaman pendengar.
   - **Referensi:** [[11-Daikoku2022-Human-Automated-Similarity|Daikoku et al. (2022)]].

---

## 📖 3. Glosarium Kata-Kata Teknis pada Bab I

| Istilah Teknis | Penjelasan Sederhana (Untuk Jawab Penguji) |
| :--- | :--- |
| **Music Information Retrieval (MIR)** | Bidang ilmu komputer yang fokus mengekstrak informasi bermakna (genre, tempo, emosi, kemiripan) dari sinyal audio musik secara otomatis. |
| **Collaborative Filtering** | Metode rekomendasi tradisional berbasis pola kesukaan pengguna lain ("orang yang suka lagu A biasanya suka lagu B"), tanpa melihat isi/emosi lagunya. |
| **Mood Arc** | Kurva atau lintasan perubahan suasana hati yang terencana dari awal playlist hingga akhir playlist (misal: dari sedih ke gembira). |
| **Valence & Arousal** | Dua sumbu emosi: *Valence* = tingkat positif/negatif perasaan (senang vs sedih); *Arousal* = tingkat energi/aktivasi (bersemangat vs tenang). |
| **Transformer Embeddings** | Representasi vektor numerik hasil ekstraksi model AI modern (jaringan saraf *Transformer*) yang menangkap makna semantik atau akustik secara padat. |
| **K-Nearest Neighbors (KNN)** | Algoritma pencarian yang mengambil $K$ kandidat lagu dengan jarak koordinat terdekat terhadap titik target (*waypoint*) yang dicari. |
| **Waypoint** | Titik-titik perantara di sepanjang kurva *mood arc* yang menjadi target koordinat untuk setiap urutan lagu ke-$1, 2, \dots, M$ dalam playlist. |
| **Static-Point Matching** | Pencocokan lagu yang hanya melihat satu nilai rata-rata emosi keseluruhan lagu dan mengabaikan perubahan emosi dari awal sampai akhir lagu. |
| **Smoothness Index ($\mathcal{S}$)** | Metrik yang mengukur seberapa halus (kecil selisih jaraknya) perpindahan emosi antartrek berturutan; **semakin kecil nilainya semakin halus**. |
| **Evenness Index ($\mathcal{E}$)** | Metrik yang mengukur keseragaman jarak langkah antar-waypoint; nilai mendekati nol berarti laju perubahan emosi berjalan konsisten/rata. |
| **Intra-Song Mood Dynamics** | Pergeseran atau dinamika perubahan suasana hati yang terjadi di dalam satu lagu itu sendiri dari bagian awal hingga bagian akhir. |
| **Outro & Intro** | *Outro* adalah bagian penutup sebuah lagu (dalam riset ini: detik 42–45); *Intro* adalah bagian pembuka lagu berikutnya (detik 15–18 setelah *offset* adaptasi). |
| **Batch Run** | Eksekusi pengujian otomatis secara massal (540 skenario rute playlist sekaligus) agar hasil evaluasi stabil dan bebas kebetulan. |
| **Blind A/B Listening Test** | Uji dengar buta di mana responden membandingkan dua audio (Versi A dan Versi B) tanpa tahu mana buatan model usulan dan mana buatan model acuan, agar penilaian bebas bias. |
| **Listener Fatigue** | Kelelahan pendengaran responden akibat mendengarkan audio terlalu lama; dicegah dengan memotong stimulus uji menjadi klip transisi terisolasi 30 detik saja. |
| **Wilcoxon Signed-Rank Test** | Uji statistik non-parametrik untuk membandingkan dua kelompok berpasangan (Model Usulan vs Baseline) ketika data tidak diasumsikan berdistribusi normal (seperti skor Likert). |
| **Cronbach's Alpha ($\alpha$)** | Ukuran konsistensi internal butir pertanyaan kuesioner; kuesioner dianggap reliabel/andal jika nilai $\alpha \ge 0{,}70$. |
| **Korelasi Peringkat Spearman** | Metode statistik untuk mengukur kekuatan hubungan antara dua variabel berbasis peringkat (misal: apakah turunnya nilai $\mathcal{S}$ komputer sejalan dengan naiknya skor kepuasan manusia). |
| **KNN Deterministik** | Pencarian KNN yang hasilnya selalu sama dan konsisten setiap kali dijalankan ulang (tanpa unsur acak), sehingga perbandingan dengan baseline adil dan dapat direproduksi. |
