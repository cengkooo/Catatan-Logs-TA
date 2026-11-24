---
title: "Draf Naskah Bab 1: Pendahuluan (Format UNESCO 15,5 x 23 cm)"
tags:
  - draft
  - bab1
  - naskah
  - pendahuluan
  - deam
  - unesco
  - murni-komputasional
status: "READY FOR COMPILATION"
date: 2026-11-24
---

# ✍️ Bab I Pendahuluan (Skenario 1: Murni Komputasional)

*Dokumen sinkronisasi narasi naskah Bab I mengikuti kaidah Bahasa Peneliti anti-slop dan standar tata tulis UNESCO ITERA (Times New Roman 11 pt, spasi 1,5, sitasi IEEE murni).*

---

## 1.1 Latar Belakang

Perkembangan platform penyiaran musik digital (*music streaming services*) seperti Spotify, Apple Music, dan Deezer telah mengubah paradigma interaksi manusia dengan katalog audio berskala masif. Berdasarkan laporan industri dan studi sistem temu kembali informasi musik (*Music Information Retrieval* / MIR), lebih dari 60% waktu mendengarkan musik dihabiskan melalui kurasi daftar putar (*playlist*). Namun, mayoritas sistem rekomendasi konvensional masih mengandalkan pendekatan penyaringan kolaboratif (*collaborative filtering*) dan pencocokan kemiripan statis yang memperlakukan preferensi pengguna secara independen per trek, tanpa mempertimbangkan kontinuitas alur emosional di sepanjang sesi mendengarkan.

Kebutuhan pendengar modern telah bergeser ke arah daftar putar berbasis konteks dan aktivitas (seperti belajar, berolahraga, meditasi, dan tidur), di mana perubahan suasana hati (*mood*) diharapkan mengikuti lintasan afektif tertentu yang terkontrol (*mood arc*). Platform penyiaran komersial telah merespons kebutuhan ini, seperti penerapan fitur *Flow Moods* pada Deezer (Bontempelli et al., 2022) untuk mengarahkan pendengar ke suasana hati tertentu, serta eksplorasi model sekuensial berbasis *reinforcement learning* (Tomasi et al., 2023). Studi empiris skala masif oleh Schweiger et al. (2025) pada jutaan playlist kurasi manusia membuktikan bahwa koherensi sekuensial dan kehalusan transisi antartrek berturutan (*sequential transition coherence*) berkorelasi langsung terhadap kenyamanan dan retensi pendengar. Transisi antarlagu yang melompat kasar di ruang emosi ($\Delta > 0,25$) terbukti meningkatkan tingkat pembatalan dengar (*skip rate*) hingga 37%.

Gagasan penyusunan playlist berbasis kurva emosi telah dirintis sejak prototipe MOODetector (Cardoso et al., 2011) dengan memetakan trek musik ke dalam ruang afektif dua dimensi Valence-Arousal model sirkumpleks Russell (1980). Pemilihan model dimensional dua dimensi ini memiliki legitimasi komputasional yang sangat kokoh. Penelitian mutakhir oleh Belaref et al. (2024) yang melakukan *data-driven decoding* membuktikan bahwa representasi laten jaringan syaraf tiruan modern (*Transformer embeddings*) secara alami merekonstruksi topologi lingkaran sirkumpleks Russell dengan korelasi keteraturan angular $r > 0,82$, di mana 75% konsep emosi terpetakan dalam deviasi sudut sangat presisi ($\Delta \theta < 30^\circ$). Hal ini menegaskan bahwa ruang Valence-Arousal merupakan geometri representasi alami yang kokoh untuk pemodelan afektif komputasional.

Penelitian acuan utama oleh Shaurya Gaur dan Donnelly (2020, 2023, 2024) mengusulkan algoritma pembangkitan mood-arc playlist dua tahap: tahap pertama menggunakan *K-Nearest Neighbors* (KNN) untuk menginterpolasi dan mengambil kandidat lagu di sekitar titik acuan (*waypoint*) lintasan emosi, disusul tahap kedua berupa penyaringan berbasis kemiripan fitur akustik. Model ini diuji pada dataset DMDD (Delbouys et al., 2018) dan menjadi acuan utama dalam pengukuran metrik kehalusan (*Smoothness Index*) serta keseragaman (*Evenness Index*) playlist.

Meskipun model Gaur dan Donnelly (2020) menunjukkan kinerja retrieval yang terarah, pendekatan tersebut menyimpan kelemahan struktural mendasar: **pencocokan titik statis (*static-point matching*)**. Pada dataset DMDD, setiap lagu direpresentasikan hanya oleh satu nilai rata-rata skalar Valence dan Arousal ($\bar{v}, \bar{a}$) untuk keseluruhan durasi audio. Representasi statis ini mengasumsikan secara keliru bahwa suasana hati lagu bersifat konstan dari awal hingga akhir. Sebagaimana dibuktikan oleh Wang et al. (2024) pada perancangan transisi musik afektif (*REMAST* di IEEE TAC), memaksakan kecocokan emosi seketika (*real-time fit*) tanpa memperhitungkan inersia dan kontinuitas transisi antar-segmen selalu memicu sentakan struktural yang merusak koherensi mendengarkan. Analisis empiris pada korpus benchmark DEAM (*Database for Emotion Analysis in Music*, Aljanaki et al., 2017) yang memuat anotasi dinamis 2 Hz pada 1.802 klip musik membuktikan bahwa **98,11% lagu mengalami pergeseran emosi internal nyata** sepanjang durasinya, dengan jarak pergeseran rata-rata awal ke akhir $\Delta = 0,1937$ dan rentang dinamis intra-lagu mencapai hingga $0,5950$. Studi Pyrovolakis et al. (2022) mengonfirmasi bahwa mereduksi lagu menjadi titik rata-rata statis menghilangkan 15% hingga 35% variansi informasi afektif audio.

Ketiadaan representasi dinamika internal ini melahirkan fenomena kegagalan perseptual yang kami definisikan sebagai **The Boundary Jump Problem**: suatu kondisi diskontinuitas emosi yang tajam ketika detik-detik akhir lagu $i$ (outro, misal berkarakter tenang di kuadran IV) bersambung langsung dengan detik-detik awal lagu $i+1$ (intro, misal berkarakter enerjik di kuadran I), meskipun kedua lagu tersebut memiliki nilai rata-rata statis yang identik. Akibatnya, playlist yang secara matematis tampak mulus pada level rata-rata trek, sebenarnya memicu sentakan emosi kasar (*boundary jump shock*) saat didengarkan secara berurutan. Hasil replikasi awal pada 540 batch run membuktikan bahwa nilai kehalusan tinggi model Gaur (0,9950) hanya merupakan artefak rute diagonal buatan (Q3 ke Q1), sedangkan pada rute lintas kuadran realistis (Q1 ke Q2 dan Q1 ke Q4), skor kehalusan baseline anjlok ke rentang 0,6628 hingga 0,7189 akibat ketiadaan informasi titik sambungan outro-intro.

Belum ada penelitian terdahulu yang menguji apakah mempertimbangkan trajektori dinamis mood internal lagu mampu menghasilkan transisi playlist mood-arc yang lebih koheren dan mulus dibandingkan pendekatan *static-point matching*. Oleh karena itu, penelitian ini mengusulkan pengembangan pipeline pembangkitan mood-arc playlist dua tahap yang diperkaya dengan mekanisme **Dynamic Mood Trajectory Alignment** menggunakan dataset benchmark DEAM.

---

## 1.2 Rumusan Masalah

Berdasarkan latar belakang masalah yang telah diuraikan, rumusan masalah dalam penelitian ini dirumuskan sebagai berikut:
1. Bagaimana merancang dan mengimplementasikan arsitektur pipeline pembangkitan *mood-arc playlist* dua tahap yang memadukan algoritma *K-Nearest Neighbors* (KNN) dengan mekanisme *Dynamic Mood Trajectory Alignment* pada dataset benchmark DEAM?
2. Bagaimana pengaruh integrasi vektor trajektori dinamis lagu terhadap peningkatan metrik kelancaran transisi (*Smoothness Index*) dan keseragaman sebaran (*Evenness Index*) playlist jika dibandingkan secara *head-to-head* terhadap model acuan *static-point matching* Gaur dan Donnelly (2020)?
3. Seberapa besar magnitudo pergeseran emosi internal (*intra-song mood dynamics*) pada dataset DEAM, dan bagaimana efektivitas formulasi penalti lompatan batas (*Boundary Jump Cost*) dalam mereduksi diskontinuitas sambungan trek berturutan?

---

## 1.3 Tujuan Penelitian

Tujuan yang hendak dicapai dalam pelaksanaan penelitian Tugas Akhir ini meliputi:
1. Merancang dan mengimplementasikan arsitektur pipeline komputasional dua tahap berbasis *KNN candidate retrieval* dan *trajectory alignment reranker* pada korpus audio DEAM (indikator keberhasilan: terwujudnya modul kode Python berbasis PyTorch modular yang mampu mengeksekusi *batch query* playlist secara deterministik dan tereproduksi).
2. Mengevaluasi performa kelancaran playlist yang dihasilkan terhadap model baseline Gaur dan Donnelly (2020) melalui pengujian komparatif 540 batch run pada rute diagonal dan lintas kuadran (indikator keberhasilan: reduksi nilai *Smoothness Index* $\ge 15\%$ tanpa mendegradasi *Evenness Index* secara signifikan, dibuktikan melalui uji signifikansi statistik non-parametrik *Wilcoxon Signed-Rank Test* dengan $p < 0,05$).
3. Mengukur magnitudo pergeseran vektor Valence-Arousal internal lagu pada 1.802 trek DEAM serta menganalisis kontribusi penalti *Boundary Jump Cost* dalam mengeliminasi anomali diskontinuitas perbatasan outro-intro antarlagu berturutan.

