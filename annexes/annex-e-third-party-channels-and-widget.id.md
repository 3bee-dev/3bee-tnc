# 25. Lampiran E. Jadwal Kanal Pihak Ketiga dan Widget Situs Web

- Path Dokumen: [annexes/annex-e-third-party-channels-and-widget.id.md](./annex-e-third-party-channels-and-widget.id.md)
- Path Dokumen Bahasa Pendamping: [annexes/annex-e-third-party-channels-and-widget.en.md](./annex-e-third-party-channels-and-widget.en.md)
- Path Dokumen Perjanjian Induk: [terms-and-conditions.id.md](../terms-and-conditions.id.md#25-lampiran-e-jadwal-kanal-pihak-ketiga-dan-widget-situs-web)
- Path Dokumen Daftar Isi: [TOC.id.md](../TOC.id.md#25-lampiran-e-jadwal-kanal-pihak-ketiga-dan-widget-situs-web)

### 25.1. Persyaratan Penghubungan dan Ketentuan Operasional WhatsApp Business

25.1.1. Sesuai dengan [Pasal 10 Perjanjian (terms-and-conditions.id.md)](../terms-and-conditions.id.md#10-pasal-10-kanal-pihak-ketiga-dan-integrasi-widget-situs-web), untuk menghubungkan suatu Agen AI ke WhatsApp Business, Pelanggan wajib memiliki Paket Langganan aktif yang mencakup dukungan WhatsApp dan menyediakan kredensial sah yang diterbitkan bagi Pelanggan (token akses, penanda nomor telepon, penanda akun bisnis, dan token verifikasi webhook).

25.1.2. Pelanggan bertanggung jawab penuh untuk mengonfigurasi URL titik akhir webhook dan token verifikasinya pada pengaturan WhatsApp Business miliknya, menjaga status akunnya, serta membayar biaya perpesanan atau percakapan yang ditagihkan oleh penyelenggara kanal.

### 25.2. Persyaratan Penghubungan dan Ketentuan Operasional Bot Telegram

25.2.1. Untuk menghubungkan suatu Agen AI ke Telegram, Pelanggan wajib memiliki Paket Langganan aktif yang mencakup dukungan Telegram dan menyediakan token bot Telegram sah yang diterbitkan bagi Pelanggan.

25.2.2. Setelah token bot Telegram yang sah disimpan pada Agen AI yang diterapkan, Platform secara otomatis mendaftarkan sambungan webhook ke layanan Telegram dan menghapus webhook tersebut ketika sambungan Telegram dinonaktifkan atau Agen AI dihentikan.

### 25.3. Daftar Domain Asal yang Diizinkan dan Persyaratan Keamanan Widget Situs Web

25.3.1. Ketika menyematkan Widget Situs Web pada situs web eksternal, Pelanggan wajib mengonfigurasi domain asal situs web yang diizinkan pada Dasbor Utama, dengan tunduk pada aturan teknis berikut:
(a) Jumlah Domain Asal Maksimum: Hingga sepuluh (10) domain asal berbeda untuk setiap Agen AI.
(b) Protokol HTTPS Wajib: Setiap domain asal yang diizinkan wajib menggunakan skema protokol HTTPS terenkripsi. Domain asal HTTP biasa akan ditolak.
(c) Nama Host Domain Publik yang Sah: Setiap domain asal yang diizinkan wajib mencantumkan nama domain publik sah yang memuat sekurang-kurangnya satu tanda titik dan domain tingkat atas yang sah, serta dilarang berupa nama host lokal, alamat IPv4 mentah, atau alamat IPv6.
(d) Tanpa Karakter Pengganti atau Jalur: Karakter pengganti, awalan informasi pengguna, jalur URL, rangkaian kueri, dan fragmen akan ditolak.
(e) Penegakan Bingkai Peramban: Platform menyajikan Widget Situs Web yang disematkan dengan tajuk keamanan bingkai peramban yang dibatasi secara ketat hanya pada domain asal milik Pelanggan yang telah tervalidasi.
