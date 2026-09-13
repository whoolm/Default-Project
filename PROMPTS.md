# PROMPTS — Siap Tempel ke OpenCode

> Kumpulan prompt untuk task-task umum. Copy → paste → jalankan.
> Semua prompt self-contained: direktori, file acuan, dan kriteria selesai sudah termasuk.
> Direktori kerja: `C:\Users\USER\Documents\Default Project`. Template: `template-ieee/`.

## Prompt 1: Buat Paper Baru dari Template

```markdown
Direktori: C:\Users\USER\Documents\Default Project
Baca dulu: CONTEXT.md, template-ieee/README_TEMPLATE.md, template-ieee/template_ieee.tex (acuan struktur).

Buat paper baru bernama <<NAMA-PAPER>> (ganti dengan nama yang saya beri; kalau belum ada, tanya dulu):

1. Copy template-ieee/template_ieee.tex → <<NAMA-PAPER>>.tex dan template-ieee/referensi_template.bib → referensi_<<NAMA-PAPER>>.bib di folder paper baru (atau root bila saya tidak minta folder baru).
2. Di <<NAMA-PAPER>>.tex: ubah \bibliography{referensi_template} → \bibliography{referensi_<<NAMA-PAPER>>}.
3. List semua placeholder: grep -n '<<' <<NAMA-PAPER>>.tex. Ganti SEMUA yang datanya sudah saya berikan; yang belum ada datanya tulis TIDAK_TERSEDIA (jangan dikarang). Placeholder format HYPHEN (<<NIM-1>>, bukan <<NIM_1>>).
4. Author block format terakhir: panggilan+NIM vertikal, afiliasi 1×, dosen di halaman judul, footer tugas tengah. Cover: siapkan \IfFileExists + \newgeometry{margin=0} + \setcounter{page}{1} seperti template.
5. Terapkan aturan IEEE: label Abstract (wajib \addto\captionsindonesian), label Abstract—/Index Terms— bold+em-dash, istilah asing \textit, sitasi \cite, tabel pakai table*, tanpa \linenumbers, tanpa bold di body.
6. Compile: .\build.ps1 (atau pipeline pdflatex → bibtex → pdflatex ×2). Target: 0 error, 0 undefined citation.
7. Verifikasi: halaman sesuai, abstrak "Abstract", sitasi ter-render, tabel tidak overflow, cover tampil.
8. Laporkan: file yang dibuat, sisa placeholder TIDAK_TERSEDIA, dan status compile. JANGAN commit/tag sebelum saya setuju.
```

## Prompt 2: Update Paper Existing

```markdown
Direktori: C:\Users\USER\Documents\Default Project
Baca dulu: CONTEXT.md dan makalah_pancasila_ieee.tex (bagian yang akan diubah saja).

Update file <<NAMA-FILE>>.tex (default: makalah_pancasila_ieee.tex) sesuai instruksi saya berikut: <<DESKRIPSI-PERUBAHAN>>.

Aturan:
1. Sebelum edit, cross-check \cite{...} ↔ pancasila_referensi_fix.bib bila perubahan menyentuh sitasi (konflik K-01 fix vs final — default pakai fix; tanya saya bila ragu).
2. Ubah minimal, format IEEE untouched kecuali saya minta: \textit untuk istilah asing, tanpa bold body, table* untuk tabel lebar.
3. Compile penuh: .\build.ps1 (pdflatex → bibtex → pdflatex ×2). Jangan dipersingkat jadi 2× pdflatex saja (menyebabkan bibliografi kosong).
4. Verifikasi: 0 error, 0 undefined, diff hanya di bagian yang saya minta.
5. Laporkan diff + status compile. JANGAN commit sebelum saya setuju.
```

## Prompt 3: Optimasi PDF (Target ≤ 3 MB)

