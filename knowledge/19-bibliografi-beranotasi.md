# 19 — Bibliografi beranotasi dan cara menilai sumber

**Metode:** kumpulan terpilih dari paper asli, dokumentasi resmi, dan panduan lembaga; ditelusuri hingga 24 September 2026. Ini **bukan** inventaris seluruh penelitian AI dan bukan tinjauan sistematis. Tautan pada dokumentasi hidup perlu diperiksa ulang ketika versi produk berubah. Temuan paper selalu dibatasi oleh model, data, tugas, serta masa penelitian. Bacalah metode dan keterbatasan sumber asli sebelum memakai klaim dalam konteks berisiko.

## Fondasi model

1. **Vaswani dkk. (2017), [Attention Is All You Need](https://arxiv.org/abs/1706.03762).** Paper asli Transformer; berguna untuk memahami perhatian dan pemrosesan urutan. Eksperimen awal terutama terjemahan, bukan bukti perilaku semua chatbot kini.
2. **Brown dkk. (2020), [Language Models are Few-Shot Learners](https://arxiv.org/abs/2005.14165).** Menunjukkan tugas dapat dideskripsikan dengan contoh tanpa pembaruan parameter saat inferensi. Perilaku terukur pada model/data masa itu.
3. **Ouyang dkk. (2022), [Training Language Models to Follow Instructions with Human Feedback](https://arxiv.org/abs/2203.02155).** Demonstrasi dan preferensi manusia meningkatkan kepatuhan terhadap instruksi pada pengujian yang dilaporkan; tetap ada kesalahan.
4. **Shanahan (2023), [Talking About Large Language Models](https://arxiv.org/abs/2212.03551).** Telaah konseptual tentang bahasa untuk membicarakan LLM; jangan menyimpulkan proses internal hanya dari dialog.

## Prompt, penalaran, dan konteks

5. **Google, [Prompt design strategies](https://ai.google.dev/gemini-api/docs/prompting-strategies).** Petunjuk resmi tentang instruksi jelas, contoh, pemecahan tugas. Berlaku terutama pada keluarga produk mereka dan dapat diperbarui.
6. **Anthropic, [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents).** Kerangka rekayasa konteks dan desain alat; artikel teknis penyedia, bukan eksperimen universal.
7. **Wei dkk. (2022), [Chain-of-Thought Prompting](https://arxiv.org/abs/2201.11903).** Keuntungan contoh langkah penalaran pada beberapa benchmark dan model; hasil tidak otomatis berlaku untuk semua model modern.
8. **Wang dkk. (2022), [Self-Consistency Improves Chain of Thought Reasoning](https://arxiv.org/abs/2203.11171).** Beberapa jalur sampel membantu beberapa tugas penalaran; ada biaya komputasi dan risiko semua jalur berbagi kesalahan.
9. **Lanham dkk. (2023), [Measuring Faithfulness in Chain-of-Thought Reasoning](https://arxiv.org/abs/2307.13702).** Penjelasan langkah terlihat tidak selalu setia pada mekanisme penyebab jawaban; variasi tergantung tugas/model.
10. **Liu dkk. (2023), [Lost in the Middle](https://arxiv.org/abs/2307.03172).** Posisi informasi dalam konteks panjang dapat memengaruhi hasil pada tugas/model yang diuji; uji kembali pada sistem baru.

## Retrieval, alat, dan alur

11. **Lewis dkk. (2020), [Retrieval-Augmented Generation](https://arxiv.org/abs/2005.11401).** Menggabungkan memori parametris dengan retrieval untuk tugas pengetahuan; peningkatan bergantung pada retrieval dan pembanding penelitian.
12. **Es dkk. (2023), [RAGAS](https://arxiv.org/abs/2309.15217).** Menawarkan metrik pemisah retrieval, kesetiaan jawaban, dan generasi; nilai otomatis perlu diaudit.
13. **Yao dkk. (2022/2023), [ReAct](https://arxiv.org/abs/2210.03629).** Menggabungkan langkah penalaran dan tindakan; gambaran pola, bukan resep agen universal.
14. **Schick dkk. (2023), [Toolformer](https://arxiv.org/abs/2302.04761).** Studi model yang mempelajari panggilan alat; lingkungan produksi memerlukan izin dan observasi.
15. **Madaan dkk. (2023), [Self-Refine](https://arxiv.org/abs/2303.17651).** Iterasi umpan balik dalam percobaan yang dilaporkan; gunakan umpan balik eksternal untuk tugas yang sulit diverifikasi sendiri.
16. **Kamoi dkk. (2024), [When Can LLMs Actually Correct Their Own Mistakes?](https://arxiv.org/abs/2406.01297).** Telaah kritis temuan koreksi diri; menekankan peran umpan balik eksternal yang andal. Ini sintesis riset, bukan satu eksperimen baru.

## Evaluasi dan faktualitas

17. **Liang dkk. (2022), [Holistic Evaluation of Language Models](https://arxiv.org/abs/2211.09110).** Kerangka evaluasi beberapa metrik dan skenario; angka spesifik dapat usang.
18. **Anthropic, [Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents).** Definisi tugas, ulangan, penilai, jejak, dan keadaan akhir; pengalaman produk penyedia.
19. **Zheng dkk. (2023), [Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena](https://arxiv.org/abs/2306.05685).** Menguji hakim model dan bias posisi/panjang; tidak menggantikan pemeriksaan manusia pada kasus kritis.
20. **Yang dkk. (2023), [Rethinking Benchmark and Contamination](https://arxiv.org/abs/2311.04850).** Variasi redaksi dapat menyamarkan kebocoran benchmark; dukung pemakaian set uji baru.
21. **Lin dkk. (2021), [TruthfulQA](https://arxiv.org/abs/2109.07958).** Benchmark miskonsepsi yang sering ditiru model; jangan memindahkan persentase model lama ke model sekarang.
22. **Zuccon dkk. (2023), [ChatGPT Hallucinates when Attributing Answers](https://arxiv.org/abs/2309.09401).** Uji keberadaan dan relevansi sitasi pada domain tertentu; periksa sitasi setiap proyek secara langsung.

## Keamanan dan input multimodal

23. **Greshake dkk. (2023), [Indirect Prompt Injection](https://arxiv.org/abs/2302.12173).** Mendemonstrasikan konten yang diambil sebagai jalur serangan; risiko bergantung desain sistem.
24. **NIST (2024), [AI RMF Generative AI Profile, AI 600-1](https://doi.org/10.6028/NIST.AI.600-1).** Rangka untuk identifikasi dan pengelolaan risiko generatif; bukan sertifikasi otomatis suatu produk.
25. **OWASP, [Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/).** Taksonomi risiko aplikasi, termasuk prompt injection; periksa edisi saat implementasi.
26. **Google, [Structured output](https://ai.google.dev/gemini-api/docs/structured-output), [file prompting](https://ai.google.dev/gemini-api/docs/files), dan [document processing](https://ai.google.dev/gemini-api/docs/document-processing).** Sumber resmi fitur format dan media; batas dukungan tergantung model/API dan tanggal.

## Cara memperbarui kajian ini

Setiap kali memilih model/fitur baru: catat tanggal dan versi dokumentasi, jalankan set uji kecil milikmu, cari paper replikasi atau hasil yang berlawanan, lalu ubah rekomendasi di berkas terkait. Simpan perubahan dengan alasan; jangan menghapus keterbatasan ketika ada satu eksperimen yang tampak mendukung hipotesis.