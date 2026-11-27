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

### 🔗 Catatan Terkait
- [[00-Index-Catatan]]
- [[Model-Emosi-Sirkumpleks-Russell-1980]]
- [[Bab-2-Tinjauan-Pustaka]]
