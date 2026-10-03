# 10 — Input multimodal: gambar, audio, video, dan PDF

**Fungsi:** memberi AI bahan di luar teks sekaligus memahami informasi yang hilang selama pemrosesannya. Model dan produk memiliki kemampuan berbeda; cek dokumentasi versi sebelum mengandalkan fitur khusus. Panduan resmi [Google tentang berkas media](https://ai.google.dev/gemini-api/docs/files) dan [pemrosesan dokumen](https://ai.google.dev/gemini-api/docs/document-processing) menunjukkan contoh alur multimodal, bukan jaminan kualitas untuk setiap berkas.

## Mengapa hasil bisa salah?

Gambar bisa buram/terpotong; halaman PDF hasil pindai bisa gagal OCR; tabel bercabang dan catatan kaki dapat hilang; audio berisik menyulitkan transkripsi; video berisi peristiwa di antaraframe yang dibaca sistem. Model dapat mengisi bagian yang tak jelas dengan tebakan yang terdengar wajar. Bahkan ketika teks berhasil diekstrak, tata letak, urutan baca, dan hubungan antara gambar serta keterangan dapat berubah.

## Protokol input menurut jenis

| Media | Siapkan | Minta hasil antara | Validasi |
|---|---|---|---|
| Gambar | resolusi cukup, fokus objek, konteks ukuran | deskripsi bagian yang benar-benar terlihat | inspeksi manual label/angka |
| PDF | judul, nomor halaman, versi, apakah pindai | kutipan dan halaman sebelum sintesis | buka halaman yang dikutip |
| Audio | durasi, bahasa, pembicara, izin | transkrip dengan segmen tak jelas | dengarkan bagian kritis |
| Video | durasi, adegan penting, pertanyaan terarah | urutan kejadian dan cap waktu | periksa klip pada cap waktu |

## Pertanyaan yang tepat

Kurang baik: “Analisis gambar ini secara mendalam.” Lebih jelas: “Dari tangkapan layar beranda pada lebar ponsel ini, identifikasi tiga masalah navigasi yang **terlihat**; sebut lokasi visual dan apa yang tidak dapat disimpulkan hanya dari gambar. Jangan menebak perilaku interaktif tanpa mencoba halaman.”

Untuk PDF penelitian: “Temukan metode, ukuran sampel, dan hasil utama pada halaman yang tepat; laporkan teks yang tidak terbaca; pisahkan hasil penulis dari tafsirmu.” Jika tugas bergantung pada tabel numerik, cocokkan angka dari tabel asli dan hitung ulang bila perlu.

## Multimodal bukan bukti dampak pada manusia

Model yang melihat tangkapan layar bisa mengomentari warna dan susunan, tetapi tidak dapat menyimpulkan bahwa semua pengguna nyaman, bahwa situs dapat diakses dengan pembaca layar, atau bahwa aroma/rasa fisik dihasilkan oleh tampilan. Hal itu memerlukan uji antarmuka, teknologi bantu, atau riset manusia sesuai hipotesisnya.

## Evaluasi

Buat lima bahan berkualitas baik dan lima sulit: blur, tabel multi kolom, audio beraksen, grafik tanpa label, serta video dengan kejadian cepat. Nilai akurasi ekstraksi sebelum menilai kualitas sintesis. Jika ekstraksi gagal, perbaiki bahan (pemindaian/teks asli/crop), jangan hanya memperindah prompt.

## Audit grafik dan diagram

Grafik memerlukan pembacaan judul, sumbu, skala, satuan, legenda, populasi, serta sumber data. Sumbu terpotong dapat membuat perubahan kecil tampak besar; titik tanpa label dapat sulit diekstrak tepat. Tanyakan angka hanya jika tercetak jelas atau data mentah tersedia. Bila model mengestimasi nilai dari gambar, labeli “perkiraan visual” dan jangan pakai untuk perhitungan presisi.

## Video dan transkrip

Ringkasan video perlu membedakan “terlihat pada bingkai”, “terdengar pada audio”, dan “disimpulkan”. Cap waktu dan identitas pembicara harus diverifikasi, terutama saat adegan cepat atau suara saling tumpang tindih. Jika rekaman memuat orang nyata, perlakukan identitas dan persetujuan penggunaan sebagai bagian dari desain tugas. Untuk rapat, keputusan final tidak selalu sama dengan ide yang disebut dalam diskusi; carilah kalimat persetujuan atau dokumen keputusan.

## Tata letak dokumen sebagai data

Pada PDF dua kolom, ekstraksi teks bisa menyatukan akhir kolom kiri dengan awal kolom kanan dalam urutan salah. Tabel sering memisahkan nilai dan kepala kolom. Untuk klaim penting, tampilkan gambar halaman atau sumber terstruktur, lalu cocokkan lokasi visual. Apabila mesin hanya melihat teks OCR, jelaskan batas ini alih-alih menyatakan telah memeriksa seluruh layout.

**Sumber:** [Google, file prompting](https://ai.google.dev/gemini-api/docs/files); [Google, document processing](https://ai.google.dev/gemini-api/docs/document-processing); [NIST AI RMF](https://doi.org/10.6028/NIST.AI.600-1).