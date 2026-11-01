# 22. Lampiran B. Kebijakan Penggunaan yang Dapat Diterima dan Spesifikasi Unggahan Dokumen

- Path Dokumen: [annexes/annex-b-acceptable-use-and-uploads.id.md](./annex-b-acceptable-use-and-uploads.id.md)
- Path Dokumen Bahasa Pendamping: [annexes/annex-b-acceptable-use-and-uploads.en.md](./annex-b-acceptable-use-and-uploads.en.md)
- Path Dokumen Perjanjian Induk: [terms-and-conditions.id.md](../terms-and-conditions.id.md#22-lampiran-b-kebijakan-penggunaan-yang-dapat-diterima-dan-spesifikasi-unggahan-dokumen)
- Path Dokumen Daftar Isi: [TOC.id.md](../TOC.id.md#22-lampiran-b-kebijakan-penggunaan-yang-dapat-diterima-dan-spesifikasi-unggahan-dokumen)

### 22.1. Kategori Konten Terlarang dan Penggunaan Melawan Hukum

22.1.1. Sesuai dengan [Pasal 8 Perjanjian (terms-and-conditions.id.md)](../terms-and-conditions.id.md#8-pasal-8-kewajiban-pelanggan-penggunaan-yang-dapat-diterima-dan-tindakan-terlarang), Pelanggan dilarang menggunakan Agen AI, Etalase Web Terkelola, Widget Situs Web, sambungan WhatsApp, atau sambungan Telegram mana pun untuk mengiklankan, mendistribusikan, atau memproses konten yang berkaitan dengan:
(a) Narkotika ilegal, psikotropika, bahan kimia prekursor, atau sediaan farmasi tanpa izin edar.
(b) Perjudian daring, taruhan olahraga, lotre, atau permainan untung-untungan tanpa izin.
(c) Pornografi, layanan eksplisit secara seksual, citra intim non-konsensual, atau segala bentuk eksploitasi maupun kekerasan seksual terhadap anak.
(d) Senjata api, amunisi, bahan peledak, atau bahan berbahaya yang dibatasi oleh undang-undang.
(e) Barang curian, barang dagangan bermerek palsu, perangkat lunak bajakan, atau tiruan tanpa izin.
(f) Skema Ponzi, skema piramida, penghimpunan dana investasi tanpa izin, pencucian uang, atau penipuan pembayaran.
(g) Perangkat peretasan berbahaya, pencurian kredensial, halaman pengelabuan, atau penyamaran menyesatkan atas merek pihak ketiga maupun instansi pemerintah.

### 22.2. Jenis Berkas Unggahan Dokumen, Batas Ukuran, dan Pembatasan Struktural

22.2.1. Berkas yang diunggah oleh Pelanggan atau Akun Operatornya divalidasi berdasarkan ekstensi berkas, panjang bita, tanda tangan berkas, dan struktur internal sebelum diproses:
(a) Jenis Berkas Basis Pengetahuan yang Didukung: Dokumen PDF, TXT, MD, CSV, DOCX, XLSX, dan PPTX.
(b) Jenis Berkas Ekstraktor Katalog AI yang Didukung: Dokumen PDF, TXT, dan MD.
(c) Batas Berkas Portable Document Format (PDF): Ukuran berkas maksimum dua puluh megabita (20 MB) dan panjang maksimum seratus (100) halaman. Berkas PDF yang dienkripsi atau dilindungi kata sandi, berkas PDF yang memuat lampiran berkas tertanam, serta berkas PDF yang menggunakan arsitektur formulir XML dinamis akan ditolak.
(d) Batas Dokumen Perkantoran (DOCX, XLSX, PPTX): Ukuran berkas terkompresi maksimum sepuluh megabita (10 MB), ukuran arsip tidak terkompresi maksimum seratus megabita (100 MB), dan maksimum dua ribu (2.000) entri arsip internal. Dokumen perkantoran yang memuat makro tertanam atau entitas XML eksternal yang tidak aman akan ditolak.
(e) Batas Berkas Nilai Terpisah Koma (CSV): Ukuran berkas maksimum sepuluh megabita (10 MB), yang divalidasi sebagai konten teks asli.
(f) Batas Teks Biasa dan Markdown (TXT, MD): Ukuran berkas maksimum dua megabita (2 MB). Berkas yang mengandung tanda tangan eksekusi biner atau bita kosong akan ditolak.
(g) Batas Unggahan Sekaligus: Maksimum lima (5) berkas dan ukuran muatan gabungan maksimum lima puluh megabita (50 MB) per permintaan unggahan.

### 22.3. Pengaman Keamanan AI, Penyaring Visi, dan Batas Laju Sesi Pengunjung

22.3.1. Platform menerapkan pengendalian waktu jalan otomatis berikut pada seluruh Agen AI yang diterapkan:
(a) Pengaman Injeksi Instruksi: Pesan obrolan yang masuk diperiksa oleh pendeteksi pola dua tingkat dan model klasifikasi keamanan independen untuk memblokir instruksi yang mencoba mengesampingkan aturan sistem atau mengekstraksi instruksi internal.
(b) Penyaring Pemrograman di Luar Ruang Lingkup: Permintaan yang meminta Agen AI belanja atau resepsionis komersial untuk menulis, memperbaiki, atau menjalankan kode perangkat lunak akan ditolak atau diarahkan kembali ke bantuan toko.
(c) Pengaman Visi Virtual Try-On: Foto yang dikirimkan untuk Virtual Try-On dievaluasi oleh pengklasifikasi kelayakan visi independen sebelum pembuatan gambar, dan permintaan dibatasi hingga satu permintaan per tiga puluh (30) detik per pengirim dengan batas waktu pembuatan tiga ratus (300) detik.
(d) Batas Laju Sesi Pengunjung yang Dapat Dikonfigurasi: Pelanggan dapat mengonfigurasi batas permintaan per sesi pengunjung pada Dasbor Utama antara satu (1) hingga sepuluh ribu (10.000) permintaan per jendela waktu satu (1) hingga empat (4) menit untuk respons obrolan dan pembuatan Virtual Try-On, atau mengaturnya menjadi tanpa batas.
