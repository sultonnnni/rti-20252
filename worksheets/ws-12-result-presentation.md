# WS-12: Result Presentation & Visualization

## Pertemuan 12 — Penyajian Hasil & Visualisasi

**Nama:** Ahmad Sultoni
**NIM:** 240202850
**Mata Kuliah:** Research & Teknologi Informasi (RTI)

---

# RESULT PRESENTATION PLAN

**Research Question:**

Bagaimana pengaruh implementasi arsitektur Hybrid (Nginx Load Balancing dan Redis Caching) dibandingkan sistem tanpa optimasi terhadap penurunan Response Time dan peningkatan Throughput pada sistem e-learning saat beban puncak?

**Metrik Utama:**

1. Response Time (ms)
2. Throughput (req/sec)

---

# Latihan 1 — Tabel Hasil

### Tabel 1. Hasil Pengujian Performa Sistem E-Learning (n = 5 Run per Skenario)

| Skenario                              | Response Time (ms) Mean ± Std | Throughput (req/sec) Mean ± Std | n |
| ------------------------------------- | ----------------------------- | ------------------------------- | - |
| Hybrid (Load Balancing + Redis Cache) | 120 ± 6                       | 850 ± 12                        | 5 |
| Load Balancing Only                   | 148 ± 8                       | 735 ± 15                        | 5 |
| Cache Only                            | 173 ± 9                       | 645 ± 18                        | 5 |
| Baseline                              | 245 ± 11                      | 420 ± 20                        | 5 |

### Interpretasi Awal

Berdasarkan nilai rata-rata, arsitektur Hybrid menghasilkan response time paling rendah dan throughput paling tinggi dibandingkan seluruh skenario lainnya. Hal ini menunjukkan bahwa kombinasi load balancing dan caching memberikan dampak positif terhadap performa sistem e-learning pada kondisi beban tinggi.

---

## Checklist Tabel

* [x] Self-contained (judul jelas, satuan ada, N tercantum)
* [x] Mean ± Std ditampilkan
* [x] Diurutkan berdasarkan metrik utama (Response Time)
* [x] Format konsisten di seluruh tabel

---

# Latihan 2 — Rencana Visualisasi

### Grafik 1

| Komponen     | Keterangan                                |
| ------------ | ----------------------------------------- |
| Jenis Grafik | Grouped Bar Chart + Error Bar             |
| Pesan Utama  | Perbandingan Response Time antar skenario |
| Data         | Mean Response Time ± Std                  |

**Interpretasi yang diharapkan:**

Hybrid memiliki waktu respons paling rendah sehingga memberikan pengalaman pengguna yang lebih baik dibandingkan skenario lainnya.

---

### Grafik 2

| Komponen     | Keterangan                             |
| ------------ | -------------------------------------- |
| Jenis Grafik | Grouped Bar Chart + Error Bar          |
| Pesan Utama  | Perbandingan Throughput antar skenario |
| Data         | Mean Throughput ± Std                  |

**Interpretasi yang diharapkan:**

Hybrid mampu memproses lebih banyak request per detik dibandingkan Baseline maupun skenario ablation.

---

### Grafik 3

| Komponen     | Keterangan                             |
| ------------ | -------------------------------------- |
| Jenis Grafik | Box Plot                               |
| Pesan Utama  | Distribusi hasil antar-run             |
| Data         | Seluruh hasil Response Time dari 5 run |

**Interpretasi yang diharapkan:**

Menunjukkan stabilitas performa setiap skenario serta mendeteksi kemungkinan outlier.

---

## Ringkasan Visualisasi

| # | Jenis Grafik          | Pesan                          | Data yang Digunakan |
| - | --------------------- | ------------------------------ | ------------------- |
| 1 | Bar Chart + Error Bar | Perbandingan Response Time     | Mean ± Std          |
| 2 | Bar Chart + Error Bar | Perbandingan Throughput        | Mean ± Std          |
| 3 | Box Plot              | Distribusi dan Stabilitas Data | Semua Run           |

---

# Latihan 3 — Bias Detection

### Evaluasi Contoh

**Skenario:**

* Metode A = 91.2%
* Metode B = 90.8%
* Y-Axis dimulai dari 90%

| Pertanyaan                        | Jawaban                                                                                   |
| --------------------------------- | ----------------------------------------------------------------------------------------- |
| Apakah Y-axis menyesatkan?        | Ya. Selisih hanya 0.4% tetapi terlihat sangat besar karena skala dipotong mulai dari 90%. |
| Apakah error bar ditampilkan?     | Tidak. Variasi data tidak terlihat.                                                       |
| Apakah semua kondisi ditampilkan? | Ya.                                                                                       |
| Apa solusinya?                    | Gunakan Y-axis dari 0 atau berikan justifikasi yang jelas, serta tambahkan error bar.     |

---

## Evaluasi Grafik Penelitian

### Bias Check

* [x] Y-axis dimulai dari 0 atau diberi justifikasi
* [x] Error bar ditampilkan
* [x] Semua skenario ditampilkan
* [x] Tidak menggunakan efek 3D
* [x] Tidak ada cherry-picking data

### Hasil Evaluasi

Semua visualisasi yang direncanakan telah memenuhi prinsip visualisasi ilmiah yang objektif dan dapat dipertanggungjawabkan.

---

# Refleksi

Tabel dan grafik memiliki fungsi yang berbeda namun saling melengkapi. Tabel memberikan informasi numerik secara presisi sehingga pembaca dapat mengetahui nilai yang tepat dari setiap metrik. Sebaliknya, grafik membantu pembaca mengenali pola, tren, dan perbedaan antar-skenario secara cepat.

Apabila hanya menggunakan tabel, pola performa sulit dikenali karena pembaca harus membandingkan banyak angka. Sebaliknya, jika hanya menggunakan grafik, informasi numerik detail menjadi hilang. Oleh karena itu penelitian ilmiah membutuhkan keduanya agar hasil dapat dipahami secara menyeluruh.

Dalam praktiknya, grafik yang dibuat tanpa memperhatikan skala sumbu atau tanpa menampilkan error bar dapat menimbulkan interpretasi yang menyesatkan. Oleh karena itu setiap visualisasi harus melalui proses pengecekan bias sebelum digunakan sebagai dasar pengambilan kesimpulan.

---

# Kesimpulan

Penyajian hasil penelitian dilakukan menggunakan kombinasi tabel dan grafik agar data lebih mudah dipahami. Berdasarkan hasil eksperimen, arsitektur Hybrid (Nginx Load Balancing + Redis Caching) menunjukkan performa terbaik dengan Response Time terendah dan Throughput tertinggi. Seluruh visualisasi dirancang mengikuti prinsip visualisasi ilmiah yang objektif, transparan, dan bebas bias sehingga siap digunakan pada tahap analisis statistik berikutnya.
