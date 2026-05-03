# WS-04: Research Question & Hypothesis

> Bab 4 — Research Question, Contribution & Hypothesis

**Nama** : Ahmad Sultoni  
**NIM** : 240202850  
**Mata Kuliah** : Research & Teknologi Informasi (RTI)  

---

## RQ-CONTRIBUTION-HYPOTHESIS

**Gap Statement**  
Sebagian besar penelitian sebelumnya masih menggunakan dataset simulasi dan belum membandingkan secara langsung metode caching dan load balancing dalam kondisi beban tinggi pada sistem e-learning.

---

## Research Question

**Tipe** : [x] Comparison  [ ] Improvement  [ ] Exploratory  

**Formulasi**  
Apakah metode caching (Redis) menghasilkan response time yang lebih rendah dibandingkan load balancing dalam meningkatkan performa sistem e-learning berbasis web pada kondisi concurrent user tinggi?

**Variabel IV (Independent Variable)**  
Metode optimasi (Caching vs Load Balancing)

**Variabel DV (Dependent Variable)**  
Performa sistem (response time, throughput)

**Metrik**  
- Response time (ms)  
- Throughput (request/second)  

**Dataset / Konteks**  
Simulasi beban pengguna pada sistem e-learning berbasis web (menggunakan skenario concurrent user)

**Baseline**  
Load Balancing

---

## Quality Check RQ

[x] Variabel spesifik  
[x] Metrik jelas  
[x] Baseline ada  
[x] Konteks disebutkan  
[x] Memerlukan eksperimen  

---

## Contribution Statement

**Apa yang baru diketahui**  
Penelitian ini memberikan perbandingan langsung antara metode caching dan load balancing dalam kondisi beban tinggi pada sistem e-learning, yang sebelumnya belum diuji secara spesifik dengan pendekatan yang sama.

**Jenis kontribusi**  
[x] Comparison  [ ] Improvement  [ ] Novel approach  

**Gap yang diisi**  
Data gap dan method gap pada evaluasi performa sistem e-learning.

---

## Hypothesis Pair

**H₀ (Null Hypothesis)**  
Tidak terdapat perbedaan signifikan pada response time antara metode caching dan load balancing dalam sistem e-learning.

**H₁ (Alternative Hypothesis)**  
Metode caching menghasilkan response time yang secara signifikan lebih rendah dibandingkan load balancing dalam sistem e-learning.

**Threshold**  
p-value < 0.05  

**Justifikasi threshold**  
Nilai 0.05 merupakan standar umum dalam pengujian statistik untuk menentukan signifikansi perbedaan antar metode.

---

## Latihan 1 — Dari Gap ke RQ

**Gap dari WS-03:**  
Penggunaan dataset tidak realistis dan belum adanya perbandingan langsung metode optimasi dalam konteks e-learning.

**RQ versi pertama (bebas):**  
> Metode optimasi mana yang paling baik untuk meningkatkan performa e-learning?

### Evaluasi RQ

| Komponen | Ada? | Isi |
|----------|------|-----|
| Metode spesifik | Tidak | Masih umum |
| Metrik terukur | Tidak | Belum ada |
| Baseline | Tidak | Belum jelas |
| Dataset/konteks | Tidak | Belum disebutkan |

**Tipe RQ:** Comparison  

---

**RQ versi revisi (final):**  
> Apakah metode caching (Redis) menghasilkan response time lebih rendah dibandingkan load balancing pada sistem e-learning dengan jumlah pengguna tinggi?

---

## Latihan 2 — Hypothesis Pair

| Komponen | Isi |
|----------|-----|
| H₀ | Tidak ada perbedaan signifikan response time antara caching dan load balancing |
| H₁ | Caching menghasilkan response time lebih rendah dibanding load balancing |
| Metrik | Response time |
| Threshold | p-value < 0.05 |
| Justifikasi threshold | Standar umum dalam analisis statistik |

**Apakah hipotesis ini falsifiable?**  
[x] Ya  

**Cara membuktikannya salah**  
Jika hasil uji statistik menunjukkan p-value ≥ 0.05, maka tidak ada perbedaan signifikan dan H₀ tidak dapat ditolak.

---

## Latihan 3 — Rantai Operasionalisasi

| Tahap | Isi |
|------|-----|
| RQ | Apakah caching lebih cepat dibanding load balancing pada e-learning? |
| Variable (IV) | Jenis metode optimasi (Caching vs Load Balancing) |
| Variable (DV) | Response time dan throughput |
| Metric | ms dan request/second |
| Data source | Simulasi beban user pada sistem e-learning |
| Analysis method | Uji statistik (t-test) |

**Apakah rantai lengkap?**  
[x] Ya  

---

## Refleksi

**Judul**  
Analisis Performa Web Server Menggunakan Load Balancing  

**RQ yang diekstrak**  
Apakah load balancing meningkatkan performa web server?

**Komponen yang hilang**  
RQ tersebut belum menyebutkan metrik yang jelas, dataset yang digunakan, serta tidak ada baseline pembanding. Hal ini membuat penelitian kurang kuat karena tidak memiliki arah eksperimen yang spesifik.

---
