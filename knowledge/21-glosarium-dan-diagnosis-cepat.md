# 21 — Glosarium kerja dan diagnosis cepat

Istilah di bawah diberi arti **operasional** untuk membaca kajian dan merancang uji. Makna teknis yang tepat dapat berubah menurut paper atau produk; periksa dokumentasi saat mengimplementasikan.

| Istilah | Arti kerja | Mengapa relevan |
|---|---|---|
| Token | unit input/output yang diproses model | biaya, panjang konteks, batas keluaran |
| Parameter model | nilai yang dipelajari saat pelatihan | berbeda dari contoh/berkas dalam prompt |
| Inferensi | menjalankan model untuk menghasilkan keluaran | konteks dan aturan decoding berlaku di sini |
| Pretraining | pelatihan pada data skala besar sebelum tugas tertentu | memberi pola umum, bukan fakta terkini otomatis |
| Fine-tuning | pelatihan lanjutan yang mengubah parameter | bukan sinonim memberi dokumen ke prompt |
| Prompt | instruksi dan bahan yang diajukan pada suatu interaksi | menentukan tugas dan kondisi jawaban |
| System instruction | instruksi tingkat aplikasi/sistem | berbeda otoritas dari dokumen asing |
| Few-shot | beberapa contoh tugas di konteks saat inferensi | memperjelas pola tanpa mengubah parameter |
| Context window | kapasitas konteks masukan/keluaran menurut sistem | tidak menjamin pemanfaatan merata |
| Context engineering | memilih dan memelihara bahan yang masuk ke model | mengurangi kebisingan dan versi keliru |
| RAG | retrieval disusul generasi berdasarkan hasil retrieval | mendukung informasi eksternal yang terlacak |
| Retrieval | menemukan kandidat dokumen/petikan relevan | tahap yang dapat gagal sebelum generasi |
| Ranking/reranking | mengurutkan kandidat hasil pencarian | menentukan bukti mana masuk konteks |
| Precision | proporsi temuan yang relevan | mendeteksi terlalu banyak hasil yang tak berguna |
| Recall | proporsi bahan relevan yang berhasil ditemukan | mendeteksi bukti yang terlewat |
| Grounding | mengaitkan jawaban ke bahan/sumber/alat yang tersedia | perlu audit dukungan klaim |
| Hallucination/confabulation | keluaran yang tidak sesuai fakta atau dukungan | definisi berbeda menurut konteks penelitian |
| Abstain | menahan jawaban pasti saat bukti tidak cukup | sering lebih baik daripada menebak |
| Calibration | kecocokan keyakinan dengan frekuensi benar | prosa yakin bukan ukuran kalibrasi |
| Rubrik | aturan dan ukuran untuk menilai hasil | memudahkan perbaikan yang terarah |
| Benchmark | kumpulan tugas baku untuk mengukur sistem | dapat usang atau tercemar data pelatihan |
| Set uji | contoh untuk menilai di luar contoh pengembangan | membatasi overfitting prompt |
| Regression test | contoh yang sebelumnya lulus dan harus tetap lulus | mendeteksi kerusakan setelah perubahan |
| LLM-as-a-judge | model menilai keluaran model lain | cepat, tetapi dapat bias |
| Structured output | keluaran yang mengikuti format/skema mesin | validitas struktur ≠ kebenaran isi |
| Tool use | pemanggilan pencarian, kode, kalkulator, aplikasi | periksa efek alat di lingkungan nyata |
| Agent | sistem yang memilih dan mengulangi tindakan menuju tujuan | memerlukan batas, log, kondisi berhenti |
| Prompt injection | instruksi penyerang melalui input/konten asing | memerlukan batas otoritas dan hak alat |
| Latency | waktu dari permintaan sampai hasil | bagian mutu layanan, terutama tugas berulang |

## Diagnosis gejala → sumber masalah → bab

| Gejala | Hipotesis utama | Periksa |
|---|---|---|
| AI menjawab pertanyaan yang berbeda | tujuan atau instruksi ambigu | `02`, `03` |
| Keputusan lama muncul lagi | konteks/memori versi usang | `04`, `08` |
| Output rapi tetapi angka keliru | alat tidak dipakai atau nilai salah | `09`, `13` |
| Kutipan palsu | pencarian atau audit sumber gagal | `07`, `08`, `13` |
| JSON valid tetapi tidak sesuai data | pemeriksaan hanya format | `05`, `12` |
| Hasil model baru tidak konsisten | versi/konfigurasi/variasi generasi | `11`, `12` |
| Dua revisi tidak membaik | umpan balik tanpa bukti baru | `06`, `14` |
| Agen menyatakan sukses tanpa efek | keadaan akhir tidak diperiksa | `09`, `15` |
| Dokumen mengambil alih tugas | injeksi dari sumber asing | `03`, `16` |
| Hasil “baik” tetapi pengguna gagal | kriteria salah atau audiens tak diuji | `02`, `12`, `20` |

## Peringatan istilah yang sering disalahgunakan

“Panjang konteks” bukan kapasitas memahami seluruh isi dengan akurasi sama; “sitasi” bukan bukti jika halaman tidak mendukung klaim; “reasoning” dalam jawaban bukan jendela transparan ke mekanisme internal; “akurasi 90%” tanpa data uji dan definisi kasus tidak bermakna; “otomatis” bukan berarti tanpa pengawasan. Periksa selalu *apa yang diukur* dan *apa yang berhasil terjadi*.

**Bacaan rujukan:** [Transformer](https://arxiv.org/abs/1706.03762); [RAG](https://arxiv.org/abs/2005.11401); [ketepatan penjelasan penalaran](https://arxiv.org/abs/2307.13702); [evaluasi agen](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents).