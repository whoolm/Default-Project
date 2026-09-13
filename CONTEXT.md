# CONTEXT — Default Project

> Dokumen briefing untuk AI agent. Baca ini dulu sebelum task apapun.

## 1. Apa Ini

**Makalah Ceritas + Makalah Pancasila**: repo dokumentasi produk (PRD baseline `v1.0-prd` dari 6 chat DeepSeek, 376 pesan) + output nyata berupa makalah "Pancasila sebagai Sistem Filsafat dan Ideologi Negara" (IEEEtran journal, 2 kolom, 19 hlm, 422 sitasi, PDF 0.65 MB pasca-optimasi) + template LaTeX reusable (`template-ieee/`, tag `template-v2.0`). Aplikasi web (RISE 1–6) eksplisit DITUNDA — fase ini hanya paper/template/docs.

## 2. Struktur Direktori

```
Default Project/
├── PRD.md + 9 dokumen pendukung  → dokumentasi produk
├── WORKFLOW.md                    → SOP lengkap (baca kalau butuh detail)
├── PROMPTS.md                     → prompt siap pakai
├── makalah_pancasila_ieee.*       → makalah final (IEEE, 19 hlm)
├── pancasila_referensi_fix.bib    → daftar pustaka final
├── cover_page.png                 → cover original (5.66 MB, 2487×3508)
├── cover_page_opt.jpg             → cover optimized 518 KB (dipakai PDF)
├── template-ieee/                 → template reusable (nested git repo)
└── arsip/                         → 43 file iterasi lama
```

Dokumen pendukung: `MANIFEST.md`, `README.md`, `ROADMAP.md`, `PENDING_DECISIONS.md`, `TRACEABILITY.md/.csv`, `METODOLOGI_RESEARCH.md`, `PDF_OPTIMIZATION.md`, `AUDIT_REPORT.md`, `CHANGELOG.md`, `CONTRIBUTING.md`. Data mentah: `raw/` → `extracted/` → `memory/`.

## 3. Aturan Wajib

- Format: IEEEtran journal, 2 kolom, pdflatex
- Pipeline compile: `pdflatex → bibtex → pdflatex ×2` (4-pass, via `.\build.ps1`)
- Abstrak label: "Abstract" (wajib `\addto\captionsindonesian{\renewcommand{\abstractname}{Abstract}}`)
- Istilah asing: `\textit{...}`
- Sitasi: `\cite{key}` → `[1]`, `\cite{a,b,c}` → `[1]–[3]`
- Bold di body: DILARANG (hanya judul & label `Abstract—`/`Index Terms—` bold+em-dash)
- Tabel lebar penuh: `\begin{table*}` (bukan `table`)
- Cover: PNG/JPG full-page via `\newgeometry{margin=0}` + `\IfFileExists`, gambar 2000+ px (standar 2480×3508)
- Placeholder template: format HYPHEN `<<NAMA-PLACEHOLDER>>` (bukan underscore)
- Jangan mengarang: data tak ada = `TIDAK_TERSEDIA`; konflik dicatat dua versi, JANGAN diputuskan sepihak

## 4. Yang Sudah Selesai

- ✅ PRD (tag v1.0-prd) + traceability v2 (69 TR: 54 confirmed, 13 inferred, 2 conflicting)
- ✅ Template IEEE (tag template-v2.0, compile 0 error, placeholder HYPHEN)
- ✅ Makalah final (0.65 MB, 19 hlm, 10150 kata, 422 sitasi, 0 error/undefined)
- ✅ PDF optimized 10.44 → 0.65 MB (-93.8%, strategi S1: cover PNG→JPG 2000px q85)
- ✅ Parent repo clean (hasil optimasi AKTIF di working tree, status DITUNDA — lihat §5)

## 5. Yang Masih Terbuka

> Semua K/PD diputuskan 13 Sep 2026 — lihat `DECISIONS.md` (tag `decisions-v1.0`).

- **Keputusan final (DECIDED):** K-01=`pancasila_referensi_fix.bib`; K-02=panggilan+NIM vertikal; K-03=NIM samping nama; K-04=dosen di halaman judul; K-05=cover image full-page; K-06=abstrak ala Elsevier; K-07=`pdflatex`; K-08=rentang 91–94 (metrik pakai 91); K-09=judul existing di `makalah_pancasila_ieee.tex`; K-10–K-13 RIWAYAT (jangan dibuka ulang); PD-01–PD-03 diabaikan; PD-04 minta file (opsional); PD-05 rentang 91–94; PD-06–PD-09 konsisten; PD-10–PD-12 validasi/terima; PD-13 = 6 NFR terukur
- **NFR terukur (PD-13):** compile ≤30 dtk; PDF ≤3 MB; visual vektor + cover ≥150 dpi; 0 error; template→draft ≤2 jam; cross-check sitasi 100%
- **Optimasi PDF DITUNDA (2026-09-13)**: belum commit/rollback; `.bak` masih ada — putuskan (a) COMMIT (b) ROLLBACK (c) TERIMA+S5

## 6. File Kunci

| Butuh | Baca |
|---|---|
| Cara pakai template | `template-ieee/README_TEMPLATE.md` |
| SOP lengkap | `WORKFLOW.md` |
| Prompt siap tempel | `PROMPTS.md` |
| Requirement | `PRD.md` |
| Keputusan terbuka | `PENDING_DECISIONS.md` |
| Timeline | `ROADMAP.md` |
| Requirement → sumber chat | `TRACEABILITY.md` |
| Metode riset | `METODOLOGI_RESEARCH.md` |
| Log optimasi + pelajaran | `PDF_OPTIMIZATION.md` |
| Struktur LaTeX | `template-ieee/template_ieee.tex` |
| Contoh realisasi | `makalah_pancasila_ieee.tex` |
