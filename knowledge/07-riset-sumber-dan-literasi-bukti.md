# 07 — Riset, penelusuran sumber, dan literasi bukti

**Fungsi:** memberi AI bahan yang benar dan mengetahui seberapa jauh kesimpulan boleh dibuat. Untuk pertanyaan yang waktunya berubah, pencarian biasanya prasyarat, bukan tambahan kosmetik.

## Rumuskan pertanyaan penelitian

Tentukan populasi/konteks, tindakan atau objek yang dibandingkan, hasil yang ingin diketahui, rentang waktu, jenis bukti, dan lokasi. Contoh: “Pada pengunjung website ponsel berbahasa Indonesia, apakah pengendalian animasi meningkatkan keberhasilan tugas atau mengurangi ketidaknyamanan dibanding animasi otomatis?” Ini jauh lebih terarah daripada “warna apa yang disukai semua orang?”. Untuk riset terapan, bedakan data penelitian laboratorium, studi lapangan, hasil uji internal, dan preferensi satu pengguna.

## Hirarki praktis pemilihan sumber

| Klaim | Mulai dari | Periksa juga |
|---|---|---|
| Perilaku API/model saat ini | dokumentasi resmi produk | versi, tanggal pembaruan, uji sendiri |
| Metode penelitian tertentu | paper asli + data/metode | replikasi dan batas sampel |
| Standar/rangka risiko | lembaga penerbit resmi | edisi berlaku dan lingkup yurisdiksi |
| Harga/jadwal/jabatan | halaman resmi terbaru | tanggal saat diakses |
| Pengalaman pengguna lokal | riset pengguna dan analitik proyek | bias sampel dan keterwakilan |

Sumber primer tidak otomatis benar; paper yang memperkenalkan metode punya insentif menonjolkan keberhasilannya, sedangkan dokumentasi penyedia menjelaskan produknya sendiri. Bandingkan sumber yang benar-benar independen bila konsekuensinya besar. Catat penulis/penerbit, tahun, metode, sampel/tugas, dan apakah kesimpulan didukung langsung atau diturunkan lewat inferensi.

## Prosedur 8 langkah

1. Tulis pertanyaan dan kriteria inklusi/eksklusi; batasi tenggat pencarian.
2. Cari istilah alternatif, sinonim, dan sumber yang bisa membantah hipotesis.
3. Buka sumber asli; jangan mengandalkan cuplikan mesin pencari.
4. Simpan metadata: judul, URL/DOI, penerbit, tanggal publikasi, versi, tanggal akses.
5. Ekstrak klaim persis yang relevan beserta lokasi halaman/bagian.
6. Nilai kekuatan bukti dan batas generalisasi.
7. Tulis pernyataan menurut kekuatan bukti: “pada studi X” berbeda dari “secara universal”.
8. Audit satu per satu bahwa tautan **ada** dan **mendukung klaim di dekatnya**.

Meminta AI “berikan 20 referensi ilmiah” tanpa membuka referensi berisiko menghasilkan tautan yang ada tetapi tidak relevan, bahkan referensi karangan. Studi [Zuccon dkk.](https://arxiv.org/abs/2309.09401) memperlihatkan masalah atribusi pada model dan kumpulan pertanyaan yang mereka uji; solusinya adalah audit sumber, bukan menghafal persentase hasil studinya.

## Matriks bukti yang dapat dipakai ulang

| Klaim | Jenis | Sumber dan lokasi | Metode | Batas | Status |
|---|---|---|---|---|---|
| “Teknik A membantu tugas B” | hasil studi | paper/halaman | model, dataset, pembanding | belum diuji di proyek ini | indikasi |
| “Fitur produk X tersedia” | spesifikasi | dokumentasi/tanggal | rilis produk | dapat berubah | perlu cek ulang |
| “Desain ini akan nyaman untuk semua” | dugaan | tidak ada | tidak ada | variasi individu besar | tolak |

## Penanda ketidakpastian

Gunakan kategori: **terkonfirmasi oleh sumber langsung**, **didukung terbatas**, **inferensi yang masuk akal**, **belum terverifikasi**, **bertentangan antar sumber**. Jelaskan apa yang akan mengubah kategori. Jangan memakai probabilitas persen yang tampak presisi tanpa model kalibrasi dan data pembanding.

## Membaca paper dengan pertanyaan yang tepat

Catat tujuan penelitian, sampel/dataset, metode pengukuran, pembanding, hasil utama, ukuran efek bila ada, kendali terhadap faktor lain, dan keterbatasan yang ditulis penulis. Tanyakan apakah klaim yang ingin kamu pakai merupakan hasil langsung atau tafsiranmu. Misalnya paper *Lost in the Middle* menguji posisi informasi pada tugas dan model tertentu; ia tidak membuktikan bahwa setiap dokumen panjang harus dipotong atau setiap model selalu gagal membaca bagian tengah.

## Pencarian yang dapat diulang

Simpan kueri, tanggal pencarian, domain/pangkalan data, filter, dan alasan sumber dimasukkan/dikeluarkan. Cari istilah yang berlawanan dengan hipotesis awal agar tidak hanya mengumpulkan konfirmasi. Pisahkan sumber terbitan asli dari artikel yang mengutipnya. Jika menulis “tinjauan menyeluruh”, jelaskan proses pencarian dan apa yang mungkin luput; bila hanya memilih sumber representatif, sebut itu kajian naratif.

## Klaim ilmiah dalam proyek pengguna

Kesimpulan “beberapa peserta menyukai desain A” dari lima wawancara bukan “manusia secara umum menyukai desain A”. Kesimpulan “panduan resmi merekomendasikan kendali animasi” bukan “kenyamanan meningkat 30%” tanpa eksperimen yang mengukur itu. Hindari mengubah korelasi menjadi sebab. Bila praktik dinilai bermanfaat tetapi belum teruji di targetmu, rekomendasikan prototipe dan uji; dokumentasikan ketidakpastian sebelum peluncuran.

**Latihan:** ambil lima klaim dari satu jawaban AI. Telusuri sumber asli tiap klaim dan beri status dukungan: langsung, sebagian, tidak mendukung, atau sumber tidak ditemukan. Perbaiki kesimpulan yang melampaui bukti.

**Sumber:** [paper RAG](https://arxiv.org/abs/2005.11401); [studi atribusi referensi](https://arxiv.org/abs/2309.09401); [NIST AI RMF](https://doi.org/10.6028/NIST.AI.600-1).