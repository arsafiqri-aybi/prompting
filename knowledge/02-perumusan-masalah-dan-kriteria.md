# 02 — Perumusan masalah, spesifikasi, dan kriteria hasil

**Fungsi:** mengubah keinginan yang abstrak menjadi tugas yang dapat dikerjakan dan diuji. Pada banyak pekerjaan, kualitas sasaran lebih penting daripada hiasan kata pada prompt.

## Enam pertanyaan sebelum meminta jawaban

1. **Tujuan:** keputusan atau tindakan apa yang akan diambil dari hasil ini?
2. **Pengguna:** siapa yang membaca dan apa tingkat pengetahuannya?
3. **Lingkup:** topik, tempat, waktu, ukuran, bahasa, dan apa yang berada di luar tugas?
4. **Bahan:** dokumen, data, pengalaman pengguna, atau sumber resmi apa yang tersedia?
5. **Keluaran:** bentuk yang akan dipakai selanjutnya: ringkasan, tabel, kode, rencana, berkas?
6. **Sukses dan kegagalan:** apa syarat wajib, kesalahan fatal, dan siapa yang memutuskan hasil diterima?

Dokumentasi Google menganjurkan petunjuk yang jelas dan spesifik, contoh, serta perincian tugas kompleks [Google, *Prompt design strategies*](https://ai.google.dev/gemini-api/docs/prompting-strategies). Itu panduan penggunaan model, bukan bukti bahwa satu susunan kata selalu optimal.

## Contoh konkret: proyek website yang nyaman

Permintaan awal: “Buat website yang memanjakan pancaindra dan terbukti secara psikologi.” Masalahnya: website tidak bisa menghadirkan bau/rasa fisik melalui layar; “terbukti” ambigu; audiens dan perangkat tidak disebut; kenyamanan sangat bergantung pada orang dan konteks.

Spesifikasi yang lebih dapat diuji:

> Rancang halaman beranda untuk pengguna ponsel berbahasa Indonesia yang mencari informasi layanan. Prioritas: teks terbaca, navigasi mudah, animasi dan audio dapat dikendalikan, serta halaman dapat digunakan dengan papan ketik dan pembaca layar. Berikan lima prinsip desain, bukti sumber primer untuk setiap klaim psikologis, pengecualian/ketidakpastian, dan rencana uji dengan minimal lima tugas pengguna yang realistis. Jangan menyimpulkan bahwa bau atau rasa dihasilkan oleh situs. Keluaran: tabel keputusan desain dan protokol uji. Jelaskan asumsi yang belum diputuskan.

Ini **contoh rancangan tugas**, bukan klaim bahwa desain tersebut pasti lebih nyaman bagi semua orang. Penilaian harus mencakup uji pada pengguna yang relevan dan metrik aksesibilitas yang dipilih sesuai konteks.

## Spesifikasi penerimaan

Tuliskan rubrik **sebelum** meminta hasil. Contoh penelitian untuk website:

| Dimensi | Lulus jika | Gagal jika |
|---|---|---|
| Klaim ilmiah | setiap klaim penting memiliki sumber yang benar-benar mendukung | ada sumber karangan atau klaim lebih kuat daripada bukti |
| Kesesuaian audiens | istilah dijelaskan dan bahasa sesuai | bergantung pada pengetahuan teknis yang tak diasumsikan |
| Keterterapan | setiap rekomendasi menyebut kondisi, pemilik, dan cara uji | hanya slogan “ramah pengguna” |
| Aksesibilitas | kendali pengguna dan kebutuhan beragam dipertimbangkan | animasi/suara otomatis tanpa kontrol |
| Ketidakpastian | membedakan bukti kuat, indikasi awal, dan asumsi | menjanjikan efek universal |

Rubrik harus punya bobot dan gerbang: misalnya sebuah referensi palsu membatalkan hasil walau gaya tulis sangat baik. Nilai total tanpa gerbang dapat menyembunyikan kesalahan berbahaya.

## Menentukan informasi yang perlu ditanyakan

Jika detail yang hilang bisa mengubah pilihan substantif, minta klarifikasi: audiens anak atau dewasa, kebutuhan data terkini, hak pakai materi, batas waktu/biaya. Bila tidak kritis, tetapkan asumsi secara eksplisit dan teruskan pekerjaan. Pertanyaan yang baik menawarkan pilihan beserta dampaknya.

## Dua kesalahan umum

- **Merinci format tanpa kriteria isi:** meminta “tabel 12 kolom” tidak memperjelas apa yang benar.
- **Terlalu banyak tujuan sekaligus:** “lengkap, singkat, mendalam, murah, tanpa risiko, kreatif” perlu urutan prioritas dan kompromi yang dapat diterima.

## Menulis kontrak hasil

Kontrak hasil yang kuat menghubungkan setiap syarat ke satu cara pemeriksaan. Contoh: “memuat semua layanan” membutuhkan daftar layanan resmi sebagai acuan; “cepat dipahami” memerlukan tugas pengguna dan ukuran kinerja; “akurat” membutuhkan pemilik sumber dan aturan menangani konflik. Jika suatu syarat tidak dapat diperiksa, pilih proksi yang masuk akal dan sebut keterbatasannya. Jangan hanya mengganti kata kabur dengan angka buatan.

| Keinginan | Definisi operasional yang bisa dicoba | Batas interpretasi |
|---|---|---|
| “Mudah dipahami” | peserta target dapat menjelaskan fungsi halaman dan menyelesaikan tugas | hasil sampel kecil tidak berlaku universal |
| “Lengkap” | mencakup semua butir dari daftar kebutuhan yang disetujui | daftar kebutuhan bisa belum lengkap |
| “Dapat dipercaya” | klaim penting punya sumber asli, tanggal, dan kesesuaian | sumber sendiri dapat salah |
| “Kreatif” | beberapa alternatif berbeda yang tetap memenuhi batas | penilaian gaya bergantung audiens |

## Ketika tujuan saling bertentangan

Tentukan urutan prioritas eksplisit. Misalnya untuk ringkasan penelitian: (1) tidak ada klaim salah, (2) menyebut keterbatasan utama, (3) mudah dibaca, (4) sesingkat mungkin. Jika membatasi ke 100 kata menghilangkan batasan penting, biarkan jawaban lebih panjang atau gunakan dua lapis: ringkasan 100 kata dan lampiran metode. Evaluasi trade-off dengan tujuan keputusan pengguna, bukan dengan panjang sebagai satu-satunya ukuran.

## Mengubah tujuan menjadi dataset uji

Tulis satu baris per contoh: masukan, kondisi yang membuatnya sulit, hasil yang diharapkan, kesalahan fatal, serta siapa yang memberi label. Beri contoh negatif: pertanyaan tanpa data, sumber usang, dan istilah ambigu. Mulai dari 10 contoh; tambah kasus kegagalan nyata secara bertahap. Menyusun dataset sebelum melihat keluaran mengurangi kecenderungan mendefinisikan “bagus” setelah melihat jawaban yang kita sukai.

**Latihan:** tulis satu prompt untuk tugasmu, lalu tukar frasa “bagus/menarik/lengkap” dengan kriteria yang dapat diperiksa. Simpan lima contoh sulit dan lihat apakah spesifikasi cukup untuk menilai semuanya.

**Sumber lanjutan:** [Google, strategi prompt](https://ai.google.dev/gemini-api/docs/prompting-strategies); [Anthropic, evaluasi agen](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents); [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework).