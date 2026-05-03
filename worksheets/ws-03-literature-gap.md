# WS-03: Literature Mapping & Gap

> Bab 3 — Literature Review, Research Gap & Baseline

**Nama** : Ahmad Sultoni  
**NIM** : 240202850  
**Mata Kuliah** : Research & Teknologi Informasi (RTI)  

---

## LITERATURE MAPPING

**Topik**      : Optimasi Performa Sistem E-learning Berbasis Web  
**Database**   : Google Scholar  
**Query**      : "web application performance" AND "e-learning" AND ("caching" OR "load balancing")  
**Tahun**      : 2020–2024  
**Hasil awal** : ±28 paper → screening → 6 paper relevan  

---

## Literature Matrix (Concept-Centric)

| Study | Tahun | Method | Data | Result | Limitation |
|-------|------|--------|------|--------|------------|
| Zhang et al. | 2023 | Load Balancing | Simulasi traffic | Response time turun ±30% | Tidak diuji di sistem nyata |
| Kumar et al. | 2022 | Caching (Redis) | Log server web | Latency menurun signifikan | Skala pengujian kecil |
| Lee et al. | 2021 | CDN Optimization | Traffic global | Throughput meningkat | Tidak spesifik e-learning |
| Ahmad et al. | 2022 | Auto Scaling | Simulasi cloud | CPU lebih stabil | Tidak bahas biaya & efisiensi |
| Chen et al. | 2024 | Hybrid (Caching + LB) | Dataset sintetis | Performa meningkat | Dataset tidak realistis |
| Rahman et al. | 2023 | Queue Management | Request dataset | Delay berkurang | Tidak diuji pada beban tinggi |

---

## Pola yang ditemukan

**Metode dominan**  
Sebagian besar penelitian menggunakan load balancing dan caching untuk mengatasi bottleneck pada server.

**Dataset yang digunakan**  
Mayoritas masih menggunakan data simulasi atau sintetis.

**Limitasi yang berulang**  
- Tidak diuji pada kondisi nyata  
- Beban pengguna tidak mencerminkan jam sibuk  
- Tidak spesifik pada sistem e-learning  

---

## GAP IDENTIFICATION

### Gap 1 — Data & Context Gap

**Deskripsi**  
Sebagian besar penelitian masih menggunakan dataset simulasi, sehingga belum merepresentasikan kondisi nyata sistem e-learning di lingkungan kampus.

**Bukti**  
Dari 6 paper, 5 menggunakan data simulasi atau sintetis.

**Signifikansi**  
Hasil penelitian berpotensi tidak akurat saat diterapkan langsung pada sistem nyata.

---

### Gap 2 — Method Gap

**Deskripsi**  
Belum banyak penelitian yang membandingkan langsung metode optimasi seperti caching dan load balancing dalam satu skenario yang sama.

**Bukti**  
Hanya satu paper yang menggunakan pendekatan hybrid, namun masih berbasis dataset sintetis.

**Signifikansi**  
Belum jelas metode mana yang paling efektif dalam kondisi beban tinggi.

---

## Gap utama yang dipilih

**Data Gap + Method Gap**

---

## Kenapa gap ini penting?

Masalah performa e-learning biasanya muncul saat jam sibuk, tetapi penelitian sebelumnya belum menguji kondisi tersebut secara realistis. Selain itu, belum ada perbandingan metode optimasi dalam kondisi yang sama, sehingga solusi yang ada belum tentu cocok diterapkan di lingkungan kampus.

---

## BASELINE SELECTION

| Baseline | Relevansi | Representatif | Source |
|----------|----------|--------------|--------|
| Load Balancing | Menangani banyak request | Umum di sistem web | Zhang et al., 2023 |
| Caching (Redis) | Mempercepat akses data | Banyak digunakan | Kumar et al., 2022 |

---

## Apakah termasuk straw man?

**Tidak**

**Justifikasi**  
Metode yang digunakan merupakan praktik umum dalam pengembangan sistem web, sehingga perbandingan tetap adil.

---

## REFLEKSI

Perbedaan antara klaim “belum ada yang meneliti ini” dengan research gap yang valid terletak pada bukti. Klaim tanpa bukti hanya asumsi, sedangkan gap harus didukung oleh analisis beberapa penelitian sebelumnya.

Untuk membuktikan gap, perlu ditunjukkan bahwa ada pola keterbatasan yang sama, seperti penggunaan dataset yang tidak realistis atau metode yang belum dibandingkan secara langsung. Dari situ dapat disimpulkan bahwa masih ada ruang untuk penelitian lanjutan.
