# 04 — Rekayasa konteks, memori, dan berkas proyek

**Fungsi:** memilih informasi yang benar, relevan, dan cukup bagi keputusan saat ini. Konteks adalah semua yang masuk ke model saat menjawab: instruksi, percakapan, berkas, hasil alat, serta keluaran sementara. Memori produk, bila tersedia, memiliki mekanisme dan batas tersendiri; jangan berasumsi semua percakapan selalu diingat.

## Prinsip yang diuji

Jendela konteks yang besar tidak berarti semua bagian dokumen dipakai merata. Pada beberapa eksperimen tanya jawab multidokumen dan pencarian pasangan nilai, kinerja turun ketika fakta relevan ada di tengah konteks panjang [Liu dkk., *Lost in the Middle*](https://arxiv.org/abs/2307.03172). Hasil ini bukan hukum universal untuk setiap model, dokumen, dan tugas. Anthropic menyarankan konteks dengan informasi bersinyal tinggi dan struktur jelas [*Effective context engineering*](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents).

## Pilih bahan dengan matriks kegunaan

| Jenis bahan | Sertakan jika | Simpan sebagai arsip jika |
|---|---|---|
| Tujuan dan definisi selesai | selalu untuk tugas kompleks | tugas sudah selesai dan aturan tidak dipakai lagi |
| Keputusan proyek | memengaruhi jawaban sekarang | digantikan keputusan terbaru dengan jejak versi |
| Dokumen rujukan | menjawab pertanyaan, dapat diperiksa asalnya | panjang tetapi tidak relevan |
| Riwayat percakapan | memuat persetujuan/koreksi aktif | basa-basi atau revisi usang |
| Hasil alat | menyediakan fakta atau bukti baru | duplikat, gagal, atau sudah tidak berlaku |

## Protokol berkas panjang

1. Inventaris: judul, pemilik, tanggal, versi, jenis, dan tingkat kepercayaan.
2. Cari bagian yang menjawab pertanyaan; pertahankan halaman/baris/URL yang bisa ditelusuri.
3. Kutip petikan secukupnya dan tandai keterbatasan ekstraksi tabel/gambar.
4. Jika banyak berkas, susun peta klaim ↔ bukti ↔ sumber ↔ tanggal; tampilkan konflik.
5. Setelah menjawab, cek dua atau tiga klaim penting langsung ke bahan asli.

Mengirim seluruh berkas tanpa memilih potongan bisa memboroskan ruang dan mempersulit verifikasi. Namun ringkasan terlalu agresif bisa menghapus pengecualian penting. Pilih strategi menurut tugas dan uji kehilangan informasi.

## Memori lintas sesi

Simpan fakta yang stabil (tujuan, istilah, audiens, keputusan desain) terpisah dari status yang cepat berubah (tanggal, harga, versi, siapa bertanggung jawab). Buat `DECISIONS.md` dengan tanggal dan alasan, `SOURCES.md` dengan URL/versi, serta `OPEN-QUESTIONS.md` berisi informasi belum tersedia. Saat pekerjaan diteruskan, perbarui ringkasan kerja: apa sudah selesai, bukti, keterbatasan, langkah berikutnya. Mengulang semua percakapan dari awal bisa membawa asumsi yang telah dibatalkan.

## Contoh paket konteks untuk proyek website

```text
Keputusan tetap: target pembaca Indonesia; prioritas aksesibilitas.
Pertanyaan saat ini: struktur beranda mana yang paling memudahkan pencarian layanan?
Sumber: hasil wawancara pengguna (tanggal, jumlah, metode); peta konten versi 2.
Batas: temuan lima pengguna adalah indikasi untuk desain, bukan estimasi populasi.
Output: dua alternatif wireframe tekstual, alasan dan rencana uji.
```

## Kegagalan yang perlu dicari

Versi lama disajikan sebagai final; sumber tanpa tanggal dipakai untuk keadaan sekarang; kutipan dokumen tak mendukung simpulan; model mengikuti instruksi yang tersembunyi di dalam dokumen. Atasi dengan metadata, pembatasan otoritas bahan, pencarian terarah, dan uji pada contoh konflik.

## Strategi merangkum tanpa kehilangan jejak

Ringkasan kerja tidak boleh hanya memuat “sudah dibahas”. Simpan keputusan dengan sumber/versi dan alasan, daftar hal terbuka, serta apa yang dibatalkan. Contoh ringkasan yang lebih baik: “Pada 24 September, tim memilih menu 4 item berdasarkan uji prototipe n=6; ini hipotesis sementara, belum diuji pembaca layar; opsi 6 item ditunda.” Ringkasan ini memungkinkan langkah berikutnya tanpa mengubah uji eksploratif menjadi fakta universal.

## Mengatasi konflik sumber

Berikan tingkat otoritas operasional: dokumen keputusan terbaru dari pemilik proyek untuk kebijakan internal, standar resmi untuk aturan berlaku, paper asli untuk hasil eksperimen, komentar lama untuk riwayat saja. Jika dua sumber sama-sama sah dan bertentangan, jangan diam-diam memilih. Tulis “versi A menyatakan X per tanggal D, versi B menyatakan Y per tanggal E”, lalu tentukan siapa yang berwenang menetapkan keadaan akhir. Mencampur paragraf dari dua versi berisiko menghasilkan kebijakan yang tidak pernah disetujui.

## Uji kehilangan konteks

Masukkan sebuah fakta acuan penting pada awal, tengah, dan akhir tiga dokumen yang sama panjang; jaga isi lain tetap. Mintalah ekstraksi lokasi bukti dan jawaban, ulangi beberapa kali. Jika performa berubah karena posisi, pertimbangkan pencarian terarah atau pemilihan kutipan lebih ringkas. Ini menguji sistemmu sendiri dan lebih berguna daripada menganggap hasil *Lost in the Middle* berlaku identik bagi setiap model.

**Latihan:** beri model 15 potongan dokumen, beberapa usang dan dua saling bertentangan. Bandingkan hasil “semua sekaligus” dengan “potongan relevan + metadata + pertanyaan eksplisit”. Nilai keterlacakan dan kesalahan, bukan hanya kerapian jawaban.

**Sumber:** [*Lost in the Middle*](https://arxiv.org/abs/2307.03172); [Anthropic, context engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents); [Google, long context](https://ai.google.dev/gemini-api/docs/long-context).