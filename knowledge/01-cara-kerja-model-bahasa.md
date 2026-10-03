# 01 — Bagaimana jawaban model bahasa terbentuk

**Pertanyaan inti:** apa yang terjadi dari teks pengguna sampai jawaban keluar, dan apa akibatnya bagi mutu hasil?

## Alur konseptual

1. **Tokenisasi:** input dipecah menjadi unit model, yang dapat berupa kata, bagian kata, tanda baca, atau unsur lain. Banyak model multimodal juga memproses representasi nonteks. Panjang konteks dihitung dalam token, bukan jumlah halaman.
2. **Representasi:** token dan informasi posisi diubah menjadi vektor; lapisan Transformer memakai perhatian untuk menggabungkan informasi dari posisi lain. Paper asli memperkenalkan Transformer untuk tugas urutan; rincian model produk modern dapat berbeda [Vaswani dkk.](https://arxiv.org/abs/1706.03762).
3. **Pelatihan:** pada model bahasa autoregresif, parameter disesuaikan agar memberi probabilitas tinggi pada kelanjutan teks dalam data latihan. Kemampuan mengikuti contoh di dalam prompt dapat muncul tanpa memperbarui parameter saat inferensi [Brown dkk.](https://arxiv.org/abs/2005.14165).
4. **Penyelarasan instruksi:** demonstrasi manusia dan preferensi dapat dipakai untuk melatih model agar keluaran lebih sesuai dengan maksud pengguna; ini meningkatkan kegunaan, tetapi tidak membuat setiap klaim otomatis benar [Ouyang dkk.](https://arxiv.org/abs/2203.02155).
5. **Inferensi:** sistem memilih token keluaran satu demi satu sesuai distribusi yang dihitung model dan aturan decoding. Jawaban jadi rangkaian generasi yang dipengaruhi instruksi, konteks, alat, konfigurasi, serta variasi antar percobaan.

Secara ringkas, sebuah model autoregresif memperkirakan `P(token_berikutnya | token_sebelumnya, konteks, parameter_model)`. Rumus ini menggambarkan mekanisme keluaran, **bukan** definisi lengkap kemampuan bernalar, dan tidak membuktikan model memiliki pengalaman sadar. Bahasa seperti “AI berpikir” berguna sebagai metafora kerja; teks penjelasan langkah model juga tidak otomatis merupakan rekaman setia proses internalnya [Lanham dkk.](https://arxiv.org/abs/2307.13702).

## Empat sumber jawaban yang sering tercampur

| Sumber | Contoh | Risiko | Cara memeriksa |
|---|---|---|---|
| Parameter hasil pelatihan | definisi umum | usang, salah, bias | cek sumber terbaru untuk klaim penting |
| Konteks percakapan/berkas | keputusan proyek yang disertakan | terpotong, ambigu, bertentangan | tandai bagian relevan dan asalnya |
| Keluaran alat | hasil pencarian, kalkulator, program | alat gagal; sumber buruk | periksa log alat dan hasil sebenarnya |
| Generalisasi/generasi | ide, ringkasan, dugaan | tambahan tanpa dukungan | pisahkan fakta dan saran/inferensi |

Perbedaan ini menjelaskan mengapa model dapat tampak yakin terhadap referensi yang tidak ada. Dalam satu studi pada pertanyaan domain spesifik, referensi yang dikarang model sering tidak mendukung klaim; angka studinya tidak boleh digeneralisasi ke semua model dan tugas [Zuccon dkk.](https://arxiv.org/abs/2309.09401).

## Mengapa permintaan yang sama bisa berubah hasilnya?

Instruksi dapat ditafsirkan berlainan, konteks dapat berubah, sampling bisa menghasilkan token berbeda, dan sistem/versi model dapat diperbarui. Stabilitas output tidak sama dengan kebenaran: jawaban yang konsisten bisa konsisten salah. Sebaliknya, variasi tidak selalu buruk pada tugas kreatif. Lakukan pengulangan dan uji pada contoh yang mewakili sebelum menilai suatu teknik.

## Implikasi praktis

- Untuk **fakta terbaru**, pasok sumber yang dapat diverifikasi; jangan anggap pengetahuan hasil pelatihan sebagai basis data waktu nyata.
- Untuk **angka**, minta perhitungan dengan alat dan periksa satuan, asumsi, serta hasil akhir.
- Untuk **dokumen panjang**, jangan berasumsi seluruh isinya digunakan sama baiknya; performa bisa berubah menurut posisi bukti [Liu dkk.](https://arxiv.org/abs/2307.03172).
- Untuk **keputusan penting**, nilai kualitas bukti dan verifikasi hasil di luar teks jawaban.

## Diagnostik satu menit

Jika jawaban buruk, tanyakan: Apakah masalahnya salah memahami tujuan, kehilangan konteks, tidak memiliki fakta, salah perhitungan, salah menggunakan alat, atau penilaian hasil yang kabur? Pilih perbaikan berdasarkan sumber kegagalannya. Prompt yang lebih panjang tidak memperbaiki sumber yang tidak ada.

## Apa yang sebenarnya berubah saat kamu memberi prompt?

Pada percakapan biasa, kamu tidak mengedit bobot model. Kamu mengubah **kondisi masukan** yang dipakai model untuk menghitung kelanjutan. Contoh dalam prompt dapat menggeser penafsiran tugas, sementara dokumen dapat menjadi sumber fakta yang dipakai pada saat itu. Ini menjelaskan perbedaan antara *in-context learning*, pelatihan lanjutan/fine-tuning, dan retrieval. Fine-tuning mengubah parameter melalui proses pelatihan tersendiri; RAG memilih teks eksternal saat inferensi; memori aplikasi menyimpan informasi di luar parameter, lalu mungkin memasukkannya lagi ke konteks. Cara implementasi tiap produk bisa berbeda.

## Perbedaan model, produk, dan alur kerja

Satu chatbot mungkin memadukan model bahasa, filter keamanan, instruksi aplikasi, pencarian web, penyimpanan percakapan, dan konektor. Dari respons yang tampak, kamu tidak selalu tahu komponen mana yang menyebabkan perbaikan. Jika ingin menyimpulkan “model X lebih akurat”, kontrol sumber, alat, prompt, dan cara penilaian; jika tidak, sebut “sistem X pada konfigurasi ini”. Hal ini penting saat membandingkan produk yang memiliki akses data berbeda.

## Demonstrasi mini: fakta tidak ada dalam konteks

Misalkan sebuah model ditanya “siapa pemilik keputusan UX versi 4?” tanpa dokumen proyek. Ada tiga respons yang mungkin: menebak nama, menjelaskan tidak memiliki data, atau mencari berkas proyek bila alat tersedia. Hanya dua yang terakhir mempertahankan keterlacakan. Setelah dokumen diberikan, uji apakah model menemukan **nama, tanggal, dan versi**; nama yang benar dari dokumen lama tetap bisa salah untuk keputusan sekarang.

## Batas penjelasan mekanisme

Deskripsi alur token membantu memprediksi jenis kegagalan, tetapi tidak menunjukkan seluruh algoritme internal setiap model tertutup. Kapasitas penalaran, pilihan jalur respons, dan tahap pelatihan dapat berbeda. Jika ingin menguji mekanisme, rumuskan hipotesis yang dapat dipatahkan: “memindahkan bukti dari tengah ke awal dokumen meningkatkan ekstraksi pada sistem ini”. Uji dengan pasangan dokumen yang isinya sama, ubah hanya posisi bukti, ulangi pada beberapa kasus. Jangan menyimpulkan niat, pemahaman, atau kesadaran hanya dari satu teks keluaran.

**Latihan:** minta AI menjelaskan sebuah topik yang kamu kuasai dalam tiga kondisi: tanpa bahan, dengan dua bahan yang saling bertentangan, dan dengan dokumen sumber bertanggal. Catat mana yang berasal dari sumber dan mana yang berupa dugaan. Jangan pakai hasil ini untuk mengambil keputusan berisiko tanpa verifikasi.

**Sumber utama:** [Transformer](https://arxiv.org/abs/1706.03762); [few-shot](https://arxiv.org/abs/2005.14165); [RLHF](https://arxiv.org/abs/2203.02155); [ketepatan penjelasan penalaran](https://arxiv.org/abs/2307.13702).