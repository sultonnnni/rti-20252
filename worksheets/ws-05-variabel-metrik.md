# WS-05: Variabel & Metrik

> Bab 5 — Metric, Measurement & Data

**Nama** : Ahmad Sultoni  
**NIM** : 240202850  
**Mata Kuliah** : Research & Teknologi Informasi (RTI)  

---

## VARIABLE & METRIC DEFINITION

**Research Question**  
Apakah metode caching (Redis) menghasilkan response time yang lebih rendah dibandingkan load balancing dalam meningkatkan performa sistem e-learning berbasis web pada kondisi concurrent user tinggi?

---

| Variabel | Tipe | Konsep | Metrik | Skala | Satuan | Cara Mengukur | Justifikasi |
|----------|------|--------|--------|-------|--------|---------------|-------------|
| Metode optimasi | IV | Pendekatan optimasi performa server | Kategori (Caching vs Load Balancing) | Nominal | — | Mengatur konfigurasi server sesuai metode yang diuji | Mewakili perbedaan pendekatan utama dalam optimasi sistem |
| Performa sistem (Response Time) | DV | Kecepatan sistem merespon request | Rata-rata response time | Ratio | ms | Mengukur waktu dari request dikirim hingga response diterima | Langsung merepresentasikan kecepatan akses pengguna |
| Performa sistem (Throughput) | DV | Kemampuan sistem menangani request | Jumlah request per detik | Ratio | request/second | Menghitung jumlah request yang berhasil diproses per detik | Menggambarkan kapasitas sistem dalam kondisi beban tinggi |
| Jumlah user | CV | Beban sistem | Jumlah concurrent user | Ratio | user | Menentukan jumlah user pada setiap skenario pengujian | Mengontrol agar perbandingan tetap adil |
| Spesifikasi server | CV | Lingkungan sistem | CPU, RAM server | Nominal | — | Menjaga konfigurasi server tetap sama selama eksperimen | Menghindari bias dari perbedaan hardware |
| Dataset request | CV | Pola akses sistem | Skenario request (login, akses materi, dll) | Nominal | — | Menggunakan skenario request yang sama di setiap pengujian | Menjaga konsistensi data uji |

---

## Alignment Check

RQ → Concept → Variable → Metric → Data → Result  

[x] Setiap langkah terdokumentasi  
[x] Tidak ada lompatan logis  
[x] Metrik mengukur konsep yang dimaksud  

---

## Latihan 1 — Operationalization Chain

**RQ:**  
Apakah caching lebih cepat dibanding load balancing pada sistem e-learning dengan banyak pengguna?

| Variabel | Tipe | Konsep Abstrak | Metrik Konkret | Skala (NOIR) | Satuan |
|----------|------|---------------|----------------|-------------|--------|
| Metode optimasi | IV | Pendekatan sistem | Caching vs Load Balancing | Nominal | — |
| Response time | DV | Kecepatan sistem | Waktu respon rata-rata | Ratio | ms |
| Throughput | DV | Kapasitas sistem | Request per detik | Ratio | request/s |
| Jumlah user | CV | Beban sistem | Jumlah user aktif | Ratio | user |

**Apakah ada lompatan logis?**  
[x] Tidak  

---

## Latihan 2 — Evaluasi Metrik

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Representative | 5 | Response time langsung mencerminkan performa sistem dari sudut pandang pengguna |
| Sensitive | 4 | Perubahan kecil pada sistem masih bisa terdeteksi melalui perubahan waktu respon |
| Feasible | 5 | Mudah diukur menggunakan tools monitoring server |

**Apakah perlu secondary metric?**  
[x] Ya  

**Secondary metric:** Throughput  
**Alasan:**  
Karena response time saja belum cukup menggambarkan performa sistem secara keseluruhan, sehingga perlu metrik tambahan untuk melihat kemampuan sistem dalam menangani banyak request.

---

**Contoh ceiling effect:**  
Jika semua metode menghasilkan response time yang hampir sama (misalnya <100 ms), maka perbedaan antar metode menjadi sulit terlihat.

---

## Latihan 3 — Data Quality Check

| Dimensi | Pertanyaan | Jawaban | Strategi Mitigasi |
|---------|-----------|---------|------------------|
| Completeness | Apakah semua data terkumpul? | Kemungkinan ada data yang hilang saat load tinggi | Melakukan logging otomatis |
| Consistency | Apakah ada kontradiksi data? | Bisa terjadi jika server tidak stabil | Menjalankan eksperimen berulang |
| Validity | Apakah benar mengukur performa? | Ya, karena metrik langsung dari sistem | Gunakan tools monitoring terpercaya |
| Representativeness | Apakah data mewakili kondisi nyata? | Belum sepenuhnya | Gunakan variasi jumlah user |

---

## Refleksi

Memilih metrik setelah melihat data disebut p-hacking karena peneliti bisa saja memilih metrik yang paling menguntungkan hasilnya. Hal ini membuat penelitian menjadi tidak objektif.

Berbeda dengan eksplorasi data yang sah, eksplorasi dilakukan setelah analisis utama dan biasanya diberi label sebagai temuan tambahan. Sedangkan p-hacking dilakukan untuk memanipulasi hasil agar terlihat signifikan sejak awal.

---
