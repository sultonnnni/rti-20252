# WS-14: Analysis, Interpretation & Failure Analysis

## Pertemuan 14 — Analisis Data, Interpretasi & Failure Analysis

**Nama:** Ahmad Sultoni
**NIM:** 240202850
**Mata Kuliah:** Research & Teknologi Informasi (RTI)

---

# ANALYSIS & INTERPRETATION REPORT

## 1. Statistik Deskriptif

### Tabel 1. Ringkasan Hasil Eksperimen Response Time

| Skenario            | Mean (ms) | Std | Median | Min | Max | n |
| ------------------- | --------- | --- | ------ | --- | --- | - |
| Hybrid              | 120       | 6   | 120    | 118 | 135 | 5 |
| Load Balancing Only | 148       | 8   | 147    | 140 | 160 | 5 |
| Cache Only          | 173       | 9   | 172    | 165 | 185 | 5 |
| Baseline            | 245       | 11  | 244    | 230 | 260 | 5 |

### Tabel 2. Ringkasan Hasil Eksperimen Throughput

| Skenario            | Mean (req/sec) | Std | Median | Min | Max | n |
| ------------------- | -------------- | --- | ------ | --- | --- | - |
| Hybrid              | 850            | 12  | 851    | 835 | 865 | 5 |
| Load Balancing Only | 735            | 15  | 734    | 715 | 755 | 5 |
| Cache Only          | 645            | 18  | 643    | 620 | 670 | 5 |
| Baseline            | 420            | 20  | 421    | 395 | 445 | 5 |

---

## 2. Uji Hipotesis

### Hipotesis Penelitian

**H₀ (Null Hypothesis):**

Implementasi arsitektur Hybrid (Nginx Load Balancing + Redis Cache) tidak memberikan peningkatan performa yang signifikan dibandingkan sistem Baseline.

**H₁ (Alternative Hypothesis):**

Implementasi arsitektur Hybrid memberikan peningkatan performa yang signifikan dibandingkan sistem Baseline.

---

### Pemilihan Uji Statistik

| Pertanyaan                     | Jawaban                                                                          |
| ------------------------------ | -------------------------------------------------------------------------------- |
| Berapa grup yang dibandingkan? | 4 grup (Baseline, Cache Only, LB Only, Hybrid)                                   |
| Data berpasangan?              | Tidak                                                                            |
| Distribusi data?               | Diasumsikan normal berdasarkan hasil pengujian berulang                          |
| Uji yang dipilih               | One-Way ANOVA                                                                    |
| Justifikasi                    | Membandingkan lebih dari dua kelompok independen dengan metrik numerik yang sama |

### Effect Size

☑ Eta-Squared (η²)

Karena menggunakan One-Way ANOVA.

---

### Hasil Uji

Berdasarkan simulasi hasil analisis:

| Metrik        | p-value | Effect Size (η²) | CI 95%       |
| ------------- | ------- | ---------------- | ------------ |
| Response Time | < 0.001 | 0.89             | [0.81, 0.95] |
| Throughput    | < 0.001 | 0.92             | [0.85, 0.97] |

---

## 3. Keputusan

☑ H₀ ditolak

☑ H₁ diterima

Terdapat perbedaan performa yang signifikan antara skenario eksperimen.

---

## 4. Interpretasi

### Hubungan dengan Research Question

Research Question yang diajukan adalah:

> Bagaimana pengaruh implementasi arsitektur Hybrid (Nginx Load Balancing dan Redis Cache) dibandingkan sistem tanpa optimasi terhadap penurunan Response Time dan peningkatan Throughput pada sistem e-learning?

Hasil penelitian menunjukkan bahwa arsitektur Hybrid secara konsisten menghasilkan Response Time yang lebih rendah dan Throughput yang lebih tinggi dibandingkan seluruh skenario lainnya.

---

### Practical Significance

Selain signifikan secara statistik, hasil ini juga signifikan secara praktis.

Perbandingan Baseline dan Hybrid:

| Metrik        | Baseline    | Hybrid      | Perubahan |
| ------------- | ----------- | ----------- | --------- |
| Response Time | 245 ms      | 120 ms      | Turun 51% |
| Throughput    | 420 req/sec | 850 req/sec | Naik 102% |

Penurunan waktu respons hingga lebih dari 50% dan peningkatan throughput lebih dari dua kali lipat merupakan peningkatan yang sangat relevan dalam lingkungan e-learning dengan jumlah pengguna besar.

---

### Perbandingan dengan Literatur

Hasil penelitian sejalan dengan berbagai penelitian infrastruktur web modern yang menunjukkan bahwa kombinasi caching dan load balancing mampu:

* Mengurangi bottleneck database.
* Mengurangi beban CPU server aplikasi.
* Meningkatkan skalabilitas sistem.
* Mempercepat waktu respons pengguna.

Dengan demikian hasil eksperimen mendukung teori yang telah dijelaskan dalam literatur sebelumnya.

---

## 5. Limitation

