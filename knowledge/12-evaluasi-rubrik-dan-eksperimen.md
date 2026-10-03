# 12 — Evaluasi, rubrik, dan eksperimen

**Fungsi:** membedakan perbaikan nyata dari jawaban yang hanya terdengar lebih meyakinkan. Evaluasi adalah pondasi terpenting jika kamu ingin hasil AI “terbaik”. Framework [HELM](https://arxiv.org/abs/2211.09110) menekankan evaluasi pada beberapa skenario dan metrik; evaluasi agen modern juga membedakan tugas, percobaan, penilai, jejak, dan keadaan akhir [Anthropic](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents).

## Empat tingkat pemeriksaan

1. **Struktur:** file tersedia, JSON valid, panjang/bahasa/kolom sesuai.
2. **Isi:** fakta benar, cakupan memadai, tidak menambahkan klaim tanpa bukti.
3. **Proses:** alat yang tepat dipakai, sumber ditelusuri, instruksi prioritas dipatuhi.
4. **Dampak:** pengguna dapat menyelesaikan tugas; perubahan benar-benar bekerja dalam lingkungan nyata.

Metrik tingkat 1 mudah diotomatisasi, tetapi tidak menjamin tingkat 2–4. “Sudah membuat file” pun harus dicek keberadaan dan isinya, bukan berdasarkan teks respons.

## Desain set uji

Kumpulkan kasus umum, langka, ambigu, dokumen bertentangan, input panjang, data rusak, permintaan terbaru, dan kasus “jawaban tidak tersedia”. Contoh harus mencerminkan penggunaan nyata sekaligus mengekspos risiko tinggi. Hindari kebocoran contoh uji ke instruksi dan overfitting karena terus menerus mengedit prompt agar lolos satu set publik. Penelitian tentang kontaminasi benchmark menunjukkan kemiripan data latih dan uji dapat menyamarkan kemampuan generalisasi [Yang dkk.](https://arxiv.org/abs/2311.04850); untuk penggunaan praktis, buat set uji privat yang baru.

## Rubrik contoh 100 poin

| Dimensi | Bobot | Tolok ukur |
|---|---:|---|
| Akurasi fakta | 30 | klaim dibandingkan sumber primer |
| Relevansi dan cakupan | 20 | menjawab semua syarat prioritas |
| Dukungan bukti | 20 | sitasi benar dan dekat klaim |
| Keterterapan | 15 | langkah nyata, asumsi, pemilik uji |
| Format dan kejelasan | 10 | dapat dibaca/diproses |
| Ketidakpastian | 5 | mengakui hal yang tidak diketahui |

**Gerbang gagal otomatis:** sumber palsu, angka salah yang mengubah keputusan, atau data sensitif bocor. Bobot hanyalah contoh; ubah sesuai risiko tugas. Nilai 80/100 yang mengandung satu kesalahan fatal tetap gagal.

## Penilaian oleh model lain

Penilai AI bisa membantu menyortir banyak keluaran, tetapi dapat bias terhadap panjang jawaban, posisi pilihan A/B, gaya, atau dirinya sendiri. Paper [MT-Bench/Chatbot Arena](https://arxiv.org/abs/2306.05685) membahas bias semacam itu. Rotasikan urutan kandidat, butakan identitas model, beri contoh penilaian manusia, dan audit sampel yang disengketakan. Untuk fakta kritis, pakai pemeriksaan langsung terhadap sumber.

## Pelaporan eksperimen

Catat tanggal, versi model, prompt, izin alat, dokumen, jumlah kasus, definisi lulus, jumlah gagal fatal, skor per kategori, variasi antar ulangan, latensi/biaya. Lihat perubahan per segmen, bukan hanya rerata. Bila sampel kecil, tulis “indikasi pada 20 kasus ini”, bukan “terbukti untuk semua tugas”.

## Membuat penilai yang dapat dipercaya

Untuk dimensi objektif, gunakan pemeriksaan deterministik: JSON dapat diparse, file ada, hitungan cocok, rujukan dapat dibuka. Untuk dimensi semantis, tulis rubrik dengan contoh lulus/gagal, minta dua penilai pada sampel penting, dan ukur ketidaksepakatan. Jika dua manusia sering berbeda, definisi rubrik perlu diperjelas sebelum menyalahkan model. Penilai AI boleh mempercepat triase, tetapi jalankan pemeriksaan manusia untuk hasil yang berdampak tinggi dan kasus ketika penilai otomatis tidak yakin.

## Kasus negatif dan ketahanan

Sertakan “jawaban tidak ada di bahan”, dokumen dengan angka saling bertentangan, pertanyaan yang memerlukan perhitungan, dan instruksi asing dalam sumber. Tes ini mengungkap overclaim, kesalahan otoritas, dan alat yang tidak dipakai. Ukur juga performa per jenis kasus; perbaikan rata-rata yang meningkatkan kesalahan fatal pada satu segmen tidak otomatis diterima.

## Uji setelah perubahan

Pisahkan set pengembangan dari set uji baru. Gunakan set pengembangan untuk merancang prompt, lalu uji sekali pada set baru. Setelah tiap kegagalan produksi, tambahkan kasusnya ke regresi; cegah pengeditan yang memperbaiki kasus itu sambil merusak kasus lama. Jika skema output berubah, tes struktur harus ikut berubah. Sertakan perubahan versi sumber, bukan hanya perubahan prompt.

**Latihan:** susun 30 kasus (20 normal, 10 sulit), nilai dua prompt. Setelah memilih pemenang, uji pada 10 kasus baru yang belum dilihat. Jika keunggulannya hilang, kembali ke diagnosis kegagalan.

**Sumber:** [HELM](https://arxiv.org/abs/2211.09110); [Anthropic, evals](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents); [Zheng dkk., LLM judge](https://arxiv.org/abs/2306.05685).