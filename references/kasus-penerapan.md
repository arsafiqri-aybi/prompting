# Kasus penerapan dan pemeriksaan perilaku

Contoh berikut adalah skenario rancangan untuk memahami keputusan, bukan laporan uji pemicu otomatis pada platform.

| Pesan pengguna | Tindakan yang diharapkan |
| --- | --- |
| “Website cookies ini kurang enak dipakai di HP; perbaiki” | Cari versi situs saat ini, temukan hambatan seluler, lakukan perbaikan yang diminta, periksa interaksi dan tampilan; tanyakan hanya jika target situs tidak teridentifikasi. |
| “Tombol samping Pilih Cookies itu harusnya Hampers, fokus ke situ” | Gunakan konteks situs yang aktif, ubah bagian itu saja, periksa navigasi yang terdampak, laporkan hasil. |
| “Aku ingin memahami cara meningkatkan hasil AI; jangan buat skill dulu” | Bahas kerangka ilmu dan pilihan, berhenti sebelum membuat atau memasang skill. |
| “Sekarang eksekusi ya” setelah rancangan disetujui | Laksanakan rancangan yang masih berlaku sampai hasil nyata tersedia, tanpa meminta brief ulang. |
| “Buat prompt agar chatbot menyusun modul dari jurnal” | Keluarkan prompt siap pakai dengan masukan dan batas penting; jangan menyusun modul kecuali juga diminta. |
| “Buat modul dari jurnal terlampir” | Baca jurnal, buat modul dan periksa akurasi; jangan hanya menulis prompt. |
| “Ringkas laporan ini” tanpa lampiran | Minta laporan atau tautan yang dapat diakses; jangan mengarang isi. |
| “Bandingkan harga terbaru tiga layanan” | Cari sumber harga saat ini bila tersedia; berikan tanggal dan syarat perbandingan; jangan menyajikan angka ingatan sebagai harga hari ini. |
| “Apa itu RAG?” | Jawab singkat langsung, tanpa kontrak tugas atau alur panjang. |
| “Perbaiki ejaan kata ini” | Lakukan perubahan mekanis langsung. |
| “Kirim draf ini ke Deni” dengan dua calon penerima | Pastikan identitas penerima sebelum mengirim. |
| “Hasilnya harus setara Work” di Chat dengan alat lebih terbatas | Kerjakan semaksimal alat yang tersedia; jelaskan batas konkret bila hasil meminta kemampuan yang tidak ada. |

Untuk pemeriksaan manual setelah skill dibuat, nilai pada contoh yang relevan: **target pengguna terjaga**, **klarifikasi proporsional**, **keluaran nyata selesai**, **fakta penting didukung**, **pemeriksaan sesuai medium**, dan **aksi tidak melampaui instruksi**. Nilai 0 gagal, 1 sebagian, 2 memenuhi; cantumkan bukti. Pisahkan uji isi dengan pemanggilan eksplisit dari uji pemilihan otomatis pada chat baru. Daftar contoh ini sendiri bukan bukti peningkatan kualitas atau kesetaraan dengan mode Work.
