# 00 — Peta ilmu dan metode belajar

**Tujuan:** memahami mengapa suatu interaksi AI menghasilkan jawaban tertentu, lalu mengubah prosesnya secara terukur. **Cakupan:** terutama AI generatif berbasis model bahasa, termasuk saat model membaca berkas, mencari informasi, memakai alat, atau bekerja sebagai agen. **Diperbarui:** 24 September 2026. Dokumen ini merupakan sintesis naratif sumber primer dan eksperimen praktis yang diusulkan, bukan telaah sistematis atau jaminan bahwa satu teknik akan unggul pada semua model.

## Model mental kerja

Hasil yang berguna muncul dari rangkaian keputusan: `(tujuan dan kriteria) → (model dan kemampuan) → (instruksi + konteks + data) → (pencarian atau alat) → (keluaran) → (pemeriksaan) → (perbaikan)`. Perbaikan prompt hanyalah salah satu tuas. Jika data masukan keliru, pencarian gagal, alat tidak tepat, atau penilaiannya lemah, merapikan kalimat prompt saja tidak cukup. Ini selaras dengan pemisahan tugas, uji, penilai, jejak, dan hasil nyata dalam praktik evaluasi agen [Anthropic, *Demystifying evals*](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents).

## Tiga tingkat yang perlu dibedakan

| Tingkat | Pertanyaan | Keahlian utama | Bukti bahwa kamu menguasainya |
|---|---|---|---|
| Pengguna terampil | Apa yang harus kutanyakan dan kuberikan? | spesifikasi, konteks, sumber, umpan balik | keluaran memenuhi rubrik dan dapat ditelusuri |
| Perancang alur | Bagaimana tugas berulang menjadi andal? | pencarian, alat, pemeriksaan, evaluasi, pengamanan | uji pada kasus normal dan sulit, hasil dapat diulang |
| Peneliti model | Mengapa model memiliki perilaku tersebut? | probabilitas, Transformer, pelatihan, inferensi, evaluasi kausal | dapat membaca paper dan menguji hipotesis mekanisme |

Fokus kumpulan ini dua tingkat pertama, dengan dasar teknis yang cukup untuk memahami keterbatasannya. [Transformer](https://arxiv.org/abs/1706.03762), [few-shot learning](https://arxiv.org/abs/2005.14165), dan [pelatihan mengikuti instruksi](https://arxiv.org/abs/2203.02155) memberi landasan tingkat ketiga.

## Cara membaca folder

1. Baca `01`–`04` untuk memahami mesin, tujuan, instruksi, dan konteks.
2. Baca `05`–`10` untuk mendesain contoh, penalaran, riset, RAG, alat, dan input multimodal.
3. Baca `11`–`16` untuk memilih konfigurasi, mengevaluasi, memverifikasi, mengiterasi, mengorkestrasi, dan mengamankan.
4. Gunakan `17`–`18` untuk studi kasus, templat, dan latihan; baca `19` untuk menilai sumber.

## Metode riset yang dipakai

Utamakan paper yang memperkenalkan metode atau eksperimen, dokumentasi resmi pembuat teknologi untuk perilaku produk, serta panduan risiko dari lembaga/komunitas yang bertanggung jawab. Bedakan: **hasil percobaan** (terbatas pada model, tugas, data, dan waktu penelitian), **panduan penyedia** (praktik untuk produknya, dapat berubah), dan **saran kerja** (hipotesis operasional yang harus kamu uji sendiri). Jangan mengubah hasil pada satu benchmark menjadi hukum umum. Untuk standar risiko, baca [NIST AI 600-1](https://doi.org/10.6028/NIST.AI.600-1); untuk ancaman aplikasi LLM, baca [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/).

## Eksperimen dasar yang dapat kamu ulang

Pilih satu tugas nyata, misalnya menulis ringkasan penelitian pengalaman pengguna. Simpan 10 contoh input yang beragam: mudah, ambigu, panjang, usang, data bertentangan, dan dokumen berisi instruksi asing. Tetapkan rubrik sebelum mencoba model: akurasi 0–4, ketercakupan 0–4, dukungan sumber 0–4, format 0–2, serta kesalahan fatal ya/tidak. Jalankan versi A (permintaan biasa) dan B (spesifikasi, konteks, bukti, format) pada input yang sama; catat model, tanggal, alat, dan revisi prompt. Nilai tanpa melihat label A/B jika memungkinkan. Hitung juga waktu/biaya, karena hasil sedikit lebih baik bisa jadi tidak sepadan dengan proses yang jauh lebih mahal. Langkah ini adalah rancangan latihan, bukan hasil empiris yang telah diuji.

## Aturan membaca klaim di setiap berkas

- **Dapat dibuktikan:** contoh hitungan, kutipan, identitas, harga, tanggal, klaim medis/hukum/keuangan; uji terhadap sumber primer atau alat yang tepat.
- **Subjektif:** gaya, selera, kreativitas; uji dengan audiens dan contoh yang mewakili, bukan satu penilai saja.
- **Bergantung sistem:** ukuran konteks, parameter inferensi, fitur model, kebijakan data; cek dokumentasi versi yang dipakai.
- **Ketidakpastian:** bila bukti tidak cukup, keluaran yang baik bisa berupa pertanyaan, batas pengetahuan, atau keputusan untuk tidak menyimpulkan.

**Latihan awal:** tulis spesifikasi satu halaman untuk masalah nyata: pengguna, keluaran, lima syarat wajib, tiga kesalahan fatal, sumber yang tersedia, dan uji penerimaan. Terapkan pada templat `18` dan bandingkan dengan prompt awalmu.

**Bacaan lanjutan:** [Google, strategi desain prompt](https://ai.google.dev/gemini-api/docs/prompting-strategies); [Anthropic, rekayasa konteks](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents); [bibliografi beranotasi](19-bibliografi-beranotasi.md).