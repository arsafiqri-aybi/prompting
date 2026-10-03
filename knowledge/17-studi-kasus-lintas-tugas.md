# 17 — Studi kasus utuh: dari permintaan ke hasil yang dapat diaudit

Studi kasus di bawah adalah **rancangan kerja dan contoh hipotetis**, bukan eksperimen pengguna yang telah dilaksanakan. Gunakan rubrik dan pengukuran nyata untuk menilai hasil di proyekmu.

## Kasus A — Riset desain website yang nyaman

**Masalah awal:** “Buat situs yang membuat semua pancaindra nyaman berdasarkan penelitian valid.”

**Langkah 1, perjelas batas:** layar dan speaker memengaruhi penglihatan/pendengaran, interaksi perangkat memengaruhi sentuhan/persepsi tubuh; klaim bau dan rasa fisik memerlukan medium di luar halaman web. Kenyamanan berbeda antar orang. Tentukan audiens, perangkat, tugas, dan risiko desain; jangan menyimpulkan efek universal.

**Langkah 2, rencana bukti:** cari penelitian asli untuk klaim persepsi, panduan resmi untuk aksesibilitas, dan data pengguna lokal. Simpan pertanyaan, metode, sampel, pembanding, hasil, batasan, tanggal. Untuk setiap prinsip seperti kendali animasi, bedakan “rekomendasi desain yang masuk akal” dari “efek yang telah diukur pada populasi target”.

**Langkah 3, permintaan terstruktur:**

```text
Tujuan: buat dua alternatif beranda layanan untuk ponsel.
Audiens: pembaca berbahasa Indonesia; karakteristik lain belum diketahui.
Bahan: ringkasan wawancara [ID dan tanggal], peta konten [versi], sumber penelitian [URL].
Prioritas: keberhasilan tugas, aksesibilitas, kendali atas suara/animasi.
Hasil: tabel keputusan–alasan–bukti–risiko–uji; dua wireframe teks.
Larangan klaim: jangan nyatakan nyaman bagi semua atau mereproduksi bau/rasa.
Ketidakpastian: identifikasi asumsi dan data pengguna yang masih dibutuhkan.
```

**Langkah 4, uji:** pengguna mencoba menemukan informasi layanan dan menyelesaikan formulir; catat keberhasilan, waktu, kesalahan, kebingungan, dan pengalaman pengguna yang relevan. Inspeksi dengan keyboard/pembaca layar. Bandingkan dua alternatif pada tugas sama, catat konteks dan jumlah partisipan. Bila sampel kecil, jangan gunakan kata “terbukti universal”.

**Kegagalan yang bisa ditangkap:** referensi psikologi tidak mendukung kesimpulan, animasi nyaman untuk sebagian tetapi mengganggu sebagian lain, ilustrasi terlihat bagus tetapi navigasi gagal. Hubungkan hasilnya dengan ilmu `02`, `07`, `12`, `16`.

## Kasus B — Ringkasan penelitian dari lima PDF

**Tujuan:** menjawab satu pertanyaan riset dengan penelusuran sumber. **Alur:** inventaris judul/versi → ekstraksi metode dan hasil dengan nomor halaman → tabel per studi → identifikasi konflik → sintesis yang tidak melampaui data → audit lima klaim penting. Jika satu PDF berupa pindai dan tabelnya tak terbaca, perbaiki OCR atau tandai belum diverifikasi sebelum menghitung. Output minimum: pertanyaan, kriteria pencarian, tabel studi, kesimpulan, batas, dan tautan ke bahan asli.

**Tes penerimaan:** semua referensi ditemukan; halaman mendukung kutipan; jumlah studi dan peserta benar; hasil kontradiktif tidak disembunyikan; dokumen yang tak terbaca diberi label. Tolak hasil bila model mengarang halaman atau metode. Hubungkan `04`, `07`, `08`, `10`, `13`.

## Kasus C — Kode untuk kalkulator estimasi biaya

**Tujuan:** membuat fungsi yang menghitung biaya dari jumlah unit × tarif dengan pajak dan diskon. **Spesifikasi:** tipe input, mata uang, aturan pembulatan, nilai nol/negatif, batas maksimum, tarif yang berlaku, dan siapa pemilik data tarif. **Alur:** tulis contoh input-output → implementasi kecil → jalankan tes batas → tinjau hasil manual → dokumentasi dan berkas.

**Tes penerimaan:** 100 unit × Rp2.000 = Rp200.000 sebelum penyesuaian; diskon/pajak mengikuti urutan yang disetujui; nilai negatif ditolak; total dari alat cocok dengan perhitungan manual pada tiga contoh; pesan galat dapat dipahami. Tidak cukup mengatakan “kode selesai”; file dan tes harus ada. Hubungkan `02`, `09`, `12`, `15`.

## Kasus D — Pertanyaan informasi yang baru berubah

**Tujuan:** mengetahui aturan layanan yang berlaku pada tanggal tertentu. **Alur:** cari dokumen resmi terkini → catat tanggal berlaku, pembaruan, dan wilayah → bandingkan dengan arsip lama → jelaskan perubahan dan ketidakpastian → anjurkan pemeriksaan ahli bila konsekuensi hukum/keuangan tinggi. Jangan mengandalkan jawaban generik dari model tanpa sumber bertanggal. Hindari menarik aturan suatu negara ke negara lain. Hubungkan `07`, `11`, `13`, `16`.

## Matriks diagnosis lintas kasus

| Gejala | Kemungkinan sebab | Perubahan pertama yang layak diuji |
|---|---|---|
| Jawaban fasih tetapi salah tahun | sumber usang/tidak dibuka | cari sumber resmi terbaru |
| Kutipan ada tetapi tak mendukung | generasi melampaui bukti | audit klaim ↔ petikan |
| Format benar, kesimpulan buruk | rubrik hanya struktural | tambah penilai semantis |
| Model berkali-kali mengulang kesalahan | tak ada umpan balik baru | berikan data/tes eksternal |
| Alur lama dan mahal | terlalu banyak langkah | hapus tahap yang tak meningkatkan skor |

**Bacaan penghubung:** [RAG](https://arxiv.org/abs/2005.11401); [evaluasi agen](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents); [NIST GenAI Profile](https://doi.org/10.6028/NIST.AI.600-1).