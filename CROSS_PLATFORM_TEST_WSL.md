# Cross-Platform Test Report — WSL Ubuntu

Tanggal: 2026-09-13
Platform: WSL2 Ubuntu (LAPTOP-IC5DBJ69) + TeX Live 2025 (Debian)
Metode: `wsl -d Ubuntu -u root bash -c "./build.sh"`

## Hasil
| Template | build.sh | PDF | Status |
|---|---|---|---|
| template-ieee | ✅ 4-pass | 85.548 B | PASS |
| template-elsevier | ✅ 4-pass | 203.826 B | PASS |

## Bug yang Ditemukan & Diperbaiki

### 1. `babel-indonesian` tidak ada di Ubuntu minimal
- **Gejala:** `! Package babel Error: Unknown option 'indonesian'`
- **Fix:** `apt install texlive-lang-other`

### 2. `IEEEtran.cls` tidak ada di `texlive-latex-extra`
- **Gejala:** `! LaTeX Error: File 'IEEEtran.cls' not found.`
- **Fix:** `apt install texlive-publishers`

### 3. `microtype` font expansion gagal di elsarticle + Linux
- **Gejala:** `! pdfTeX error (font expansion): auto expansion is only possible with scalable fonts.`
- **Akar:** `elsarticle` di Linux tidak punya scalable font default; `microtype` gagal font expansion
- **Fix:** Tambah `\usepackage[T1]{fontenc}` + `\usepackage{lmodern}` sebelum `microtype`
- **Catatan:** Bug ini HANYA muncul di Linux — di Windows font fallback menyembunyikannya. Cross-platform test menemukannya.

## Environment Tested
- WSL2 2.7.14 di Windows 11
- Ubuntu (resolute) + TeX Live 2025/Debian
- User: whoolm (UID bukan root)

## Status Gap 5: ✅ CLOSED — build.sh verified di Linux via WSL2