```markdown
Direktori: C:\Users\USER\Documents\Default Project
Baca dulu: CONTEXT.md dan PDF_OPTIMIZATION.md (strategi S1 + pelajaran pipeline).

Optimasi <<NAMA-FILE>>.pdf (default: makalah_pancasila_ieee.pdf, saat ini 0.65 MB pasca-S1 — hanya jalankan bila PDF > 3 MB atau saya minta eksplisit):

1. Diagnosa: ukuran PDF, jumlah halaman (PyMuPDF), list image (pdfimages -list), file cover perujuk di .tex (baris \includegraphics).
2. Eksekusi S1 SAJA: resize cover ke lebar 2000 px + simpan JPG q85 sebagai cover_page_opt.jpg (pertahankan cover_page.png asli). Ubah referensi \includegraphics di .tex ke file opt.
3. Compile LENGKAP: pdflatex → bibtex → pdflatex ×2 (wajib ada bibtex; tanpa itu bibliografi kosong).
4. Verifikasi SAMA-SEPERTI-SEBELUM: halaman identik, jumlah kata identik, jumlah sitasi [n] identik, teks vektor ter-ekstrak, 0 error/undefined, banding ketajaman cover (Laplacian, render 150 dpi).
5. JANGAN commit/rollback otomatis. Biarkan working tree + .bak utuh, lalu laporkan opsi: (a) COMMIT (hapus .bak, git add pdf+tex+opt.jpg) (b) ROLLBACK (kembalikan .bak) (c) TERIMA+S5. S2/S3 butuh Ghostscript (tidak tersedia); S5 DILARANG tanpa izin eksplisit saya.
```

## Prompt 4: Verifikasi Typesetting 100% IEEE

```markdown
Direktori: C:\Users\USER\Documents\Default Project
Baca dulu: CONTEXT.md dan template-ieee/README_TEMPLATE.md (§ Aturan Format IEEE).

Audit typesetting file <<NAMA-FILE>>.tex (default: makalah_pancasila_ieee.tex) + PDF-nya:

1. Cek: (a) \documentclass[journal]{IEEEtran}, 2 kolom; (b) label "Abstract" (bukan "Ringkasan"); (c) Abstract—/Index Terms— bold+em-dash; (d) semua istilah asing \textit; (e) tidak ada bold di body (hanya judul/label); (f) sitasi \cite → [n]/[n]–[m]; (g) tabel lebar pakai table*; (h) tanpa \linenumbers; (i) \markboth header terisi; (j) \IEEEPARstart di paragraf pembuka; (k) \bibliographystyle{IEEEtran}; (l) cover full-page + \setcounter{page}{1}.
2. Cross-check \cite ↔ .bib: laporkan sitasi yatim (tanpa padanan .bib) dan referensi menganggur (tanpa \cite).
3. Hitung kata abstrak (target 150–250) dan jumlah keywords (target 5–7).
4. Keluarkan tabel temuan: lokasi (nomor baris) | masalah | perbaikan usulan. Perbaiki hanya yang saya setujui, satu per satu, tanpa mengubah isi substansi.
```

## Prompt 5: Troubleshooting Compile LaTeX

```markdown
Direktori: C:\Users\USER\Documents\Default Project
Baca dulu: CONTEXT.md, WORKFLOW.md §7, template-ieee/BUILD_TEST.md.

File <<NAMA-FILE>>.tex (default: template-ieee/template_ieee.tex) gagal compile. Lakukan:

1. Jalankan pipeline penuh dan tangkap log: pdflatex → bibtex → pdflatex ×2 (atau .\build.ps1). Tampilkan error/warning relevan (Missing $, no line here to end, missing \item, undefined citation, Overfull/Underfull, file not found).
2. Diagnosis sesuai tabel known-error: placeholder underscore → HYPHEN; bbl kosong (tanpa \cite) → tambah sitasi demo; komentar .bib mengandung @token → tulis ulang; cover Overfull → \makebox[\linewidth][c]; abstrak "Ringkasan" → cek \addto\captionsindonesian; tabel overflow → table*; [?] → bibtex + cross-check .bib (konflik fix vs final).
3. Perbaiki akar masalah saja, placeholder <<...>> tetap utuh kecuali itu sumber errornya.
4. Compile ulang sampai 0 error + 0 undefined. Underfull \hbox di author block = kosmetik, abaikan.
5. Laporkan: error awal | penyebab | perbaikan | status akhir compile.
```

