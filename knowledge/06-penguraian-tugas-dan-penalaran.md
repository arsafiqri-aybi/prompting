# 06 — Penguraian tugas, penalaran, dan langkah antara

**Fungsi:** mengurangi kesalahan pada tugas yang memerlukan beberapa keputusan. Penguraian berguna jika ada ketergantungan nyata: misalnya mencari dokumen sebelum menyimpulkan, menghitung sebelum menyusun rekomendasi, atau menguji kode sebelum mengatakan selesai.

## Pilih bentuk alur sesuai masalah

| Bentuk | Pakai saat | Risiko |
|---|---|---|
| Satu permintaan | tugas pendek dan jelas | mudah melewatkan syarat tersembunyi |
| Rencana → kerjakan → cek | pekerjaan beberapa tahap | rencana bisa tidak diperbarui oleh bukti baru |
| Cabang alternatif → bandingkan | pilihan desain/strategi | biaya bertambah; penilaian bisa subjektif |
| Cari sumber → tulis klaim → verifikasi | fakta terbaru/berisiko | sumber yang ditemukan mungkin salah atau usang |
| Eksekusi alat → cek hasil | hitung/kode/data | instruksi alat dan keadaan sistem bisa berubah |

Paper [Chain-of-Thought Prompting](https://arxiv.org/abs/2201.11903) menunjukkan contoh langkah penalaran meningkatkan beberapa tugas aritmetika, simbolik, dan pengetahuan umum pada model yang diuji. [Self-consistency](https://arxiv.org/abs/2203.11171) menunjukkan beberapa jalur jawaban dapat membantu pada benchmark tertentu. Hasil ini tidak menjamin permintaan “berpikirlah selangkah demi selangkah” selalu meningkatkan model modern; lebih aman minta **rencana yang dapat diuji, perhitungan, bukti, dan jawaban akhir yang jelas**. Rangkaian teks penalaran yang terlihat tidak selalu menjelaskan proses internal secara setia [Lanham dkk.](https://arxiv.org/abs/2307.13702).

## Titik kontrol yang berguna

Untuk laporan penelitian: (1) rumuskan pertanyaan dan kriteria bukti; (2) cari sumber; (3) catat metode/temuan/batas; (4) bandingkan klaim yang bertentangan; (5) tulis kesimpulan; (6) audit sitasi. Untuk website: (1) kebutuhan pengguna; (2) sketsa; (3) implementasi; (4) uji aksesibilitas/performa; (5) perbaikan. Setiap tahap menghasilkan artefak yang bisa diperiksa, bukan sekadar teks panjang yang tampak logis.

## Penalaran yang dapat diperiksa

- **Aritmetika:** tulis variabel, satuan, rumus, dan gunakan kalkulator/program.
- **Analisis sumber:** tautkan tiap klaim ke petikan sumber dan jelaskan tingkat inferensi.
- **Desain:** cantumkan alternatif, kriteria, trade-off, dan tes yang membedakannya.
- **Diagnosa kesalahan:** tulis hipotesis, prediksi hasil, uji, dan pembaruan kesimpulan.

Permintaan untuk “menjelaskan proses” bisa membantu pengguna mengaudit langkah, tetapi jangan memperlakukan prosa itu sebagai bukti bahwa model benar. Untuk kasus kompleks, validasi lewat fakta, kode yang dijalankan, atau evaluator eksternal.

## Hindari penguraian palsu

Memecah kalimat sederhana menjadi 20 agen atau 10 prompt dapat menambah biaya, kesalahan antar langkah, dan titik kehilangan konteks. Mulai dengan alur sesingkat mungkin. Tambahkan tahap ketika uji menunjukkan jenis kegagalan yang jelas. Dalam kajian koreksi diri, perbaikan lebih andal ketika mendapat umpan balik eksternal yang dapat dipercaya daripada hanya diminta mengoreksi jawaban tanpa bukti baru [Kamoi dkk.](https://arxiv.org/abs/2406.01297).

## Aturan memutuskan apakah satu tahap layak dipisah

Pisahkan tahap bila keluarannya dapat diverifikasi sendiri dan merupakan input penting bagi tahap berikut: daftar sumber → ekstraksi hasil → sintesis. Jangan pisahkan hanya karena jumlah kalimat banyak. Tuliskan untuk setiap tahap: **input**, **operasi**, **bukti lulus**, **aksi jika gagal**. Contoh pengujian kode: input berupa spesifikasi dan repo, operasi mengubah fungsi, bukti lulus berupa tes dan inspeksi, aksi gagal berupa diagnosis galat; menulis “kode sudah diperbaiki” tanpa tes bukan bukti.

## Menjaga batas inferensi

Langkah antara dapat memperbanyak kesempatan mengarang. Pada sintesis riset, setiap tahap harus mempertahankan pasangan klaim–sumber. Ringkasan antara yang mengatakan “sebagian besar studi mendukung” perlu menyebut berapa studi, apa ukuran “mendukung”, dan apakah desainnya sebanding. Jika empat penelitian berbeda populasi dan ukuran, agregasi angka langsung bisa menyesatkan. Gunakan daftar kontradiksi sebelum menyimpulkan.

## Pemakaian banyak kandidat

Menghasilkan tiga opsi dapat membantu ide desain dan mencari alternatif, tetapi pemilihan harus menggunakan rubrik yang ditentukan sebelumnya. Untuk fakta, tiga jawaban yang setuju bukan tiga sumber independen; semua dapat berasal dari model dan bias yang sama. Jika biaya tinggi, pilih kapan multi-sampling benar-benar memperbaiki hasil melalui uji pada kasus sulit.

**Latihan:** pilih tugas yang sering gagal, coba satu respons langsung dan satu respons dengan hasil antara yang diperiksa. Beri skor pada hasil akhir dan jumlah kesalahan yang terdeteksi sebelum selesai.

**Sumber:** [Wei dkk.](https://arxiv.org/abs/2201.11903); [Wang dkk.](https://arxiv.org/abs/2203.11171); [Lanham dkk.](https://arxiv.org/abs/2307.13702); [Kamoi dkk.](https://arxiv.org/abs/2406.01297).