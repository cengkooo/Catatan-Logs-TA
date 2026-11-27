---
title: "Algoritma Rekomendasi Platform Streaming Musik (Spotify, Apple Music, Deezer, YouTube Music)"
tags:
  - note/tanya-jawab
  - learning-qa
  - music-recommender-systems
  - streaming-platforms
topik: "Algoritma Rekomendasi Platform Streaming"
status: "berkembang"
rujukan_paper:
  - "[[06-Bontempelli2022-Flow-Moods-Deezer]]"
  - "[[05-Schweiger2025-Playlist-Coherence]]"
  - "[[25-Bendada2023-Scalable-Playlist-Continuation]]"
  - "[[Covington2016-YouTube-DNN]]"
  - "[[Tomasi2023-RL-Playlist-Continuation]]"
created: 2026-11-28
updated: 2026-11-28
---

# 💬 Algoritma Rekomendasi Platform Streaming Musik (Spotify, Apple Music, Deezer, YouTube Music)

- **Topik:** `Algoritma Rekomendasi Platform Streaming`
- **Status Pemahaman:** `berkembang`

---

## ❓ Pertanyaan #1
> Jelaskan detail algoritma apa yang digunakan oleh Spotify, Apple Music, Deezer, dan YouTube Music.

### 💡 Jawaban

Keempat platform penyiaran musik ini sama-sama menghadapi katalog puluhan juta lagu dan ratusan juta pengguna, namun masing-masing menekankan arsitektur inti yang berbeda sesuai kekuatan data dan produknya.

#### 1. Spotify: BaRT + Tiga Pilar Sinyal (CF, NLP, Audio)
Di halaman utama (*Home screen*), Spotify menggunakan mesin orkestrasi dan perankingan bernama **BaRT (*Bandits for Recommendations as Treatments*)**.
- **Contextual Multi-Armed Bandits (BaRT):** Memandang setiap rak/kartu playlist sebagai "perlakuan" (*treatment*) untuk memaksimalkan keterlibatan pengguna. BaRT menyeimbangkan **Exploitation** (menyajikan musik yang pasti disukai dari riwayat dengar) dan **Exploration** (mengenalkan lagu/genre baru lewat strategi seperti $\epsilon$-greedy agar pengguna tidak terjebak *filter bubble*). Sinyal umpan balik utamanya adalah apakah pengguna mendengarkan trek **lebih dari 30 detik** atau melakukan *skip* lebih awal.
- **Tiga Pilar Data Penyuplai BaRT:**
  1. **Collaborative Filtering (CF):** Memetakan matriks interaksi pengguna-lagu berskala masif, termasuk **playlist co-occurrence** (melihat lagu apa saja yang sering dikumpulkan bersamaan oleh kurator atau pengguna dalam satu playlist/sesi).
  2. **Natural Language Processing (NLP) & Cultural Vectoring:** Model NLP (termasuk *transformer*) memindai teks web, blog musik, ulasan, berita budaya, biografi artis, dan lirik lagu untuk memetakan konteks kultural ke ruang vektor kontinu. Ini membantu mengatasi *cold-start* dan menangkap tren subgenre baru.
  3. **Audio Analysis (Raw Audio / Spectrogram):** Jaringan saraf tiruan (*deep neural networks*, seperti CNN/RNN pada spektrogram) mengekstrak karakteristik akustik langsung dari berkas audio mentah (tempo, kunci nada, timbre, *danceability*, *energy*, *acousticness*). Lagu baru tanpa riwayat putar tetap bisa direkomendasikan berdasarkan kemiripan bunyi.
- **Konteks Riset Sekuensial:** Pada riset lanjutan, tim Spotify juga mengeksplorasi *Reinforcement Learning* untuk kelanjutan playlist sekuensial (Tomasi et al., 2023) serta analisis jutaan playlist kurasi manusia (*Spotify Million Playlist Dataset*) yang membuktikan bahwa lompatan emosi antartrek berurutan memicu *skip* (Schweiger et al., 2025).

