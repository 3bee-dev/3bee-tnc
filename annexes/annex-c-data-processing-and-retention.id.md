# 23. Lampiran C. Jadwal Pemrosesan dan Penyimpanan Data

- Path Dokumen: [docs/platform-legal/annexes/annex-c-data-processing-and-retention.id.md](./annex-c-data-processing-and-retention.id.md)
- Path Dokumen Bahasa Pendamping: [docs/platform-legal/annexes/annex-c-data-processing-and-retention.en.md](./annex-c-data-processing-and-retention.en.md)
- Path Dokumen Perjanjian Induk: [docs/platform-legal/terms-and-conditions.id.md](../terms-and-conditions.id.md#23-lampiran-c-jadwal-pemrosesan-dan-penyimpanan-data)
- Path Dokumen Daftar Isi: [docs/platform-legal/TOC.id.md](../TOC.id.md#23-lampiran-c-jadwal-pemrosesan-dan-penyimpanan-data)

### 23.1. Kategori Subjek Data, Data Pribadi, dan Peran Pemrosesan

23.1.1. Data yang Diproses sebagai Pemroses Data (Pelanggan sebagai Pengendali Data sesuai dengan [Pasal 12 pada docs/platform-legal/terms-and-conditions.id.md](../terms-and-conditions.id.md#12-pasal-12-peran-data-tujuan-pemrosesan-penyimpanan-sub-pemroses-transfer-lintas-batas-dan-penanganan-insiden)):
(a) Subjek Data: Pengguna Akhir (pembeli, pengunjung situs web, pengguna WhatsApp, pengguna Telegram) dan orang perseorangan yang disebutkan dalam Konten Pelanggan.
(b) Kategori Data Pribadi: Pesan percakapan, cuplikan kontak yang diberikan secara sukarela dalam obrolan (nama, nomor telepon, alamat, atau surat elektronik hingga tiga baris tersemat dengan masing-masing tiga ratus karakter), foto pencarian produk, foto pengguna dan foto ruangan Virtual Try-On, nomor telepon dan nama profil WhatsApp, penanda pengguna dan penanda obrolan Telegram, serta tanda kriptografis pengunjung satu arah.
(c) Kegiatan Pemrosesan: Menerima, menyimpan sementara dalam memori sesi, mengevaluasi terhadap pengaman keamanan, meneruskan ke Model AI untuk sintesis respons atau gambar, mengirimkan respons melalui kanal yang terhubung, dan mencatat Analitik Pengunjung yang telah dide-identifikasi.

23.1.2. Data yang Diproses sebagai Pengendali Data Independen (Penyedia sebagai Pengendali Data):
(a) Subjek Data: Pemegang akun Pelanggan, perwakilan, dan pengguna Akun Operator.
(b) Kategori Data Pribadi: Alamat surat elektronik, nomor telepon, nama lengkap, nama bisnis, nama pengguna, kredensial terenkripsi atau teracak secara kriptografis, alamat jaringan klien, token perangkat, catatan langganan dan tagihan, entri buku besar Saldo Kredit, dan log audit administratif.
(c) Kegiatan Pemrosesan: Pendaftaran akun, verifikasi identitas, autentikasi, penagihan, rekonsiliasi pembayaran, pencatatan pemakaian kuota, penegakan keamanan, dukungan pelanggan, dan kepatuhan hukum.

### 23.2. Jadwal Jangka Waktu Penyimpanan Data dan Aturan Penghapusan Otomatis

23.2.1. Platform menerapkan jangka waktu penyimpanan spesifik berikut:
(a) Kode Sekali Pakai Pendaftaran: Lima (5) menit (300 detik).
(b) Sesi Pendaftaran yang Belum Selesai: Lima belas (15) menit (900 detik).
(c) Token Akses Dasbor Utama: Lima belas (15) menit (900 detik).
(d) Token Penyegar Dasbor Utama: Tujuh (7) hari kalender (604.800 detik), atau hingga keluar lebih awal atau terjadi perubahan kata sandi.
(e) Token Perangkat Masuk Tepercaya: Tiga puluh (30) hari kalender.
(f) Penghitung Batas Kegagalan Masuk: Lima belas (15) menit.
(g) Aliran Log Penerapan Waktu Nyata: Dua (2) jam.
(h) Riwayat Obrolan Pengguna Akhir, Titik Pemeriksaan Alur Kerja, Status Sesi Web, dan Cuplikan Kontak Tersemat: Dua puluh empat (24) jam (86.400 detik) sejak interaksi sesi terakhir, ditambah hingga dua puluh empat (24) jam pada penyimpanan lokal peramban web milik Pengguna Akhir sendiri pada Etalase Web Terkelola atau Widget Situs Web.
(i) Penyangga Balasan Waktu Nyata yang Belum Terkirim: Sepuluh (10) menit (600 detik).
(j) Analitik Pengunjung (Laporan Sesi Mentah, Catatan Harian per Pengunjung, dan Rekapitulasi Harian): Sembilan puluh (90) hari kalender, atau dihapus lebih awal pada saat penghapusan manual Agen AI atau penghapusan basis data pasca-penangguhan.
(k) Basis Data Khusus Agen AI yang Ditangguhkan atau Dihentikan Akibat Penurunan Paket: Lima belas (15) hari kalender ([SUSPENSION RETENTION DAYS]) sejak waktu Penangguhan Penagihan atau penghentian per agen, yang setelahnya basis data khusus per agen tersebut dihapus secara permanen.
(l) Cuplikan Audit Tindakan Akun Administratif: Kolom Data Pribadi (alamat surat elektronik, nomor telepon, nama lengkap, dan nama bisnis) disimpan dalam teks jelas selama tiga ratus enam puluh lima (365) hari kalender dan kemudian disamarkan secara otomatis dan tidak dapat dipulihkan (dengan hanya menyisakan karakter pertama dan domain surat elektronik, empat digit terakhir nomor telepon, serta inisial nama), sementara metadata audit non-pribadi (penanda akun, nama pengguna, peran, tindakan, alasan, dan waktu) disimpan secara permanen demi integritas audit.
(m) Akun Pelanggan, Buku Besar Saldo Kredit, dan Catatan Tagihan/Pembayaran: Disimpan selama akun Pelanggan masih ada dan selama [FINANCIAL RECORD RETENTION YEARS, e.g., ten (10) years] setelahnya guna memenuhi kewajiban perpajakan, akuntansi, dan pembuktian sengketa berdasarkan undang-undang.

### 23.3. Kategori Sub-Pemroses yang Diizinkan dan Pengamanan Transfer Lintas Batas

23.3.1. Penyedia menggunakan Sub-Pemroses dalam kategori fungsional berikut:
(a) Penyedia Infrastruktur Awan dan Basis Data Terkelola: Untuk kontainer waktu jalan aplikasi, penyimpanan basis data relasional/dokumen, singgahan sesi dalam memori, dan pengindeksan pencarian kemiripan vektor.
(b) Penyedia Tepi Jaringan, Perutean Domain, Perlindungan Bot, dan Penyimpanan Objek: Untuk perutean subdomain khusus, keamanan lalu lintas web, tantangan verifikasi bot otomatis, serta penyimpanan objek awan atas gambar produk, logo merek, dan media Virtual Try-On.
(c) Penyedia Model Akal Imitasi: Untuk pembuatan obrolan model bahasa besar, klasifikasi keamanan, pengenalan karakter optik dan ekstraksi dokumen, analisis visi komputer, serta sintesis gambar Virtual Try-On.
(d) Penyedia Gerbang Pembayaran Berlisensi: Untuk memproses pembayaran langganan dan isi ulang Saldo Kredit dalam Rupiah Indonesia.
(e) Penyedia Surat Elektronik Transaksional: Untuk mengirimkan kode sekali pakai, peringatan keamanan, pengingat pembayaran, dan pemberitahuan penagihan.
(f) Penyedia Autentikasi Identitas: Untuk autentikasi akses masuk tunggal pihak ketiga opsional.

23.3.2. Apabila Sub-Pemroses memproses Data Pribadi di luar wilayah Republik Indonesia, Penyedia memilih penyedia komersial bereputasi baik yang tunduk pada komitmen keamanan data dan kerahasiaan serta hanya mengirimkan elemen data yang diperlukan bagi tugas pemrosesan terkait.