## Prompt 6: Commit + Tag + Arsip

```markdown
Direktori: C:\Users\USER\Documents\Default Project
Baca dulu: CONTEXT.md dan WORKFLOW.md §6.

Siapkan commit untuk: <<DAFTAR-FILE-ATAU-PERUBAHAN>>.

1. Jalankan git status + git diff --stat. Pastikan hanya file yang saya maksud yang berubah. Artefak (*.aux/.log/.bbl/.blg/.out/.spl) dan *.bak JANGAN ikut (hapus .bak dulu bila ada; artefak hanya ikut bila saya minta eksplisit).
2. Bila ini hasil optimasi PDF, pastikan keputusan saya sudah jelas: (a) COMMIT / (b) ROLLBACK / (c) TERIMA+S5. Tanpa keputusan = berhenti, jangan commit.
3. Usulkan pesan commit sesuai konvensi (feat:/fix:/docs:/perf:/chore:) + tag bila rilis (paper-v1.0 untuk paper; JANGAN geser v1.0-prd/template-v2.0).
4. Bila ada versi lama yang digantikan, pindahkan ke arsip/ (jangan edit isi arsip).
5. Catat rencana di CHANGELOG.md (tanggal UTC, file, alasan, bahasa Indonesia). Eksekusi commit+tag HANYA setelah saya menyetujui pesan dan daftar file. Tampilkan perintah yang akan dijalankan sebelum eksekusi.
```

## Prompt 7: Resolve Pending Decisions

```markdown
Direktori: C:\Users\USER\Documents\Default Project
Baca dulu: CONTEXT.md, PENDING_DECISIONS.md (PD-01–PD-13 + K-01–K-13), dan DECISIONS.md (bila sudah ada; bila belum ada, anggap semua item belum diputuskan).

Resolve item terbuka berikut: <<ID-ITEM>> (default: mulai dari K-01, lalu K-02 dst; PD-item bila saya minta eksplisit).

Aturan main (W AJIB dipatuhi):
1. Baca konteks item: baris terkait di PENDING_DECISIONS.md (§A/§B/§C/§D) + sumber chat yang dirujuk (PRD.md Lampiran B, TRACEABILITY.md TR terkait). Jangan mengarang — data tak ada = TIDAK_TERSEDIA.
2. Usulkan SATU keputusan + alternatif, masing-masing dengan alasan 2-3 kalimat dari bukti chat. Tandai jelas sebagai USULAN — JANGAN putuskan sendiri.
3. BERHENTI setelah usulan. Tunggu jawaban saya. JANGAN lanjut ke item berikutnya tanpa konfirmasi eksplisit saya.
4. Setelah saya konfirmasi: tulis ke DECISIONS.md (buat baru bila belum ada) dengan format: ID | keputusan | tanggal UTC | alasan 2-3 kalimat. Update status di PENDING_DECISIONS.md: OPEN → DECIDED: <keputusan + tanggal>.
5. Catat alasan ke CHANGELOG.md (tanggal UTC, file, alasan, bahasa Indonesia).
6. Commit terpisah per batch keputusan yang saya setujui (pesan: docs: decide <ID> - <keputusan singkat>). Tampilkan git status + diff sebelum commit; eksekusi HANYA setelah saya setuju.
7. Laporkan: item diputuskan | sisa OPEN | file diubah.
```

## Prompt 8: Buat Varian Elsevier

```markdown
Direktori: C:\Users\USER\Documents\Default Project
Baca dulu: CONTEXT.md, template-ieee/template_ieee.tex (struktur acuan), template-ieee/README_TEMPLATE.md, template-ieee/build.ps1.

Konversi template-ieee/ → template-elsevier/ (repo baru terpisah, tanpa .git lama):

1. Copy struktur folder template-ieee/ → template-elsevier/ KECUALI .git/ (jangan bawa histori). Sertakan: .tex, .bib, build.ps1, clean.ps1, Makefile, .gitignore, README_TEMPLATE.md (akan disesuaikan), cover_page.png.
2. Di .tex baru: ganti \documentclass[journal]{IEEEtran} → \documentclass[preprint,12pt]{elsarticle}. Tambah paket yang dibutuhkan elsarticle; hapus paket khusus IEEE yang konflik (cite, stfloats bila bermasalah — uji via compile).
3. Ganti \bibliographystyle{IEEEtran} → \bibliographystyle{elsarticle-num} dan sesuaikan \bibliography{...} ke nama .bib baru.
4. Ganti author block: \IEEEauthorblockN{} + \IEEEauthorblockA{} → \author{} + \address{} (format elsarticle: \author[nama], \address[afiliasi], \ead untuk email bila ada; NIM sebagai catatan kaki \fnref/\tnoteref bila diminta).
5. Ganti \begin{IEEEkeywords}...\end{IEEEkeywords} → \begin{keyword}...\end{keyword}.
6. Sesuaikan struktur depan: \markboth{...}{...} → \begin{frontmatter} + \title + \author/\address + \begin{abstract}...\end{abstract} + \begin{keyword}...\end{keyword} + \end{frontmatter}. Label abstrak ikut gaya Elsevier (Abstract bold bila itu keputusan K-06 yang berlaku).
7. Pertahankan struktur cover page (titlepage + \newgeometry{margin=0} + \IfFileExists + \restoregeometry + \setcounter{page}{1}) dan equivalent \IEEEPARstart (drop cap manual atau paket lettrine bila perlu).
8. Sesuaikan build.ps1, clean.ps1, Makefile, .gitignore, README_TEMPLATE.md (nama file baru, perintah compile tetap pdflatex → bibtex → pdflatex ×2, troubleshooting khas elsarticle).
9. Compile test sampai 0 error + 0 undefined citation (placeholder HYPHEN <<...>> tetap utuh; jangan pecahkan format placeholder).
10. Git init terpisah di template-elsevier/, commit awal, tag elsevier-v1.0. JANGAN commit ke parent repo sebelum saya setuju; laporkan status compile + diff struktur vs template-ieee.
```

## Prompt 9: Audit Kesehatan Repo

```markdown
Direktori: C:\Users\USER\Documents\Default Project
Baca dulu: CONTEXT.md, MANIFEST.md (daftar file resmi), PENDING_DECISIONS.md, DECISIONS.md (bila ada), TRACEABILITY.md, PRD.md (§5 FR).

Audit repo, HANYA laporan — JANGAN auto-fix apapun:

1. git status (harus clean; laporkan modified/untracked termasuk *.bak dan artefak).
2. git log --oneline -10 (cek konsistensi pesan feat:/fix:/docs:/perf:/chore:).
3. git tag (cek tag vs commit: v1.0-prd, template-v2.0, paper-v* / elsevier-v* bila ada).
4. Cari file yatim: *.aux/*.bbl/*.blg/*.log/*.out/*.spl di root (harus 0), *.bak (harus 0), file di root yang tidak muncul di MANIFEST.md.
5. Cross-check MANIFEST.md: setiap file yang terdaftar benar-benar ada (tandai hilang), dan setiap file di root terdaftar (tandai tak terdaftar).
6. Cross-check PENDING_DECISIONS.md vs DECISIONS.md: item OPEN yang sudah ada keputusan (inkonsistensi), item DECIDED tanpa jejak di DECISIONS.md/CHANGELOG.md.
7. Cross-check TRACEABILITY.md vs PRD.md: requirement (FR-01–FR-14) tanpa jejak TR; TR conflicting (TR-38, TR-68) yang statusnya berubah.
8. Cek nested repo template-ieee/ (dan template-elsevier/ bila ada): git status + tag masing-masing.
9. Output: tabel temuan | status (OK/WARN/ERROR) | rekomendasi (tanpa eksekusi). Urutkan by prioritas: ERROR dulu.
10. Laporkan ringkasan 3 baris: sehat / butuh perhatian / kritis. Tunggu instruksi saya sebelum perbaiki apapun.
```
