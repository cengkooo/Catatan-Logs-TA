---
title: "Panduan Ekstraksi Fitur Audio Menggunakan Librosa"
tags:
  - note/techstack
  - engineering
  - cheat-sheet
  - audio-processing
  - python
  - librosa
stack: "Python & Librosa"
versi: "0.10.x"
created: 2026-11-23
updated: 2026-11-23
---

# ⚙️ Panduan Ekstraksi Fitur Audio Menggunakan Librosa

- **Ekosistem / Tool:** `Python / Librosa`
- **Versi Rujukan:** `librosa >= 0.10.0`
- **Fungsi di Pipeline TA:** Memuat sinyal mentah wav/mp3 dari DEAM, menghitung representasi spektrogram, mengekstrak fitur akustik sekunder (MFCC, Chroma, Spectral Contrast, Tempogram) untuk pemodelan audio baseline dan verifikasi trajektori.

---

## 💡 Ringkasan & Aturan Baku Pra-proses Audio

1. **Sample Rate ($sr$):** Standar riset MIR umumnya menggunakan `sr=22050` Hz (cukup untuk rentang frekuensi manusia dan efisien secara komputasi). Hindari resampling berulang yang tidak perlu.
2. **Mono vs Stereo:** Selalu konversi sinyal ke **mono** (`mono=True`), karena variasi spatial stereo tidak relevan dalam prediksi Valence-Arousal global dan menggandakan beban komputasi.
3. **Offset & Durasi DEAM:** Pada dataset DEAM, **15 detik pertama adalah instruksi/pemanasan** anotator yang wajib dieliminasi (`offset=15.0, duration=45.0`).

---

## 💻 Code Snippet Siap Pakai (Modular DEAM Audio Loader)

```python
import librosa
import numpy as np
import soundfile as sf

def load_deam_clip(audio_path: str, sr: int = 22050, offset: float = 15.0, duration: float = 45.0):
    """
    Memuat klip audio DEAM sesuai protokol resmi riset:
    - Sample rate: 22050 Hz
    - Konversi mono
    - Skip 15 detik pertama (offset=15.0)
    - Ambil tepat 45 detik (durasi eksperimen)
    """
    y, sr = librosa.load(audio_path, sr=sr, mono=True, offset=offset, duration=duration)
    
    # Validasi panjang array sinyal (45s * 22050 = 992.250 sampel)
    expected_samples = int(sr * duration)
    if len(y) < expected_samples:
        # Zero-padding jika file sedikit lebih pendek
        y = np.pad(y, (0, expected_samples - len(y)), mode='constant')
    else:
        y = y[:expected_samples]
        
    return y, sr

def extract_acoustic_features(y: np.ndarray, sr: int = 22050):
    """
    Mengekstrak fitur akustik agregat untuk baseline model:
    - MFCC (20 koefisien + delta)
    - Chroma STFT (12 bins nada untuk harmoni/valence)
    - Spectral Contrast (kontras energi frekuensi)
    - Tempo (BPM untuk korelasi arousal)
    """
    # 1. MFCC (Mel-Frequency Cepstral Coefficients)
    mfcc = librosa.feature.mfcc(y=y, sr=sr, n_mfcc=20)
    mfcc_mean = np.mean(mfcc, axis=1)
    mfcc_std = np.std(mfcc, axis=1)
    
    # 2. Chroma STFT (Representasi harmonik)
    chroma = librosa.feature.chroma_stft(y=y, sr=sr)
    chroma_mean = np.mean(chroma, axis=1)
    
    # 3. Spectral Contrast
    contrast = librosa.feature.spectral_contrast(y=y, sr=sr)
    contrast_mean = np.mean(contrast, axis=1)
    
    # 4. Tempo / Rhythm
    tempo, _ = librosa.beat.beat_track(y=y, sr=sr)
    
    # Vektor fitur gabungan (20+20+12+7+1 = 60 dimensi)
    feature_vector = np.hstack([mfcc_mean, mfcc_std, chroma_mean, contrast_mean, [float(tempo)]])
    return feature_vector
```

---

## ⚠️ Common Pitfalls & Troubleshooting

| Gejala Masalah | Akar Penyebab | Solusi / Best Practice |
| :--- | :--- | :--- |
| `UserWarning: PySoundFile failed. Trying audioread instead.` | Backend file pembaca tidak mendukung format atau file korup | Install `soundfile` versi modern (`pip install soundfile`) dan pastikan format file berupa `.mp3` atau `.wav` murni. |
| Dimensi output time-series tidak presisi kelipatan 0.5s (2 Hz) | Parameter `hop_length` bawaan Librosa (512) menghasilkan resolusi ~43 Hz, bukan 2 Hz | Hitung `hop_length` khusus: $hop\_length = \frac{sr}{frekuensi\_target} = \frac{22050}{2} = 11025$. |
| Memori RAM habis saat looping ribuan lagu | Objek audio besar tidak dibersihkan oleh garbage collection | Jangan simpan array sinyal `y` mentah di dalam list global. Langsung ekstrak fitur matriks numerik lalu simpan ke `.npy` / `.parquet`. |

---

## 🔗 Referensi & Catatan Terkait
- Dokumentasi Librosa: https://librosa.org/doc/latest/index.html
- Terkait ke: [[02-Formulasi-Ekstraksi-Trajectory|Ekstraksi-Trajectory]] | [[06-Log-Training-Baseline-Gaur|1_TRAIN_BASELINE]] | [[Phase-04-Coding-Eksperimen-DEAM]] | [[00-Index-Catatan]]
