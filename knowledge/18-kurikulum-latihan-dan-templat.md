# 18 — Kurikulum 12 minggu dan templat siap pakai

**Tujuan belajar:** pada akhir latihan, kamu bisa mendefinisikan pekerjaan AI, memilih bahan/alat, mengaudit hasil, dan menunjukkan peningkatan di set uji yang belum dipakai untuk menyusun prompt. Durasi bisa disesuaikan; proyek nyata lebih penting daripada mengikuti kalender secara kaku.

## Peta latihan

| Minggu | Fokus | Hasil yang harus disimpan | Uji minimum |
|---|---|---|---|
| 1 | tujuan dan rubrik | brief satu halaman, 10 kasus | dua pembaca sepakat arti “lulus” |
| 2 | cara kerja model | diagram alur dan catatan kegagalan | bedakan pengetahuan internal, konteks, alat |
| 3 | prompt dan contoh | versi A/B + log perubahan | uji kasus normal dan negatif |
| 4 | berkas dan konteks | peta keputusan/sumber | satu konflik versi ditemukan |
| 5 | literasi bukti | matriks 10 klaim ↔ sumber | semua URL dibuka dan mendukung |
| 6 | RAG | 15 pertanyaan dokumen | pisahkan salah retrieval dan generasi |
| 7 | alat | skrip atau kalkulator sederhana | 3 contoh manual cocok |
| 8 | dokumen multimodal | ekstraksi PDF/gambar | 5 bagian sulit diaudit |
| 9 | konfigurasi | dua model/versi diuji | biaya per kasus lulus dicatat |
| 10 | evaluasi | 30 kasus dengan skor | kasus baru tetap diuji |
| 11 | keamanan | kasus injeksi dan data sensitif | tidak ada aksi tak berizin |
| 12 | proyek akhir | laporan metode, artefak, batas | penilai lain dapat mengulang uji |

## Templat A — Brief pekerjaan

```markdown
# Brief AI — [judul]
Keputusan yang dibantu:
Pengguna hasil dan tingkat pengetahuannya:
Ruang lingkup, waktu, lokasi:
Bahan tersedia + versi + hak pakai:
Output yang akan dipakai:
Syarat wajib (urut prioritas):
Kesalahan fatal:
Asumsi yang boleh dibuat:
Hal yang harus ditanyakan dahulu:
Siapa mengesahkan hasil:
```

## Templat B — Prompt berbasis bukti

```text
Tugas: [kata kerja + objek + pemakaian akhir].
Konteks: [pengguna, batas, keputusan terdahulu].
Bahan: [dokumen/URL/ID, tanggal, versi].
Kerjakan: [1 ekstraksi; 2 sintesis; 3 uji kontradiksi].
Untuk setiap klaim penting, berikan [tautan/halaman/baris] yang mendukung.
Pisahkan fakta sumber, inferensi, dan rekomendasi.
Jika sumber kurang, tulis pertanyaan atau status "belum terverifikasi".
Hasil dalam: [tabel/berkas/skema].
Sebelum selesai, cek: [daftar penerimaan].
```

## Templat C — Audit jawaban

```markdown
| ID klaim | Klaim persis | Sumber asli & lokasi | Dukungan (langsung/sebagian/tidak ada) | Risiko bila salah | Tindakan |
|---|---|---|---|---|---|
```

Jangan isi lokasi dengan halaman yang ditebak. Jika tidak ada bukti, tulis “tidak ditemukan”.

## Templat D — Set uji dan hasil eksperimen

```markdown
Model/versi/tanggal:
Prompt dan alat yang diizinkan:
Dokumen dan versinya:
Kasus: ID, tipe, input, jawaban acuan atau rubrik, tingkat risiko.
Metrik: jumlah lulus, kesalahan fatal, biaya per lulus, waktu.
Hasil A/B: skor per kategori dan kegagalan spesifik.
Keputusan: apa yang berubah, mengapa, kapan diuji ulang.
```

## Templat E — Serah terima proyek panjang

```markdown
Tujuan dan kriteria selesai:
Sudah dilakukan (dengan bukti):
Keputusan final (tanggal dan pemilik):
Sumber/berkas dan versi terkini:
Hal terbuka, konflik, serta dugaan:
Langkah berikut yang dapat diuji:
Larangan tindakan / kebutuhan izin:
```

## Templat F — Umpan balik yang dapat ditindaklanjuti

```text
Pada bagian [lokasi], keluaran menyatakan [klaim].
Masalahnya [jenis + bukti pembanding].
Dampaknya [mengubah keputusan apa].
Ubah menjadi [perubahan spesifik] sambil mempertahankan [bagian benar].
Jalankan ulang [tes lama] dan [tes baru] lalu laporkan hasilnya.
```

## Proyek akhir

Ambil pekerjaan nyata, misalnya panduan desain dari riset pengguna. Serahkan brief, kumpulan sumber, log pencarian, versi prompt, artefak hasil, 30 kasus uji, tabel skor, 5 audit klaim, daftar risiko, dan keputusan “siap/tidak siap” dengan alasan. Orang lain harus bisa memeriksa hasil tanpa mengandalkan keyakinanmu terhadap kefasihan AI.

**Rujukan metode:** [Google, prompt](https://ai.google.dev/gemini-api/docs/prompting-strategies); [Anthropic, evaluasi agen](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents); [HELM](https://arxiv.org/abs/2211.09110).