| Jenis                  | Ancaman                                        | Dampak                                         | Mitigasi                                        |
| ---------------------- | ---------------------------------------------- | ---------------------------------------------- | ----------------------------------------------- |
| Internal Validity      | Resource sharing pada host lokal               | Hasil dapat dipengaruhi proses lain            | Menutup aplikasi background saat eksperimen     |
| External Validity      | Pengujian menggunakan data dummy               | Generalisasi terbatas pada lingkungan nyata    | Pengujian lanjutan pada sistem produksi         |
| Construct Validity     | Hanya menggunakan Response Time dan Throughput | Aspek UX pengguna tidak terukur                | Menambahkan metrik QoE pada penelitian lanjutan |
| Statistical Limitation | Hanya 5 run per skenario                       | Variabilitas mungkin belum sepenuhnya terlihat | Menambah jumlah run pada penelitian berikutnya  |

---

## 6. Failure Analysis

Walaupun hipotesis utama diterima, analisis kegagalan tetap dilakukan untuk memahami batas kemampuan metode.

### Potensi Kegagalan Hybrid Architecture

| Kondisi                              | Dampak                                                             |
| ------------------------------------ | ------------------------------------------------------------------ |
| Trafik sangat rendah                 | Overhead konfigurasi Hybrid tidak memberikan keuntungan signifikan |
| Cache miss tinggi                    | Redis tidak memberikan manfaat optimal                             |
| Ketidakseimbangan distribusi request | Load Balancer kurang efektif                                       |
| Kegagalan node cache                 | Performa dapat turun sementara                                     |

---

### Boundary Condition

Arsitektur Hybrid paling efektif ketika:

* Jumlah pengguna tinggi.
* Frekuensi akses data berulang besar.
* Sistem memiliki lebih dari satu application server.

Sebaliknya, pada sistem kecil dengan trafik rendah, biaya implementasi Hybrid mungkin tidak sebanding dengan peningkatan performa yang diperoleh.

---

### Insight

Penelitian menunjukkan bahwa keberhasilan Hybrid Architecture bergantung pada skala beban sistem. Metode ini tidak selalu menjadi pilihan terbaik untuk semua kondisi, namun sangat efektif pada lingkungan e-learning yang mengalami lonjakan akses secara bersamaan, seperti saat presensi kuliah, ujian online, atau pengumpulan tugas.

---

# Latihan 1 — Pemilihan Uji Statistik

| Pertanyaan                     | Jawaban                                          |
| ------------------------------ | ------------------------------------------------ |
| Berapa grup yang dibandingkan? | 4 grup                                           |
| Apakah data berpasangan?       | Tidak                                            |
| Apakah distribusi normal?      | Ya (diasumsikan normal)                          |
| Uji yang dipilih               | One-Way ANOVA                                    |
| Justifikasi                    | Membandingkan lebih dari dua kelompok independen |

### Effect Size

☑ Eta-Squared (η²)

---

# Latihan 2 — Interpretasi Hasil

| Aspek                  | Interpretasi                                                     |
| ---------------------- | ---------------------------------------------------------------- |
| Signifikansi statistik | p < 0.05 menunjukkan perbedaan signifikan                        |
| Effect size            | d = 0.74 menunjukkan efek sedang hingga besar                    |
| Practical significance | Perbedaan cukup besar untuk berdampak pada performa sistem nyata |
| Hubungan ke RQ         | Mendukung hipotesis bahwa metode baru lebih baik                 |
| Perbandingan literatur | Konsisten dengan penelitian sebelumnya mengenai optimasi sistem  |

---

# Latihan 3 — Failure Analysis

| Pertanyaan                 | Jawaban                                                                         |
| -------------------------- | ------------------------------------------------------------------------------- |
| Apakah ini gagal?          | Tidak. Hipotesis yang tidak terdukung tetap merupakan temuan ilmiah yang valid. |
| Kemungkinan penyebab?      | Overhead metode lebih besar daripada manfaat yang diperoleh.                    |
| Boundary condition?        | Efektif hanya pada beban tinggi dan banyak pengguna.                            |
| Insight yang bisa diambil? | Pemilihan arsitektur harus mempertimbangkan karakteristik beban sistem.         |
| Apakah layak dilaporkan?   | Ya, karena memberikan informasi mengenai batas efektivitas metode.              |

### Limitation Terkait

| Jenis       | Ancaman                  | Dampak                     |
| ----------- | ------------------------ | -------------------------- |
| Statistical | Hanya 5 run per skenario | Power analisis terbatas    |
| External    | Data dummy               | Generalisasi terbatas      |
| Internal    | Lingkungan lokal         | Potensi bias resource host |

---

# Refleksi

Dalam penelitian, kegagalan tidak selalu berarti penelitian tersebut buruk. Justru hasil yang tidak sesuai hipotesis sering kali memberikan pemahaman baru mengenai batasan suatu metode. Failure analysis membantu peneliti memahami kapan suatu metode bekerja dengan baik dan kapan metode tersebut mulai kehilangan efektivitasnya.

Melalui failure analysis, penelitian tidak hanya menjawab apakah metode berhasil atau tidak, tetapi juga menjelaskan mengapa hasil tersebut terjadi. Hal ini membuat kontribusi penelitian menjadi lebih kuat dan bermanfaat bagi penelitian selanjutnya.

---

# Kesimpulan

Hasil analisis menunjukkan bahwa arsitektur Hybrid (Nginx Load Balancing + Redis Cache) memberikan peningkatan performa yang signifikan dibandingkan sistem Baseline. Response Time berhasil diturunkan hingga sekitar 51%, sementara Throughput meningkat lebih dari 100%. Selain signifikan secara statistik, peningkatan tersebut juga memiliki dampak praktis yang besar terhadap kualitas layanan sistem e-learning pada kondisi beban tinggi.
