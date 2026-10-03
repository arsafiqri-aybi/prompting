# 20 — Pondasi ilmu pendukung untuk menguasai hasil AI

**Tujuan:** mengetahui disiplin yang menjelaskan mengapa teknik praktis dalam folder ini berhasil atau gagal. Kamu tidak harus menjadi pakar semuanya sebelum memakai AI, tetapi setiap disiplin memberi cara menguji satu jenis kesalahan yang berbeda.

## 1. Epistemologi dan literasi ilmiah

Epistemologi membahas apa yang dapat dianggap pengetahuan dan alasan untuk mempercayainya. Untuk AI, pisahkan **observasi** (“pada uji 20 kasus, 16 lulus”), **interpretasi** (“prompt baru mungkin membantu”), dan **klaim kausal** (“prompt baru menyebabkan perbaikan”). Klaim kausal memerlukan pembanding, kontrol terhadap faktor lain, dan ruang generalisasi yang jelas. Satu paper tidak membuktikan efektivitas universal; dokumentasi resmi membuktikan fitur yang dideskripsikan penyedia pada versi tertentu, bukan keandalan faktual setiap output. Gunakan matriks bukti dalam `07`.

## 2. Statistika dan desain eksperimen

Nilai satu jawaban bisa berubah karena variasi generasi atau penilai. Tentukan sampel yang mencakup penggunaan nyata, uji kasus tepi, laporkan jumlah observasi, dan bandingkan tingkat gagal fatal. Jika prompt A lulus 17/20 dan B lulus 18/20, selisih satu kasus belum cukup untuk menyebut B secara umum lebih baik; periksa kasusnya, ulangi, dan gunakan set uji baru. Hindari memperbaiki prompt berkali-kali di set uji yang sama karena akan cocok dengan contoh itu tanpa meningkatkan generalisasi. [HELM](https://arxiv.org/abs/2211.09110) memberi contoh mengapa evaluasi perlu melampaui satu angka; [Yang dkk.](https://arxiv.org/abs/2311.04850) membahas masalah kontaminasi benchmark.

## 3. Teori informasi dan pencarian informasi

Konteks terbatas, jadi pilih sinyal yang memengaruhi tugas. Dalam retrieval, **precision** = dokumen relevan yang ditemukan ÷ semua dokumen yang ditemukan; **recall** = dokumen relevan yang ditemukan ÷ semua dokumen relevan yang tersedia. Misal 8 dari 10 petikan terambil relevan, precision = 0,8; bila sebenarnya ada 20 petikan relevan, recall = 0,4. Membatasi hasil pencarian terlalu ketat dapat menaikkan precision tetapi menurunkan recall. Jawaban model bisa gagal karena bukti tidak ditemukan, walaupun generasi setelahnya baik. Paper [RAG](https://arxiv.org/abs/2005.11401) dan [RAGAS](https://arxiv.org/abs/2309.15217) membantu memisahkan tahap ini.

## 4. Teori keputusan

“Terbaik” bergantung pada kerugian bila salah, biaya pemeriksaan, latensi, dan nilai hasil. Pada tugas berisiko rendah, draf cepat mungkin cukup; pada tugas berisiko tinggi, jawaban yang menahan diri dan memberi rujukan untuk verifikasi bisa lebih bernilai. Jika biaya verifikasi adalah 5 menit dan kesalahan yang tidak terdeteksi bisa merugikan besar, verifikasi layak diprioritaskan. Angka dan fungsi biaya harus ditentukan dari konteks pengguna, bukan dipaksakan oleh model.

## 5. Interaksi manusia dan komputer

Tujuan pengguna, bahasa, beban kognitif, kendali, aksesibilitas, dan umpan balik membentuk hasil yang berguna. Jawaban paling akurat secara teknis dapat gagal bila terlalu panjang atau tak dapat dipahami oleh pembaca yang harus bertindak. Uji artefak pada orang dan tugas yang mewakili; bedakan preferensi dari keberhasilan tugas. Untuk sistem yang memakai agen, tampilkan status, hasil tindakan, dan kesalahan sehingga pengguna dapat mengoreksi. Panduan risiko [NIST](https://doi.org/10.6028/NIST.AI.600-1) juga menekankan peran manusia dalam penilaian sistem.

## 6. Rekayasa perangkat lunak dan pengujian

Prompt, skema, alat, berkas proyek, dan rubrik adalah komponen sistem. Versioning, log perubahan, tes regresi, validasi input-output, serta pemisahan lingkungan uji dan produksi membantu membuat hasil stabil. Dalam proyek coding, keberhasilan adalah perilaku program di lingkungan nyata, bukan klaim “sudah dites”. Dalam tugas penulisan, analoginya adalah audit klaim ke sumber, bukan sekadar membaca ulang gaya.

## 7. Keamanan informasi dan tata kelola data

Prinsip hak akses minimum, pemisahan data dan instruksi, pembatasan operasi alat, perlindungan data pribadi, dan pencatatan tindakan mengurangi risiko. Ketika model membaca web atau berkas asing, ia memproses materi yang bisa memuat perintah penyerang. Ketika menulis ke aplikasi lain, kesalahan bisa mempunyai konsekuensi luar. Lihat [OWASP](https://owasp.org/www-project-top-10-for-large-language-model-applications/) dan [paper injeksi](https://arxiv.org/abs/2302.12173).

## 8. Dasar machine learning jika ingin memahami mesin lebih jauh

Pelajari probabilitas bersyarat, aljabar linear (vektor/matriks), turunan dan gradien, optimisasi, pembagian data latih-uji, overfitting, jaringan saraf, attention, serta pelatihan preferensi. Urutan yang mudah: latihan statistik kecil → model klasifikasi sederhana → jaringan saraf → Transformer → eksperimen prompting/RAG. Buku [Deep Learning](https://www.deeplearningbook.org/) menata aljabar linear, probabilitas, komputasi numerik, dasar ML, dan optimisasi sebelum model mendalam; [CS229 Stanford](https://cs229.stanford.edu/) memberi landasan ML yang terstruktur.

## Peta masalah → ilmu

| Masalah nyata | Disiplin untuk diagnosis | Uji pertama |
|---|---|---|
| Jawaban memiliki referensi palsu | epistemologi, riset | audit sumber asli |
| Retrieval melewatkan dokumen | pencarian informasi | recall@k pada pertanyaan acuan |
| Jawaban terdengar baik tetapi tidak membantu | HCI | tes pengguna dan tugas nyata |
| Prompt A tampak unggul pada tiga contoh | statistika | set uji baru, kasus lebih beragam |
| Agen mengaku mengirim pesan padahal gagal | rekayasa perangkat lunak | cek keadaan aplikasi |
| Dokumen menyuntik perintah | keamanan | uji batas otoritas dan hak alat |

**Latihan:** tulis satu kegagalan AI yang pernah kamu lihat, identifikasi dua disiplin paling relevan, dan rancang pengamatan yang dapat membedakan dua kemungkinan penyebabnya.