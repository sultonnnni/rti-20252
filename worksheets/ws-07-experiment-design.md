
# WS-07: Experimental Design & Validity

 Pertemuan 07 — Desain Eksperimen & Validitas Validasi Infrastruktur

 **Nama** : Ahmad Sultoni
 **NIM** : 240202850
 **Mata Kuliah** : Research & Teknologi Informasi (RTI)

---

## Latihan 1 — Desain Eksperimen

**RQ:** Bagaimana pengaruh implementasi arsitektur Hybrid (Load Balancing Nginx & Redis Caching) dibandingkan dengan sistem tanpa optimasi terhadap reduksi *response time* dan peningkatan *throughput* e-learning pada kondisi beban puncak?

**Tipe eksperimen:** [X] Comparison / [X] Ablation / [ ] Parameter

*(Catatan: Riset ini merupakan gabungan **Comparison** untuk membandingkan Hybrid vs Baseline, dan **Ablation** untuk melepas komponen Caching atau LB secara parsial demi mengukur kontribusi masing-masing).*

| Kondisi | Deskripsi | IV Value | CV Settings |
| --- | --- | --- | --- |
| **Control (Baseline)** | Arsitektur standar e-learning komersial umum tanpa modifikasi performa. | Single-Server (1 App Server, No Cache, Direct DB) | Spek VM vCPU/RAM sama, database MySQL identik, injeksi workload via JMeter 200 concurrent users konstan selama 10 menit. |
| **Treatment 1 (Ablation: Cache Only)** | Arsitektur dengan modifikasi pada layer data untuk mereduksi I/O kemacetan DB. | 1 App Server + Redis Cache Aktif | Identik dengan pengaturan kontrol (Spek VM, DB, skrip beban JMeter 200 users, durasi 10 menit). |
| **Treatment 2 (Ablation: LB Only)** | Arsitektur dengan perluasan horizontal untuk membagi beban komputasi CPU. | 2 App Server + Nginx Load Balancer (No Cache) | Identik dengan pengaturan kontrol (Spek VM, DB, skrip beban JMeter 200 users, durasi 10 menit). |
| **Treatment 3 (Proposed: Hybrid)** | Integrasi penuh redundansi jaringan dan akselerasi data secara simultan. | 2 App Server + Nginx LB + Redis Cache Aktif | Identik dengan pengaturan kontrol (Spek VM, DB, skrip beban JMeter 200 users, durasi 10 menit). |

---

## Latihan 2 — Fairness Checklist

Evaluasi keadilan komparasi objek uji dalam arsitektur eksperimen.

| Kriteria | Status | Detail |
| --- | --- | --- |
| **Dataset identik** | ✅ *Passed* | Seluruh skenario menggunakan database MySQL dengan skema, indeks, dan volume data *dummy* yang sama persis (10.000 record data mahasiswa & materi). |
| **Preprocessing setara** | ✅ *Passed* | Tidak ada pembersihan data di layer aplikasi; struktur *payload* JSON permintaan dari JMeter dibuat seragam untuk seluruh kondisi. |
| **Tuning effort setara** | ✅ *Passed* | Nginx menggunakan konfigurasi default untuk alokasi *worker processes*, dan Redis dikunci pada alokasi memori maksimal yang sama di tiap skenario. |
| **Environment identik** | ✅ *Passed* | Semua skenario berjalan di atas arsitektur virtualisasi lokal yang sama (`docker-compose`) dengan batasan *resource* VM yang diisolasi ketat. |
| **Metrik evaluasi sama** | ✅ *Passed* | Seluruh data performa ditarik dari metrik *Latency/Response Time* (ms) dan *Throughput* (req/sec) yang dicatat otomatis oleh Prometheus. |

**Ada yang tidak fair?** [ ] Ya / [X] Tidak

> **Justifikasi perbaikan jika ada:** Semua parameter lingkungan dikunci secara rigid. Satu-satunya komponen yang berubah antar sesi pengujian hanyalah status aktif/nonaktif dari konfigurasi kontainer Nginx dan Redis (IV murni).

---

## Latihan 3 — Threat Analysis

Analisis ancaman terhadap validitas kesimpulan eksperimen.

| Threat Type | Ancaman Spesifik | Mitigasi |
| --- | --- | --- |
| **Internal** | *Resource borrowing* atau fluktuasi CPU spikes pada komputer host yang mengacaukan kalkulasi waktu respon. | Menjalankan eksperimen pada kondisi sistem host bersih dari aplikasi background, mengisolasi core CPU core via Docker runtime, dan melakukan *warm-up* sistem selama 2 menit sebelum pencatatan log dimulai. |
| **External** | Karakteristik trafik dari generator JMeter terlalu linear dan mekanis, sehingga kurang merepresentasikan sifat trafik acak mahasiswa asli. | Menggunakan fitur *Gaussian Random Timer* pada JMeter untuk menyuntikkan *delay* acak manusia saat mengakses menu e-learning. |
| **Construct** | Pengukuran *Response Time* rata-rata (*Average*) menutupi anomali lonjakan eror sesaat (*outliers*). | Menambahkan metrik *Percentile Latency* (p95 dan p99) di Grafana untuk menangkap fluktuasi riil sistem saat mencapai batas hancur. |
| **Conclusion** | Jumlah pengujian (*run*) terlalu sedikit sehingga variasi data dianggap kebetulan secara statistik. | Melakukan pengulangan (*replika*) sebanyak 10 kali pengujian mandiri untuk setiap skenario, kemudian menarik nilai tengahnya. |

**Ancaman mana yang paling sulit dimitigasi?** External Validity (Validitas Eksternal).
**Mengapa?**

> Karakteristik beban kerja buatan (*synthetic workload*) dari JMeter di lingkungan lokal tidak akan pernah bisa 100% menduplikasi kompleksitas latensi jaringan internet publik dan perilaku anarki ribuan mahasiswa asli saat berebut presensi di jam sibuk kampus nyata.

---

## Refleksi

> Sebuah paper melaporkan "metode kami mengalahkan semua baseline." Apa 3 pertanyaan pertama yang harus diajukan untuk mengevaluasi klaim ini?

**Jawaban:**

1. **Apakah baseline yang digunakan sudah di-tuning secara optimal?** (Sering terjadi bias di mana baseline sengaja dibiarkan berjalan menggunakan konfigurasi default yang lemah, sementara metode usulan dikonfigurasi habis-habisan agar terlihat superior).
2. **Apakah lingkungan pengujian (*environment*) benar-benar identik?** (Harus dipastikan apakah baseline diuji pada spesifikasi hardware, volume database, dan tingkat kepadatan beban trafik yang sama persis dengan metode yang diusulkan).
3. **Bagaimana distribusi data performanya di luar nilai rata-rata?** (Harus diverifikasi apakah keunggulan tersebut konsisten di level tinggi persentil trafik seperti p95/p99, atau hanya unggul secara rata-rata matematika akibat manipulasi data pencilan/*outliers*).