#### 2. Apple Music: Pendekatan "Algo-torial" (Human-in-the-Loop + ML)
Apple Music menggabungkan kurasi manusia (*editorial*) dan pembelajaran mesin (*algorithmic*) dalam satu siklus umpan balik tertutup yang sering disebut **"algo-torial"**.
- **Human-in-the-Loop sebagai Sinyal Otoritatif:** Tim editor musik global dan DJ Apple Music menyusun playlist unggulan (seperti *Today's Hits*, *New Music Daily*, *Rap Life*). Ketika lagu baru ditempatkan di playlist editorial, jutaan pengguna langsung mendengarkannya sehingga menghasilkan data interaksi berkecepatan tinggi (*play*, *skip*, *love*). Model ML kemudian membaca sinyal tersebut untuk memahami *siapa* yang cocok menerima lagu itu di mix personal (*New Music Mix*, *Favorites Mix*, *Discovery Station*).
- **Sinyal Telemetri & Ekosistem:**
  - **Sinyal implisit:** durasi putar sebelum berhenti, *skip rate*, pemutaran ulang, kueri pencarian, serta konteks waktu dan perangkat.
  - **Sinyal eksplisit:** tombol *Love/Dislike*, penambahan ke pustaka pribadi, *pre-add*, dan berbagi tautan.
  - **Kontinuitas historis:** memanfaatkan riwayat panjang sejak era iTunes (rating, *play count*) serta integrasi ekosistem seperti **Shazam**.
- **Arsitektur ML:** Menggunakan *Collaborative Filtering*, *Deep Learning Embeddings* untuk memetakan perilaku sekuensial dan metadata lagu ke ruang vektor berdimensi tinggi, serta pencarian tetangga terdekat (*Approximate Nearest Neighbor* / ANN) untuk mengambil kandidat *top-N* secara *real-time*.

#### 3. Deezer: Latent Factor CF + CNN Audio Embeddings + Flow Moods
Deezer banyak memublikasikan risetnya secara terbuka di konferensi **ACM RecSys**, terutama seputar fitur radio personal tanpa henti bernama **Flow** dan pengembangannya **Flow Moods** (Bontempelli et al., 2022).
- **Latent Factor Collaborative Filtering:** Melatih *user embeddings* dan *track embeddings* berdimensi rendah dari riwayat putar, *skip*, favorit, dan playlist. Kedekatan pengguna dan lagu diukur di ruang laten menggunakan metrik seperti *cosine similarity*.
- **CNN Audio Embeddings untuk Mengatasi Cold-Start & Skalabilitas Mood:** Pada *Flow Moods*, kurator musik profesional memberi anotasi *mood* secara manual pada ribuan lagu benih (*seed*). Deezer kemudian melatih model *Convolutional Neural Networks* (CNN) pada sinyal audio/spektrogram untuk menghasilkan *audio embeddings* dan memprediksi label *mood* tersebut ke jutaan lagu di katalog global.
- **Limitasi Flow Moods:** Pengguna memilih salah satu dari 6 kategori *mood* diskrit tertutup (*Chill, Focus, Melancholy, Motivation, Party, You & Me*). Sistem ini belum mendukung perpindahan *mood* bertahap secara kontinu (*dynamic mood-arc*).
- **Pemodelan Kognitif & Sekuensial:** Riset Deezer juga mengeksplorasi model memori kognitif manusia (seperti arsitektur *ACT-R*) untuk memodelkan perilaku mendengarkan berulang (*repeat listening*) agar seimbang antara lagu nostalgia dan temuan baru.

#### 4. YouTube Music: Two-Stage Retrieval (Two-Tower) + Deep Ranking
Berakar pada arsitektur klasik Google/YouTube oleh **Covington, Adams, dan Sargin (2016)** yang berkembang menjadi **Two-Tower Neural Networks** modern, YouTube Music memisahkan sistemnya menjadi dua tahap penyaringan (*funnel*) untuk menangani skala miliaran item dan pengguna:
- **Tahap 1: Candidate Generation (Retrieval via Two-Tower):**
  - Bertujuan menyaring jutaan/miliaran item menjadi **ratusan kandidat** dengan *recall* tinggi.
  - Menggunakan arsitektur **Two-Tower**:
    - *User Tower* mengodekan riwayat tonton/dengar, token pencarian, dan konteks (waktu, perangkat) menjadi vektor pengguna $u \in \mathbb{R}^d$.
    - *Item Tower* mengodekan fitur item (embedding audio, genre, artis, popularitas) menjadi vektor item $v \in \mathbb{R}^d$.
  - Karena *Item Tower* bisa dihitung *offline* lebih dulu, pencarian kandidat dilakukan sangat cepat saat aplikasi dibuka lewat *dot product* / *cosine similarity* menggunakan *Approximate Nearest Neighbors* (ANN). Model juga memakai fitur *example age* agar konten baru tetap mendapat peluang (*freshness*).
- **Tahap 2: Ranking (Deep Scoring Model):**
  - Bertujuan mengurutkan ratusan kandidat menjadi **puluhan rekomendasi teratas** dengan presisi tinggi menggunakan fitur interaksi yang lebih kaya (*cross-features* antara pengguna, artis/kanal, dan konteks).
  - **Objektif Pelatihan:** Alih-alih hanya memprediksi klik (*CTR*, yang rentan terhadap *clickbait*), YouTube Music mengoptimalkan **perkiraan durasi dengar/tonton (*expected watch/listen time*)** menggunakan *weighted logistic regression* (interaksi positif diberi bobot sesuai durasi dengar).

#### Ringkasan Perbandingan & Relevansi ke Tugas Akhir

| Platform | Mesin / Paradigma Utama | Kekuatan Khas | Keterbatasan terhadap *Dynamic Mood-Arc* |
| :--- | :--- | :--- | :--- |
| **Spotify** | BaRT (Contextual Bandits) + CF + NLP + Audio | Eksplorasi vs. eksploitasi *real-time* & *playlist co-occurrence* | Fokus ke relevansi umum dan umpan balik *skip* 30 detik; belum menjamin kurva *mood* kontinu bebas *boundary jump*. |
| **Apple Music** | "Algo-torial" (Editorial + CF + Deep Embeddings + ANN) | Sinergi kurator manusia + sinyal historis iTunes & Shazam | Bergantung pada kurasi editorial dan profil selera jangka panjang, bukan lintasan emosi antarsegmen dalam satu lagu. |
| **Deezer** | Latent Factor CF + CNN Audio Embeddings (*Flow Moods*) | Skalabilitas anotasi *mood* dari kurator ke jutaan lagu via CNN | *Flow Moods* terkunci pada 6 kategori *mood* diskrit tertutup, belum mendukung transisi lintasan emosi kontinu. |
| **YouTube Music** | Two-Stage: Two-Tower Retrieval + Deep Ranking (*Watch Time*) | Skalabilitas ekstrem & optimasi durasi dengar (*engagement*) | Mengoptimalkan durasi dengar dan kecocokan preferensi global, bukan koherensi transisi emosi antar-ujung lagu (*outro-to-intro*). |

**Benang Merah ke Tugas Akhir:**
Keempat platform komersial tersebut unggul dalam memprediksi *lagu apa* yang cocok dengan selera pengguna, tetapi belum memodelkan **dinamika emosi internal di dalam lagu** (seperti *intro* vs. *outro*) untuk menyusun playlist *mood-arc* kontinu tanpa sentakan transisi (*boundary jump problem*).

---

### 📚 Referensi
- **Berkas Literatur Internal Repo:**
  - [[06-Bontempelli2022-Flow-Moods-Deezer]] — Bontempelli et al. (2022), *Flow Moods: Recommending Music by Moods on Deezer* (ACM RecSys / Deezer Research).
  - [[05-Schweiger2025-Playlist-Coherence]] — Schweiger et al. (2025), analisis empiris koherensi sekuensial pada *Spotify Million Playlist Dataset*.
  - [[25-Bendada2023-Scalable-Playlist-Continuation]] — Bendada et al. (2023), arsitektur *Automatic Playlist Continuation* pada Spotify MPD dan Deezer.
  - `Catatan-Memori/Catatan-Memori-Logs/06-Naskah-Draft/01-Skenario-Murni-Komputasional/Bab-2-Tinjauan-Pustaka.md` (rujukan Tomasi et al., 2023 tentang RL pada katalog Spotify).
- **Literatur & Sumber Teknis Publik:**
  - Covington, P., Adams, J., & Sargin, E. (2016). *Deep Neural Networks for YouTube Recommendations*. Proceedings of the 10th ACM Conference on Recommender Systems (RecSys).
  - Dokumentasi & artikel teknis terkait Spotify BaRT (*Bandits for Recommendations as Treatments*), Apple Music *algo-torial* curation, dan Deezer Research (ACM RecSys).

---

## ❓ Pertanyaan #2
> Apabila dibandingkan dengan Tugas Akhir yang saya ajukan (termasuk ML, DL, atau apa?), algoritma yang digunakan oleh 4 platform tersebut masuk kategori apa (Machine Learning, Deep Learning, atau apa)? Dan MIR itu apa?

### 💡 Jawaban

#### 1. Posisi Tugas Akhir Anda: ML Klasik (Instance-Based) + Pemodelan Matematis Deterministik
Berdasarkan rancangan pada [[Bab-3-Metodologi]] (*Two-Stage KNN + Dynamic Trajectory Alignment Reranker* pada dataset DEAM), Tugas Akhir Anda **bukan Deep Learning** (tidak melatih jaringan saraf tiruan dengan *backpropagation*), melainkan kombinasi dari:
1. **Classical / Instance-Based Machine Learning (Non-Parametric):** Pada Tahap 1 (*Candidate Retrieval*), Anda menggunakan **K-Nearest Neighbors (KNN)** berbasis jarak Euclidean di ruang Valence-Arousal untuk mengambil $K=20$ kandidat terdekat di sekitar *waypoint*. Meski memakai `torch` (PyTorch) untuk akselerasi matriks GPU, perannya di sini adalah mempercepat komputasi jarak tensor, bukan melatih *neural network*.
2. **Pemodelan Matematis & Optimasi Multi-Objektif Deterministik (Algorithmic / Vector-Space Reranking):** Pada Tahap 2 (*Reranking*), Anda memakai aljabar vektor dan geometri ruang sirkumpleks:
   - Ekstraksi vektor trajektori internal lagu ($\vec{\mathbf{t}}_k = (\Delta v_k, \Delta a_k)$) dan sudut polar ($\theta_k$).
   - Keselarasan arah via *Cosine Similarity*.
   - Penalti *Boundary Jump Cost* ($\mathcal{BJC}$) dan skor komposit linier terbobot ($w_1, w_2, w_3$).
- **Keunggulan pendekatan ini untuk S1/Sempro:** Cepat, *reproducible* (`seed=42`), ringan tanpa kebutuhan dataset jutaan lagu untuk *training* berat, serta sangat transparan untuk *Code Walkthrough* di sidang karena setiap bobot dan jarak bisa dijelaskan secara matematis baris demi baris.

#### 2. Klasifikasi Algoritma 4 Platform Streaming: Hybrid (ML Klasik + Deep Learning + Non-ML)
Keempat platform komersial tidak hanya memakai satu jenis algoritma, melainkan **sistem hibrida berlapis** yang menggabungkan ML klasik, Deep Learning (DL), hingga kurasi manusia:

| Platform | Bagian Machine Learning (ML Klasik / Statistik / RL) | Bagian Deep Learning (DL) | Bagian Non-ML / Heuristik / Manusia |
| :--- | :--- | :--- | :--- |
| **Spotify** | - **Contextual Multi-Armed Bandits (BaRT)** (*Reinforcement Learning* ringan untuk *explore-exploit*)<br>- **Collaborative Filtering** (*Matrix Factorization* / *co-occurrence* playlist) | - **NLP / Transformer** untuk membaca teks web, blog, dan lirik (*cultural vectoring*)<br>- **CNN / RNN** pada spektrogram audio mentah (*Audio Analysis*) | Aturan bisnis *30-second stream* & penyaringan editorial untuk playlist kurasi manusia |
| **Apple Music** | - **Collaborative Filtering** (matriks interaksi pengguna-lagu)<br>- Pencarian vektor **ANN** (*Approximate Nearest Neighbor*) | - **Deep Learning Embeddings** untuk memetakan pola dengar sekuensial & metadata ke ruang vektor berdimensi tinggi | **Human Editorial Curation** (kurator musik & DJ global sebagai pemicu sinyal dalam pendekatan *"algo-torial"*) |
| **Deezer** | - **Latent Factor Collaborative Filtering** (*user* & *track embeddings* + *cosine similarity*)<br>- **ACT-R** (pemodelan kognitif untuk *repeat listening*) | - **CNN Audio Embeddings** pada spektrogram untuk memetakan dan menskalakan label *mood* ke jutaan lagu (*Flow Moods*) | **Anotasi kurator profesional** untuk ribuan lagu benih (*seed*) dan 6 tombol kategori *mood* diskrit |
| **YouTube Music** | - **Weighted Logistic Regression** (dalam fungsi objektif *ranking* untuk memprediksi *expected watch/listen time*)<br>- Pencarian **ANN** pada tahap *retrieval* | - **Two-Tower Neural Networks** (*User Tower* & *Item Tower* berbasis DNN)<br>- **Deep Ranking Network** dengan *cross-features* | Heuristik *example age* (penyesuaian umur konten untuk menjaga *freshness*) |

#### 3. Apa itu MIR (*Music Information Retrieval*)?
**MIR (*Music Information Retrieval*)** adalah bidang ilmu interdisipliner yang berfokus pada cara mengekstrak, memahami, mengorganisasi, dan menemukan kembali informasi bermakna dari data musik (baik berupa sinyal audio mentah, lirik, metadata, maupun perilaku pendengar).

MIR memadukan beberapa disiplin ilmu sekaligus:
- **Pemrosesan Sinyal Audio (*Digital Signal Processing*):** mengekstrak tempo (BPM), spektrum frekuensi, timbre (MFCC), kunci nada, hingga struktur lagu (*intro, verse, chorus, outro*).
- **Ilmu Komputer & AI (ML/DL):** membangun model klasifikasi genre, transkripsi musik otomatis, pengenalan emosi, dan sistem rekomendasi.
- **Psikologi Musik & Musikologi:** memahami bagaimana manusia mempersepsikan musik (contohnya **Model Emosi Sirkumpleks Russell 1980** pada dimensi *Valence* dan *Arousal*).

**Posisi Tugas Akhir Anda di dalam Peta MIR:**
Tugas Akhir Anda berada tepat di persimpangan dua subbidang utama MIR:
1. **MER (*Music Emotion Recognition*):** Merepresentasikan emosi lagu secara dinamis dalam ruang 2D *Valence-Arousal* (memanfaatkan deret waktu 2 Hz dari dataset DEAM).
2. **APC (*Automatic Playlist Continuation* / *Mood-Arc Playlist Generation*):** Menyusun urutan lagu secara otomatis mengikuti lintasan suasana hati tertentu dengan menjaga kehalusan transisi antartrek.

---

## ❓ Pertanyaan #3
> Berikan pernyataan tegas mengenai jenis algoritma Tugas Akhir saya (apakah termasuk ML atau ada istilah algoritma lain yang lebih tepat), dan jelaskan di bagian mana letak kebaruan (*novelty*) dan urgensi (*urgency*) Tugas Akhir saya dibanding 4 platform streaming yang sudah menggunakan Deep Learning.

### 💡 Jawaban

#### 1. Pernyataan Tegas Jenis Algoritma Tugas Akhir Anda
> **Pernyataan siap pakai untuk Sempro:**
> *"Penelitian Tugas Akhir ini merupakan **Sistem Rekomendasi Musik Hibrida Berbasis Retrieval-and-Reranking Dua Tahap (Two-Stage Retrieval-and-Reranking)** dalam domain **Music Information Retrieval (MIR)**. Tahap pertamanya menggunakan **Machine Learning Klasik Non-Parametrik (Instance-Based Learning)** melalui algoritma **K-Nearest Neighbors (KNN)** untuk penelusuran kandidat, sedangkan tahap keduanya menggunakan **Algoritma Optimasi Sekuensial Berbasis Aljabar Vektor Deterministik (Dynamic Trajectory Alignment Reranker)**."*

Secara spesifik, TA Anda **bukan Deep Learning** dan **bukan Reinforcement Learning** karena tidak melatih bobot jaringan saraf tiruan (*neural network*) maupun agen kebijakan (*policy network*). Istilah paling akurat untuk menyebut pendekatan Anda adalah:
- **Two-Stage Retrieval-and-Reranking Pipeline** (arsitektur sistem), dengan isi:
  1. **Instance-Based Machine Learning:** *K-Nearest Neighbors* (KNN) pada Tahap 1.
  2. **Deterministic Vector-Space Trajectory Alignment & Multi-Objective Reranking:** pemodelan matematis arah gerak emosi dan penalti *Boundary Jump Cost* ($\mathcal{BJC}$) pada Tahap 2.

#### 2. Mengapa Tetap Punya Novelty & Urgency Tinggi Meski 4 Platform Sudah Pakai Deep Learning?
Dosen penguji sering bertanya: *"Spotify, Apple Music, Deezer, dan YouTube Music sudah pakai Deep Learning canggih, lalu apa urgensi dan kebaruan riset kamu yang cuma pakai KNN + Reranker matematis?"*

Jawabannya terletak pada **perbedaan masalah yang diselesaikan**, bukan sekadar adu canggih model:

1. **Deep Learning di 4 Platform Fokus pada *Relevance* ("Lagu Apa yang Anda Suka"), Bukan *Intra-Song Emotion Trajectory* ("Bagaimana Emosi Bergerak dari Outro ke Intro"):**
   - **Spotify (BaRT + CF + NLP + Audio CNN)**, **Apple Music (Algo-torial)**, dan **YouTube Music (Two-Tower DNN)** memodelkan setiap lagu sebagai **satu titik embedding global** atau skor relevansi untuk memprediksi apakah pengguna akan mendengarkan >30 detik.
   - **Deezer (Flow Moods)** memang sudah memakai CNN Audio Embeddings untuk memetakan *mood*, tetapi terkunci pada **6 kategori *mood* diskrit tertutup** (*Chill, Focus, Melancholy, Motivation, Party, You & Me*) sehingga belum mendukung lintasan emosi kontinu (*dynamic mood-arc*).
   - Akibatnya, baik platform industri maupun model acuan akademik **Gaur & Donnelly (2020)** sama-sama memperlakukan lagu seolah-olah emosinya statis (*static-point matching*).

2. **Bukti Empiris Kegagalan *Static-Point Matching* (*Urgency*):**
   - **Realitas Data (DEAM):** 98,11% lagu dari 1.802 klip DEAM mengalami pergeseran emosi internal yang nyata sepanjang durasinya (jarak rata-rata awal ke akhir $\Delta = 0,1937$ dan rentang dinamis hingga $0,5950$). Mereduksi lagu menjadi satu titik rata-rata menghilangkan 15% hingga 35% variansi informasi afektif (Pyrovolakis et al., 2022).
   - **Dampak Nyata ke Pengguna (*Skip Rate*):** Studi skala masif Schweiger et al. (2025) pada jutaan playlist Spotify dan Deezer membuktikan bahwa lompatan emosi antartrek berurutan sebesar $\Delta > 0,25$ meningkatkan *skip rate* hingga **37%**.
   - **Kegagalan Baseline pada Rute Realistis:** Replikasi awal pada 540 *batch run* menunjukkan skor kehalusan tinggi model Gaur (0,9950) hanya terjadi pada rute diagonal buatan (Q3 ke Q1), sedangkan pada rute lintas kuadran realistis (Q1 ke Q2 dan Q1 ke Q4), performanya anjlok ke **0,6628 sampai 0,7189** akibat *The Boundary Jump Problem* (sambungan *outro* lagu $i$ tidak cocok dengan *intro* lagu $i+1$).

3. **Mengapa Tidak Cukup Diselesaikan dengan Deep Learning Generatif (seperti REMAST)?**
   - Penelitian terbaru **REMAST (Wang et al., 2024, IEEE TAC)** memang sudah menyelesaikan *soft transition*, tetapi dengan cara **menyintesis musik simbolik baru (MIDI)** untuk menjembatani transisi. Cara ini tidak bisa diterapkan pada platform streaming resmi (Spotify, Deezer, dll.) karena rekaman audio asli artis berhak cipta **tidak boleh diubah atau dimodifikasi strukturnya**.
   - Sementara pendekatan **Reinforcement Learning (Tomasi et al., 2023)** untuk kelanjutan playlist membutuhkan komputasi pelatihan yang sangat berat, sulit diinterpretasikan (*black-box*), dan mengabaikan kurva koordinat emosi eksplisit.

4. **Letak *Novelty* (Kebaruan) Tugas Akhir Anda:**
   - **Novelty Representasi:** Mengubah representasi lagu pada penyusunan *mood-arc playlist* dari **titik statis tunggal** menjadi **vektor trajektori dinamis internal (2 Hz)** yang menangkap segmen *intro*, *outro*, magnitudo, dan sudut orientasi emosi ($\theta = \text{atan2}(\Delta a, \Delta v)$).
   - **Novelty Algoritma Perankingan:** Memperkenalkan penalti **Boundary Jump Cost ($\mathcal{BJC}$)** di dalam *Dynamic Trajectory Alignment Reranker* untuk menjaga kehalusan transisi fisik *outro-to-intro* pada **rekaman audio utuh** (tanpa memodifikasi audio seperti REMAST), dengan kompleksitas ringan, deterministik, dan transparan secara matematis.

---

	### 🔗 Catatan Terkait
- [[00-Index-Catatan]]
- [[Model-Emosi-Sirkumpleks-Russell-1980]]
- [[Bab-2-Tinjauan-Pustaka]]
