# 08 — Retrieval-augmented generation (RAG) dan dokumen

**Fungsi:** menjawab berdasarkan kumpulan dokumen tertentu atau sumber yang berubah tanpa mengandalkan isi parameter model semata. RAG menggabungkan pencarian bagian relevan dengan generasi jawaban; paper awal menunjukkan perbaikan pada beberapa tugas tanya jawab serta faktualitas relatif terhadap baseline yang mereka uji [Lewis dkk.](https://arxiv.org/abs/2005.11401). RAG tidak membuat semua jawaban benar.

## Alur umum

`Pertanyaan → normalisasi kueri → cari kandidat → pilih/ranking ulang → tampilkan potongan + metadata → hasilkan jawaban → cek kutipan dan jawaban`.

Ada beberapa desain pencarian: leksikal (cocok istilah persis), semantik (kemiripan makna), atau gabungan. Dokumen dipecah menjadi potongan; ukuran potongan, overlap, metadata, dan kualitas OCR memengaruhi hasil. Namun tidak ada ukuran potongan universal: uji terhadap dokumen serta jenis pertanyaanmu.

## Kesalahan pada setiap tahap

| Tahap | Kegagalan | Uji terpisah |
|---|---|---|
| Indeks | versi usang atau bagian dokumen hilang | cek cakupan dan pembaruan |
| Kueri | istilah pengguna berbeda dari dokumen | kueri alternatif dan recall |
| Ranking | paragraf mirip tetapi tak menjawab | nilai relevansi top-k secara manual |
| Generasi | menyimpulkan lebih dari sumber | uji kesetiaan klaim ke petikan |
| Sitasi | kutipan salah halaman/tautan | buka sumber dan cocokkan kalimat |

Framework [RAGAS](https://arxiv.org/abs/2309.15217) mengusulkan pemisahan mutu retrieval, pemanfaatan konteks, dan generasi. Metrik otomatis dapat membantu pemantauan, tetapi audit manusia masih diperlukan pada kasus penting dan saat penilai model bisa keliru.

## Kebijakan jawaban berbasis dokumen

```text
Jawab hanya klaim yang didukung oleh sumber yang diberikan.
Untuk tiap klaim penting, tampilkan ID dokumen dan lokasi bagian.
Bila dua sumber berbeda, tulis kedua versi, tanggal, dan kemungkinan sebabnya.
Bila tidak ada dukungan, tulis "tidak ditemukan dalam sumber yang tersedia".
Pisahkan rekomendasi/inferensi dari fakta dokumen.
```

Instruksi tersebut membantu menata jawaban, tetapi tidak menjamin model benar-benar taat. Pemeriksaan sitasi tetap perlu. Jika kumpulan dokumen tidak lengkap, “tidak ditemukan” berarti tidak ditemukan **dalam kumpulan itu**, bukan tidak ada di dunia.

## Metrik yang bermakna

**Retrieval:** recall@k dari pertanyaan yang diketahui jawabannya, relevansi top-k, cakupan versi. **Jawaban:** ketepatan, klaim tanpa dukungan, ketepatan sitasi, pengakuan saat bukti tidak ada. **Operasional:** latensi, biaya, perubahan setelah dokumen diperbarui. Pisahkan kegagalan pencarian dari kegagalan model agar perbaikan diarahkan ke komponen yang tepat.

## Contoh untuk pustaka proyek

Pertanyaan “apa keputusan terakhir tentang navigasi website?” memerlukan berkas keputusan yang terbaru, bukan seluruh teori UX. Tandai tanggal dan versi; bila ada dua keputusan yang bertentangan, tampilkan konflik dan minta pemilik proyek menentukan yang berlaku. Jangan mengarang keputusan baru hanya agar jawaban tampak lengkap.

## Memilih potongan dan metadata

Potongan terlalu kecil dapat memisahkan angka dari label tabel atau pengecualiannya; terlalu besar dapat membawa banyak informasi tak relevan. Pertahankan judul bagian, nomor halaman, versi, tanggal berlaku, dan identitas dokumen bersama potongan. Untuk kebijakan yang diperbarui, keputusan terbaru tidak selalu mengganti seluruh bagian lama. Tetapkan aturan apakah arsip dikeluarkan dari hasil pencarian atau disajikan sebagai sejarah dengan label jelas.

## Pertanyaan yang butuh lebih dari satu sumber

Contoh “apa perubahan kebijakan antara versi 2 dan 3?” membutuhkan kedua versi. Retrieval yang hanya memilih dokumen paling baru akan gagal walau petikannya relevan. Susun kueri yang mencari masing-masing versi, lalu bandingkan butir yang sejajar. Untuk pertanyaan multi-langkah, simpan asal setiap bagian penalaran; jangan menempelkan satu sitasi pada kesimpulan yang sebenarnya memerlukan dua sumber.

## Audit sistem secara bertahap

Jika jawaban salah, periksa apakah bukti benar masuk dalam top-k. Jika tidak, perbaiki pengindeksan/kueri/ranking. Jika ya tetapi model mengabaikannya, perbaiki cara mengemas konteks/instruksi/kapasitas model. Jika jawaban benar tetapi sitasinya salah, perbaiki pemetaan kutipan. Mengubah semua komponen sekaligus membuatmu tidak tahu sebab peningkatan atau kemunduran.

**Latihan:** buat 10 pertanyaan yang jawabannya ada di kumpulan berkas dan 5 yang tidak ada. Ukur apakah retrieval menemukan bukti dan apakah jawaban menahan diri untuk lima pertanyaan negatif.

**Sumber:** [Lewis dkk., RAG](https://arxiv.org/abs/2005.11401); [Es dkk., RAGAS](https://arxiv.org/abs/2309.15217); [Liu dkk., konteks panjang](https://arxiv.org/abs/2307.03172).