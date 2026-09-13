# NFR Validation Report

Tanggal: 2026-09-13
Metode: ukur realita proyek existing (Windows, TeX Live 2026, pdflatex + bibtex)
File: `makalah_pancasila_ieee.tex` + `pancasila_referensi_fix.bib` + `cover_page_opt.jpg`

## Hasil pengukuran

| NFR | Target (PD-13) | Realita | Status |
|---|---|---|---|
| NFR-01 Compile | ≤ 30 dtk | 4,57 dtk (full 4-pass: pdflatex→bibtex→pdflatex×2); 1,54 dtk (single pass) | ✅ PASS |
| NFR-02 Size | ≤ 3 MB | 0,65 MB (`makalah_pancasila_ieee.pdf` pasca full-build) | ✅ PASS |
| NFR-03 Visual | Vektor + cover ≥ 150 dpi | Cover `cover_page_opt.jpg` 2000×2821 px ≈ 242 dpi @A4 full-page; isi vektor pdflatex | ✅ PASS |
| NFR-04 Errors | 0 error | 0 baris `^!` di `.log`; 0 `Citation undefined` pasca full-build; 1 `Overfull \hbox` minor (bukan error) | ✅ PASS |
| NFR-05 Waktu draft | template→draft ≤ 2 jam | N/A — butuh paper baru untuk validasi | ⚠️ BELUM TERUJI |
| NFR-06 Cite | 100% cross-check sitasi↔bib | 100% — 172 blok `\cite`, 365 kunci total, 72 unik; `.bib` 72 entri; orphan 0, bib tak tersitasi 0 | ✅ PASS |

## Perintah yang dijalankan

```powershell
# Full build + ukur
$t = Measure-Command { pdflatex -interaction=nonstopmode makalah_pancasila_ieee.tex | Out-Null; bibtex makalah_pancasila_ieee | Out-Null; pdflatex -interaction=nonstopmode makalah_pancasila_ieee.tex | Out-Null; pdflatex -interaction=nonstopmode makalah_pancasila_ieee.tex | Out-Null }
# Size, cover, errors, cite-match via skrip nfr_check.py (regex \\cite + @key)
```

## Rekomendasi

- NFR yang sudah OK: NFR-01, NFR-02, NFR-03, NFR-04, NFR-06 — tidak perlu revisi target.
- NFR yang perlu revisi: tidak ada (semua yang terukur PASS dengan margin besar).
- NFR-05: butuh paper baru untuk validasi (ukur waktu template→draft ≤ 2 jam pada proyek berikutnya, mis. template-elsevier).
- Catatan: 1 `Overfull \hbox` tersisa — kosmetik, tidak melanggar NFR-04 (0 error). Boleh dirapikan oportunistik, bukan blocker.
- Catatan hitung sitasi: total kunci `\cite` terukur 365 (172 blok, 72 unik) — angka "422 sitasi" di CONTEXT/MANIFEST kemungkinan menghitung dengan metode berbeda; yang mengikat untuk NFR-06 adalah 72/72 unik = 100%.
