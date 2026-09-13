# Workflow Research — Makalah Ilmu Hadis

> Adaptasi alur 9 langkah dari `RESEARCH_PUSTAKA_WORKFLOW.md` (proyek Pancasila 2026)
> untuk topik Ilmu Hadis: periodisasi, penghimpunan, pemalsuan + penyelamatan.
> File ini TIDAK menggantikan `RESEARCH_PUSTAKA_WORKFLOW.md` — hanya adaptasi.

## Pemetaan Adaptasi

| Langkah | Pancasila | → Hadis |
|---|---|---|
| 1 Ideasi | Pancasila sebagai sistem filsafat | Periodisasi + pemalsuan hadis |
| 2 Perplexity | 15 artikel Pancasila | 15 artikel hadis (periodisasi/kodifikasi/pemalsuan) |
| 3 LeapSpace | 4 prompt filosofis | 4 prompt: (1) periodisasi, (2) penghimpunan, (3) pemalsuan, (4) era digital |
| 4 Consensus | Konsensus Pancasila | Konsensus tentang pemalsuan hadis |
| 5 Elicit | Ekstraksi metodologi | Ekstraksi: sumber hadis, kriteria, temuan |
| 6 Peta Sitasi | Seed Latif, Madung | Seed: Ajaj al-Khatib, M.M. Azami, Subhi as-Salih, Ibn al-Jauzi |
| 7 Penulisan | SciSpace + Claude | SciSpace + Claude + **shamela.ws** (kitab Arab) |
| 8 Deep Research | 10 dimensi Pancasila | 10 dimensi hadis |
| 9 Kompilasi | pdflatex IEEE | XeLaTeX + Arab |

## 9 Langkah Adaptasi

### Langkah 1 — Ideasi & Pemetaan (Hadis)
**Tool:** DeepSeek (orkestrator) + LeapSpace brainstorming
**Input:** Periodisasi sejarah hadis (5 periode) + penghimpunan + pemalsuan
**Query:**
> "Brainstorming terstruktur tentang Ilmu Hadis: (1) periodisasi 5 periode
> (Nabi, sahabat, tabi'in, ulama, modern), (2) penghimpunan & kodifikasi,
> (3) pemalsuan (maudu') + upaya penyelamatan. Identifikasi 5 pertanyaan riset,
> 10 keyword (Arab-ID-EN), outline makalah, gap research."
**Output wajib:**
- [ ] 5 research question
- [ ] 10 keyword (Arab + ID + EN)
- [ ] Outline makalah
- [ ] Daftar gap research

### Langkah 2 — Pencarian Literatur Awal (Perplexity)
**Tool:** Perplexity Academic/Pro
**Catatan:** Kitab primer Arab (Bukhari, Muslim) TIDAK ada di Perplexity —
cari di sunnah.com / shamela.ws (lihat `KITAB_PRIMER.md`).

### Langkah 3 — Brainstorming Mendalam (LeapSpace, 4 prompt)
**Strategi:** P1 & P4 = Deep Research, P2 & P3 = Copilot (maks 500 karakter/prompt)
- P1 (Deep Research): periodisasi 5 periode
- P2 (Copilot): penghimpunan (hifz vs kitabah)
- P3 (Copilot): pemalsuan (kritis/komparatif)
- P4 (Deep Research): era digital / relevansi kontemporer
Detail query siap pakai: lihat `QUERY_LIBRARY.md`.

### Langkah 4 — Validasi Konsensus (Consensus)
**Tool:** Consensus (Consensus Meter + Study Snapshots)
**Fokus:** Konsensus tentang pemalsuan hadis (definisi maudu', isnad vs matan,
kontekstualitas larangan penulisan awal).
**Catatan:** Consensus **bukan** meta-analisis formal (maks 20 artikel).
Contoh query: lihat `QUERY_LIBRARY.md` Sub-tema 1–3.

### Langkah 5 — Ekstraksi Terstruktur (Elicit)
**Tool:** Elicit (Agen Penelitian)
**Ekstrak:** (1) sumber hadis/kitab yang dikaji, (2) kriteria penilaian
(sanad/matan), (3) temuan utama, (4) framework (jarh wa ta'dil, takhrij).
Ikuti standar PRISMA 2020 bila systematic review.

### Langkah 6 — Pemetaan Sitasi
**Tool:** Semantic Scholar → Research Rabbit → Connected Papers → Scite
**Seed paper (kajian hadis modern):**
- Ajaj al-Khatib (Ushul al-Hadits)
- M.M. Azami (Studies in Hadith Methodology)
- Subhi as-Salih (kajian hadis)
- Ibn al-Jauzi (al-Maudhu'at — primer klasik, kemungkinan TIDAK terindex
  di database sitasi modern; cari manual)
**Output wajib:**
- [ ] Semantic Scholar: TL;DR + Ask-this-paper
- [ ] Research Rabbit: visual citation graph
- [ ] Connected Papers: Prior/Derivative works
- [ ] Scite: Smart Citations (supporting/contrasting/mentioning)

### Langkah 7 — Penulisan & Referensi
**Tool:** SciSpace (Citation Generator) + Claude (draf) + **shamela.ws** (kitab Arab)
**Catatan khusus hadis:**
- Kitab/buku klasik TIDAK di Crossref — cari manual di
  sunnah.com / shamela.ws / archive.org (lihat `KITAB_PRIMER.md`).
- Buku klasik abad pertengahan (Ibn al-Jauzi, dll) banyak tidak terindex —
  sitasi manual, verifikasi judul + penulis.
- Hadis spesifik butuh takhrij manual — AI tidak bisa memverifikasi sanad.
**Output wajib:**
- [ ] File `.bib` (artikel modern via DOI + entri manual kitab klasik)
- [ ] Draft awal
- [ ] Spot-check 5 DOI random via Crossref

### Langkah 8 — Deep Research Komprehensif (Gemini)
**Tool:** Gemini Deep Research
**Cakup 10 dimensi hadis:**
1. Periodisasi masa Nabi (periwayatan lisan, sahabat penghafal)
2. Masa sahabat (penghimpunan awal, larangan/izin penulisan)
3. Masa tabi'in (kodifikasi resmi era Umar bin Abdul Aziz, tadwin)
4. Masa ulama (kitab Sittah, kriteria seleksi al-Bukhari/Muslim)
5. Metodologi kritik sanad (jarh wa ta'dil)
6. Metodologi kritik matan
7. Pemalsuan (maudu'): motif politik/teologis/sosial
8. Upaya penyelamatan klasik (Ibn al-Jauzi, Ibn Qayyim)
9. Upaya modern (takhrij digital, dorar.net, sunnah.com)
10. Tantangan era digital (hoaks hadis, AI, etika bermedia) + research gaps
**Syarat:** minimal 30 sumber Scopus/SINTA 1-2 (2015–2026) + matriks perbandingan.
**Kendala yang diketahui:** Gemini kadang server penuh — tunda dan kerjakan
tool lain dulu (pelajaran dari proyek Pancasila).

### Langkah 9 — Unduh & Kompilasi
**Tool:** OpenCode (skrip Python) + **XeLaTeX** (dukungan Arab) + font Arab
**Output wajib:**
- [ ] PDF referensi terunduh di `referensi/`
- [ ] Log unduhan (berhasil/gagal per URL)
- [ ] `makalah.pdf` compile bersih (Arab tampil benar)
**Catatan:** Template IEEE pdflatex proyek Pancasila TIDAK cukup untuk teks Arab —
pakai XeLaTeX + paket Arab (mis. `arabxetex`/`polyglossia`), verifikasi rendering.

## Query Perplexity

> "Cari 15 artikel ilmiah terbaru (2021-2026) tentang [sub-tema]. Fokus pada
> [aspek]. Berikan DOI, judul, penulis, ringkasan 1 paragraf per artikel."

### Sub-tema:
1. Periodisasi sejarah hadis
2. Penghafalan & kodifikasi hadis
3. Pemalsuan hadis (maudu')
4. Upaya penyelamatan hadis (takhrij, jarh wa ta'dil)

(Query lengkap per sub-tema: lihat `QUERY_LIBRARY.md`.)

## Checklist Verifikasi (Setelah 9 Langkah)

- [ ] Semua DOI terverifikasi (buka di browser)
- [ ] 0 sitasi yatim (`\cite` tanpa padanan `.bib`)
- [ ] 0 referensi menganggur (`.bib` tanpa `\cite`)
- [ ] Tidak ada halusinasi (judul + penulis match)
- [ ] Kitab klasik terverifikasi manual (judul Arab + penulis benar)
- [ ] PRISMA flow lengkap (kalau systematic review)

## File Terkait

- `RESEARCH_PUSTAKA_WORKFLOW.md` (root) — alur asli Pancasila, JANGAN dimodifikasi
- `QUERY_LIBRARY.md` — query siap pakai (Perplexity/LeapSpace/Consensus/Elicit/Gemini)
- `KITAB_PRIMER.md` — daftar 9 kitab primer + link
- `BUKU_MODERN.md` — daftar buku kajian hadis modern
- `referensi/TRACKER.md` — tracker status referensi