---

## 1.4 Batasan Penelitian

Ruang lingkup dan batasan operasional dalam penelitian ini ditetapkan sebagai berikut:
1. Dataset yang digunakan terbatas pada korpus benchmark audio terbuka DEAM (*Database for Emotion Analysis in Music*, Aljanaki et al., 2017) yang mencakup 1.802 klip musik berdurasi 45 detik dengan anotasi emosi kontinu berfrekuensi 2 Hz.
2. Sesuai protokol resmi anotasi DEAM, 15 detik pertama dari setiap klip audio diabaikan (*offset lead-in 15.0 detik*) karena merupakan fase adaptasi anotator manusia, sehingga analisis dinamika internal bertumpu pada 30 detik rekaman stabil ($90 \text{ timestamp}$ per lagu).
3. Ruang koordinat afektif dibatasi pada model sirkumpleks dua dimensi ortogonal Russell (1980) yang mencakup dimensi Valence dan Arousal dalam rentang dinormalisasi $[-1.0, +1.0]$.
4. Evaluasi kinerja playlist berfokus pada evaluasi komputasional objektif berbasis formulasi matematis *Smoothness Index*, *Evenness Index*, dan *Boundary Jump Cost* pada lingkungan GPU; penelitian pada skenario ini tidak mencakup pengujian persepsi subjektif responden manusia (*user listening study*).
5. Algoritma retrieval kandidat tahap pertama dibatasi pada *K-Nearest Neighbors* (KNN) deterministik guna menjamin transparansi perbandingan yang adil terhadap model acuan Gaur dan Donnelly (2020).

---

## 1.5 Manfaat Penelitian

Pelaksanaan penelitian ini diharapkan dapat memberikan kontribusi pada dua aspek utama:
1. **Manfaat Teoretis (Keilmuan):** Memperkaya khazanah penelitian *Music Information Retrieval* (MIR) dan komputasi afektif audio dengan memberikan bukti empiris mengenai pentingnya memperlakukan rekaman musik sebagai kurva trajektori temporal kontinu alih-alih titik rata-rata statis, serta mengukuhkan pemodelan sirkumpleks modern sebagai representasi yang relevan secara matematis.
2. **Manfaat Praktis (Industri):** Menyediakan rancangan algoritma optimasi transisi sekuensial berlatensi rendah yang siap diadaptasi oleh penyedia layanan penyiaran musik digital (*streaming platforms*) untuk meningkatkan koherensi dan kenyamanan dengar pada playlist berbasis suasana hati otomatis.

---

## 1.6 Sistematika Penulisan

Sistematika penulisan laporan proposal Tugas Akhir ini disusun ke dalam lima bab utama yang saling terhubung:
* **BAB I PENDAHULUAN:** Menguraikan konteks industri streaming, urgensi transisi mood-arc, identifikasi The Boundary Jump Problem pada baseline Gaur, justifikasi empiris dataset DEAM, rumusan masalah, tujuan berindikator kuantitatif, batasan penelitian, manfaat, dan sistematika naskah.
* **BAB II TINJAUAN PUSTAKA:** Menyajikan landasan teoretis model sirkumpleks Russell yang direvalidasi secara modern, dinamika temporal dan jeda persepsi emosi musik, representasi fitur akustik audio, kajian kritis model acuan Gaur dan Donnelly serta model transisi halus REMAST, tabel perbandingan komparatif 14 paper *state-of-the-art* standar UNESCO, sintesis kesenjangan riset tiga lapis, dan diagram kerangka pemikiran.
* **BAB III METODOLOGI:** Memaparkan alur penelitian enam tahap, protokol pengumpulan dan pembersihan data DEAM berstandar *anti-leakage*, formulasi matematika pipeline dua tahap terbobot penalti boundary jump, spesifikasi lingkungan komputasi untuk menjamin reprodusibilitas, serta skenario pengujian komparatif 540 batch run beserta uji signifikansi statistik.
* **BAB IV HASIL DAN PEMBAHASAN:** Menyajikan hasil pengujian komparasi model usulan terhadap baseline Gaur pada berbagai konfigurasi rute kuadran, analisis ablasi parameter pembobotan, serta pembahasan dekonstruksi boundary jump.
* **BAB V KESIMPULAN DAN SARAN:** Merangkum jawaban atas rumusan masalah berdasarkan bukti numerik eksperimental serta menguraikan rekomendasi pengembangan lanjutan bagi penelitian mendatang.
