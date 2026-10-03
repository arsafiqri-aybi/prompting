# 15 — Agen, orkestrasi, dan alur beberapa langkah

**Fungsi:** mengatur kapan AI merencanakan, memilih alat, mengeksekusi, membaca hasil, memperbaiki kesalahan, dan berhenti. Agen adalah sistem dengan model + aturan + alat + keadaan/lingkungan; keberhasilannya tidak dapat dinilai dari kelancaran teks final saja. [ReAct](https://arxiv.org/abs/2210.03629) memberi salah satu contoh akademis interaksi penalaran dan tindakan; implementasi nyata bergantung pada izin dan lingkungan.

## Komponen minimum

**Pemicu** (tugas pengguna), **tujuan dan batas** (apa yang boleh dilakukan), **keadaan** (bahan dan kemajuan), **pemilih tindakan**, **alat**, **pemeriksa hasil**, **kondisi berhenti**, dan **jejak audit**. Tugas berakhir setelah keadaan tujuan tercapai, bukan setelah agen berkata “selesai”.

## Pola alur

| Pola | Contoh | Kapan dipakai |
|---|---|---|
| Satu alat lalu jawab | cari halaman resmi | satu pertanyaan faktual |
| Rantai | ekstrak → hitung → jelaskan | dependensi jelas |
| Bercabang | dua solusi desain → uji | ada alternatif sungguhan |
| Ulang terkontrol | revisi kode → jalankan tes | ada umpan balik objektif |
| Persetujuan sebelum tindakan | draf pesan → pemeriksaan orang | konsekuensi eksternal penting |

Jangan memakai banyak agen atau lapisan rencana hanya demi tampak canggih. Biaya dan kesalahan koordinasi meningkat ketika keadaan disalin, sumber berbeda versi, atau agen saling memperkuat dugaan. Mulai dengan satu alur yang dapat diaudit; pecah peran bila independensi atau spesialisasi terbukti membantu pada uji.

## Desain keadaan dan serah terima

Pada setiap tahap catat: input, sumber/versi, hasil, kesalahan, asumsi, keputusan berikut, dan bukti. Untuk tugas panjang, simpan keputusan stabil di berkas; jangan mengandalkan ingatan samar percakapan. Batasi ruang tindakan: alat baca dan tulis terpisah, parameter divalidasi, retry aman, dan aksi yang sulit dibalik membutuhkan pemeriksaan yang sesuai.

## Evaluasi agen

Ukur *end state*: file benar-benar ada, tes lulus, pesan tercatat bila memang dikirim, data tidak berubah di luar izin. Simpan jejak tindakan sehingga kegagalan bisa dilokalisasi. Dokumentasi [Anthropic tentang evals agen](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents) membedakan jawaban akhir dan keadaan lingkungan; gunakan prinsip itu juga untuk alur pribadimu.

## Satu contoh: menyusun kajian dari banyak sumber

Tahap 1: rumuskan pertanyaan dan standar bukti. Tahap 2: temukan sumber primer. Tahap 3: ekstrak hasil dan batas. Tahap 4: tulis naskah dengan klaim terhubung. Tahap 5: audit tautan, tanggal, dan sitasi. Tahap 6: simpan berkas dan periksa keberadaannya. Kegagalan pada tahap 2 tidak dapat “diperbaiki” dengan menulis lebih fasih pada tahap 4.

## Kondisi berhenti dan anggaran

Tentukan jumlah percobaan, waktu, dan biaya yang masuk akal. Contoh: cari maksimal lima sumber primer relevan sebelum menyimpulkan; bila belum cukup, catat celah bukti dan minta arahan, jangan menyatakan kesimpulan pasti. Untuk kode, batasi siklus tes/perbaikan dan tampilkan kegagalan terakhir bila masalah belum selesai. Anggaran mencegah agen berputar tanpa kemajuan, tetapi batas tidak boleh dipakai untuk menyembunyikan pekerjaan yang gagal.

## Keadaan yang cukup untuk melanjutkan pekerjaan

Serah terima minimal memuat tujuan, keputusan yang berlaku, versi berkas, hasil alat, kegagalan, asumsi, dan tindakan berikut. Jika hanya menyimpan ringkasan “sudah mencari sumber”, agen berikutnya mungkin mengulang pencarian atau memakai klaim tanpa dukungan. Simpan ID sumber dan lokasi serta alasan sumber lain ditolak. Hapus informasi sensitif yang tak dibutuhkan dari catatan.

## Perbedaan orkestrasi dan kolaborasi banyak agen

Satu alur dapat mengerjakan beberapa tahap secara berurutan tanpa memerlukan beberapa agen terpisah. Banyak agen bisa membantu bila riset sumber dan uji kode benar-benar independen, tetapi hasilnya masih harus disatukan, konflik diputuskan, dan sumber dibuktikan. Ukur apakah pembagian peran memperbaiki tingkat lulus setelah menghitung biaya koordinasi dan risiko duplikasi.

**Latihan:** buat alur untuk tugas 3 tahap yang sering kamu lakukan. Berikan satu kondisi berhenti dan satu tes pada setiap tahap; catat kapan alur harus meminta data baru.

**Sumber:** [ReAct](https://arxiv.org/abs/2210.03629); [Toolformer](https://arxiv.org/abs/2302.04761); [Anthropic, evaluasi agen](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents).