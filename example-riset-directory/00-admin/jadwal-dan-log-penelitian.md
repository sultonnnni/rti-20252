# Jadwal & Log Pelaksanaan Penelitian

Catatan kronologis pelaksanaan tiap tahap (sumber: riwayat commit git & dokumen `09-docs/tahap-N-*.md`). Tanggal mengikuti `git log`.

## Log Pelaksanaan

| Tanggal | Tahap | Aktivitas | Referensi |
|---|---|---|---|
| 2026-05-10 s.d. 2026-05-12 | Tahap 1 & 2 | Perancangan arsitektur e-learning purwarupa dan skema database; konfigurasi kontainerisasi `docker-compose` untuk Flask v3.0, Nginx v1.25, Redis v7.2, dan MySQL v8.0 secara lokal; verifikasi konektivitas end-to-end[cite: 1]. | [09-docs/tahap-1-arsitektur.md](../09-docs/tahap-1-arsitektur.md), [09-docs/tahap-2-implementasi-environment.md](../09-docs/tahap-2-implementasi-environment.md) |
| 2026-05-13 | Tahap 3 | Penyusunan skrip injeksi beban kerja menggunakan Apache JMeter dengan parameter kontrol tetap (Seed 42) untuk mensimulasikan beban puncak 200 concurrent users selama 10 menit[cite: 1]. | [09-docs/tahap-3-skrip-jmeter.md](../09-docs/tahap-3-skrip-jmeter.md) |
| 2026-05-14 s.d. 2026-05-15 | Tahap 3 | Eksekusi matriks pengujian beban penuh sebanyak 20 run (4 skenario arsitektur × 5 replikasi/run). Pembersihan cache memori RAM dan restart kontainer Docker secara ketat di setiap pergantian run untuk mitigasi validitas internal[cite: 1]. | commit "Mark Tahap 3 complete after running full 20-run JMeter matrix" (2026-05-15) |
| 2026-05-16 | Tahap 4 | Ekstraksi otomatis data numerik performa dari instrumen monitoring Prometheus dan Grafana[cite: 1]; penyusunan pipeline preprocessing data cleaning di Python; perhitungan matematis batas pencilan menggunakan Interquartile Range (IQR)[cite: 1]. | [09-docs/tahap-4-preprocessing-data.md](../09-docs/tahap-4-preprocessing-data.md), [06-output/](06-output/) |
| 2026-05-18 | Tahap 4 | Menjalankan uji statistik komparatif inferensial menggunakan metode One-Way ANOVA menghasilkan nilai signifikansi $p < 0.001$ dan ukuran efek ($\eta^2 = 0.92$)[cite: 1]; dokumentasi failure analysis terhadap data pencilan 135 ms pada Hybrid Run 4 akibat CPU spikes komputer host[cite: 1]. | [09-docs/tahap-4-analisis-statistik.md](../09-docs/tahap-4-analisis-statistik.md) |
| 2026-05-20 s.d. 2026-05-25 | Tahap 5 | Penyusunan draf laporan ilmiah utuh berstruktur IMRAD (Introduction, Method, Results, Discussion); finalisasi visualisasi tabel deskriptif performa Response Time dan Throughput[cite: 1]. | [09-docs/tahap-5-draf-paper.md](../09-docs/tahap-5-draf-paper.md), [08-laporan/UAS_RisetTI_4IKRA_240202850_AhmadSultoni.pdf](../08-laporan/UAS_RisetTI_4IKRA_240202850_AhmadSultoni.pdf)[cite: 1] |

## Status Ringkas

- **Tahap 1–4**: Selesai (dataset final: matriks 20 run / 5 replikasi per kombinasi skenario arsitektur, divalidasi dengan IQR dan One-Way ANOVA)[cite: 1].
- **Tahap 5**: Laporan penelitian ilmiah utuh berformat IMRAD telah selesai disusun secara komprehensif untuk evaluasi UAS mata kuliah Research & Teknologi Informasi (RTI)[cite: 1].

## Item Tindak Lanjut (Checklist Sebelum Submission)

- [x] Lengkapi matriks literatur dengan paper *related work* yang relevan mengenai optimasi Nginx dan Redis[cite: 1].
- [x] Hitung batas sebaran data pencilan secara matematis menggunakan rumus Interquartile Range ($Q1=119$, $Q3=121$, $IQR=2$)[cite: 1].
- [x] Tetapkan bahasa final naskah — **Selesai:** Menggunakan Bahasa Indonesia ilmiah baku sesuai standar publikasi[cite: 1].
- [x] Pindahkan konten laporan ke dalam format lembar jawaban evaluasi CPL/CPMK Fakultas Sains dan Teknologi UPB Kebumen[cite: 1].
- [x] Finalisasi penempatan tabel deskriptif ringkasan kinerja Response Time dan Throughput[cite: 1].
- [x] Review akhir seluruh klaim numerik agar konsisten 100% antar bab (Rata-rata Hybrid: Response Time $120\pm6$ ms, Throughput $850\pm12$ req/sec)[cite: 1].

## Korespondensi & Catatan Bimbingan

Catatan komunikasi, asistensi, dan arahan revisi bersama Dosen Pengampu / Pembimbing Mata Kuliah Research & Teknologi Informasi (RTI) Universitas Putra Bangsa.

| Tanggal | Media / Saluran | Agenda / Topik Bimbingan | Status & Tindak Lanjut |
|---|---|---|---|
| 2026-05-11 | Tatap Muka / Ruang Dosen | Diskusi penentuan skenario eksperimen ablasi (4 skenario infrastruktur) dan parameter injeksi beban JMeter[cite: 1]. | **Disetujui:** Melanjutkan ke tahap isolasi server aplikasi berbasis Docker kontainer[cite: 1]. |
| 2026-05-15 | WhatsApp / Online | Laporan penyelesaian 20 run data mentah dan temuan unpredicted finding bahwa skenario LB Only bekerja lebih responsif dibanding Cache Only[cite: 1]. | **Arahan Dosen:** Analisis logika pemrosesan routing Flask secara mendalam pada bab pembahasan untuk menjelaskan fenomena tersebut[cite: 1]. |
| 2026-05-19 | Google Meet | Konsultasi hasil uji normalitas data dan One-Way ANOVA ($p < 0.001$) serta penanganan jujur terhadap outlier Run 4[cite: 1]. | **Disetujui:** Pendekatan Open Data dan transparansi anomali dinilai sangat baik untuk etika penelitian[cite: 1]. |
| 2026-05-25 | Tatap Muka / Lab Komputer | Review akhir draf naskah ujian IMRAD lengkap dengan identitas Ahmad Sultoni (NIM: 240202850) sebelum dikompilasi menjadi dokumen PDF akhir[cite: 1]. | **ACC Akhir:** Laporan dinyatakan valid, memenuhi seluruh capaian CPL/CPMK, dan siap dikumpulkan[cite: 1]. |
