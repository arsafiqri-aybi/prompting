# 11 — Pemilihan model dan konfigurasi inferensi

**Fungsi:** mencocokkan kemampuan sistem dengan jenis pekerjaan. Model terbaik untuk satu benchmark belum tentu paling baik untuk dokumenmu, bahasamu, biaya, atau kebutuhan privasimu.

## Matriks pemilihan

| Dimensi | Pertanyaan konkret | Cara uji |
|---|---|---|
| Ketepatan tugas | apakah mampu mengekstrak, menulis, menghitung, mengode? | contoh nyata dan kasus tepi |
| Keterbaruan | apakah mempunyai akses sumber kini? | satu pertanyaan yang berubah dan validasi URL |
| Input/output | dukungan teks, gambar, PDF, JSON, alat | uji berkas dan skema sesungguhnya |
| Panjang konteks | batas teknis dan kualitas pemanfaatannya? | dokumen panjang dengan bukti pada berbagai posisi |
| Biaya/latensi | berapa waktu dan biaya per hasil lulus? | biaya per kasus **lulus**, bukan per panggilan |
| Risiko data | kebijakan penyimpanan, lokasi, akses? | telaah syarat produk dan kontrol organisasi |

## Setelan generasi

Istilah seperti *temperature*, *top-p*, dan *top-k* berkaitan dengan cara token dipilih, tetapi **dukungan dan rekomendasinya berbeda menurut model dan versi**. Dokumentasi Google membahas parameter tersebut dan pada beberapa model terbaru menyarankan setelan bawaan; jangan mengasumsikan menurunkan temperature selalu meningkatkan akurasi [Google, text generation](https://ai.google.dev/gemini-api/docs/text-generation). Untuk keluaran deterministik seperti ekstraksi, evaluasi versi model dan validasi format lebih penting daripada mengandalkan satu angka sampling. Beberapa layanan dapat mengubah model di balik nama alias; catat identitas versi bila tersedia.

## Kebijakan memilih kompleksitas

Mulai dengan model yang cukup untuk kriteria hasil dan alat yang dibutuhkan. Jika gagal, diagnosis: kurang informasi → retrieval; perhitungan → kode; format → skema; perencanaan → uraian tugas; kapasitas penalaran → uji model lain. Jangan langsung memilih model terbesar untuk semua tugas. Alternatif yang lebih murah dapat memadai pada klasifikasi sederhana, sementara tugas riset sulit mungkin membutuhkan alat dan model lebih kuat.

## Rancangan perbandingan adil

Gunakan input sama, sumber sama, izin alat sama, rubrik sama, dan beberapa percobaan jika ada variasi. Tulis versi dan tanggal, lalu laporkan kategori kasus tempat satu model unggul atau gagal. Jangan hanya menilai keindahan gaya. Saat membandingkan model dengan kemampuan alat berbeda, laporkan hal itu sebagai perbedaan sistem, bukan kemampuan model murni.

## Biaya nyata per hasil

Hitung bukan hanya biaya satu panggilan, tetapi percobaan gagal, pencarian, pemeriksaan manusia, panjang keluaran, dan pekerjaan ulang. Ilustrasi: sistem A menghabiskan 100 unit biaya untuk 80 kasus lulus, jadi 1,25 unit per lulus; sistem B menghabiskan 70 unit untuk 40 kasus lulus, jadi 1,75 per lulus. Metrik ini tetap menyembunyikan dampak kegagalan fatal; laporkan keduanya. Angka ilustratif ini bukan tarif layanan tertentu.

## Kontrol variabel yang sering terlewat

Sumber yang berbeda, waktu pencarian, instruksi sistem, riwayat percakapan, jumlah kesempatan merevisi, akses alat, dan penilai yang sudah tahu jawaban kandidat dapat memengaruhi hasil. Untuk membandingkan model, simpan paket input identik, kecuali perbedaan fitur yang memang sedang diukur. Jika menguji model baru dengan kemampuan gambar pada tugas yang sebelumnya hanya diberi OCR teks, jelaskan bahwa input juga berubah.

## Perubahan produk

Ketersediaan model, batas konteks, setelan sampling, dan harga dapat berubah. Gunakan halaman model resmi pada hari pengujian, tulis tanggalnya, dan bila hasil penting simpan contoh masukan serta keluaran sebagai jejak. Jangan menyalin angka spesifikasi dari dokumen ini ke keputusan pembelian tanpa memeriksa halaman penyedia yang berlaku.

**Latihan:** bandingkan dua konfigurasi pada 20 pertanyaan dari berkas proyek. Hitung `biaya total / jumlah kasus lulus` dan tandai semua kesalahan fatal. Simpan konfigurasi dan sumber tanggal uji.

**Sumber:** [Google, model dan metode generasi](https://ai.google.dev/api/models); [Google, text generation](https://ai.google.dev/gemini-api/docs/text-generation); [HELM, evaluasi lintas skenario](https://arxiv.org/abs/2211.09110).