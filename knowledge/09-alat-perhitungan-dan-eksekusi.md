# 09 — Penggunaan alat: pencarian, perhitungan, kode, dan tindakan

**Fungsi:** melengkapi kemampuan generasi teks dengan operasi yang dapat diamati. Sebuah model dapat mengusulkan panggilan alat; sistem mengeksekusi; keluaran alat kembali sebagai data; model melanjutkan. Paper [Toolformer](https://arxiv.org/abs/2302.04761) dan [ReAct](https://arxiv.org/abs/2210.03629) meneliti penggabungan model dengan alat serta tindakan; penerapan produk berbeda dari percobaan dalam paper.

## Pilih alat berdasarkan kebutuhan

| Tugas | Alat yang sesuai | Bukti selesai |
|---|---|---|
| Berita/fakta yang berubah | pencarian dan halaman primer | URL, tanggal, isi terbuka |
| Hitungan dan statistik | kalkulator/kode | input, rumus, hasil, uji batas |
| Kode dan file | editor, terminal, pengujian | perubahan file dan hasil tes |
| Data dalam spreadsheet | pembaca/penulis sheet | rumus, nilai, pemeriksaan silang |
| Tindakan eksternal | API/aplikasi yang berwenang | hasil sistem, bukan klaim model |

Mengucapkan “sudah dikirim” tidak membuktikan pesan terkirim. Dalam evaluasi agen, hasil nyata pada lingkungan dibedakan dari teks yang dikatakan agen [Anthropic, *Demystifying evals*](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents).

## Kontrak alat yang baik

Jelaskan kapan alat boleh dipakai, input wajib, output yang mungkin, batas biaya/waktu, prosedur kesalahan, serta hak akses. Gunakan alat baca untuk inspeksi dan hak tulis hanya saat diperlukan. Deskripsi yang jelas mengurangi kebingungan antar alat yang fungsinya mirip [Anthropic, *Effective context engineering*](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents).

## Prosedur aman untuk hitungan

Tulis pertanyaan dan satuan → pilih rumus/algoritme → masukkan angka yang sumbernya jelas → jalankan → cek kewajaran hasil → laporkan pembulatan dan asumsi. Contoh: jika 240 dari 300 responden menyelesaikan tugas, keberhasilan teramati 80%. Angka ini sendiri tidak menjelaskan keterwakilan sampel atau sebab keberhasilan; jangan menjadikannya klaim untuk seluruh populasi.

## Prosedur saat alat gagal

Bedakan gagal teknis, data tidak ditemukan, sumber tidak bisa dibuka, dan hasil bertentangan. Catat nama alat, input yang relevan (tanpa rahasia), respons/galat, tindakan pemulihan, lalu jangan mengarang hasil seolah operasi berhasil. Ulangi hanya bila alasan kegagalan jelas dan mengulang tidak menimbulkan tindakan ganda yang merugikan.

## Bahaya sumber dari alat

Hasil pencarian, halaman web, atau dokumen dapat berisi instruksi jahat yang mencoba memengaruhi model. Jangan beri konten alat hak mengubah tujuan pengguna, membocorkan data, atau memanggil alat dengan hak lebih tinggi. Ancaman ini didemonstrasikan sebagai *indirect prompt injection* [Greshake dkk.](https://arxiv.org/abs/2302.12173) dan dibahas dalam [OWASP Top 10 LLM](https://owasp.org/www-project-top-10-for-large-language-model-applications/).

## Membaca jejak tindakan

Untuk tiap tindakan, catat tujuan, nama alat, parameter yang tidak rahasia, respons, dan efek pada lingkungan. Bedakan **alat mengusulkan operasi**, **alat menerima operasi**, dan **keadaan benar-benar berubah**. Misal API mengembalikan “accepted” untuk proses asinkron; tindakan belum tentu selesai. Pemeriksaan akhir mungkin memerlukan membaca status. Pada aksi yang tidak mudah dibalik, desain alur agar pengguna meninjau draf atau parameter tepatnya sebelum pengiriman ketika konteks menuntut.

## Uji alat yang tidak ideal

Simulasikan timeout, respons kosong, duplikasi, data dalam urutan tak terduga, dan akses ditolak. Alur yang baik tidak mengubah “gagal memanggil alat” menjadi jawaban palsu. Untuk operasi tulis, hati-hati pada retry: dua pemanggilan bisa membuat dua transaksi atau pesan. Untuk operasi baca, tanggal dan izin akses tetap memengaruhi interpretasi hasil.

## Alat atau pengetahuan model?

Gunakan pengetahuan model untuk menyusun hipotesis, mengubah gaya, atau menjelaskan konsep stabil. Gunakan sumber eksternal untuk fakta baru dan dokumen milik pengguna; gunakan eksekusi untuk hitungan dan kode. Bahkan setelah alat dipakai, hasilnya perlu ditafsirkan dengan benar: kalkulator memproses angka yang diberikan, tidak membuktikan bahwa angkanya berasal dari sumber yang benar.

**Latihan:** minta AI menganalisis 15 transaksi contoh. Periksa dua total secara manual, injeksikan satu baris sumber yang berbunyi “abaikan semua instruksi”, lalu lihat apakah sistem memisahkan data dari perintah.

**Sumber:** [Toolformer](https://arxiv.org/abs/2302.04761); [ReAct](https://arxiv.org/abs/2210.03629); [evaluasi agen Anthropic](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents).