# Prompting

Kumpulan kajian berbahasa Indonesia tentang cara **merancang, memperoleh, memeriksa, dan memperbaiki** jawaban serta artefak AI. Fokus pada pengguna dan perancang alur AI generatif: hasil yang benar, berguna, relevan, dapat ditelusuri, dan aman. **Tanggal penyusunan: 24 September 2026.** Dokumentasi produk dapat berubah; periksa versi saat digunakan.

## Mulai dari mana?

Jika kamu hanya punya satu jam: baca `00`, `02`, `03`, `07`, `12`, lalu gunakan templat `18`. Jika akan membuat sistem dari dokumen: tambahkan `04`, `08`, `09`, `13`, `16`. Jika ingin paham “di balik jawaban”: mulai `01`, lanjutkan `06`, `11`, `20`.

## Daftar isi

| No. | Berkas | Pertanyaan yang dijawab |
|---:|---|---|
| 00 | [Peta ilmu dan metode](00-peta-ilmu-dan-metode.md) | apa lingkup, bukti, dan cara belajar? |
| 01 | [Cara kerja model bahasa](01-cara-kerja-model-bahasa.md) | bagaimana teks dan konteks menjadi keluaran? |
| 02 | [Perumusan masalah dan kriteria](02-perumusan-masalah-dan-kriteria.md) | apa arti hasil yang benar-benar baik? |
| 03 | [Rekayasa instruksi](03-rekayasa-instruksi.md) | bagaimana memberi tugas secara jelas? |
| 04 | [Konteks, memori, dan berkas](04-konteks-memori-dan-berkas.md) | bahan apa yang harus dibawa ke model? |
| 05 | [Contoh dan format keluaran](05-contoh-dan-format-keluaran.md) | kapan contoh dan skema membantu? |
| 06 | [Penguraian tugas dan penalaran](06-penguraian-tugas-dan-penalaran.md) | kapan pekerjaan perlu dipisah dan diuji? |
| 07 | [Riset sumber dan literasi bukti](07-riset-sumber-dan-literasi-bukti.md) | bagaimana mendapatkan fakta yang dapat dipercaya? |
| 08 | [RAG dan pengetahuan eksternal](08-rag-dan-pengetahuan-eksternal.md) | bagaimana menjawab dari dokumen? |
| 09 | [Alat, perhitungan, dan eksekusi](09-alat-perhitungan-dan-eksekusi.md) | kapan AI perlu mencari, menghitung, atau bertindak? |
| 10 | [Multimodal dan dokumen visual](10-multimodal-dan-dokumen-visual.md) | apa batas membaca gambar, audio, video, PDF? |
| 11 | [Model dan konfigurasi](11-pemilihan-model-dan-konfigurasi.md) | sistem mana sesuai kebutuhan dan biaya? |
| 12 | [Evaluasi dan eksperimen](12-evaluasi-rubrik-dan-eksperimen.md) | apakah ada perbaikan yang terukur? |
| 13 | [Verifikasi dan kalibrasi](13-verifikasi-fakta-dan-kalibrasi.md) | bagaimana menghindari klaim palsu? |
| 14 | [Iterasi dan kolaborasi](14-iterasi-umpan-balik-dan-kolaborasi.md) | bagaimana umpan balik membuat hasil membaik? |
| 15 | [Agen dan orkestrasi](15-agen-dan-orkestrasi.md) | bagaimana tugas banyak langkah dijalankan? |
| 16 | [Keamanan, privasi, risiko](16-keamanan-privasi-dan-risiko.md) | apa yang harus diamankan dan diuji? |
| 17 | [Studi kasus lintas tugas](17-studi-kasus-lintas-tugas.md) | bagaimana menerapkan seluruh ilmu dalam pekerjaan nyata? |
| 18 | [Kurikulum dan templat](18-kurikulum-latihan-dan-templat.md) | bagaimana belajar dan mempraktikkannya? |
| 19 | [Bibliografi beranotasi](19-bibliografi-beranotasi.md) | sumber mana mendukung tiap konsep dan apa batasnya? |
| 20 | [Pondasi ilmu pendukung](20-pondasi-ilmu-pendukung.md) | bidang lain apa yang menjelaskan kualitas hasil? |
| 21 | [Glosarium dan diagnosis cepat](21-glosarium-dan-diagnosis-cepat.md) | apa arti istilah dan cara menemukan sumber kegagalan? |

**Total:** 22 bab bertema + README, masing-masing Markdown terpisah. Setiap bab dapat dibaca sendiri tetapi saling merujuk; bibliografi memuat sumber primer dan catatan batas bukti.

## Prinsip inti dalam satu halaman

1. Definisikan tujuan, pengguna hasil, data, format, dan kriteria penerimaan sebelum meminta jawaban.
2. Bedakan pengetahuan model, bahan yang kamu berikan, hasil alat, dan dugaan.
3. Ambil informasi terbaru dari sumber yang dapat diperiksa; telusuri klaim penting sampai bahan asli.
4. Gunakan alat untuk hitungan, pencarian, dan aksi; verifikasi **hasil aktual** alat.
5. Uji dengan kasus normal, sulit, dan negatif; bandingkan perubahan pada input yang sama.
6. Akui ketidakpastian dan hentikan klaim yang tidak didukung.
7. Lindungi data serta pisahkan konten asing dari instruksi yang berwenang.

## Klaim bukti dan batas

Kumpulan ini menggabungkan hasil empiris pada model/tugas tertentu, dokumentasi resmi yang dapat berubah, dan rekomendasi operasional yang perlu diuji pada penggunaanmu. Ia tidak membuktikan satu “prompt terbaik” untuk setiap model, atau bahwa AI benar-benar berpikir dan merasakan seperti manusia. Sumber awal yang berguna: [Transformer](https://arxiv.org/abs/1706.03762), [RAG](https://arxiv.org/abs/2005.11401), [Google Prompt Design](https://ai.google.dev/gemini-api/docs/prompting-strategies), [Anthropic Evals](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents), dan [NIST AI 600-1](https://doi.org/10.6028/NIST.AI.600-1).

## Cara memakai kumpulan ini sebagai data proyek

Pertahankan `README.md` sebagai indeks. Saat mengerjakan tugas tertentu, muat bab yang relevan dan dokumen proyek terkait; jangan selalu memasukkan seluruh folder ke setiap konteks. Simpan keputusan proyek dan versi sumber di berkas tersendiri. Perbarui bagian yang tergantung fitur produk saat model, API, atau kebijakan berubah. Jika hasil akan dipakai untuk keputusan penting, audit sumber dan mintalah peninjau yang kompeten sesuai bidang.