# 13 — Verifikasi fakta, halusinasi, dan ketidakpastian

**Fungsi:** mencegah keluaran yang lancar bahasanya dianggap benar tanpa bukti. “Halusinasi” dipakai untuk beragam kegagalan: klaim faktual palsu, tambahan yang tidak didukung bahan, kutipan palsu, atau inferensi yang dinyatakan sebagai fakta. NIST menggunakan istilah *confabulation* sebagai salah satu risiko AI generatif [NIST AI 600-1](https://doi.org/10.6028/NIST.AI.600-1).

## Bedakan empat klaim

- **Fakta eksternal:** “standar X diterbitkan tahun Y” → buka penerbit resmi.
- **Fakta dokumen:** “laporan menyebut 40 responden” → buka halaman/kalimat.
- **Hasil hitung:** “penurunan 25%” → periksa rumus, pembagi, satuan.
- **Inferensi:** “karena itu strategi A lebih sesuai” → cek asumsi dan alternatif.

Jawaban dengan empat jenis klaim ini memerlukan empat jenis verifikasi. Satu sitasi di akhir paragraf tidak otomatis mendukung semua isinya.

## Protokol audit klaim penting

1. Tandai klaim yang bila salah akan mengubah keputusan.
2. Pecah kalimat majemuk menjadi klaim atomik.
3. Temukan sumber primer atau bukti pengukuran; cocokkan ruang lingkup dan tanggal.
4. Periksa apakah sumber mendukung **persis** klaim, bukan hanya topik umumnya.
5. Tandai status: didukung, sebagian, bertentangan, tidak ditemukan.
6. Jika tidak didukung, hapus, beri label hipotesis, atau cari bukti baru.

Dalam [TruthfulQA](https://arxiv.org/abs/2109.07958), model yang diuji dapat meniru miskonsepsi umum; angka benchmark tersebut terikat pada model dan periode studi. Dalam studi [atribusi referensi](https://arxiv.org/abs/2309.09401), meminta referensi tidak otomatis menjamin sitasi nyata atau tepat. Karena itu, tingkat keyakinan yang terdengar dalam bahasa tidak sama dengan kalibrasi empiris.

## Abstain dengan tepat

Pilihan respons yang valid: “dokumen yang tersedia tidak menyebutnya”, “versi sumber A dan B berbeda”, “aku bisa menghitung setelah memperoleh pembagi”, atau “butuh profesional karena keputusan ini berisiko tinggi”. Hindari ketidakpastian kabur yang ditambahkan ke semua kalimat; sebut **hal apa** yang tidak diketahui dan langkah pemeriksaan berikutnya.

## Verifikasi berlapis menurut dampak

| Dampak kesalahan | Pemeriksaan yang layak |
|---|---|
| Rendah: ide judul | penilaian manusia dan kesesuaian gaya |
| Menengah: laporan internal | cek sumber sampel dan angka utama |
| Tinggi: medis/hukum/keuangan/keamanan | verifikasi penuh sumber terkini dan peninjau ahli yang relevan |

## Jangan bergantung pada koreksi diri kosong

“Periksa lagi jawabanmu” tanpa fakta baru dapat menghasilkan keyakinan baru yang salah. Kajian kritis tentang koreksi diri menemukan hasil yang lebih kuat ketika ada umpan balik eksternal yang dapat dipercaya [Kamoi dkk.](https://arxiv.org/abs/2406.01297). Mintalah AI mencari sumber asli, menjalankan tes, atau membandingkan dengan kunci jawaban; gunakan pengulangan sampling hanya sebagai sinyal, bukan bukti.

## Kalibrasi dan bahasa keyakinan

Kalibrasi berarti tingkat keyakinan berkaitan dengan frekuensi benar pada banyak kasus serupa, bukan sekadar mengatakan “saya 90% yakin”. Jika sistem menandai 100 jawaban sebagai berkeyakinan 80%, kira-kira 80 di antaranya semestinya benar pada set uji sejenis agar angka itu terkalibrasi. Tanpa data seperti itu, gunakan label kualitatif yang dijelaskan: ada sumber primer langsung, sumber parsial, atau tidak ada sumber. Bahkan sumber primer dapat keliru; keyakinan harus mencakup mutu sumber dan kecocokan penerapannya.

## Apa yang harus dilakukan dengan konflik?

Konflik dapat berasal dari tanggal yang berbeda, definisi istilah berbeda, populasi studi berbeda, atau satu sumber salah. Jangan otomatis memilih sumber terbaru; aturan lama bisa tetap berlaku untuk kasus historis. Sajikan dua klaim beserta waktu dan lingkup, jelaskan alasan konflik yang didukung bukti, lalu tunjukkan data tambahan yang akan menyelesaikan. Bila konflik tidak terselesaikan, kesimpulan yang baik menahan diri pada bagian itu.

## Sitasi yang benar-benar bekerja

Tautan ke beranda organisasi tidak cukup untuk mendukung angka spesifik. Petikan yang menyebut hasil X pada populasi Y tidak mendukung klaim umum X untuk semua orang. Tabel klaim–lokasi sumber dalam `07` membantu memeriksa satu kalimat pada satu waktu. Untuk dokumen yang mungkin berubah, simpan tanggal akses atau versi. Jika sumber hanya bersifat sekunder, cari sumber aslinya sebelum memutuskan.

**Latihan:** ambil sebuah laporan AI dan temukan tiga klaim yang paling berisiko. Audit ke sumber; tulis ulang kesimpulan agar kekuatan bahasanya sesuai bukti.

**Sumber:** [NIST GenAI Profile](https://doi.org/10.6028/NIST.AI.600-1); [TruthfulQA](https://arxiv.org/abs/2109.07958); [studi sitasi](https://arxiv.org/abs/2309.09401); [koreksi diri](https://arxiv.org/abs/2406.01297).