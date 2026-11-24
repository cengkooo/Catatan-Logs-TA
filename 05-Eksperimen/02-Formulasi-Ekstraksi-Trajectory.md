---
title: Formulasi & Ekstraksi Vektor Trajectory Mood
tags:
  - eksperimen
  - trajectory
  - matematika
aliases:
  - Ekstraksi-Trajectory
  - Formulasi Trajectory
---
# 📐 Formulasi & Ekstraksi Vektor Trajectory Mood

Catatan perancangan algoritma ekstraksi arah dan magnitudo perubahan mood lagu.

---

## 🧮 Formulasi Matematis

Diberikan sebuah lagu $i$ dengan deret waktu anotasi sepanjang $T$ timestep:
$$ \mathbf{P}_i = [ (V_i(t_1), A_i(t_1)), (V_i(t_2), A_i(t_2)), \dots, (V_i(t_T), A_i(t_T)) ] $$

### 1. Vektor Perpindahan Global (Displacement Vector)
$$ \vec{\mathbf{v}}_i = (V_i(t_T) - V_i(t_1), A_i(t_T) - A_i(t_1)) $$
* **Magnitudo:** $\|\vec{\mathbf{v}}_i\| = \sqrt{\Delta V^2 + \Delta A^2}$
* **Arah / Sudut:** $\theta_i = \text{atan2}(\Delta A, \Delta V)$

### 2. Kriteria Trajectory Alignment (Penyelarasan Arah)
Misalkan target transisi pada titik ke-$k$ pada playlist adalah vektor $\vec{\mathbf{u}}_k$:
$$ \text{Sim}_{\text{trajectory}}(\vec{\mathbf{v}}_i, \vec{\mathbf{u}}_k) = \cos(\theta) = \frac{\vec{\mathbf{v}}_i \cdot \vec{\mathbf{u}}_k}{\|\vec{\mathbf{v}}_i\| \|\vec{\mathbf{u}}_k\|} $$
* Nilai mendekati $+1.0$: Arah lagu selaras dengan transisi yang diinginkan pengguna.
* Nilai mendekati $-1.0$: Arah lagu berlawanan (misal pengguna ingin naik semangat, lagu malah turun sedih).
