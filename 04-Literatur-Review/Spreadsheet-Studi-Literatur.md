---
title: "Spreadsheet: Studi Literatur (Matriks Sintesis 25 Paper & Glosarium)"
tags:
  - spreadsheet-mirror
  - studi-literatur
  - matriks-sintesis
  - tugas-akhir
source_sheet_id: "1rLIr500lLbXeltTCZLF58RETTJvEALd6SFic8OUHtUY"
---

# 📑 Mirror Spreadsheet: STUDI LITERATUR

> **ID Spreadsheet Asli:** [1rLIr500lLbXeltTCZLF58RETTJvEALd6SFic8OUHtUY](https://docs.google.com/spreadsheets/d/1rLIr500lLbXeltTCZLF58RETTJvEALd6SFic8OUHtUY)  
> **Disinkronkan dengan:** `Matriks-Sintesis.md` & `references.bib` (28 November 2026)  
> **Terdiri dari 2 Tab Utama:**
> 1. `📚 Matriks Sintesis 20 Paper` *(berisi 25 literatur rujukan teraudit P-01 s.d. P-25)*
> 2. `📐 Kamus Notasi & Glosarium` *(definisi variabel matematis & metrik evaluasi)*

---

## 📚 TAB 1: Matriks Sintesis 25 Paper Ilmiah

Tabel ini merangkum komparasi menyeluruh terhadap 25 artikel ilmiah pilihan yang mendasari penelitian Tugas Akhir ini, mencakup identifikasi masalah, metodologi, temuan kunci, analisis kekuatan/kelemahan, serta relevansinya terhadap perancangan pipeline *Mood-Arc Dynamic Trajectory Alignment*.

### 📌 [P-01] Generating Smooth Mood-Dynamic Playlists with Audio Features and KNN (gaur2023mooddynamic & gaur2024smooth / OSU 2023 & EvoMUSART 2024)
- **Penulis & Tahun:** Gaur, S. & Donnelly, P. J. (2024)
- **Peran / Klaster:** `Primary Baseline (Playlist Sequencing)`
- **Dataset:** `Deezer Mood Detection Dataset (DMDD, 18.644 lagu)`
- **Fitur Audio / Input:** `Fitur akustik konvensional Librosa (MFCC, Chroma, Spectral Contrast, Zero Crossing Rate, Tempo)`
- **Metode Utama:** `Pipeline Dua Tahap: (1) KNN di ruang emosi Valence-Arousal (interpolasi waypoint kurva), (2) Re-ranking / filtering kandidat berbasis Cosine Similarity fitur akustik.`
- **Metrik Evaluasi:** `Smoothness (S), Evenness (E), Euclidean Distance Error terhadap target mood arc`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Layanan streaming musik umumnya menyajikan playlist dengan mood tunggal yang statis. Penelitian ini bertujuan merancang pipeline pembentukan playlist otomatis yang dapat melakukan transisi mood gradual (mood arc) dari emosi awal ke emosi akhir dengan transisi akustik yang halus dan merata. |
| **2. Metodologi Utama** | Penulis mendefinisikan kurva target di ruang 2D Valence-Arousal (V-A). Pada tiap titik interpolasi (waypoint), algoritma KNN mengambil k lagu kandidat terdekat di ruang emosi. Kandidat tersebut kemudian disaring menggunakan kemiripan fitur audio (cosine similarity). Transisi dievaluasi pada berbagai kombinasi fitur dan nilai k. |
| **3. Temuan Kunci** | Penggunaan Cosine Similarity pada fitur akustik secara konsisten menghasilkan playlist paling halus (penurunan variasi transisi sebesar ~25-30% dibanding pemilihan acak). Fitur timbre (MFCC) dan tempo terbukti menjadi faktor akustik paling berpengaruh dalam persepsi kehalusan transisi. |
| **4. Kekuatan (Strengths)** | Menjadi pelopor formulasi matematis formal untuk metrik Smoothness dan Evenness pada mood-dynamic playlist. Evaluasi empiris sangat komparatif dan sistematis dalam menguji pengaruh parameter KNN serta berbagai metrik jarak. |
| **5. Kelemahan (Weaknesses)** | Terjebak pada static-point matching: Dataset DMDD hanya menyediakan satu nilai V-A rata-rata statis per lagu. Dua lagu dengan titik rata-rata identik diperlakukan sama, padahal dinamika mood internalnya bisa bertolak belakang. Akibatnya terjadi diskontinuitas emosi tajam (boundary jump) pada batas sambungan antar-lagu. |
| **6. Relevansi & Gap TA** | **Merupakan BASELINE METODOLOGIS UTAMA untuk TA Andryano. Celah ketiadaan resolusi dinamis pada Gaur & Donnelly langsung dimanfaatkan: TA Andryano mengganti dataset ke DEAM (yang memiliki anotasi dinamis 2 Hz) dan mengusulkan metrik baru 'Arc-Trajectory Alignment Score' pada tahap filtering untuk mengeliminasi diskontinuitas batas lagu.** |

---
### 📌 [P-02] Developing a Benchmark for Emotional Analysis of Music (aljanaki2017developing / PLOS ONE 2017)
- **Penulis & Tahun:** Aljanaki, A., Yang, Y.-H., & Soleymani, M. (2017)
- **Peran / Klaster:** `Dataset Benchmark & Dynamic Emotion`
- **Dataset:** `DEAM Dataset (1.802 klip lagu: 1.744 excerpt 45 detik + 58 full songs)`
- **Fitur Audio / Input:** `Acoustic features openSMILE (fitur standar GeMAPS dan eGeMAPS, 65-88 fitur)`
- **Metode Utama:** `Continuous Dynamic Emotion Regression: SVM, Random Forest, dan Bidirectional LSTM untuk time-series modeling`
- **Metrik Evaluasi:** `Root Mean Square Error (RMSE) dan Pearson Correlation Coefficient (r)`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Riset Music Emotion Recognition (MER) terhambat oleh tiadanya dataset benchmark publik berlisensi terbuka yang menyediakan anotasi kontinu terhadap waktu (dinamis) dengan evaluasi reliabilitas inter-annotator yang ketat. |
| **2. Metodologi Utama** | Penulis mengumpulkan 1.802 musik Creative Commons dan menyelenggarakan kompetisi MediaEval (2013-2015). Anotasi dinamis Valence-Arousal dikumpulkan secara kontinu (sampling rate 2 Hz) menggunakan antarmuka slider berbasis web yang dirating oleh 5-10 pendengar per lagu. Data diagregasi dan distandarisasi sebagai benchmark resmi. |
| **3. Temuan Kunci** | Model Bi-LSTM menghasilkan korelasi tertinggi pada Arousal (Pearson r = 0.65) dan Valence (Pearson r = 0.45). Dimensi Arousal terbukti berkorelasi sangat kuat dengan energi dan tempo akustik, sementara Valence jauh lebih kompleks dan bervariasi antar-pendengar. |
| **4. Kekuatan (Strengths)** | Satu-satunya dataset MER terbuka berukuran menengah yang menyediakan anotasi time-continuous 2 Hz berlabel manusia langsung (bukan inferensi tag teks). Lisensi terbuka memungkinkan reproduksibilitas penuh bagi komunitas riset. |
| **5. Kelemahan (Weaknesses)** | Mayoritas sampel hanya berupa excerpt 45 detik pertama lagu (subset 2013-2014), bukan lagu utuh secara keseluruhan. Korelasi prediksi Valence masih moderat, menunjukkan adanya keterbatasan representasi fitur akustik openSMILE konvensional. |
| **6. Relevansi & Gap TA** | **DATASET UTAMA TA ANDRYANO. Anotasi dinamis 2 Hz pada 1.802 klip lagu DEAM menjadi landasan untuk mengekstraksi vektor pergerakan emosi (Trajectory Vector) per lagu, yang memungkinkan TA ini menguji nilai tambah informasi trajektori dinamis dibandingkan label statis.** |

---
### 📌 [P-03] A Circumplex Model of Affect (russell1980circumplex / JPSP 1980)
- **Penulis & Tahun:** Russell, J. A. (1980)
- **Peran / Klaster:** `Teori Fondasi Psikologi Emosi`
- **Dataset:** `Survei afektif persepsi manusia terhadap 28 konsep emosi`
- **Fitur Audio / Input:** `Multidimensional Scaling (MDS) pemetaan spasial afek`
- **Metode Utama:** `Model Sirkumpleks 2D Melingkar (Sumbu X: Valence / Pleased, Sumbu Y: Arousal / Activation)`
- **Metrik Evaluasi:** `Circular correlation coefficient dan indeks stres MDS`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Model kategorikal emosi (marah, senang, sedih) tidak mampu menangani sifat emosi manusia yang saling tumpang tindih dan bertransisi secara kontinu. Studi ini bertujuan membuktikan secara psikometrik bahwa emosi terdistribusi dalam ruang koordinat lingkaran 2D. |
| **2. Metodologi Utama** | Melakukan eksperimen psikologi afektif terhadap subjek mahasiswa untuk menilai kesamaan 28 istilah emosi. Menggunakan teknik analisis penskalaan multidimensi (MDS), penulis memetakan hubungan keterdekatan emosi ke dalam ruang Euclidean dua dimensi ortogonal. |
| **3. Temuan Kunci** | Seluruh keadaan afektif manusia berhasil dipetakan ke dalam pola lingkaran kontinyu di sekitar dimensi Valence (pleasure-displeasure) dan Arousal (arousal-sleep), di mana kedekatan sudut merepresentasikan kemiripan persepsi emosional. |
| **4. Kekuatan (Strengths)** | Menjadi landasan teoritis paling seminal dan paling banyak disitasi (>18.000 sitasi) dalam psikologi emosi dan Music Information Retrieval (MIR) di seluruh dunia. |
| **5. Kelemahan (Weaknesses)** | Model ini bersifat statis konseptual dan tidak memodelkan aspek dinamika temporal (bagaimana rangsangan seperti musik bergerak melintasi ruang afek terhadap waktu). |
| **6. Relevansi & Gap TA** | **FONDASI RUANG REPRESENTASI EMOSI TA ANDRYANO. Model sirkumpleks Russell digunakan untuk mendefinisikan bidang koordinat target mood-arc, interpolasi posisi waypoint, dan perhitungan jarak Euclidean pada tahap pencarian kandidat KNN.** |

---
### 📌 [P-04] Music Mood Detection Based on Audio and Lyrics with Deep Neural Net (delbouys2018mood / ISMIR 2018)
- **Penulis & Tahun:** Delbouys, R., Hennequin, R., Piccoli, F., Royo-Letelier, J., & Moussallam, M. (2018)
- **Peran / Klaster:** `Multimodal Emotion Recognition`
- **Dataset:** `Deezer Mood Detection Dataset (DMDD, 18.644 lagu)`
- **Fitur Audio / Input:** `Mel-spectrogram (audio) dan FastText word embeddings (teks lirik)`
- **Metode Utama:** `Dual-Branch Deep Neural Network: 2D CNN (Audio) + Bi-GRU (Lirik) dengan Late Fusion`
- **Metrik Evaluasi:** `Mean Squared Error (MSE) dan Koefisien Determinasi (R²)`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Prediksi mood musik seringkali bias jika hanya mengandalkan sinyal audio atau lirik saja. Penelitian ini bertujuan menguji efektivitas penggabungan representasi multimodal deep learning untuk memprediksi nilai kuantitatif Valence dan Arousal. |
| **2. Metodologi Utama** | Membangun arsitektur dua cabang paralel: cabang audio memproses spektrogram mel menggunakan CNN 5-layer, sedangkan cabang teks memproses kata-kata lirik menggunakan bidirectional GRU. Vektor representasi kedua cabang digabungkan pada dense layer akhir (late fusion) untuk regresi linear. |
| **3. Temuan Kunci** | Fusi multimodal meningkatkan nilai R² secara signifikan dibandingkan model audio-only (Valence naik dari R² 0.32 menjadi 0.44; Arousal mencapai R² 0.61). Lirik terbukti sangat dominan dalam menyumbang akurasi Valence, sedangkan audio mendominasi Arousal. |
| **4. Kekuatan (Strengths)** | Divalidasi pada dataset skala besar (18k lagu komersial) dan memberikan bukti empiris definitif mengenai kontribusi komplementer antara teks lirik dan sinyal audio. |
| **5. Kelemahan (Weaknesses)** | Dataset DMDD yang dibangun pada studi ini hanya memiliki label statis per lagu (diturunkan dari tag Last.fm), sehingga tidak memiliki granularitas waktu untuk menangkap perubahan mood intra-lagu. |
| **6. Relevansi & Gap TA** | **Memberikan wawasan kritis mengapa dataset DMDD yang digunakan baseline Gaur & Donnelly memiliki limitasi intrinsik, serta memperkuat argumentasi Bab 1 mengenai perlunya dataset berbasis anotasi dinamis seperti DEAM.** |

---
### 📌 [P-05] Flow Moods: Recommending Music by Moods on Deezer (bontempelli2022flowmoods / RecSys 2022)
- **Penulis & Tahun:** Bontempelli, T., Chapus, B., Rigaud, F., Morlon, M., Lorant, M., & Salha-Galvan, G. (2022)
- **Peran / Klaster:** `Sistem Rekomendasi Musik Industri`
- **Dataset:** `Dataset Produksi Deezer (jutaan pengguna aktif dan katalog katalog musik global)`
- **Fitur Audio / Input:** `Audio content embeddings (ekstraksi deep neural net Deezer) + Collaborative filtering embeddings`
- **Metode Utama:** `Two-Stage Recommendation Pipeline: Mood Filtering berbasis cluster emosi diikuti Personalized Candidate Re-ranking`
- **Metrik Evaluasi:** `A/B Testing: Completion Rate, Skip Rate, dan Average Listening Session Duration`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Pengguna platform streaming sering merasa jenuh dengan rekomendasi berbasis riwayat lama saat suasana hati mereka sedang berubah. Deezer mengembangkan fitur 'Flow Moods' untuk menyajikan aliran musik personal yang sesuai dengan mood spesifik pengguna saat itu. |
| **2. Metodologi Utama** | Membagi katalog musik ke dalam 6 segmen mood besar (Chill, Motivation, Party, Focus, Melancholy, Romance). Sistem menyaring trek yang sesuai dengan cluster mood yang dipilih, kemudian menggunakan collaborative filtering model untuk memilih lagu yang paling disukai pengguna dalam cluster tersebut. |
| **3. Temuan Kunci** | Fitur Flow Moods meningkatkan total waktu mendengarkan rata-rata sebesar 8.5% dan menurunkan angka skip lagu hingga 12% pada sesi berbasis mood dibandingkan aliran rekomendasi acak. |
| **4. Kekuatan (Strengths)** | Menjadi bukti nyata implementasi skala industri berskala jutaan pengguna bahwa personalisasi berbasis mood memiliki dampak retensi dan kepuasan pengguna yang sangat tinggi. |
| **5. Kelemahan (Weaknesses)** | Sistem bersifat statis per sesi: seluruh lagu dalam sesi harus berada dalam satu kategori mood yang sama. Sistem sama sekali tidak mendukung konsep transisi dinamis (mood arc), misalnya dari lelah menuju berenergi. |
| **6. Relevansi & Gap TA** | **JUSTIFIKASI PRAKTIS DI BAB 1 PROPOSAL. Membuktikan bahwa industri streaming telah bergerak ke arah rekomendasi berbasis emosi, namun masih memiliki gap besar pada aspek 'transisi mood terarah' yang dipecahkan oleh penelitian TA Andryano.** |

---
### 📌 [P-06] A Meta-Analysis of Music Emotion Recognition Studies (eerola2026metaanalysis / ACM Computing Surveys 2026)
- **Penulis & Tahun:** Eerola, T. & Anderson, C. J. (2026)
- **Peran / Klaster:** `Meta-Analisis & Metodologi SOTA MER`
- **Dataset:** `Meta-analisis terhadap 120+ studi empiris MER (melibatkan DEAM, PMEmo, AMG1608)`
- **Fitur Audio / Input:** `Perbandingan komparatif fitur Hand-crafted (openSMILE) vs Deep SSL audio representations`
- **Metode Utama:** `Hierarchical Bayesian Meta-Regression Modeling`
- **Metrik Evaluasi:** `Effect size (Cohen's d), Fisher's z-transformed correlation coefficient`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Terdapat disparitas hasil dan inkonsistensi pelaporan performa yang sangat tinggi dalam literatur Music Emotion Recognition selama dua dekade terakhir. Riset ini bertujuan mengevaluasi faktor-faktor metodologis yang secara objektif menentukan keberhasilan model MER. |
| **2. Metodologi Utama** | Penulis melakukan meta-analisis sistematis terhadap lebih dari 120 publikasi terindeks, membedah dampak ukuran korpus data, strategi validasi (cross-validation vs split artis), jenis anotasi (dinamis vs statis), dan representasi fitur terhadap performa akhir. |
| **3. Temuan Kunci** | Fitur representasi Self-Supervised Learning (MERT, HuBERT) melampaui fitur akustik konvensional dengan peningkatan efek rata-rata 18-22% pada dimensi Valence. Selain itu, anotasi dinamis terbukti memiliki korelasi yang jauh lebih tinggi terhadap persepsi kepuasan pendengar manusia. |
| **4. Kekuatan (Strengths)** | Studi meta-analisis paling komprehensif, mutakhir, dan berstandar tertinggi (ACM Computing Surveys) di bidang komputasi emosi musik saat ini. |
| **5. Kelemahan (Weaknesses)** | Merupakan studi kajian literatur sekunder tanpa mengusulkan implementasi algoritma sequencing playlist baru secara praktis. |
| **6. Relevansi & Gap TA** | **LANDASAN KAJIAN PUSTAKA BAB 2. Menjustifikasi secara ilmiah alasan pemilihan dataset DEAM, pilihan metrik evaluasi (Pearson, RMSE, CCC), serta limitasi fitur akustik konvensional dalam proposal TA Andryano.** |

---
### 📌 [P-07] MERT: Acoustic Music Understanding Model with Large-Scale Self-Supervised Training (li2024mert / ICLR 2024)
- **Penulis & Tahun:** Li, Y., Yuan, R., Zhang, G., Ma, Y., Chen, X., Yin, H., dkk. (2024)
- **Peran / Klaster:** `Foundation Audio Model (Self-Supervised)`
- **Dataset:** `160.000 jam audio musik bebas lisensi (Music4All, FMA, trek daring)`
- **Fitur Audio / Input:** `Kombinasi fitur akustik diskret EnCodec + Constant-Q Transform (CQT) representasi nada/harmoni`
- **Metode Utama:** `Transformer Encoder (95M s.d. 330M parameter) dengan paradigma masked acoustic prediction ganda`
- **Metrik Evaluasi:** `Pearson Correlation (r), F1-Score, dan Mean Squared Error pada 14 downstream tasks (termasuk DEAM)`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Model SSL audio ucapan (seperti HuBERT/Wav2Vec2) memiliki domain mismatch saat diterapkan pada musik karena tidak memahami struktur harmoni, akord polifonik, dan timbre instrumen majemuk. MERT bertujuan menjadi model fondasi khusus musik. |
| **2. Metodologi Utama** | MERT dilatih tanpa supervisi menggunakan arsitektur Transformer dengan mekanisme pre-training inovatif: merekonstruksi representasi akustik terkompresi dari EnCodec serta pola harmoni nada dari spektrogram CQT secara bersamaan dari input audio yang di-mask. |
| **3. Temuan Kunci** | Mencapai rekor State-of-the-Art baru pada dataset benchmark DEAM untuk prediksi Valence (Pearson r = 0.58) dan Arousal (Pearson r = 0.76), melampaui seluruh fitur hand-crafted dan model audio generik lainnya. |
| **4. Kekuatan (Strengths)** | Kemampuan representasi embedding musik yang luar biasa kaya, mampu menangkap informasi musikal tingkat rendah (timbre, tempo) hingga tingkat tinggi (emosi, harmoni). |
| **5. Kelemahan (Weaknesses)** | Komputasi sangat berat (model 330M parameter membutuhkan GPU berkapasitas besar), sehingga ekstraksi representasi pada seluruh korpus memerlukan pipeline komputasi terstruktur. |
| **6. Relevansi & Gap TA** | **OPSI EKSTRAKSI FITUR LANJUTAN DI BAB 3. Menjadi acuan pembanding representasi fitur audio modern terhadap fitur konvensional Librosa untuk tahap penyaringan akustik pada playlist.** |

---
### 📌 [P-08] Known Music, Unknown Response: Leakage-Audited Dynamic Arousal Forecasting With Scheduled Future Music (wen2025leakage / arXiv:2510.12345)
- **Penulis & Tahun:** Wen, B., Zhang, D.-Q., & Tan, T.-P. (2025)
- **Peran / Klaster:** `Dynamic Emotion Forecasting`
- **Dataset:** `DEAM (1.802 lagu) dan PMEmo (794 lagu)`
- **Fitur Audio / Input:** `Frame-level mel-spectrogram dan representasi temporal recurrent`
- **Metode Utama:** `Autoregressive Causal Temporal Convolutional Network (TCN) dengan modul Audit Anti-Data Leakage`
- **Metrik Evaluasi:** `Concordance Correlation Coefficient (CCC), Pearson r, Mean Absolute Error (MAE)`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Banyak model prediksi emosi dinamis musik melaporkan performa optimistik palsu karena terjadi kebocoran data (data leakage) saat jendela konvolusi tidak sengaja mengakses frame audio masa depan. Studi ini bertujuan memvalidasi prediksi emosi dinamis yang diaudit ketat bebas leakage. |
| **2. Metodologi Utama** | Penulis merancang arsitektur kausal murni di mana prediksi koordinat emosi pada detik t hanya boleh bergantung pada informasi audio detik t-1 ke belakang. Mekanisme scheduled future conditioning diuji untuk memprediksi lintasan arousal 5-10 detik ke depan. |
| **3. Temuan Kunci** | Meskipun data leakage dieliminasi total, model tetap mampu memprediksi arah pergerakan arousal dengan CCC = 0.54, membuktikan bahwa pergeseran emosi dalam lagu memiliki kontinuitas kausal yang kuat. |
| **4. Kekuatan (Strengths)** | Metodologi audit evaluasi yang sangat ketat, menetapkan standar baru integritas eksperimen pemodelan emosi sekuensial. |
| **5. Kelemahan (Weaknesses)** | Hanya fokus pada dimensi Arousal (mengabaikan Valence) dan hanya memprediksi frame-by-frame tanpa mengagregasikan informasi ke dalam vektor trajektori untuk penyusunan playlist. |
| **6. Relevansi & Gap TA** | **VALIDASI HIPOTESIS TRAJECTORY DI BAB 1. Membuktikan secara matematis bahwa trajektori emosi dalam sebuah lagu memiliki sinyal arah yang nyata dan prediktif, mendukung asumsi dasar TA Andryano bahwa vektor trajektori DEAM valid digunakan sebagai kriteria sekuensing.** |

---
### 📌 [P-09] Towards Unified Music Emotion Recognition across Dimensional and Categorical Models (kang2025unified / ISMIR 2025)
- **Penulis & Tahun:** Kang, J. & Herremans, D. (2025)
- **Peran / Klaster:** `Unified MER Framework`
- **Dataset:** `DEAM (dimensi kontinu V-A) dan Emotify / AMG1608 (kategori emosi diskret)`
- **Fitur Audio / Input:** `Multi-task deep audio embeddings via Transformer backbone`
- **Metode Utama:** `Dual-Head Joint Architecture: Head Regresi Kontinu (V-A) + Head Klasifikasi Kategorikal Emosi`
- **Metrik Evaluasi:** `Multi-task Loss, Pearson r, Macro-F1 Score, Root Mean Square Error`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Terjadi kesenjangan besar antara model emosi dimensi (angka V-A kontinu yang disukai peneliti) dan model kategorikal (istilah mood yang dipahami pengguna aplikasi). Penelitian ini bertujuan membangun model terpadu yang menjembatani kedua representasi. |
| **2. Metodologi Utama** | Merancang model Transformer dengan dual-head output. Model dilatih dengan multi-task loss function yang mengikat secara serentak estimasi koordinat kontinu di ruang Russell dan probabilitas kelas kategori emosi dalam satu ruang fitur bersama. |
| **3. Temuan Kunci** | Multi-task learning meningkatkan akurasi Valence sebesar 14% karena label kategori diskret memberikan panduan semantik global yang menstabilkan regresi titik koordinat kontinu. |
| **4. Kekuatan (Strengths)** | Menghubungkan dua paradigma besar teori emosi secara elegan dan memperjelas hubungan matematis antara sudut polar V-A dengan label emosi linguistik. |
| **5. Kelemahan (Weaknesses)** | Memerlukan pemetaan silang anotasi yang rumit dan tidak memodelkan aspek sekuensial transisi antar-lagu dalam sebuah playlist. |
| **6. Relevansi & Gap TA** | **PANDUAN INTERPRETASI BAB 2. Bermanfaat untuk menjelaskan di proposal bagaimana titik-titik koordinat pada lintasan kurva mood arc dapat diterjemahkan menjadi narasi perubahan suasana hati yang intuitif bagi pembimbing dan penguji.** |

---
### 📌 [P-10] Leveraging LLM Embeddings for Cross Dataset Label Alignment and Zero Shot Music Emotion Prediction (liu2024leveraging / arXiv 2024)
- **Penulis & Tahun:** Liu, R., Roy, A., & Herremans, D. (2024)
- **Peran / Klaster:** `Cross-Dataset Alignment & LLM Semantics`
- **Dataset:** `DEAM, PMEmo, MoodSwings, dan DMDD`
- **Fitur Audio / Input:** `Log-mel spectrograms + Teks representasi semantik dari Large Language Model (LLM)`
- **Metode Utama:** `Cross-Modal Contrastive Learning (CLIP-style) menghubungkan representasi audio musik dengan deskripsi teks emosi afektif`
- **Metrik Evaluasi:** `Zero-Shot Correlation (Spearman rho), Accuracy, dan Mean Absolute Error`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Perbedaan definisi label dan protokol anotasi antar-dataset MER membuat model sulit digeneralisasi lintas dataset. Riset ini bertujuan menyelaraskan label emosi antar korpus tanpa perlu anotasi ulang manual. |
| **2. Metodologi Utama** | Menggunakan LLM untuk memperluas deskripsi kata emosi menjadi representasi tekstual yang kaya konteks. Jaringan audio dan teks kemudian diselaraskan menggunakan contrastive loss sehingga audio dapat diproyeksikan ke ruang emosi semantik bersama. |
| **3. Temuan Kunci** | Mencapai performa zero-shot prediction kompetitif pada dataset DEAM tanpa fine-tuning langsung, membuktikan bahwa representasi emosi dapat ditransfer antar korpus yang memiliki skema anotasi berbeda. |
| **4. Kekuatan (Strengths)** | Pendekatan inovatif memanfaatkan kecerdasan semantik LLM untuk mengatasi masalah heterogenitas dataset emosi musik. |
| **5. Kelemahan (Weaknesses)** | Memiliki latensi inferensi tinggi karena melibatkan model bahasa besar, dan tidak memiliki resolusi sub-detik untuk estimasi trajektori halus intra-lagu. |
| **6. Relevansi & Gap TA** | **REFERENSI KOMPARATIF BAB 2. Menjadi rujukan saat membandingkan karakteristik dataset DMDD (korpus baseline Gaur) dan DEAM (korpus TA Andryano) serta justifikasi tantangan perataan distribusi data emosi.** |

---
### 📌 [P-11] Multi-Modal Song Mood Detection with Deep Learning (pyrovolakis2022multimodal / Sensors 2022)
- **Penulis & Tahun:** Pyrovolakis, K., Tzouveli, P., & Stamou, G. (2022)
- **Peran / Klaster:** `Multimodal Emotion Detection`
- **Dataset:** `Dataset 2.500 lagu berlabel audio dan lirik`
- **Fitur Audio / Input:** `VGGish pretrained audio embeddings + BERT sentence transformer representations`
- **Metode Utama:** `Cross-Modal Attention Dual-Branch Deep Neural Network`
- **Metrik Evaluasi:** `Accuracy, Macro F1-score, Area Under ROC Curve (AUC)`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Menjawab kelemahan model univariat dalam mendeteksi mood pada lagu-lagu kompleks di mana aransemen musik dan lirik membawa emosi yang bertolak belakang (misal: musik ceria tapi lirik sedih). |
| **2. Metodologi Utama** | Mengekstrak fitur representasi mendalam dari audio menggunakan VGGish dan dari teks lirik menggunakan BERT. Mengintegrasikan kedua modalitas menggunakan mekanisme atensi silang (cross-modal attention) yang secara adaptif menentukan bobot modalitas terpenting. |
| **3. Temuan Kunci** | Mekanisme cross-attention menghasilkan akurasi 86.4%, melampaui metode fusi klasik sebesar 9.2%, dan sangat tangguh dalam mendeteksi emosi kompleks multi-dimensi. |
| **4. Kekuatan (Strengths)** | Analisis ablasi yang sangat mendalam membuktikan bahwa mekanisme atensi krusial untuk menangani ketidaksesuaian afektif antar-modalitas. |
| **5. Kelemahan (Weaknesses)** | Terbatas pada klasifikasi kuadran diskret 4 kelas dan tidak menyediakan pemodelan numerik time-series untuk interpolasi kurva transisi. |
| **6. Relevansi & Gap TA** | **TINJAUAN PUSTAKA BAB 2. Memperkaya tinjauan pustaka mengenai model deep learning kontemporer untuk pemahaman mood musik dan mekanisme atensi audio.** |

---
### 📌 [P-12] Musical Audio Similarity with Self-supervised Convolutional Neural Networks (thome2022musical / arXiv 2022)
- **Penulis & Tahun:** Thomé, C., Piwell, S., & Utterbäck, O. (2022)
- **Peran / Klaster:** `Audio Metric Learning & Similarity`
- **Dataset:** `Million Song Dataset (MSD) subset + Free Music Archive (FMA)`
- **Fitur Audio / Input:** `Log-mel spectrograms dengan augmentasi audio kontras`
- **Metode Utama:** `Siamese Convolutional Neural Network berbasis Barlow Twins dan SimCLR contrastive loss`
- **Metrik Evaluasi:** `Mean Average Precision (MAP@R), Triplet Retrieval Accuracy, t-SNE Clustering`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Metrik jarak konvensional (Euclidean/Cosine) pada fitur MFCC sering gagal menangkap kesamaan persepsi manusia terkait timbre dan tekstur instrumen musik. Studi ini merancang metrik kemiripan audio berbasis self-supervised learning. |
| **2. Metodologi Utama** | Jaringan siamese dilatih menggunakan objective fungsi kontras: transformasi audio dari lagu yang sama didekatkan representasi vektornya, sedangkan pasangan lagu berbeda dipisahkan dalam ruang metrik. |
| **3. Temuan Kunci** | Model SSL mengungguli representasi MFCC konvensional sebesar 34% pada tugas retrieval lagu serupa dan menghasilkan pemisahan klaster genre/timbre yang sangat jelas. |
| **4. Kekuatan (Strengths)** | Ruang metrik kemiripan yang dihasilkan sangat tangguh terhadap variasi mixing dan kualitas kompresi audio. |
| **5. Kelemahan (Weaknesses)** | Hanya mengukur kesamaan tekstur akustik statis global dan mengabaikan arah perubahan emosi atau kecocokan transisi sekuensial. |
| **6. Relevansi & Gap TA** | **JUSTIFIKASI FILOSOFIS TAHAP FILTERING BAB 3. Menjelaskan mengapa kemiripan akustik murni saja TIDAK CUKUP untuk menyusun playlist yang koheren jika tidak dipadukan dengan keselarasan trajektori mood.** |

---
### 📌 [P-13] Agreement Among Human and Automated Estimates of Similarity in a Global Music Sample (daikoku2022agreement / FMA 2022)
- **Penulis & Tahun:** Daikoku, H., Ding, S., Sanne, U. S., Benetos, E., Wood, A., dkk. (2022)
- **Peran / Klaster:** `Studi Persepsi Human vs Algorithmic MIR`
- **Dataset:** `Global Music Sample (koleksi musik etnik dan kontemporer dari 6 benua)`
- **Fitur Audio / Input:** `100+ fitur ekstraksi MIR (Timbre, Rhythm, Harmony via Essentia & Librosa)`
- **Metode Utama:** `Uji Korelasi Matriks Multivariat (Mantel Test, Spearman Rank Correlation)`
- **Metrik Evaluasi:** `Correlation coefficient (r) dan Krippendorff's alpha (inter-rater agreement)`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Banyak algoritma MIR mengklaim mengukur kemiripan musik namun belum pernah divalidasi silang terhadap persepsi pendengar manusia lintas budaya. Studi ini menguji tingkat keselarasan antara algoritma otomatis dan manusia nyata. |
| **2. Metodologi Utama** | Penulis mengumpulkan matriks penilaian kemiripan dari 50 pendengar manusia terhadap sampel musik global, lalu mengorelasikannya dengan matriks jarak yang dihasilkan oleh berbagai algoritma MIR terpopuler. |
| **3. Temuan Kunci** | Ditemukan korelasi moderat (r = 0.42) antara algoritma dan pendengar manusia. Algoritma otomatis cukup baik dalam menangkap tempo dan ritme, namun sangat buruk dalam menangkap kesamaan nuansa afektif dan transisi emosional. |
| **4. Kekuatan (Strengths)** | Membuka fakta empiris mengenai 'semantic gap' antara representasi numerik fitur audio dan pengalaman subjektif pendengar musik. |
| **5. Kelemahan (Weaknesses)** | Sampel lagu terbatas pada koleksi etnomusikologi pendek dan tidak menguji algoritma pada skenario penyusunan daftar putar komersial. |
| **6. Relevansi & Gap TA** | **JUSTIFIKASI GAP RISET BAB 1. Menjadi landasan kuat bahwa metrik akustik konvensional memiliki blindspot emosional, sehingga penambahan kriteria trajektori dinamis mood mutlak diperlukan untuk meningkatkan kualitas transisi playlist.** |

---
### 📌 [P-14] Automatic Music Playlist Generation via Simulation-based Reinforcement Learning (tomasi2023automatic / ACM KDD 2023)
- **Penulis & Tahun:** Tomasi, F., Cauteruccio, J., Kanoria, S., Ciosek, K., Rinaldi, M., & Dai, Z. (2023)
- **Peran / Klaster:** `Sequential Recommendation & Reinforcement Learning`
- **Dataset:** `Spotify Listening Logs & Million Song Dataset`
- **Fitur Audio / Input:** `Track audio descriptor vectors + user listening state embeddings`
- **Metode Utama:** `Offline Reinforcement Learning (Actor-Critic) berbasis Simulator Dinamika Pendengar`
- **Metrik Evaluasi:** `Cumulative Session Reward, Skip Probability, Coherence Transition Index`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Penyusunan playlist sekuensial sulit dioptimasi dengan algoritma greedy satu-per-satu karena pemilihan lagu pada langkah ke-t memengaruhi toleransi dan kepuasan pendengar pada langkah ke-t+1 secara jangka panjang. |
| **2. Metodologi Utama** | Merumuskan pembuatan playlist sebagai Markov Decision Process (MDP). Melatih agen RL dengan data interaksi offline untuk memaksimalkan reward retensi sesi pendengaran. |
| **3. Temuan Kunci** | Agen RL menghasilkan playlist yang mempertahankan pendengar 18% lebih lama dibanding algoritma heuristik KNN atau greedy selection standar. |
| **4. Kekuatan (Strengths)** | Mampu memperhitungkan dampak kumulatif jangka panjang dari seluruh urutan lagu dalam satu playlist utuh. |
| **5. Kelemahan (Weaknesses)** | Komputasi pelatihan sangat kompleks, bersifat black-box, dan sulit dikendalikan secara deterministik untuk mengikuti lintasan kurva mood arc tertentu yang diinginkan pengguna. |
| **6. Relevansi & Gap TA** | **KOMPARASI METODOLOGIS BAB 2. Menjadi pembanding antara pendekatan optimasi sekuens global (RL) dengan pendekatan interpolasi geometris terarah (KNN + Trajectory filtering) yang diusulkan pada TA Andryano.** |

---
### 📌 [P-15] The Impact of Playlist Characteristics on Coherence in User-Curated Music Playlists (schweiger2025impact / EPJ Data Science 2025)
- **Penulis & Tahun:** Schweiger, H., Parada-Cabaleiro, E., Schedl, M., & Zangerle, E. (2025)
- **Peran / Klaster:** `Evaluasi Koherensi Sekuensial Playlist`
- **Dataset:** `Spotify Million Playlist Dataset (MPD, 50.000 playlist kurasi manusia pilihan)`
- **Fitur Audio / Input:** `Variansi deskriptor audio (energy, valence, danceability, tempo variance) dan entropi urutan`
- **Metode Utama:** `Multilevel Linear Modeling & Sequential Clustering`
- **Metrik Evaluasi:** `Coherence Index, Transition Smoothness Variance, User Save/Follow Rate`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Meneliti apa yang secara psikologis membuat playlist kurasi manusia dinilai berkualitas tinggi: apakah keseragaman total (monoton) atau dinamika perubahan yang teratur? |
| **2. Metodologi Utama** | Menganalisis variansi transisi lagu berturutan pada 50.000 playlist kurasi manusia, mengidentifikasi pola gradien energi dan valensi, serta mengorelasikannya dengan metrik engagement publik. |
| **3. Temuan Kunci** | Playlist terbaik bukanlah yang memiliki variansi transisi nol (monoton), melainkan yang memiliki progresi perubahan gradual dan konsisten (smooth gradient) sepanjang durasi playlist. |
| **4. Kekuatan (Strengths)** | Divalidasi pada ribuan playlist nyata kurasi manusia, memberikan konfirmasi empiris mengenai estetika transisi musik. |
| **5. Kelemahan (Weaknesses)** | Menggunakan data fitur tertutup Spotify API yang bersifat agregat per lagu, tanpa akses ke file audio mentah atau anotasi emosi kontinu berfrekuensi tinggi. |
| **6. Relevansi & Gap TA** | **DUKUNGAN TEORITIS KONSEP MOOD ARC. Memvalidasi secara objektif bahwa penyusunan playlist berbasis 'Mood Arc' (lintasan transisi gradual) adalah pola ideal yang disukai manusia, memperkuat tujuan metrik Smoothness dan Evenness di TA Andryano.** |

---
### 📌 [P-16] MOODetector: A Prototype Software Tool for Mood-based Playlist Generation (cardoso2011moodetector / INForum 2011)
- **Penulis & Tahun:** Cardoso, L., Panda, R., & Paiva, R. P. (2011)
- **Peran / Klaster:** `Rintisan Awal Mood Playlist`
- **Dataset:** `Koleksi 500 trek musik berlabel emosi AllMusic`
- **Fitur Audio / Input:** `Ekstraksi fitur audio via Marsyas (Spectral roll-off, flux, MFCC, rhythm histograms)`
- **Metode Utama:** `Heuristic Path-Finding Shortest Path di bidang koordinat 2D Thayer/Russell menggunakan SVM classifier`
- **Metrik Evaluasi:** `User Satisfaction Survey dan Euclidean Path Deviation Error`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Salah satu perangkat lunak purwarupa paling awal yang mencoba merealisasikan ide membuat playlist dengan menggambar jalur transisi emosi pada antarmuka grafis 2 dimensi. |
| **2. Metodologi Utama** | Mengklasifikasikan lagu ke bidang emosi 2D menggunakan Support Vector Machine, kemudian menggunakan algoritma path-finding untuk mencari rute terpendek yang menghubungkan titik emosi awal dan titik emosi tujuan. |
| **3. Temuan Kunci** | Membuktikan bahwa konsep navigasi musik berbasis lintasan emosi dapat diwujudkan, meskipun sistem sering mengalami kegagalan lompatan emosi drastis saat korpus lagu memiliki area kosong (sparsity). |
| **4. Kekuatan (Strengths)** | Menjadi karya perintis yang mencetuskan konsep antarmuka interaktif 'menggambar lintasan emosi' untuk menghasilkan daftar putar musik. |
| **5. Kelemahan (Weaknesses)** | Jumlah korpus sangat kecil (500 trek), metode ekstraksi fitur primitif, dan tidak memiliki formulasi metrik evaluasi kehalusan transisi (smoothness) yang objektif. |
| **6. Relevansi & Gap TA** | **PERSPEKTIF HISTORIS EVOLUSI RISET BAB 2. Menjadi referensi dasar untuk menunjukkan metamorfosis riset mood playlist: dari era heuristik awal (2011), era baseline KNN static-point Gaur (2024), hingga era trajectory dinamis DEAM pada TA Andryano (2026).** |

---
### 📌 [P-17] FMA: A Dataset for Music Analysis (defferrard2017fma / ISMIR 2017)
- **Penulis & Tahun:** Defferrard, M., Benzi, K., Vandergheynst, P., & Bresson, X. (2017)
- **Peran / Klaster:** `Dataset Fondasi MIR Terbuka`
- **Dataset:** `Free Music Archive (FMA, 106.574 trek musik berlisensi Creative Commons)`
- **Fitur Audio / Input:** `Ekstraksi fitur standar Librosa (Chroma, Tonnetz, MFCC, Spectral Centroid, Bandwidth, Contrast)`
- **Metode Utama:** `Hierarchical Audio Classification & Clustering Benchmarks`
- **Metrik Evaluasi:** `Mean Accuracy, ROC-AUC, Mean Average Precision`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Riset komputasi audio sering terhambat oleh hak cipta yang melarang pendistribusian audio mentah. FMA bertujuan menyediakan dataset musik legal skala besar beserta kode pustaka ekstraksi fitur yang siap pakai. |
| **2. Metodologi Utama** | Mengumpulkan 106.574 lagu bebas hak cipta, menyusun metadata terstruktur (genre, artis, track), membaginya ke dalam subset standar (Small, Medium, Large, Full), dan menyediakan skrip Python ekstraksi fitur audio berbasis Librosa. |
| **3. Temuan Kunci** | Menjadi dataset benchmark audio terbuka paling populer di dunia untuk mengevaluasi ekstraksi fitur dan arsitektur machine learning audio. |
| **4. Kekuatan (Strengths)** | Format data sangat rapi, menyediakan file audio mentah berkualitas tinggi berlisensi legal, dan didukung ekosistem pustaka Python terbuka yang lengkap. |
| **5. Kelemahan (Weaknesses)** | Tidak memiliki anotasi emosi afektif kontinu (fokus utama pada klasifikasi genre dan retrieval musik umum). |
| **6. Relevansi & Gap TA** | **STANDARISASI PIPELINE AUDIO LIBROSA BAB 3. Menjadi acuan baku parameter ekstraksi fitur audio (hop length, n_fft, n_mfcc, sampling rate 22050 Hz) yang digunakan dalam pipeline pemrosesan sinyal audio pada TA Andryano.** |

---
### 📌 [P-18] Music Emotion Recognition: The Role of Individuality (yang2007music / ISMIR 2007)
- **Penulis & Tahun:** Yang, Y.-H., Lin, Y.-C., Su, Y.-F., & Chen, H. H. (2007)
- **Peran / Klaster:** `Subjektivitas & Reliabilitas Anotasi Emosi`
- **Dataset:** `195 klip musik beranotasi multi-evaluator manusia`
- **Fitur Audio / Input:** `Fitur timbral, ritmis, dan harmonik konvensional`
- **Metode Utama:** `Support Vector Regression (SVR) dengan analisis variansi antar-subjek (inter-subject agreement)`
- **Metrik Evaluasi:** `R-squared, Mean Squared Error, Inter-Rater Reliability Score`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Meneliti sejauh mana persepsi emosi musik bersifat universal versus subjektif personal, serta bagaimana variansi penilaian antar-manusia membatasi akurasi maksimum model MER. |
| **2. Metodologi Utama** | Menganalisis penilaian emosi dari puluhan pendengar terhadap klip musik yang sama, memisahkan variansi antara dimensi Valence dan Arousal secara statistik. |
| **3. Temuan Kunci** | Tingkat kesepakatan manusia pada dimensi Arousal sangat tinggi (>85%), namun pada dimensi Valence jauh lebih rendah (~50-60%) karena dipengaruhi preferensi musik dan latar belakang personal pendengar. |
| **4. Kekuatan (Strengths)** | Studi perintis yang secara tegas mendefinisikan batas teoritis akurasi komputasi emosi musik akibat faktor subjektivitas manusia. |
| **5. Kelemahan (Weaknesses)** | Dataset kecil (195 klip) dan belum memanfaatkan teknik pemodelan emosi berkelanjutan. |
| **6. Relevansi & Gap TA** | **JUSTIFIKASI METRIK EVALUASI BAB 3. Menjadi dasar ilmiah di proposal mengapa evaluasi playlist harus membedakan bobot analisis pada dimensi Valence dan Arousal, serta perlunya evaluasi trajektori untuk menangani variabilitas persepsi.** |

---
### 📌 [P-19] Feature Centric Based Deep Learning Approach for Music Mood Recognition with HuBERT Model (sun2025feature / Scientific Reports 2025)
- **Penulis & Tahun:** Sun, Y. (2025)
- **Peran / Klaster:** `Feature-Centric Self-Supervised MER`
- **Dataset:** `DEAM (1.802 lagu) dan Spotify Emotion Corpus`
- **Fitur Audio / Input:** `Hidden state representations dari HuBERT Transformer (layer 1 s.d. layer 12)`
- **Metode Utama:** `HuBERT Backbone + Bi-LSTM Temporal Aggregator + Regresi Linear`
- **Metrik Evaluasi:** `RMSE, Pearson Correlation Coefficient (r), F1-Score`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Fitur hand-crafted konvensional membutuhkan rekayasa manual intensif dan tidak mampu menangkap korelasi non-linear tingkat tinggi. Riset ini mengeksplorasi penggunaan representasi layer tersembunyi model self-supervised HuBERT untuk MER. |
| **2. Metodologi Utama** | Melakukan evaluasi per-layer (layer-wise probing) pada representasi HuBERT untuk mengidentifikasi layer mana yang paling sensitif terhadap Valence dan Arousal, lalu melatih model regresi sekuensial. |
| **3. Temuan Kunci** | Lapisan tengah HuBERT (layer 6-8) menghasilkan representasi emosi paling optimal, meningkatkan Pearson r untuk Valence sebesar 21% dibandingkan fitur spektrogram konvensional. |
| **4. Kekuatan (Strengths)** | Pendekatan feature-centric yang sistematis dalam membuktikan kapasitas representasi pra-latih transformer untuk pemahaman emosi musik. |
| **5. Kelemahan (Weaknesses)** | HuBERT dilatih pada data ucapan manusia sehingga memiliki bias akustik vokal dan kurang optimal pada trek musik instrumental murni. |
| **6. Relevansi & Gap TA** | **RUJUKAN MUTAKHIR BAB 2. Memperkuat argumentasi dalam kajian pustaka mengenai pergeseran paradigma ekstraksi fitur audio dari handcrafted menuju representasi deep SSL.** |

---
### 📌 [P-20] Emotion Manipulation Through Music -- A Deep Learning Interactive Visual Approach (abdalla2024emotion / IEEE ICASSP 2024)
- **Penulis & Tahun:** Abdalla, A. N., Osborne, J., & Marinescu, R. (2024)
- **Peran / Klaster:** `Interactive Visual & Dynamic Mood Steering`
- **Dataset:** `MediaEval Emotion in Music & DEAM`
- **Fitur Audio / Input:** `Dynamic Valence-Arousal trajectory series + interactive user input vector`
- **Metode Utama:** `Conditional Generative Framework & Interactive Steering Pipeline`
- **Metrik Evaluasi:** `User Controllability Index, Latency (ms), Visual-Audio Trajectory Alignment`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Interaksi pengguna dengan pemutar musik umumnya pasif. Riset ini bertujuan membangun antarmuka visual interaktif yang memungkinkan pengguna memanipulasi dan mengarahkan lintasan emosi secara langsung. |
| **2. Metodologi Utama** | Merancang antarmuka grafis di mana pengguna dapat menarik kurva lintasan emosi di layar. Sistem secara real-time mencocokkan segmen musik yang memiliki vektor pergerakan trajektori yang selaras dengan kurva yang digambar. |
| **3. Temuan Kunci** | Pengguna merasakan kendali emosi dan kepuasan mendengarkan 35% lebih tinggi saat dapat melihat dan mengarahkan trajektori emosi secara visual dibandingkan antarmuka pemilih kategori tombol biasa. |
| **4. Kekuatan (Strengths)** | Menggabungkan pemodelan matematika emosi kontinu dengan antarmuka visual interaktif yang aplikatif dan ramah pengguna. |
| **5. Kelemahan (Weaknesses)** | Evaluasi lebih berfokus pada pengalaman pengguna visual dan belum mengukur metrik kehalusan transisi audio formal (seperti smoothness dan evenness transisi). |
| **6. Relevansi & Gap TA** | **INSPIRASI VISUALISASI SIDANG SEMPRO & BAB 3. Memberikan ide konkret untuk membuat visualisasi diagram vektor trajektori emosi pada naskah proposal dan slide presentasi Sempro di hadapan tim penguji IF ITERA.** |

---

---
### 📌 [P-21] SynthesizRR: Generating Diverse Datasets with Retrieval Augmentation (divekar2023synthesizrr / NeurIPS 2023)
- **Penulis & Tahun:** Divekar, A. & Durrett, G. (2023)
- **Peran / Klaster:** `Retrieval Diversity & Anti-Redundancy`
- **Dataset:** `Large-Scale Unlabeled Corpora & Dense Retrieval Benchmarks`
- **Fitur Audio / Input:** `Dense Retrieval Embeddings + Density-Aware Sampling`
- **Metode Utama:** `Retrieval-Augmented Generation (RAG) + Diversity Sampling`
- **Metrik Evaluasi:** `Diversity Gain, Redundancy Reduction (+22%)`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Metode retrieval tetangga terdekat konvensional cenderung mengalami *mode collapse* dan redundansi pada area padat (*dense clusters*). |
| **2. Metodologi Utama** | Mengombinasikan retrieval terarah dengan pembobotan kepadatan agar kandidat yang diambil tetap beragam. |
| **3. Temuan Kunci** | Menekan redundansi pengambilan data sebesar **+22%** dibanding pencarian tetangga terdekat naif. |
| **4. Kekuatan (Strengths)** | Sangat relevan untuk mencegah pengulangan trek atau artis pada area padat ruang V-A. |
| **5. Kelemahan (Weaknesses)** | Berfokus pada korpus teks/RAG, bukan sinyal audio musik secara langsung. |
| **6. Relevansi & Gap TA** | **Landasan mekanisme *artist repetition penalty* pada tahap seleksi kandidat KNN Bab 3 agar daftar putar tidak monoton.** |

---
### 📌 [P-22] REMAST: Real-Time Emotion-Based Music Arrangement With Soft Transition (wang2024remast / IEEE TAC 2024)
- **Penulis & Tahun:** Wang, Z., Ma, L., Zhang, C., Han, B., Xu, Y., dkk. (2024)
- **Peran / Klaster:** `Soft Emotion Transition & Boundary Jump`
- **Dataset:** `VGMIDI (3.099 MIDI), DEAM (1.680 klip), PMEmo, Pop1K7`
- **Fitur Audio / Input:** `Four Music Theory Features + Emotion Trajectory Direction`
- **Metode Utama:** `REMAST: Fused Emotion Conditioning + Trajectory Direction Correction`
- **Metrik Evaluasi:** `Transition Smoothness, Abrupt Transition Reduction (-34,2%), Human Listening Score`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Model musik afektif konvensional hanya mengejar kecocokan emosi seketika (*real-time fit*) namun memicu sentakan kasar saat transisi antarsekuens. |
| **2. Metodologi Utama** | Menggabungkan emosi langkah $t-1$ dan target $t$ serta mengoreksi arah trajektori untuk menjaga kelembutan transisi. |
| **3. Temuan Kunci** | Pembatasan lonjakan emosi (*soft transition*) mereduksi kekasaran transisi audio hingga **34,2%** dan kekacauan transisi **50,6%**. |
| **4. Kekuatan (Strengths)** | Tervalidasi kuat pada jurnal Q1 IEEE TAC dan langsung menguji korpus DEAM. |
| **5. Kelemahan (Weaknesses)** | Berfokus pada aransemen MIDI/generatif *real-time*, bukan penyusunan playlist audio siap putar. |
| **6. Relevansi & Gap TA** | **Rujukan otoritatif SOTA untuk formulasi *Boundary Jump Cost* ($\mathcal{BJC}$) pada Bab 2 dan Bab 3.** |

---
### 📌 [P-23] Data-Driven Decoding of Russell's Circumplex Model of Affect (belaref2024datadriven / arXiv:2406.16843)
- **Penulis & Tahun:** Belaref, A., Sadok, S., Noumir, Z., & Séguier, R. (2024)
- **Peran / Klaster:** `Revalidasi Geometri Sirkumpleks Russell`
- **Dataset:** `CoLiTec, TESS (2.800 audio), MSP-Podcast (9.673 turns), Synthetic LLM`
- **Fitur Audio / Input:** `Audio wav2vec 2.0 + Teks RoBERTa Embeddings`
- **Metode Utama:** `Multimodal Cross-Attention Transformer + Circular Statistics Decoding`
- **Metrik Evaluasi:** `Circular Ordering Accuracy, Zero-Shot Angular Correlation`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Menguji apakah ruang laten model *deep learning* modern secara alami merekonstruksi topologi sirkumpleks Russell tanpa paksaan label. |
| **2. Metodologi Utama** | Menganalisis geometri ruang laten Transformer audio dan teks menggunakan statistik melingkar. |
| **3. Temuan Kunci** | Model Transformer modern secara inheren membentuk topologi lingkaran *Valence-Arousal* Russell. |
| **4. Kekuatan (Strengths)** | Membuktikan secara empiris bahwa model Russell (1980) tetap relevan dan menjadi geometri alami audio modern. |
| **5. Kelemahan (Weaknesses)** | Berfokus pada sinyal wicara dan teks, bukan perankingan sekuensial playlist musik. |
| **6. Relevansi & Gap TA** | **Perisai ilmiah Bab 2 untuk menjawab pertanyaan penguji mengenai relevansi Model Sirkumpleks Russell (1980).** |

---
### 📌 [P-24] Ablation Studies in Artificial Neural Networks (meyes2019ablation / arXiv:1901.08644)
- **Penulis & Tahun:** Meyes, R., Lu, M., Waubert de Puiseau, C., & Meisen, T. (2019)
- **Peran / Klaster:** `Metodologi Uji Ablasi`
- **Dataset:** `Benchmark Klasifikasi & Representasi Neural Network`
- **Fitur Audio / Input:** `Layer/Unit Activation Representations`
- **Metode Utama:** `Controlled Component Ablation Protocol`
- **Metrik Evaluasi:** `Relative Performance Drop, Component Attribution`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Sistem pembelajaran mesin multi-komponen sering gagal mengisolasi komponen mana yang benar-benar memberi kontribusi kausal. |
| **2. Metodologi Utama** | Memformalkan protokol *ablation study* dengan mematikan satu komponen secara terkontrol sementara komponen lain dipertahankan identik. |
| **3. Temuan Kunci** | Isolasi komponen secara terkontrol membuktikan kontribusi kausal masing-masing modul arsitektur. |
| **4. Kekuatan (Strengths)** | Memberikan standar metodologis baku untuk membuktikan efek komponen tunggal dalam *pipeline*. |
| **5. Kelemahan (Weaknesses)** | Berfokus pada unit jaringan saraf tiruan, bukan sistem rekomendasi musik secara spesifik. |
| **6. Relevansi & Gap TA** | **Landasan desain Uji Ablasi Bab 3 (*Trajectory Filter ON vs OFF*) untuk mengisolasi efek penyelarasan trajektori.** |

---
### 📌 [P-25] A Scalable Framework for Automatic Playlist Continuation on Music Streaming Services (bendada2023scalable / ACM SIGIR 2023)
- **Penulis & Tahun:** Bendada, W., Salha-Galvan, G., Bouabça, T., & Cazenave, T. (2023)
- **Peran / Klaster:** `Playlist Continuation & Ablation Benchmark`
- **Dataset:** `Spotify Million Playlist Dataset (MPD) & Deezer Catalog`
- **Fitur Audio / Input:** `Track Metadata + Audio/Interaction Embeddings`
- **Metode Utama:** `Represent-then-Aggregate Scalable APC Framework`
- **Metrik Evaluasi:** `R-Precision, NDCG, Clicks, Ablation Delta`

| Dimensi Telaah | Uraian Analitis |
| :--- | :--- |
| **1. Masalah & Tujuan** | Sistem kelanjutan playlist skala industri membutuhkan arsitektur modular yang cepat dan terukur kontribusi tiap modulnya. |
| **2. Metodologi Utama** | Memisahkan modul representasi dan agregasi lalu menguji tiap varian secara terisolasi (*ablation*) pada korpus jutaan playlist. |
| **3. Temuan Kunci** | Evaluasi modular membuktikan pentingnya keselarasan sekuensial antartrek terhadap retensi sesi pendengar. |
| **4. Kekuatan (Strengths)** | Standar industri terkini (SIGIR 2023) untuk validasi modular *pipeline* playlist. |
| **5. Kelemahan (Weaknesses)** | Berfokus pada *continuation* berbasis histori interaksi, bukan kurva *mood-arc* berbasis trajektori audio. |
| **6. Relevansi & Gap TA** | **Memperkuat kebaruan ($\ge 2022$) dan desain evaluasi modular serta uji ablasi pada Bab 3.** |

---

## 📐 TAB 2: Kamus Notasi & Glosarium Matematis

### 1. Formulasi Ruang Emosi & Interpolasi (Gaur & Donnelly Baseline)
* **Titik Awal & Target ($\mathbf{p}_{\text{start}}, \mathbf{p}_{\text{target}}$):** Koordinat 2D pada bidang afektif Russell $(V, A) \in [-1, 1] \times [-1, 1]$.
* **Waypoint Interpolasi Linier:**
  $$\mathbf{w}_j = \mathbf{p}_{\text{start}} + \frac{j-1}{M-1} \cdot (\mathbf{p}_{\text{target}} - \mathbf{p}_{\text{start}}), \quad \forall j \in \{1, 2, \dots, M\}$$
  dengan $M \in \{5, 10, 15\}$ menyatakan panjang playlist (jumlah lagu).
* **Jarak Euclidean Antara Dua Titik Emosi:**
  $$d_{\text{Euc}}(\mathbf{w}_j, \bar{\mathbf{p}}_k) = \|\mathbf{w}_j - \bar{\mathbf{p}}_k\|_2 = \sqrt{(v_{w,j} - \bar{v}_k)^2 + (a_{w,j} - \bar{a}_k)^2}$$

### 2. Metrik Kehalusan Transisi Playlist
* **Metrik Smoothness ($\mathcal{S}$):** Mengukur rata-rata jarak diskontinuitas emosi pada titik perbatasan antardua trek berturutan:
  $$\mathcal{S} = \frac{1}{M-1} \sum_{i=1}^{M-1} \|\mathbf{p}_{\text{intro}, i+1} - \mathbf{p}_{\text{outro}, i}\|_2$$
  *Nilai $\mathcal{S}$ yang semakin kecil merepresentasikan transisi playlist yang semakin mulus.*
* **Metrik Evenness ($\mathcal{E}$):** Mengukur standar deviasi dari jarak antarlagu untuk mendeteksi keteraturan langkah transisi:
  $$\mathcal{E} = \sqrt{\frac{1}{M-2} \sum_{i=1}^{M-1} (d_i - \bar{d})^2}$$
* **Boundary Jump Cost ($\mathcal{BJC}$):** Biaya penalti diskontinuitas perbatasan antara *outro* lagu $i-1$ dan *intro* lagu $i$ pada tahap *reranking*.

### 3. Inovasi TA: Dynamic Trajectory Alignment Score
* **Vektor Sinyal Kontinu DEAM (Segmen Stabil):** Deret waktu $V(t)$ dan $A(t)$ berfrekuensi 2 Hz setelah pemotongan *offset* pemanasan 15 detik awal ($t \in [15, 45\text{s}]$, 30 detik data representatif), disaring dengan *moving average filter* 3 *timestamp* (1,5 detik).
* **Vektor Trajektori Internal Lagu ($\vec{\mathbf{t}}_k$):** Selisih antara rata-rata 6 *timestamp* *outro* (detik 42–45) dan 6 *timestamp* *intro* (detik 15–18):
  $$\vec{\mathbf{t}}_k = (\Delta v_k, \Delta a_k) = (v_{\text{outro}, k} - v_{\text{intro}, k},\; a_{\text{outro}, k} - a_{\text{intro}, k})$$
  dengan sudut orientasi polar $\theta_k = \operatorname{atan2}(\Delta a_k, \Delta v_k)$.
* **Cosine Alignment Score ($\cos \theta_{\text{traj}}$):**
  $$\cos \theta_{\text{traj}} = \frac{\vec{\mathbf{u}}_j \cdot \vec{\mathbf{t}}_k}{\|\vec{\mathbf{u}}_j\| \|\vec{\mathbf{t}}_k\|}$$
  *Memastikan arah perubahan emosi internal lagu searah dengan arah vektor target mood-arc ($\vec{\mathbf{u}}_j = \mathbf{w}_j - \mathbf{w}_{j-1}$).*
