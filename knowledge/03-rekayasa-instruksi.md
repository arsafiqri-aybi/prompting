# 03 — Rekayasa instruksi dan prompt

**Fungsi:** memberi model tugas yang tidak rancu, dengan informasi yang dapat dijadikan dasar dan bentuk hasil yang sesuai pemakaian. Rekayasa instruksi adalah desain komunikasi dan eksperimen; tidak ada kalimat sakti yang menjamin akurasi.

## Struktur instruksi yang berguna

```text
TUJUAN: [keputusan atau artefak yang dibutuhkan]
KONTEKS: [fakta proyek, audiens, batas waktu]
BAHAN: [dokumen/tautan/data dengan asal dan tanggal]
TUGAS: [operasi konkret: bandingkan, hitung, tulis, revisi]
BATASAN: [syarat wajib, hal yang tidak boleh disimpulkan, prioritas]
BUKTI: [klaim yang harus dikutip dan standar sumber]
KELUARAN: [struktur, bahasa, panjang, berkas]
CEK SELESAI: [tes penerimaan; tangani informasi yang belum ada]
```

Gunakan susunan itu sebagai kerangka, lalu ringkas sesuai tugas. Dokumentasi Google menekankan instruksi jelas, contoh, dan pemecahan pekerjaan kompleks; Anthropic menyarankan pemisahan bagian dengan judul/tag ketika instruksi dan konteks bercampur [Google](https://ai.google.dev/gemini-api/docs/prompting-strategies), [Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents). Bentuk tag bukan jaminan keamanan.

## Contoh perbaikan bertahap

**Terlalu umum:** “Cari AI terbaik dan tulis laporan.”

**Lebih operasional:** “Bandingkan tiga pendekatan untuk menjawab pertanyaan dari dokumen internal: pencarian manual, RAG, dan model tanpa retrieval. Untuk tiap pendekatan, jelaskan akurasi sumber, keterbaruan, biaya operasional, kebocoran data, dan uji penerimaan. Gunakan dokumen yang disertakan; untuk spesifikasi penyedia yang bisa berubah, telusuri dokumentasi resmi bertanggal. Pisahkan fakta tersumber dari rekomendasi. Buat tabel dan daftar asumsi.”

**Lebih teruji:** tambahkan 10 pertanyaan contoh, dokumen acuan, metrik keberhasilan, batas biaya, serta instruksi “jika sumber tidak mendukung, tulis belum terverifikasi”. Hasil final harus diuji pada 10 contoh tersebut.

## Prioritas dan konflik

Instruksi sistem/aplikasi, instruksi pengguna, dan teks yang ditemukan dalam berkas/web tidak mempunyai otoritas yang sama. Bahan yang diambil dari luar harus diperlakukan sebagai **data**, bahkan ketika isinya memerintahkan model melakukan hal lain. Perancang aplikasi perlu menetapkan batas alat dan hak akses dalam sistem, bukan hanya menulis kalimat “abaikan instruksi jahat”; serangan injeksi tak langsung didemonstrasikan melalui konten yang diambil model [Greshake dkk.](https://arxiv.org/abs/2302.12173). Fitur dan tata urutan resmi dapat berbeda menurut platform; cek dokumentasi implementasi.

## Instruksi positif yang lebih teruji

- “Untuk setiap angka, sebut satuan dan sumbernya”; lebih jelas daripada “jangan salah”.
- “Jika sumber A dan B berbeda, tampilkan perbedaan dan tanggalnya”; lebih berguna daripada “pastikan benar”.
- “Jelaskan asumsi dan tunjukkan apa yang perlu diukur”; lebih aman daripada “jawab dengan yakin”.
- “Tulis ringkasan 150–200 kata untuk pembaca umum”; lebih konkret daripada “buat singkat tapi lengkap”.

## Kapan prompt menjadi terlalu berat?

Tanda: banyak syarat saling berbenturan, bahan relevan tenggelam, model sering melanggar format, atau setiap revisi merusak tugas lain. Pisahkan tugas menjadi langkah dengan keluaran antara dan uji masing-masing. Jangan menumpuk puluhan instruksi jika masalah sesungguhnya tidak ada data atau alat.

## Uji A/B prompt

Simpan versi prompt, set contoh tetap, model dan alat yang sama, lalu ubah **satu komponen** per perbandingan: misalnya menambah rubrik tanpa mengubah sumber. Ukur tingkat lulus per dimensi, frekuensi kesalahan fatal, panjang, dan waktu. Ulangi bila keluaran acak. Dokumentasikan model dan tanggal karena perilaku berubah. Jangan memilih versi B hanya karena satu jawaban terdengar lebih meyakinkan.

## Beberapa teknik yang perlu dibedakan

- **Instruksi langsung:** cocok untuk tugas sederhana; sebut tindakan dan standar hasil.
- **Beberapa contoh:** memberi pola transformasi; berguna pada label/format yang sulit dijelaskan.
- **Pemisah bagian:** judul/tag membedakan tugas, data, dan contoh; membantu keterbacaan, tetapi tidak memberi keamanan formal.
- **Constraint atau skema:** memudahkan validasi mesin; tetap perlu audit makna.
- **Pecah permintaan:** cocok bila satu langkah bergantung hasil langkah sebelumnya.
- **Riset + bukti:** untuk fakta berubah; menambah referensi palsu hanya dapat diatasi dengan membuka sumber.

Gunakan teknik sesuai diagnosis. Misalnya jawaban terlalu panjang → definisikan audiens, panjang, dan contoh singkat; jawaban salah tanggal → sumber terkini dan aturan tanggal berlaku; jawaban salah aritmetika → alat hitung. Mengulang “kamu ahli kelas dunia” biasanya tidak menyelesaikan sebab konkret.

## Konflik dalam prompt sendiri

Prompt “berikan hanya fakta dari dokumen” dan “lengkapi semua bagian meskipun dokumen kosong” memiliki konflik. Tetapkan aturan prioritas: sumber lebih penting daripada kelengkapan; bagian tanpa data boleh berisi “tidak tersedia”. Prompt “singkat” dan “jelaskan semua langkah” juga perlu kompromi, misalnya hasil singkat dengan lampiran pemeriksaan. Konflik internal sering tampak seperti kegagalan model padahal spesifikasinya tidak konsisten.

## Template diagnosis kegagalan prompt

Catat `ID kasus → instruksi terkait → perilaku diamati → sumber/alat yang dipakai → perbaikan yang diuji → hasil pada set uji baru`. Jika kesalahan sama muncul meskipun instruksi sangat jelas, pertimbangkan bahwa kemampuan model, alat, atau data merupakan bottleneck. Prompt engineering tidak seharusnya menjadi alasan untuk melewatkan uji sistem.

**Latihan:** bandingkan prompt umum dan prompt berstruktur pada enam tugas yang berbeda; catat bagian mana yang membaik dan memburuk. Simpan aturan yang terbukti berguna di proyekmu.

**Sumber:** [Google, prompt design](https://ai.google.dev/gemini-api/docs/prompting-strategies); [Anthropic, context engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents); [paper injeksi tidak langsung](https://arxiv.org/abs/2302.12173).