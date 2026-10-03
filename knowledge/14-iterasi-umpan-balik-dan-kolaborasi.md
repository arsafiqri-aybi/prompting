# 14 — Iterasi, umpan balik, dan kolaborasi manusia–AI

**Fungsi:** memperbaiki hasil berdasarkan kegagalan yang terlihat. Iterasi yang baik mengubah hipotesis dan menguji ulang; bukan sekadar meminta “buat lebih sempurna”. Paper [Self-Refine](https://arxiv.org/abs/2303.17651) meneliti perbaikan bertahap dengan umpan balik pada tugas yang diuji. Literatur koreksi diri juga memperingatkan bahwa umpan balik eksternal yang andal sering menentukan keberhasilan [Kamoi dkk.](https://arxiv.org/abs/2406.01297).

## Siklus kerja

1. Simpan versi awal, prompt, bahan, dan rubrik.
2. Tandai kegagalan spesifik: klaim, lokasi, dampak, contoh benar.
3. Cari penyebab: tujuan tidak jelas, sumber hilang, retrieval meleset, alat gagal, model kurang mampu, atau rubrik salah.
4. Beri umpan balik terarah beserta sumber/tes yang dibutuhkan.
5. Revisi satu komponen utama; jalankan lagi pada contoh lama dan contoh baru.
6. Catat apakah ada regresi pada aspek lain.

## Bahasa umpan balik yang informatif

Lemah: “Kurang bagus, perbaiki.” Kuat: “Bagian ketiga menyatakan bahwa lima wawancara membuktikan preferensi semua pengguna. Sumber hanya melaporkan lima peserta. Ubah menjadi temuan eksploratif, tambahkan keterbatasan sampel, dan jangan ubah tabel biaya. Setelah revisi, periksa bahwa setiap klaim kuantitatif memiliki sumber.”

## Peran manusia yang tidak boleh hilang

Manusia menentukan tujuan, nilai dan prioritas, hak penggunaan data, serta keputusan akhir yang memengaruhi orang lain. AI dapat menyusun alternatif, mencari inkonsistensi, memeriksa format, dan menyiapkan tes. Untuk keahlian khusus, manusia yang kompeten tetap diperlukan ketika hasil dipakai sebagai keputusan berisiko.

## Pembagian kerja praktis

| Tahap | AI dapat membantu | Manusia memutuskan |
|---|---|---|
| Brief | merumuskan pertanyaan dan asumsi | masalah yang layak diselesaikan |
| Riset | mencari/merangkum sumber | kecocokan sumber dan batas klaim |
| Pembuatan | draf, kode, tabel | kebutuhan sebenarnya dan izin |
| Pemeriksaan | tes format, daftar klaim | penerimaan, prioritas, risiko |

## Tanda berhenti

Berhenti mengiterasi ketika kriteria wajib lulus, kesalahan fatal tertutup, peningkatan tambahan kecil dibanding biaya, dan batas ketidakpastian jelas. Bila dua putaran tidak memperbaiki hasil, ubah strategi: tambah bukti, ganti alat, sederhanakan tugas, atau uji model lain. Mengulang prompt sama berkali-kali tanpa informasi baru tidak membangun pemahaman.

## Umpan balik dari pemakai nyata

Pujian “jawaban ini bagus” tidak cukup untuk diagnosis. Tanyakan tindakan apa yang ingin dilakukan pengguna, bagian mana yang membantu atau menghambat, dan apakah keputusan yang diambil benar. Untuk laporan, minta pembaca menunjukkan kesimpulan yang dipakai dan sumbernya. Untuk website, amati tugas yang diselesaikan alih-alih hanya bertanya apakah tampilannya disukai. Jangan mengubah umpan balik satu orang menjadi preferensi semua pengguna.

## Catatan perubahan yang berguna

Versi 1: model menambah angka tanpa sumber. Hipotesis: rubrik tidak menuntut tautan untuk angka. Versi 2: instruksi menuntut sumber di setiap angka; hasil pada 20 kasus menurunkan angka tanpa dukungan dari 6 menjadi 2, tetapi dua masih salah lokasi. Versi 3: audit lokasi petikan dan uji 10 kasus baru. Contoh ini hanya ilustrasi format log; nilai sesungguhnya harus berasal dari pengujianmu. Dengan catatan semacam ini, kamu tahu perbaikan mana bekerja dan apa risiko sisanya.

## Kapan memperbarui tujuan

Umpan balik dapat menunjukkan bahwa brief awal keliru. Misalnya pengguna sebenarnya membutuhkan pilihan tindakan, bukan laporan 30 halaman. Perbarui kontrak hasil dan rubrik sebelum mengoptimalkan gaya. Jangan terus memperbaiki produk yang tidak memecahkan masalah pengguna.

**Latihan:** simpan tiga versi dari tugas nyata. Untuk setiap perubahan, tulis prediksi “apa yang akan membaik” sebelum melihat hasil; nilai apakah prediksi benar pada kasus uji baru.

**Sumber:** [Self-Refine](https://arxiv.org/abs/2303.17651); [Kamoi dkk.](https://arxiv.org/abs/2406.01297); [Anthropic, evaluasi](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents).