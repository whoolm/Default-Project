# Workflow Research Pustaka — Template Generik

> Template reusable untuk penelitian akademik apapun.
> Berbasis alur 9 langkah dari proyek Pancasila (2026).
> Cara pakai: isi placeholder `{{TOPIK}}`, `{{SUB-TEMA}}`, dst.

## Cara Pakai

1. Copy file ini → `[nama-proyek]/WORKFLOW.md`
2. Ganti semua `{{PLACEHOLDER}}`
3. Jalankan langkah 1-9 secara berurutan
4. Isi checklist di akhir setiap langkah

## 9 Langkah Universal

### Langkah 1 — Ideasi & Pemetaan
**Tool:** DeepSeek (orkestrator) + LeapSpace brainstorming
**Input:** Topik utama `{{TOPIK}}`
**Query:**
> "Brainstorming terstruktur tentang {{TOPIK}}. Identifikasi:
> (1) 5 pertanyaan riset utama, (2) 10 keyword pencarian,
> (3) struktur outline makalah, (4) gap research yang ada."
**Output wajib:**
- [ ] 5 research question
- [ ] 10 keyword (ID + EN)
- [ ] Outline struktur (Bab I-III atau Section I-V)
- [ ] Daftar gap research

### Langkah 2 — Pencarian Literatur Awal
**Tool:** Perplexity Academic/Pro
**Query template:**
> "Cari 15 artikel ilmiah terbaru (2021-2026) tentang {{TOPIK}}, fokus pada {{ASPEK_SPESIF}}. Berikan DOI, judul, penulis, ringkasan 1 paragraf per artikel."
**Output wajib:**
- [ ] 15 referensi dengan DOI
- [ ] Tabel: No | Penulis | Judul | Jurnal | Tahun | DOI
- [ ] Klasifikasi per sub-tema

### Langkah 3 — Brainstorming Mendalam
**Tool:** LeapSpace (4 prompt)
**Strategi:** 2 prompt Deep Research (P1, P4) + 2 prompt Copilot (P2, P3)
**Batasan:** max 500 karakter per prompt
**Query template:**
- P1 (Deep Research): {{SUB-TEMA-1}} — analisis filosofis
- P2 (Copilot): {{SUB-TEMA-2}} — perbandingan
- P3 (Copilot): {{SUB-TEMA-3}} — kritis/komparatif
- P4 (Deep Research): {{SUB-TEMA-4}} — aplikasi/relevansi
**Output wajib:**
- [ ] 4 laporan LeapSpace
- [ ] Ringkasan tiap laporan (200 kata)

### Langkah 4 — Validasi Konsensus
**Tool:** Consensus (Consensus Meter + Study Snapshots + Pro Analysis)
**Query template:**
> "Apakah {{KLAIM_UTAMA}} didukung konsensus ilmiah?"
**Output wajib:**
- [ ] Consensus Meter (Yes/No/Possibly %)
- [ ] 20 artikel teratas + Study Snapshots
- [ ] Catatan: Consensus **bukan** meta-analisis formal

### Langkah 5 — Ekstraksi Terstruktur
**Tool:** Elicit (Agen Penelitian)
**Query template:**
> "{{PERTANYAAN_RISET}}. Ekstrak: (1) metodologi, (2) sampel/populasi, (3) temuan utama, (4) framework teoretis. Ikuti standar PRISMA 2020."
**Output wajib:**
- [ ] Tabel ekstraksi (metodologi, sampel, temuan)
- [ ] PRISMA flow (kalau systematic review)
- [ ] Export CSV

### Langkah 6 — Pemetaan Sitasi
**Tool:** Semantic Scholar → Research Rabbit → Connected Papers → Scite
**Query:** Seed paper: {{SEED_PAPER}}
**Output wajib:**
- [ ] Semantic Scholar: TL;DR + Ask-this-paper
- [ ] Research Rabbit: visual citation graph
- [ ] Connected Papers: Prior/Derivative works
- [ ] Scite: Smart Citations (supporting/contrasting/mentioning)

### Langkah 7 — Penulisan & Referensi
**Tool:** SciSpace (Citation Generator) + Claude (draf) + DeepSeek (sintesis)
**Output wajib:**
- [ ] File `.bib` dengan semua referensi
- [ ] Draft awal (7 bagian atau 5 section)
- [ ] Verifikasi DOI via Crossref (spot-check 5 random)

### Langkah 8 — Deep Research Komprehensif
**Tool:** Gemini Deep Research
**Query template:**
> "Lakukan deep research komprehensif tentang {{TOPIK}} dengan mencakup {{N}} dimensi analisis: [list]. Syarat: minimal 30 sumber dari jurnal Scopus/SINTA 1-2 ({{TAHUN_AWAL}}-{{TAHUN_AKHIR}})."
**Output wajib:**
- [ ] Laporan multi-dimensi (.docx atau .md)
- [ ] Daftar "Karya yang Dikutip" (target N entri)

### Langkah 9 — Unduh & Kompilasi
**Tool:** OpenCode (skrip Python) + XeLaTeX/pdflatex
**Output wajib:**
- [ ] Semua PDF referensi terunduh di folder `referensi/`
- [ ] Log unduhan (berhasil/gagal per URL)
- [ ] `makalah.pdf` compile bersih

## Checklist Verifikasi (Setelah 9 Langkah)

- [ ] Semua DOI terverifikasi (buka di browser)
- [ ] 0 sitasi yatim (`\cite` tanpa padanan `.bib`)
- [ ] 0 referensi menganggur (`.bib` tanpa `\cite`)
- [ ] Tidak ada halusinasi (judul jurnal + author match)
- [ ] PRISMA flow lengkap (kalau systematic review)

## Catatan Penting

1. **Jangan pakai satu tool saja** — setiap tool punya kekuatan berbeda
2. **DeepSeek sebagai orkestrator** — pusat kontrol, bukan pengganti
3. **Angka unduhan bisa bervariasi** — catat rentang, jangan pilih satu
4. **Kitab/buku klasik tidak di Crossref** — cari manual di archive.org / shamela.ws

## File Terkait

- `RESEARCH_PUSTAKA_WORKFLOW.md` — contoh realisasi (Pancasila 2026)
- `[proyek]/WORKFLOW.md` — copy dari file ini untuk proyek spesifik
