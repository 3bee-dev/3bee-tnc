# 24. Lampiran D. Jadwal Tingkat Layanan, Pemeliharaan, dan Dukungan

- Path Dokumen: [docs/platform-legal/annexes/annex-d-service-level-and-support.id.md](./annex-d-service-level-and-support.id.md)
- Path Dokumen Bahasa Pendamping: [docs/platform-legal/annexes/annex-d-service-level-and-support.en.md](./annex-d-service-level-and-support.en.md)
- Path Dokumen Perjanjian Induk: [docs/platform-legal/terms-and-conditions.id.md](../terms-and-conditions.id.md#24-lampiran-d-jadwal-tingkat-layanan-pemeliharaan-dan-dukungan)
- Path Dokumen Daftar Isi: [docs/platform-legal/TOC.id.md](../TOC.id.md#24-lampiran-d-jadwal-tingkat-layanan-pemeliharaan-dan-dukungan)

### 24.1. Target Ketersediaan Layanan dan Pengecualian

24.1.1. Sesuai dengan [Pasal 14 Perjanjian (docs/platform-legal/terms-and-conditions.id.md)](../terms-and-conditions.id.md#14-pasal-14-ketersediaan-layanan-pemeliharaan-pembaruan-dan-dukungan-pelanggan), Penyedia menargetkan ketersediaan Platform bulanan sebesar [UPTIME TARGET, e.g., 99.0%] untuk Dasbor Utama dan lingkungan waktu jalan Agen AI yang diterapkan selama setiap bulan kalender.

24.1.2. Perhitungan ketersediaan mengecualikan ketidaktersediaan atau penurunan kinerja yang diakibatkan oleh:
(a) Pemeliharaan Terjadwal yang diberitahukan sesuai dengan Pasal 24.2.
(b) Pemeliharaan darurat atau mitigasi keamanan berdasarkan [Pasal 14.2 Perjanjian](../terms-and-conditions.id.md#142-pemeliharaan-darurat-perbaikan-keamanan-dan-pembaruan-fitur).
(c) Gangguan, batas laju, perubahan antarmuka, atau keterlambatan webhook pada WhatsApp, Telegram, atau penyedia Model AI pihak ketiga di sisi hulu.
(d) Habisnya Kuota Paket Bulanan, Kumpulan Kredit Bulanan, atau Saldo Kredit milik Pelanggan, atau terpicunya Batas Laju Sesi Pengunjung yang dikonfigurasi oleh Pelanggan.
(e) Penangguhan langganan atau Agen AI milik Pelanggan akibat keterlambatan pembayaran ([Pasal 7 Perjanjian](../terms-and-conditions.id.md#7-pasal-7-keterlambatan-pembayaran-masa-tenggang-penangguhan-pembatalan-dan-penyimpanan-data)) atau pelanggaran Penggunaan yang Dapat Diterima ([Pasal 8](../terms-and-conditions.id.md#8-pasal-8-kewajiban-pelanggan-penggunaan-yang-dapat-diterima-dan-tindakan-terlarang) dan [Pasal 18 Perjanjian](../terms-and-conditions.id.md#18-pasal-18-jangka-waktu-penangguhan-administratif-pengakhiran-dan-keberlangsungan-pasal), serta [Lampiran B (docs/platform-legal/annexes/annex-b-acceptable-use-and-uploads.id.md)](./annex-b-acceptable-use-and-uploads.id.md)).
(f) Kesalahan pada situs web eksternal milik Pelanggan sendiri yang memuat Widget Situs Web, token Kanal Pihak Ketiga tidak sah yang dimasukkan oleh Pelanggan, atau peristiwa Keadaan Kahar berdasarkan [Pasal 20.4 Perjanjian](../terms-and-conditions.id.md#204-keadaan-kahar).

24.1.3. [LAWYER DECISION: Confirm whether the Provider offers service credits (and if so, the exact credit percentage and claim procedure) if monthly availability falls below [UPTIME TARGET], or whether availability targets are non-credit operational objectives.]

### 24.2. Jendela Pemeliharaan dan Prosedur Pemberitahuan

24.2.1. Pemeliharaan Terjadwal rutin diutamakan untuk dilaksanakan pada jam tidak sibuk ([PREFERRED MAINTENANCE WINDOW, e.g., 00:00 to 05:00 Western Indonesia Time / WIB]) dengan pemberitahuan sekurang-kurangnya [MAINTENANCE NOTICE HOURS, e.g., twenty-four (24) hours] sebelumnya melalui Dasbor Utama atau surat elektronik.

### 24.3. Tingkatan Keparahan Dukungan dan Target Waktu Tanggap

24.3.1. Pelanggan dapat menyampaikan pertanyaan dukungan melalui kanal resmi berikut selama [SUPPORT OPERATING HOURS, e.g., Monday to Friday, 09:00 to 18:00 WIB, excluding Indonesian public holidays]:
(a) Surat Elektronik: [SUPPORT EMAIL]
(b) Dukungan WhatsApp: [SUPPORT WHATSAPP NUMBER]
(c) Dukungan Telegram: [SUPPORT TELEGRAM HANDLE]

24.3.2. Target waktu tanggap awal selama jam operasional dukungan adalah:
(a) Keparahan Kritis (penghentian total Agen AI yang diterapkan atau hambatan pelunasan pembayaran): Dalam waktu [CRITICAL RESPONSE HOURS, e.g., four (4) business hours].
(b) Keparahan Tinggi (penurunan fungsi utama yang memengaruhi kanal aktif atau akses Ruang Kerja Agen): Dalam waktu [HIGH RESPONSE HOURS, e.g., eight (8) business hours].
(c) Keparahan Normal (pertanyaan umum mengenai konfigurasi, katalog, penagihan, atau pemakaian): Dalam waktu [NORMAL RESPONSE HOURS, e.g., twenty-four (24) business hours].
