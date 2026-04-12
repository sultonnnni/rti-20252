# WS-02: Problem Statement

## Bab 2 — Problem Formulation & System Context

**Nama** : Ahmad Sultoni
**NIM** : 240202850
**Mata Kuliah** : Research & Teknologi Informasi (RTI)

---

# Template A.2 — Problem Statement Builder

## Domain & Konteks

Domain : Sistem Informasi / Web Application Performance
Konteks : Aplikasi e-learning berbasis web pada lingkungan kampus

---

## System Context

Input :
Request pengguna saat membuka halaman materi atau tugas

Process :
Server memproses request, mengambil data dari database, lalu mengirimkan halaman ke pengguna

Output :
Halaman e-learning ditampilkan kepada pengguna

Outcome :
Pengguna dapat mengakses materi dengan cepat dan nyaman

Constraints :
Keterbatasan server, jaringan internet pengguna, dan desain sistem aplikasi

Stakeholders :
Mahasiswa, dosen, dan pengelola sistem e-learning

---

## Fenomena → Problem

Fenomena yang diamati :
Mahasiswa sering mengeluhkan akses e-learning yang lambat terutama saat jam sibuk

Gejala (symptom) yang terukur :
Waktu loading halaman lebih dari 5 detik saat banyak pengguna mengakses

Masalah yang didiagnosis :
Sistem belum optimal dalam menangani banyak request secara bersamaan

Masalah riset (researchable) :
Belum ada evaluasi performa sistem e-learning terhadap metode optimasi server tertentu

Variabel yang terukur :
Response time, throughput, CPU usage, dan jumlah concurrent user

---

## Problem Quality Check

[x] Clarity — Apakah satu orang membaca akan paham?
[x] Measurability — Apakah ada metrik kuantitatif?
[x] Relevance — Apakah penting untuk domain?
[x] Testability — Apakah bisa gagal?
[x] Impact — Apakah ada kontribusi jika terjawab?

---

## Problem Statement (1 paragraf)

Aplikasi e-learning berbasis web sering mengalami penurunan performa ketika diakses oleh banyak pengguna secara bersamaan, terutama pada jam kuliah. Hal ini ditunjukkan dengan meningkatnya waktu loading halaman yang melebihi 5 detik. Kondisi tersebut mengindikasikan bahwa sistem belum mampu menangani beban pengguna secara optimal. Oleh karena itu, diperlukan penelitian untuk mengevaluasi performa sistem e-learning dan menguji metode optimasi server guna meningkatkan response time dan stabilitas sistem.

---

# Latihan 1 — Dari Topik ke Masalah Riset

Topik awal:
Optimasi Performa Sistem E-learning

| Tahap                          | Hasil                                                     |
| ------------------------------ | --------------------------------------------------------- |
| Reality                        | Mahasiswa sering mengakses e-learning secara bersamaan    |
| Observed Issue (Symptom)       | Sistem e-learning menjadi lambat                          |
| Diagnosed Problem (Root Cause) | Server tidak mampu menangani banyak request               |
| Researchable Problem           | Belum ada evaluasi metode optimasi server pada e-learning |
| Measurable Variable            | Response time, throughput, CPU usage                      |

Apakah terjebak solution-first thinking?
[ ] Ya
[x] Tidak

## Jika ya, kembali ke tahap mana?

---

# Latihan 2 — System Context Decomposition

| Komponen     | Deskripsi                       |
| ------------ | ------------------------------- |
| Input        | Request pengguna                |
| Process      | Pengolahan request oleh server  |
| Output       | Halaman e-learning              |
| Outcome      | Pengguna dapat mengakses sistem |
| Constraints  | Server terbatas                 |
| Stakeholders | Mahasiswa dan dosen             |

Komponen mana yang paling relevan dengan masalah riset?
Process dan Constraints

---

# Latihan 3 — Problem Quality Check

| Kriteria      | Skor (1-5) | Justifikasi                    |
| ------------- | ---------- | ------------------------------ |
| Clarity       | 5          | Masalah jelas dan spesifik     |
| Measurability | 5          | Ada metrik performa            |
| Relevance     | 5          | Masalah nyata di e-learning    |
| Testability   | 4          | Bisa diuji dengan eksperimen   |
| Impact        | 5          | Berdampak pada banyak pengguna |

Skor total:
24 / 25

---

## Problem statement versi final (1 paragraf)

Sistem e-learning berbasis web sering mengalami penurunan performa ketika diakses oleh banyak pengguna secara bersamaan. Hal ini terlihat dari meningkatnya waktu respon yang melebihi batas normal. Kondisi tersebut menunjukkan bahwa sistem belum mampu menangani beban pengguna secara optimal. Oleh karena itu, penelitian ini bertujuan untuk mengevaluasi performa sistem dan menguji metode optimasi server untuk meningkatkan stabilitas dan kecepatan akses.

---

# Refleksi

Masalah dalam coding biasanya fokus pada memperbaiki error agar sistem bisa berjalan kembali. Sedangkan dalam penelitian, masalah tidak hanya tentang memperbaiki, tetapi juga memahami penyebab dan membuktikannya secara ilmiah. Penelitian membutuhkan batasan yang jelas dan variabel yang terukur, sedangkan coding lebih fokus pada solusi praktis. Perbedaan ini membuat pendekatan dalam penelitian menjadi lebih sistematis dan terstruktur dibandingkan dengan penyelesaian masalah saat coding.
