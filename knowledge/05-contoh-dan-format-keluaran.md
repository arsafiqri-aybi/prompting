# 05 — Contoh, demonstrasi, dan desain keluaran

**Fungsi:** menunjukkan pola hasil yang dimaksud dan memastikan keluaran dapat dipakai mesin/manusia berikutnya. Contoh dalam prompt (*few-shot*) adalah konteks saat inferensi, bukan pelatihan ulang parameter model [Brown dkk.](https://arxiv.org/abs/2005.14165).

## Kapan contoh membantu?

Saat aturan sulit diringkas, istilah internal punya arti khusus, atau bentuk keluaran harus konsisten. Pilih contoh yang **benar, relevan, beragam**, termasuk satu kasus tepi. Contoh yang salah atau bias bisa mengajar pola yang salah. Dokumentasi Google menganjurkan contoh few-shot dan kesesuaian contoh dengan tugas; perlakukan saran itu sebagai titik mulai yang perlu diuji untuk modelmu [Google](https://ai.google.dev/gemini-api/docs/prompting-strategies).

## Demonstrasi untuk ekstraksi, bukan tebak

```text
Tugas: ekstrak fakta yang tertulis dalam dokumen. Jika tidak ada, gunakan null.
Input contoh: "Layanan A diluncurkan Mei 2024; biaya belum ditetapkan."
Output contoh: {"layanan":"A","bulan_peluncuran":"2024-05","biaya":null}
Input nyata: [teks sumber]
Output: [objek mengikuti kunci yang sama, tanpa menambah fakta]
```

Definisikan apakah `null` berarti tidak ada, tidak terbaca, atau bertentangan; jika perlu, buat status terpisah. Hindari contoh yang memuat data sensitif tanpa hak pakai.

## Bentuk keluaran berdasarkan pemakai

| Penerima | Format | Pemeriksaan |
|---|---|---|
| Pembaca awam | paragraf + daftar keputusan | bahasa jelas, tidak ada klaim tanpa bukti |
| Penelaah riset | tabel klaim–sumber–metode–batasan | sumber benar-benar mendukung klaim |
| Program | JSON/CSV sesuai skema | parse valid, tipe, nilai wajib, rentang |
| Tim proyek | tugas–pemilik–tanggal–bukti selesai | dapat dilaksanakan, tanpa pemilik samar |

Jika sistem mendukung **structured output** atau skema JSON, pakai fasilitas itu dan validasi lagi setelah keluaran. Instruksi teks “tulis JSON” sendiri tidak menjamin sintaks dan nilai semantis benar. Dokumentasi resmi Google menjelaskan pemakaian subset JSON Schema untuk keluaran terstruktur; kemampuan khusus bergantung pada model/API [Google, *Structured output*](https://ai.google.dev/gemini-api/docs/structured-output).

## Mencegah contoh merusak tugas

- Jangan beri semua contoh kategori A; model bisa condong menjawab A.
- Sertakan contoh “bukti tidak cukup” agar model belajar untuk berhenti.
- Pisahkan masukan dan jawaban dengan penanda yang konsisten.
- Jangan membocorkan contoh uji ke prompt produksi bila kamu mengukur kemampuan generalisasi.
- Tinjau keluaran tidak hanya terhadap struktur, tetapi terhadap sumber asli.

## Protokol uji

Siapkan 20 input dengan label acuan bila memungkinkan: 10 umum, 5 ambigu, 5 negatif/tidak ada jawaban. Bandingkan tanpa contoh, dua contoh, dan empat contoh; pilih berdasarkan akurasi per kelas, bukan angka keseluruhan saja. Uji apakah menambah contoh malah menurunkan kinerja pada kelas langka.

## Contoh positif, negatif, dan kontra contoh

Contoh positif menunjukkan hasil yang diinginkan; kontra contoh menunjukkan kasus yang mirip tetapi **tidak** memenuhi kriteria. Untuk klasifikasi keluhan pelanggan, buat contoh “keluhan”, “saran”, dan “tidak cukup informasi” yang membedakan kategori berdasarkan isi, bukan berdasarkan panjang atau gaya tulis. Jika semua contoh keluhan memuat kata “buruk”, model mungkin menghafal kata itu dan melewatkan keluhan yang ditulis sopan. Rancang contoh yang menuntut aturan sesungguhnya.

## Validasi berlapis untuk keluaran terstruktur

Tahap 1: parse sintaks JSON/CSV. Tahap 2: periksa skema (tipe, field wajib, enumerasi). Tahap 3: periksa aturan bisnis (tanggal masuk akal, jumlah non-negatif). Tahap 4: cocokan nilai ke sumber asli. JSON valid dengan angka yang dikarang tetap salah. Simpan pesan galat yang memberi tahu apa yang gagal; bila mencoba ulang, kirim informasi kegagalan konkret.

## Ketika contoh terlalu spesifik

Contoh dapat mempersempit kreativitas atau menularkan kekeliruan. Untuk ide desain, tunjukkan keragaman format dan kriteria penilaian, lalu minta alternatif yang berbeda secara substantif. Untuk ekstraksi fakta, pilih contoh yang konservatif dan menahan diri. Biaya token contoh juga perlu dihitung terhadap kenaikan mutu hasil pada set uji; jangan menambah 20 demonstrasi hanya karena satu kasus membaik.

**Latihan:** buat skema ekstraksi untuk riset pengguna: `temuan`, `kutipan_asli`, `sumber`, `tingkat_keyakinan`, `perlu_verifikasi`. Uji dokumen yang tidak menyebut kutipan agar model tidak mengarang.

**Sumber:** [few-shot learning](https://arxiv.org/abs/2005.14165); [Google, strategi prompt](https://ai.google.dev/gemini-api/docs/prompting-strategies); [Google, output terstruktur](https://ai.google.dev/gemini-api/docs/structured-output).