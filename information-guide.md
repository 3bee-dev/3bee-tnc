# Panduan Pengisian Placeholder Dokumen Hukum (Information Guide)

Repository Path: [information-guide.md](./information-guide.md)  
Repositori Utama: [3bee-dev/3bee-tnc](https://github.com/3bee-dev/3bee-tnc)  
Dokumen Terkait:
- [terms-and-conditions.id.md](./terms-and-conditions.id.md) (Syarat dan Ketentuan Layanan - Bahasa Indonesia)
- [terms-and-conditions.en.md](./terms-and-conditions.en.md) (Terms and Conditions of Service - English)
- [TOC.id.md](./TOC.id.md) | [TOC.en.md](./TOC.en.md) (Daftar Isi / Table of Contents)
- [fact-sheet.md](./fact-sheet.md) (Lembar Fakta Teknis & Operasional Platform)
- [clause-function-map.md](./clause-function-map.md) (Pemetaan Fungsi Klausul & Daftar Keputusan Pengacara)

---

## Pendahuluan

Dokumen ini merupakan panduan praktis berbahasa Indonesia yang menjelaskan setiap teks placeholder bertanda kurung siku (`[...]`) dan penanda keputusan pengacara (`[LAWYER DECISION: ...]`) yang terdapat pada seluruh berkas dokumen hukum Platform 3Bee.

Sebelum dokumen hukum (`terms-and-conditions.id.md`, `terms-and-conditions.en.md`, dan seluruh lampiran di folder `annexes/`) dipublikasikan atau ditandatangani secara resmi, seluruh tanda kurung siku `[...]` wajib diganti dengan informasi bisnis, identitas badan hukum, alamat, kontak, dan parameter operasional yang sebenarnya.

---

## 1. Identitas Hukum & Legalitas Badan Hukum Penyedia

[COMPANY LEGAL NAME] : Masukkan nama resmi badan hukum perseroan yang bertindak sebagai pemilik dan pengelola Platform 3Bee sebagaimana tertera pada Akta Pendirian Perusahaan dan Surat Keputusan (SK) Pengesahan dari Kementerian Hukum dan Hak Asasi Manusia Republik Indonesia (Kemenkumham). Pada antarmuka situs landing page, nama yang ditampilkan adalah PT 3Bee Indonesia.  
*Contoh pengisian:* `PT 3Bee Indonesia Teknologi` atau `PT 3Bee Kecerdasan Buatan Indonesia`.

[COMPANY REGISTRATION NUMBER / NIB] : Masukkan Nomor Induk Berusaha (NIB) 13 digit yang diterbitkan oleh sistem Online Single Submission (OSS) Kementerian Investasi / BKPM Republik Indonesia, dan/atau nomor pengesahan Akta Notaris AHU dari Ditjen AHU Kemenkumham RI. NIB berfungsi sebagai tanda daftar perusahaan (TDP), izin usaha, dan akses kepabeanan resmi.  
*Contoh pengisian:* `NIB: 1234567890123 (SK Kemenkumham No. AHU-0012345.AH.01.01.Tahun 2026)`.

[REGISTERED ADDRESS] : Masukkan alamat domisili resmi kantor terdaftar perseroan lengkap dengan gedung, jalan, nomor, RT/RW, kelurahan, kecamatan, kota/kabupaten, provinsi, dan kode pos sesuai Surat Izin Domisili Usaha atau NIB.  
*Contoh pengisian:* `Gedung Graha 3Bee Lantai 5, Jl. Sutomo No. 9, RT 001 / RW 002, Kelurahan Gambir, Kecamatan Gambir, Kota Jakarta Pusat, DKI Jakarta 10110, Indonesia`.

[INCORPORATION JURISDICTION, e.g., the Republic of Indonesia] : Masukkan yurisdiksi atau negara tempat badan hukum didirikan. Untuk perusahaan berbadan hukum PT (Perseroan Terbatas), isi dengan Republik Indonesia (atau Negara Republik Indonesia pada versi Bahasa Indonesia, dan the Republic of Indonesia pada versi Bahasa Inggris).  
*Contoh pengisian:* `the Republic of Indonesia` (pada versi EN) atau `Negara Republik Indonesia` (pada versi ID).

---

## 2. Kontak Resmi & Saluran Komunikasi Operasional

[LEGAL NOTICE EMAIL] : Masukkan alamat surel (email) khusus yang dialokasikan oleh tim hukum perseroan untuk menerima surat menyurat resmi, pemberitahuan hukum (*legal notice*), klaim hak kekayaan intelektual, permintaan penegak hukum, atau somasi tertulis. Surel ini harus dipantau aktif setiap hari kerja.  
*Contoh pengisian:* `legal@3bee.id` atau `hukum@3bee.tech`.

[SUPPORT EMAIL] : Masukkan alamat surel resmi pusat bantuan layanan pelanggan (*customer support*). Surel ini digunakan pelanggan untuk mengirim tiket kendala teknis, klarifikasi tagihan, laporan keamanan (*security report*), dan permintaan rekonsiliasi pengembalian dana (*refund*).  
*Contoh pengisian:* `support@3bee.id` atau `help@3bee.tech`.

[SUPPORT WHATSAPP NUMBER] : Masukkan nomor akun resmi WhatsApp Business pusat bantuan Platform 3Bee lengkap dengan kode negara (+62). Nomor ini terhubung langsung dengan tim Customer Operations atau bot perbantuan resmi.  
*Contoh pengisian:* `+62 812-3456-7890`.

[SUPPORT TELEGRAM HANDLE] : Masukkan penanda nama pengguna (*username handle*) resmi dari bot atau perwakilan dukungan teknis Platform 3Bee di aplikasi Telegram, diawali dengan tanda `@`.  
*Contoh pengisian:* `@ThreeBeeSupportBot` atau `@3BeeCare`.

[SUPPORT OPERATING HOURS, e.g., Monday to Friday, 09:00 to 18:00 WIB, excluding Indonesian public holidays] : Masukkan jam operasional resmi layanan dukungan pelanggan. Jam operasional ini menentukan penghitungan batas waktu tanggap tiket (*response time*) pada Lampiran D (SLA).  
*Contoh pengisian:* `Senin sampai Jumat, pukul 09.00 sampai 18.00 WIB, tidak termasuk hari libur nasional resmi Republik Indonesia` (versi ID) atau `Monday to Friday, 09:00 to 18:00 WIB, excluding Indonesian public holidays` (versi EN).

---

## 3. Parameter Teknis & Domain Platform

[PLATFORM ROOT DOMAIN] : Masukkan domain utama produksi (*production root domain*) tempat sub-domain Agen AI pelanggan akan dibuat dan dijalankan secara otomatis (format: `<subdomain>.[PLATFORM ROOT DOMAIN]`). Pada berkas konfigurasi internal pengembang terdapat referensi `3bee.umkmate.com`, `3bee.tech`, atau `3bee.dev`.  
*Contoh pengisian:* `3bee.id` atau `3bee.tech` (sehingga Agen AI pelanggan beralamat di `tokoanda.3bee.id`).

[DOCUMENT VERSION, e.g., 1.0] : Masukkan nomor versi semantik dari dokumen Syarat dan Ketentuan Layanan. Nomor versi ini wajib sinkron dengan nilai `LEGAL_TERMS_VERSION` pada basis data backend (`terms_versions`), yang dicatat dalam log persetujuan setiap kali pengguna mendaftar atau menyetujui pembaruan syarat layanan.  
*Contoh pengisian:* `1.0` (untuk rilis awal) atau `1.1` (saat terdapat amandemen).

[EFFECTIVE DATE] : Masukkan tanggal kalender resmi saat dokumen Syarat dan Ketentuan Layanan ini mulai berlaku secara hukum bagi seluruh pengguna baru maupun pengguna lama yang memperbarui persetujuan.  
*Contoh pengisian:* `1 November 2026` (versi ID) atau `November 1, 2026` (versi EN).

---

## 4. Kebijakan Siklus Penagihan, Masa Tenggang, & Retensi Data

[GRACE PERIOD DAYS] : Masukkan durasi jumlah hari kalender untuk Masa Tenggang (*Grace Period*) ketika tagihan perpanjangan langganan berstatus jatuh tempo (*overdue*). Berdasarkan implementasi kode program backend (`BillingGracePeriodDays`), nilai baku adalah tiga (3) hari. Selama masa ini, Agen AI pelanggan tetap aktif berjalan di internet, namun pembuatan Agen AI baru dikunci sementara.  
*Contoh pengisian:* `tiga (3) hari kalender` (versi ID) atau `three (3) calendar days` (versi EN).

[SUSPENSION RETENTION DAYS] : Masukkan durasi jumlah hari kalender untuk Jendela Penyimpanan Data Pasca-Penangguhan (*Suspension Retention Window*) sebelum seluruh basis data per-agen dihapus permanen. Berdasarkan implementasi kode program backend (`BillingSuspendRetentionDays`), nilai baku adalah lima belas (15) hari kalender. Jika tagihan dibayar dalam kurun waktu ini, seluruh wadah Agen AI dan data basis pengetahuan otomatis dipulihkan utuh.  
*Contoh pengisian:* `lima belas (15) hari kalender` (versi ID) atau `fifteen (15) calendar days` (versi EN).

[FINANCIAL RECORD RETENTION YEARS, e.g., ten (10) years] : Masukkan jangka waktu retensi penyimpanan catatan keuangan, riwayat penagihan (*invoices*), mutasi buku besar kredit (*wallet ledger*), dan tanda bukti pembayaran Midtrans. Sesuai Pasal 11 Undang-Undang No. 8 Tahun 1997 tentang Dokumen Perusahaan dan ketentuan peraturan perundang-undangan perpajakan di Indonesia, jangka waktu penyimpanan dokumen keuangan wajib sekurang-kurangnya 10 tahun.  
*Contoh pengisian:* `sepuluh (10) tahun` (versi ID) atau `ten (10) years` (versi EN).

[REFUND POLICY] : Masukkan tautan atau ringkasan aturan kebijakan pengembalian dana (*refund*). Platform 3Bee tidak menyediakan tombol pengembalian dana otomatis mandiri; seluruh kelebihan bayar, kegagalan transaksi, atau pembayaran ganda dicatat dalam tabel audit `refund_transactions` dan ditangani secara manual oleh tim keuangan melalui surel bantuan.  
*Contoh pengisian:* `Kebijakan Pengembalian Dana 3Bee yang menyatakan bahwa biaya paket langganan yang telah aktif digunakan bersifat non-refundable (tidak dapat dikembalikan), kecuali terjadi pembayaran ganda atau anomali sistem gerbang pembayaran yang diverifikasi oleh Penyedia dalam waktu empat belas (14) hari kerja`.

---

## 5. SLA, Pemeliharaan Sistem, & Penanganan Insiden

[UPTIME TARGET, e.g., 99.0%] : Masukkan target komitmen ketersediaan layanan (*monthly uptime availability target*) untuk Dasbor Utama dan runtime komputasi Agen AI. Angka ini merupakan sasaran operasional bulanan di luar jendela pemeliharaan berkala atau gangguan penyedia hulu (cloud hosting, model AI pihak ketiga, atau Meta/Telegram).  
*Contoh pengisian:* `99,0%` (versi ID) atau `99.0%` (versi EN).

[MAINTENANCE NOTICE HOURS, e.g., twenty-four (24) hours] : Masukkan batas waktu pemberitahuan awal minimum kepada pelanggan sebelum dimulainya jendela pemeliharaan sistem terencana (*scheduled maintenance*) yang dapat menimbulkan jeda layanan sementara.  
*Contoh pengisian:* `dua puluh empat (24) jam` (versi ID) atau `twenty-four (24) hours` (versi EN).

[PREFERRED MAINTENANCE WINDOW, e.g., 00:00 to 05:00 Western Indonesia Time / WIB] : Masukkan rentang waktu jam pemeliharaan terjadwal yang dipilih pada jam-jam dengan beban lalu lintas terendah (*off-peak hours*).  
*Contoh pengisian:* `pukul 00.00 sampai 05.00 Waktu Indonesia Barat (WIB)` (versi ID) atau `00:00 to 05:00 Western Indonesia Time (WIB)` (versi EN).

[CRITICAL RESPONSE HOURS, e.g., four (4) business hours] : Masukkan target durasi waktu tanggap mula (*first response time target*) dari tim bantuan teknis untuk kendala tingkat Keparahan Kritis (seluruh sistem dasbor tidak dapat diakses atau seluruh Agen AI berhenti serentak).  
*Contoh pengisian:* `empat (4) jam kerja operasional` (versi ID) atau `four (4) business hours` (versi EN).

[HIGH RESPONSE HOURS, e.g., eight (8) business hours] : Masukkan target waktu tanggap mula untuk kendala tingkat Keparahan Tinggi (sebagian fitur inti mengalami malafungsi, seperti kegagalan pembuatan gambar Virtual Try-On atau kegagalan webhook pesan WhatsApp).  
*Contoh pengisian:* `delapan (8) jam kerja operasional` (versi ID) atau `eight (8) business hours` (versi EN).

[NORMAL RESPONSE HOURS, e.g., twenty-four (24) business hours] : Masukkan target waktu tanggap mula untuk kendala tingkat Keparahan Normal atau Rendah (pertanyaan umum, permintaan bantuan panduan konfigurasi, atau saran fitur).  
*Contoh pengisian:* `dua puluh empat (24) jam kerja operasional` (versi ID) atau `twenty-four (24) business hours` (versi EN).

[INCIDENT NOTIFICATION WINDOW HOURS, e.g., seventy-two (72) hours] : Masukkan batas waktu maksimum penyampaian pemberitahuan tertulis kepada Pelanggan setelah terkonfirmasinya insiden kebocoran Data Pribadi (*Personal Data breach*). Batas waktu ini diatur secara tegas dalam Pasal 46 Undang-Undang No. 27 Tahun 2022 tentang Pelindungan Data Pribadi (UU PDP), yaitu paling lambat 3 x 24 jam (72 jam).  
*Contoh pengisian:* `tujuh puluh dua (72) jam (3 x 24 jam)` (versi ID) atau `seventy-two (72) hours` (versi EN).

---

## 6. Batas Tanggung Jawab, Amandemen, & Pengakhiran

[AMENDMENT NOTICE DAYS, e.g., fourteen (14) calendar days] : Masukkan batas waktu pemberitahuan dini minimum kepada pelanggan sebelum perubahan material pada Syarat dan Ketentuan Layanan mulai diberlakukan secara efektif.  
*Contoh pengisian:* `empat belas (14) hari kalender` (versi ID) atau `fourteen (14) calendar days` (versi EN).

[BREACH CURE PERIOD DAYS, e.g., fourteen (14) calendar days] : Masukkan durasi waktu perbaikan (*cure period*) yang diberikan kepada pihak yang melakukan wanprestasi atau pelanggaran material atas perjanjian, terhitung sejak diterimanya surat teguran tertulis sebelum perjanjian dapat diakhiri secara sepihak.  
*Contoh pengisian:* `empat belas (14) hari kalender` (versi ID) atau `fourteen (14) calendar days` (versi EN).

[FORCE MAJEURE TERMINATION DAYS, e.g., thirty (30) consecutive calendar days] : Masukkan batas durasi peristiwa Keadaan Kahar (*Force Majeure*) berkepanjangan (seperti perang, bencana alam berskala besar, atau pemutusan internet nasional) yang menghalangi pelaksanaan kewajiban platform secara terus menerus, di mana salah satu pihak berhak mengakhiri langganan tanpa dikenakan ganti rugi.  
*Contoh pengisian:* `tiga puluh (30) hari kalender berturut-turut` (versi ID) atau `thirty (30) consecutive calendar days` (versi EN).

[LIABILITY CAP AMOUNT, e.g., one hundred percent (100%) of the total Subscription Plan fees actually paid by the Customer to the Provider during the twelve (12) months immediately preceding the event giving rise to liability, or if the Agreement has been in effect for less than twelve (12) months, the total Subscription Plan fees actually paid by the Customer to the Provider prior to such event] : Masukkan formula atau batasan nominal maksimum batas tanggung jawab keuangan agregat (*aggregate liability cap*) Penyedia atas klaim ganti rugi perdata dari Pelanggan. Standar industri SaaS B2B yang wajar dan seimbang adalah dibatasi sebesar 100% dari total biaya paket langganan yang telah dibayarkan oleh Pelanggan kepada Penyedia dalam kurun waktu 12 bulan terakhir sebelum timbulnya klaim.  
*Contoh pengisian:* `seratus persen (100%) dari total biaya Paket Langganan yang secara nyata telah dibayarkan oleh Pelanggan kepada Penyedia selama kurun waktu dua belas (12) bulan tepat sebelum terjadinya peristiwa yang mendasari timbulnya tanggung jawab hukum, atau apabila Perjanjian telah berlaku kurang dari dua belas (12) bulan, sebesar total biaya Paket Langganan yang secara nyata telah dibayarkan sebelum peristiwa tersebut` (versi ID).

[SUPER-CAP MULTIPLIER, e.g., two (2) times] : Masukkan angka pengali batas pertanggungjawaban super (*super-cap multiplier*) jika pengacara perseroan memutuskan klausul ganti rugi kekayaan intelektual (Pasal 16) dan pelanggaran kerahasiaan (Pasal 13) tidak dikecualikan tanpa batas, melainkan dibatasi hingga batas tanggung jawab khusus (misalnya 2 kali atau 3 kali lipat dari batas tanggung jawab umum).  
*Contoh pengisian:* `dua (2) kali` (versi ID) atau `two (2) times` (versi EN).

---

## 7. Yurisdiksi, Penyelesaian Sengketa, & Bahasa Kontrak

[GOVERNING LAW JURISDICTION, e.g., the Republic of Indonesia] : Masukkan hukum negara yang mengatur penafsiran dan pelaksanaan Perjanjian Layanan ini.  
*Contoh pengisian:* `Negara Republik Indonesia` (versi ID) atau `the Republic of Indonesia` (versi EN).

[NEGOTIATION PERIOD DAYS, e.g., thirty (30) calendar days] : Masukkan durasi waktu wajib dilakukannya musyawarah untuk mufakat secara damai dan beritikad baik sebelum salah satu pihak diperkenankan mengajukan gugatan ke pengadilan atau lembaga arbitrase.  
*Contoh pengisian:* `tiga puluh (30) hari kalender` (versi ID) atau `thirty (30) calendar days` (versi EN).

[GOVERNING COURT OR ARBITRATION BODY] : Masukkan forum penyelesaian sengketa akhir yang disepakati untuk memeriksa dan memutus perselisihan yang tidak dapat diselesaikan melalui musyawarah. Pilihan dapat berupa Pengadilan Negeri (misal: Pengadilan Negeri Jakarta Pusat) atau lembaga arbitrase yang mengikat (misal: Badan Arbitrase Nasional Indonesia / BANI).  
*Contoh pengisian:* `Pengadilan Negeri Jakarta Pusat` (versi ID) atau `the District Court of Central Jakarta (Pengadilan Negeri Jakarta Pusat)` (versi EN).

[PREVAILING LANGUAGE, e.g., Indonesian] : Masukkan bahasa yang dimenangkan apabila timbul perbedaan penafsiran atau pertentangan antara teks Bahasa Indonesia dan teks Bahasa Inggris. Berdasarkan ketentuan Pasal 31 Undang-Undang No. 24 Tahun 2009 tentang Bendera, Bahasa, dan Lambang Negara, serta Lagu Kebangsaan juncto Peraturan Presiden No. 63 Tahun 2019, perjanjian yang melibatkan pihak atau badan hukum Indonesia wajib menggunakan Bahasa Indonesia dan Bahasa Indonesia dimenangkan untuk memitigasi risiko pembatalan demi hukum oleh pengadilan Indonesia.  
*Contoh pengisian:* `Bahasa Indonesia` (versi ID) atau `Indonesian` (versi EN).

---

## 8. Panduan Khusus Keputusan Pengacara (Lawyer Decisions)

Bagian ini memuat panduan bagi Penasihat Hukum Perusahaan (*Legal Counsel*) dalam menelaah dan menetapkan 7 butir keputusan hukum (*Lawyer Decisions*) yang ditandai dengan `[LAWYER DECISION: ...]`:

### LD-1: Penanganan Pemotongan Pajak PPh Pasal 23 & Prosedur Faktur Pajak (Pasal 6.4.2)
- **Teks Placeholder**: `[LAWYER DECISION: Confirm whether corporate Customers required by Indonesian tax law to withhold Income Tax (such as PPh Article 23) must gross up payments or provide official withholding tax slips (Bukti Potong) to claim reimbursement, and specify the tax invoice (Faktur Pajak) issuance procedure.]`
- **Panduan Pengisian**: Sistem pembayaran Midtrans secara otomatis memungut nominal tagihan penuh (harga sudah termasuk PPN). Untuk pelanggan korporat yang memiliki kewajiban memotong PPh Pasal 23 (2% atas jasa teknologi/perangkat lunak), pengacara wajib memutuskan mekanisme yang berlaku:
  1. **Opsi Rekomendasi (Reimbursement via Bukti Potong)**: Pelanggan tetap melunasi nilai tagihan penuh pada checkout Midtrans, kemudian mengirimkan Bukti Potong PPh 23 resmi (e-Bupot) beserta NPWP ke tim keuangan Penyedia dalam waktu maksimal 30 hari kalender untuk mendapatkan pengembalian tunai (*reimbursement*) atau kompensasi Saldo Kredit sebesar nilai potongan 2%.
  2. **Prosedur Faktur Pajak**: Pelanggan yang membutuhkan Faktur Pajak masukan wajib mengisi data NPWP, NIK, nama perusahaan, dan alamat terdaftar pada menu profil sebelum pembayaran diselesaikan.

### LD-2: Mekanisme Transfer Data Lintas Batas Berdasarkan UU PDP (Pasal 12.5.2)
- **Teks Placeholder**: `[LAWYER DECISION: Confirm whether standard data transfer clauses or specific destination-country disclosures should be appended to Annex C under implementing regulations of Law No. 27 of 2022.]`
- **Panduan Pengisian**: Karena Platform 3Bee menggunakan infrastruktur cloud dan model kecerdasan buatan global (misalnya server database, komputasi edge Cloudflare, OpenAI, Google Gemini, Anthropic), data percakapan dan gambar diproses di luar wilayah Indonesia. Pengacara perlu memastikan kepatuhan terhadap Pasal 56 UU No. 27 Tahun 2022 tentang Pelindungan Data Pribadi (persetujuan eksplisit dari Pelanggan dan pemenuhan klausul perlindungan data standar / SCC jika diwajibkan oleh Peraturan Pemerintah pelaksana yang terbit).

### LD-3: Pengecualian Batas Tanggung Jawab vs Super-Cap (Pasal 17.3.1(e))
- **Teks Placeholder**: `[LAWYER DECISION: Confirm whether indemnification obligations under Article 16 and breaches of confidentiality under Article 13 are excluded from the cap in Section 17.2 or subject to a separate super-cap of [SUPER-CAP MULTIPLIER, e.g., two (2) times] the twelve-month fee basis]`
- **Panduan Pengisian**: Pasal 17.3 telah mengecualikan kelalaian berat (*gross negligence*), kesengajaan (*willful misconduct*), penipuan, cedera tubuh, dan tagihan terutang dari batasan tanggung jawab. Pengacara perlu memutuskan apakah ganti rugi pelanggaran HKI pihak ketiga (Pasal 16) dan pelanggaran kerahasiaan (Pasal 13):
  1. Bersifat tanpa batas (*uncapped*), atau
  2. Dibatasi oleh *super-cap* khusus (misalnya maksimum 2x atau 3x dari total nilai biaya langganan 12 bulan terakhir).

### LD-4: Pengesampingan Pasal 1266 Kitab Undang-Undang Hukum Perdata (Pasal 18.4.3)
- **Teks Placeholder**: `[LAWYER DECISION: Confirm whether the Parties expressly waive the provisions of Article 1266 of the Indonesian Civil Code (Kitab Undang-Undang Hukum Perdata) to the extent that a prior judicial pronouncement would otherwise be required to effect the suspension or termination of this Agreement in accordance with its terms.]`
- **Panduan Pengisian**: Dalam praktik hukum kontrak bisnis di Indonesia, Pasal 1266 KUHPerdata secara standar dikesampingkan agar penghentian wadah Agen AI dan penghapusan data secara otomatis oleh sistem scheduler backend setelah tagihan macet 15 hari tidak memerlukan penetapan atau putusan dari hakim pengadilan. Disarankan klausul pengesampingan Pasal 1266 KUHPerdata tetap dipertahankan.

### LD-5: Penentuan Forum Sengketa: Pengadilan Negeri vs Arbitrase (Pasal 20.2.2)
- **Teks Placeholder**: `[LAWYER DECISION: Select whether disputes shall be resolved exclusively by a designated District Court in Indonesia (such as the Central Jakarta District Court) or by binding arbitration administered by the Indonesian National Board of Arbitration (BANI) or another arbitration institution, and specify the seat, rules, number of arbitrators, and language of proceedings.]`
- **Panduan Pengisian**: Pengacara bersama manajemen bisnis menentukan forum penyelesaian sengketa:
  - **Pengadilan Negeri (misal Pengadilan Negeri Jakarta Pusat)**: Lebih ekonomis dari segi biaya pendaftaran perkara, cocok untuk karakteristik platform SaaS dengan pelanggan segmen UMKM/SME.
  - **Arbitrase (BANI)**: Menjamin kerahasiaan (*confidentiality*) dan bersifat final serta mengikat, namun biaya administrasi dan arbiter relatif lebih tinggi, umumnya dipilih jika platform berfokus pada klien skala korporat/enterprise besar.

### LD-6: Keberlakuan Bahasa Berdasarkan UU No. 24 Tahun 2009 (Pasal 20.3.2)
- **Teks Placeholder**: `[LAWYER DECISION: Confirm under Law No. 24 of 2009 of the Republic of Indonesia on the Flag, Language, State Emblem, and National Anthem and Presidential Regulation No. 63 of 2019 whether the Indonesian version must prevail for all Indonesian Customers and whether the English version may be designated as prevailing for non-Indonesian Customers.]`
- **Panduan Pengisian**: Berdasarkan UU No. 24 Tahun 2009 dan Perpres No. 63 Tahun 2019, teks Bahasa Indonesia wajib dimenangkan untuk seluruh pelanggan berbadan hukum atau berwarga negara Indonesia guna menghindari risiko batal demi hukum di hadapan pengadilan Indonesia. Untuk pelanggan internasional/asing di luar Indonesia, klausul dapat menetapkan bahwa versi Bahasa Inggris dimenangkan.

### LD-7: Kompensasi Kredit Layanan SLA vs Target Operasional (Lampiran D / Pasal 24.1.3)
- **Teks Placeholder**: `[LAWYER DECISION: Confirm whether the Provider offers service credits (and if so, the exact credit percentage and claim procedure) if monthly availability falls below [UPTIME TARGET], or whether availability targets are non-credit operational objectives.]`
- **Panduan Pengisian**: Kode backend saat ini tidak memiliki modul otomatis untuk menghitung kompensasi uang/kredit jika uptime turun di bawah target. Pengacara dan tim produk perlu memutuskan:
  - Apakah komitmen uptime merupakan target operasional murni (tanpa ganti rugi finansial langsung), atau
  - Memberikan hak klaim manual kepada pelanggan berupa tambahan Saldo Kredit (misalnya 5%–10% dari biaya bulanan) yang dimasukkan secara manual oleh administrator ke buku besar dompet (*wallet ledger*).
