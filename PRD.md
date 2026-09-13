# Product Requirements Document (PRD)

## Makalah Ceritas — Academic Paper Writing Assistant + Makalah Pancasila

> Bahasa: Indonesia. Sumber: 6 percakapan DeepSeek (C1–C6, total 376 pesan). Semua isi di bawah berasal dari chat; yang tidak ada datanya ditulis **TIDAK_TERSEDIA**.
> Konflik antar-chat dicatat dua versi (lihat §5, §8, Lampiran B).

---

## 1. Ringkasan Eksekutif

**Makalah Ceritas** adalah platform asisten penulisan makalah akademik (dari PRD awal C1: tipe *Academic Paper Writing Assistant Platform*, pengguna sasaran mahasiswa/peneliti/penulis akademik) yang bertujuan merapikan proses penulisan dari ideasi hingga submisi, dengan verifikasi multi-sumber dan peningkatan kualitas/koherensi tulisan.

Dalam praktiknya (keputusan pengguna di C1), pembangunan aplikasi **ditunda**; tim menempuh jalur **"LLM-only"**: DeepSeek sebagai orkestrator operasional, Claude sebagai penulis/revisor, tim OpenCode sebagai eksekutor, dan gabungan AI tools riset (Consensus, LeapSpace, Perplexity, Gemini Deep Research, Elicit, Semantic Scholar, Research Rabbit, Connected Papers, Scite, SciSpace) sebagai mesin pencari/pemeta literatur. Output nyatanya adalah **makalah "Pancasila sebagai Sistem Filsafat dan Ideologi Negara"** (ontologi–epistemologi–aksiologi, vs liberalisme/komunisme, relevansi global-digital) setebal 20 halaman (Elsevier) / 12 halaman (IEEE), dengan **72 referensi tersitasi penuh**, plus presentasi Beamer.

Status akhir menurut chat: makalah versi IEEE terkompilasi bersih (**0 error, 0 sitasi undefined, 0 overfull box**), metadata 3 penulis (Ilmu Falak, UIN Walisongo Semarang) + dosen pengampu; iterasi perapihan layout/cover masih berjalan di C5–C6.

## 2. Latar Belakang

1. Pengguna memulai dari **roadmap bergambar** (file image) dan meminta PRD dalam file `.md` (C1-msg1), lalu pembagian tugas ke OpenCode via file `.md` (C1-msg3).
2. Agar terkontrol, dipilih pendekatan **LLM-only dengan Staged Prompting dan Human-in-the-Loop** (pengguna sebagai pengontrol) — 7 Tahapan Sistematik (C1-msg5/6).
3. Sebelum membangun aplikasi, pengguna meminta **makalah + presentasi dulu dengan template Elsevier** (C1-msg7): setup direktori `D:\Research & Paper\elsevier` (ditemukan `els-cas-templates`, `elsarticle`, `ecrc-template.tex`, `EM_PM_LaTeX_Guide.pdf`), kompilasi `elsarticle`, makalah contoh METs 17 halaman, dan presentasi Beamer tema Madrid berbahasa Indonesia (C1-msg8–26).
4. Riset isi makalah Pancasila dikerjakan lewat **workflow hybrid multi-AI** (C1-msg29–78): Perplexity (15 referensi) → LeapSpace (4 prompt ≤500 karakter; prompt 1 & 4 Deep Research, 2 & 3 Copilot) → Consensus → Elicit (Agen Penelitian) → Semantic Scholar → Research Rabbit → Connected Papers → Scite (Smart Citations) → SciSpace → Gemini Deep Research (10 rencana riset) → DeepSeek (sintesis operasional) → Claude (penulisan/revisi) → OpenCode (eksekusi/compile).
5. **168 referensi** dari laporan "Riset 10 Dimensi" diunduh via skrip Python (`extract_all_urls.py`, `download_all.py`): **94 berhasil, 31 gagal** (mayoritas HTTP 403/login-wall), retry +1 berhasil, **±30 gagal persisten** (23 ResearchGate, 4 situs institusi, 1 Academia.edu, 2 Taylor & Francis) (C1-msg101–118).
6. Naskah disusun (draf 7 bagian + `.bib` 40 entri: 7 inti terverifikasi Crossref + 33 DOI minimal), direvisi Claude (abstrak 279→~230 kata, 10→6 kata kunci, hapus duplikasi, perbaiki kunci `bengbeng`→`gumilanghudaefi`, tandai 2 entri tanpa `year` + metadata penulis placeholder), lalu **dikonversi Elsevier → IEEE** (`makalah_pancasila_ieee.tex`, 12 halaman, kompilasi bersih) dan dirapikan iteratif (tabel `table*`, header/footer, penulis/afiliasi/NIM, cover, engine kompilasi) di C1-msg183–212 dan C2–C6.

## 3. Tujuan & Non-Tujuan

### Tujuan (Goals)

| ID | Tujuan | Sumber |
|----|--------|--------|
| G-01 | Merapikan penulisan makalah dari ideasi ke submisi akhir (via platform Makalah Ceritas dan/atau workflow LLM-only) | C1-msg2, C1-msg6 |
| G-02 | Menjamin integritas akademik via verifikasi multi-sumber (Consensus, Scite Smart Citations, cross-check sitasi↔bib) | C1-msg2, C1-msg54, C1-msg72, C1-msg139 |
| G-03 | Menghasilkan makalah Pancasila + presentasi siap compile (Elsevier, lalu IEEE) | C1-msg7/8, C1-msg25/26, C1-msg183–188 |
| G-04 | Mengumpulkan 168 referensi dengan 0 gagal unduh | C1-msg101–114 |
| G-05 | Finalisasi format siap submit: abstrak 150–250 kata, 5–7 kata kunci, 72/72 sitasi cocok, tabel/header/footer rapi | C1-msg139, C1-msg146, C1-msg156–170 |
| G-06 | Cover + halaman judul profesional (cover ala jurnal top-tier; halaman 1 = judul/abstrak) | C6-msg21–61 |

### Non-Tujuan (Non-Goals)

| ID | Non-Tujuan | Sumber |
|----|------------|--------|
| NG-01 | **Tidak membangun aplikasi web** (Next.js/Prisma/database/deployment) pada fase ini — di-skip eksplisit | C1-msg28–30 |
| NG-02 | DeepSeek **tidak melakukan riset sendiri**; ia bertindak sebagai operasional/orkestrator ("ingat kamu ini deepseek sebagai operasional") | C1-msg49, C1-msg52 |
| NG-03 | Tidak memakai TikZ/fontspec untuk cover (keputusan pengguna: "gamau tikzzzz"; cover = image) | C5-msg1, C6-msg125 |
| NG-04 | Tidak menebak metadata yang hilang (tahun .bib, email penulis) — wajib ditandai `% TODO(editor)` dan diisi manusia | C1-msg139 |

## 4. Persona & User Journey

### Persona

| Persona | Deskripsi (dari chat) |
|---------|-----------------------|
| Mahasiswa penulis (pengguna) | Mahasiswa Prodi Ilmu Falak, Fakultas Syariah dan Hukum, UIN Walisongo Semarang; anggota tim 3 penulis (Tri Salman Bayu Ramadhan 26020460020, M. Fakhrii Fairus Zain 26020460021, As'ad Dhiya Ulhaq 26020460028); mengontrol LLM, eksekusi PowerShell, unduh manual file login-wall |
| Dosen pengampu | Muhammad Abdur Rosyid Albana, Lc. M.H. (ditempatkan di halaman judul) |
| Orkestrator (DeepSeek) | Mensintesis bahan multi-AI, menulis skrip/prompt/kode LaTeX, mendiagnosis error kompilasi |
| Penulis/Revisor (Claude) | Menyusun & merevisi substansi, koherensi, bahasa, format; verifikasi terprogram sitasi↔bib |
| Eksekutor (Tim OpenCode) | Menjalankan prompt: unduh referensi, compile LaTeX, konversi template |
| Tools AI riset | Perplexity/LeapSpace (search), Consensus (konsensus ilmiah), Elicit/Semantic Scholar/ResearchRabbit/Connected Papers/Scite (pemetaan & validasi), Gemini Deep Research (laporan mendalam), SciSpace (penulisan+sitas), ChatGPT (generate image cover) |

### User Journey (alur yang benar-benar dijalani)

1. Roadmap gambar → PRD `.md` → task breakdown OpenCode (C1-msg1–4).
2. Pilih LLM-only 7 tahap; putuskan konten-dulu (Elsevier) sebelum aplikasi (C1-msg5–8).
3. Inspeksi direktori → install template → compile contoh → makalah METs + Beamer (C1-msg9–26).
4. Kembali ke PRD; tetapkan workflow hybrid multi-AI; tulis 4 prompt LeapSpace + 15 referensi Perplexity (C1-msg27–52).
5. Consensus → Elicit → Semantic Scholar → ResearchRabbit → Connected Papers → Scite → SciSpace (+prompt OpenCode) (C1-msg53–82).
6. Gemini Deep Research: 7→10 rencana riset final dalam 1 prompt gabungan (C1-msg83–96).
7. Unduh 168 referensi → retry gagal → audit HTML → lengkapi manual (C1-msg99–128).
8. Prompt Claude → draf + `.bib` → revisi Claude (72 referensi, abstrak 230 kata) (C1-msg129–140).
9. Compile revisi → perbaiki format (tabel, sitasi, linenumbers, footer) → metadata penulis+NIM (C1-msg141–166).
10. Pilih IEEE sebagai layout terbaik → konversi + compile bersih 12 halaman (C1-msg173–190).
11. Iterasi halaman judul (nama/NIM/afiliasi/dosen/header/footer/logo/judul) (C1-msg191–212, C2, C6-msg1–20).
12. Cover ala Springer (referensi link → desain image via ChatGPT → kode LaTeX cover terpisah tak bernomor) (C6-msg21–103).
13. Typesetting final 100% IEEE: bold/italic/sitasi (C4, C5-msg7–10, C6-msg129–137); terapkan isi docx ke file pasted tanpa ubah format (C3).

## 5. Kebutuhan Fungsional

| ID | Requirement | Deskripsi | Prioritas | Acceptance Criteria |
|----|-------------|-----------|-----------|---------------------|
| FR-01 | PRD + task breakdown `.md` | PRD Makalah Ceritas + `TASK_BREAKDOWN.md` modular (checklist, label, estimasi, good first issue) | Tinggi | File `.md` tersimpan; mencakup RISE 1–6 |
| FR-02 | Workflow LLM-only terkontrol | 7 Tahapan Sistematik + Staged Prompting + Human-in-the-Loop, diawali Tahap 0 Tech Stack | Tinggi | Tahapan terdokumentasi; pengguna pegang kontrol |
| FR-03 | Setup & compile Elsevier | Inspeksi direktori, `elsarticle.cls`, compile `pdflatex+bibtex`, makalah METs 17 hlm + Beamer Madrid | Tinggi | PDF 17 hlm dua kolom; semua elemen render |
| FR-04 | Riset multi-AI terdokumentasi | 4 prompt LeapSpace (≤500 char), 15 ref Perplexity, panduan Consensus/Elicit/Semantic Scholar/Rabbit/Connected/Scite/SciSpace, 10 rencana Gemini | Tinggi | Prompt siap pakai; laporan "Riset 10 Dimensi" |
| FR-05 | Unduhan 168 referensi | `extract_all_urls.py` + `download_all.py` + `retry_failed.py` ke `.../elsevier/referensi/`; audit HTML; manual untuk login-wall | Tinggi | 0 gagal (status chat: ±30 masih gagal — **belum terpenuhi**) |
| FR-06 | Draf + `.bib` awal | `makalah_pancasila_draft.md` 7 bagian + `pancasila_referensi.bib` (7 inti Crossref-valid + 33 DOI minimal) | Tinggi | Compile lolos; 40 referensi |
| FR-07 | Revisi Claude | Hapus duplikasi; angka konsisten (72); abstrak ~230 kata; 6 keywords; kunci `gumilanghudaefi`; `%TODO` untuk year & metadata | Tinggi | 72/72 sitasi cocok; 0 placeholder |
| FR-08 | Konversi Elsevier→IEEE | `makalah_pancasila_ieee.tex` (kelas `journal`, dua kolom) + `.bib` benar + compile `pdflatex→bibtex→pdflatex×2` | Tinggi | 12 hlm; 0 error/undefined/overfull |
| FR-09 | Halaman judul final | Nama panggilan + NIM; afiliasi 1×; dosen di judul; header `\markboth`; footer tugas tengah tak nabrak; logo; nama vertikal | Tinggi | PDF rapi; tanpa duplikasi/tabrakan |
| FR-10 | Tabel & sitasi rapi | `table*` full-width; tanpa `\linenumbers`; sitasi `[1]–[3]`; pustaka `IEEEtran` | Sedang | Tabel tak tindih; 0 `[?]` |
| FR-11 | Cover profesional | Cover image full-halaman terpisah (tak bernomor; hal.1 = judul/abstrak); desain ala Springer (latar Batavia + logo) | Sedang | Cover tampil penuh; tidak blank |
| FR-12 | Typesetting 100% IEEE | Label **Abstrak—**/**Index Terms—** bold+em-dash; 20+ istilah asing italic; bold hanya heading; petik EYD | Sedang | Lolos cek visual per C4/C5 |
| FR-13 | Abstrak "Abstract" | Judul abstrak tetap "Abstract" (bukan "Ringkasan") di semua engine | Sedang | Output PDF bertuliskan "Abstract" |
| FR-14 | Terapkan docx→tex | Isi docx ke file pasted, format untouched | Sedang | Diff hanya teks isi |

**Konflik yang dicatat (dua versi):**
- (a) **Acuan `.bib`:** C1 → `pancasila_referensi_fix.bib` (72 sitasi cocok; `final` cacat). C6-msg109 → `pancasila_referensi_final.bib` ("coba inget-inget di memory"). Keduanya dicatat; wajib verifikasi `\cite{}`↔`.bib` sebelum compile.
- (b) **Nama penulis:** evolusi lengkap+NIM (C1-msg164–166) → panggilan+NIM di samping nama (C1-msg203–212, C2) → vertikal (C2-msg9). Versi terakhir yang diminta: vertikal.

## 6. Kebutuhan Non-Fungsional

| ID | Kategori | Requirement | Target (diputuskan manusia 13 Sep 2026 — lihat DECISIONS.md PD-13) | Sumber |
|----|----------|-------------|------------------------------------------------------|--------|
| NFR-01 | Format | Template akhir IEEE Transactions/Journal dua kolom; abstrak ala Elsevier; margin ketat; tanpa teks "nyebrang" | Teks isi vektor; cover ≥ 150 dpi; 0 overfull box | C1-msg173–180 |
| NFR-02 | Kualitas kompilasi | 0 error fatal; 0 sitasi undefined; 0 overfull box; PDF 12 hlm (IEEE) / 20 hlm (Elsevier) | Compile errors = 0; compile time ≤ 30 detik; PDF size ≤ 3 MB | C1-msg187/188 |
| NFR-03 | Integritas data | 72/72 sitasi↔bib cocok; tanpa broken citation/orphan reference; `%TODO` eksplisit untuk data hilang | Cross-check sitasi = 100%; 0 orphan/yatim | C1-msg139 |
| NFR-04 | Gaya selingkung | Abstrak 150–250 kata; 5–7 kata kunci; istilah asing italic; bold hanya heading; sitasi `[n]` | Abstrak 150–250 kata; 5–7 kata kunci (validasi manusia 13 Sep 2026) | C1-msg139, C4 |
| NFR-05 | Kompatibilitas toolchain | TeX Live 2026; `pdflatex` (cover image) / `xelatex`/`lualatex` (cover programatik); tanpa TikZ/fontspec untuk jalur pdflatex; `tlmgr` tanpa `sudo` di Windows | Engine final = `pdflatex` (K-07, 13 Sep 2026); TeX Live 2026 | C5, C6-msg71, C6-msg133–135 |
| NFR-06 | Etika & legalitas | Hormati login-wall/paywall (ResearchGate, Academia.edu, Taylor & Francis); unduh manual dengan akun; cantumkan status in-press/online-first untuk ref 2026 | 100% sumber berlisensi jelas / manual ber-akun; tanpa bypass otomatis | C1-msg112–118, C1-msg139 |
| NFR-07 | Keterbatasan AI | Batas LeapSpace 500 char/prompt; Gemini dapat penuh; Claude tanpa akses direktori (via unggah/OpenCode) | Waktu template→draft ≤ 2 jam; batas LeapSpace 500 char/prompt | C1-msg39, C1-msg57, C1-msg133–136 |

## 7. Alur Sistem

```
[Roadmap gambar] → [PRD.md] → [TASK_BREAKDOWN.md]
      → [Keputusan: LLM-only, konten-dulu]
      → [Setup Elsevier] → pdflatex/bibtex → [PDF 17 hlm + Beamer]
      → [Riset multi-AI: Perplexity(15) + LeapSpace(4) + Consensus + Elicit
         + Semantic Scholar + Rabbit + Connected + Scite + SciSpace
         + Gemini Deep Research(10 rencana)]
      → [Laporan Riset 10 Dimensi (168 ref)]
      → [Unduh 168: download_all.py → retry_failed.py → audit HTML → manual]
      → [Prompt Claude] → [draf.md + .bib(40)] → [Revisi Claude (72 ref)]
      → [Compile revisi] → [Perbaiki tabel/sitasi/footer/metadata]
      → [Konversi IEEE] → [PDF 12 hlm bersih]
      → [Iterasi judul/cover] → [Typesetting 100% IEEE] → [Siap submit]
```

Peran: Pengguna (kontrol) → DeepSeek (orkestrasi) → Claude (tulis/revisi) → OpenCode (eksekusi). (C1-msg136–140)

## 8. Data & Integrasi

| Data | Detail (dari chat) |
|------|--------------------|
| Korpus literatur | 2015–2026; Scopus Q1–Q2 + SINTA 1–2; 168 entri; 72 disitasi penuh; 30 dokumen pendukung lokal (metadata dari halaman pertama) |
| Data empiris | CSIS 2023 (90,5% milenial tolak ganti ideologi; 53,7% intoleran pemimpin beda agama), PSKI-Litbang Kompas 2023 (86,1% mahasiswa tolak alternatif; 28,6% paham mendalam), Indeks Pembumian Pancasila Semarang |
| File kerja | `makalah_pancasila_draft.md`, `pancasila_referensi.bib`, `makalah_pancasila_final/revisi/gabungan/fix/ieee.*`, `pancasila_referensi_final/fix.bib`, `PKN 1.docx`, `Makalah-Pancasila-Revisi-Final-Humanized.docx`, gambar (cover_page 482×680, batavia_, garuda_pancasila, logo_walisongo, dema_fsh, hmj_if) |
| Integrasi AI | LeapSpace, Perplexity, Consensus, Elicit, Semantic Scholar, ResearchRabbit, Connected Papers, Scite, SciSpace, Gemini, ChatGPT — via prompt + tempel manual (tanpa API otomatis) |
| Integrasi file | SciSpace: Citation Generator via DOI; Claude: unggah file/`+`; OpenCode: eksekusi lokal `D:\Research & Paper\elsevier` dan `C:\Users\USER\Documents\Default Project\` |
| **Konflik data** | `.bib` acuan: `fix` (C1) vs `final` (C6) — verifikasi ulang wajib |

## 9. Arsitektur Algoritma

(TIDAK ada algoritma ML/statistik yang dibahas di chat — yang ada adalah metodologi riset + pipeline engineering. Lihat `METODOLOGI_RESEARCH.md` untuk basis riset lengkap.)

1. **Staged Prompting + Human-in-the-Loop** — 7 Tahapan Sistematik, pengguna pegang kontrol mutu tiap tahap (C1-msg6).
2. **Workflow hybrid multi-AI** — pembagian peran per tools (search → konsensus → pemetaan → validasi → deep research → orkestrasi → penulisan → eksekusi) (C1-msg30–78).
3. **PRISMA 2020** — identifikasi → skrining → eligibilitas → inklusi atas literatur 2015–2026 (C2-msg5, isi makalah).
4. **Hermeneutika filosofis** — Gadamer (*fusion of horizons*), Ricoeur (emansipatoris), lingkaran Schleiermacher; uji berlapis rasional-etis-deliberatif (isi makalah C2-msg5).
5. **Pipeline unduhan** — ekstrak URL → unduh (Session, header browser, Referer rotasi, timeout 90 dtk, 5× retry) → audit HTML-vs-PDF → manual login-wall (C1-msg102–126).
6. **Pipeline LaTeX** — `pdflatex → bibtex → pdflatex ×2`; konversi elsarticle→IEEEtran; `table*`, `\newgeometry/\restoregeometry` cover, `\addto\captionsindonesian` untuk "Abstract" (C1-msg187, C5–C6).
7. **Verifikasi terprogram Claude** — cross-check `\cite{}`↔`.bib`, hitung kata abstrak, cek duplikasi, kompilasi ringan (C1-msg139).

## 10. Metrik Keberhasilan

| Metrik | Target (dari chat) | Status di chat |
|--------|--------------------|----------------|
| PDF Elsevier terkompilasi | 17 hlm, semua elemen render | ✅ Tercapai (C1-msg24) |
| PDF IEEE terkompilasi | 12 hlm, 0 error/undefined/overfull | ✅ Tercapai (C1-msg187) |
| Kesesuaian sitasi↔bib | 72/72 (0 yatim/menganggur) | ✅ Tercapai pasca-revisi (C1-msg139) |
| Abstrak | 150–250 kata | ✅ ~230 kata |
| Kata kunci | 5–7 | ✅ 6 frasa |
| Referensi terunduh | 168, 0 gagal | ❌ ±30 masih gagal (C1-msg114) |
| Rencana riset | 10 final siap eksekusi | ✅ Final ditulis (C1-msg94) |
| Layout/cover final | Rapi ala IEEE/Springer, tanpa tabrakan/blank | 🔄 Iterasi berjalan (C5–C6) |

## 11. Risiko & Mitigasi

| Risiko | Dampak | Mitigasi (dari chat) |
|--------|--------|----------------------|
| Tool AI penuh/berkuota (Gemini, LeapSpace 500 char) | Alur riset macet | Tunda & kerjakan tool lain dulu; bagi prompt (1&4 Deep Research, 2&3 Copilot) |
| 403/login-wall/paywall (ResearchGate dkk.) | 30 file gagal | Retry ber-header; unduh manual ber-akun; cari preprint/alternatif |
| URL artikel (HTML) bukan PDF langsung | File HTML menumpuk | Audit isi; konversi hanya yang prioritas; baca profil/modul di browser saja |
| Placeholder & inkonsistensi (`[Isi sama]`, 68 vs 72, tanpa `year`, metadata generik) | Gagal screening editorial | Verifikasi terprogram; `%TODO(editor)`; perbaiki angka aktual |
| Rapuhnya layout LaTeX (thanks/pubid/linenumbers/table) | PDF acak-acakan, `[?]` | Copy dari file yang terbukti berhasil; ubah minimal; `table*`; hapus linenumbers; cek `.bib` |
| Konflik acuan `.bib` (fix vs final) | Sitasi `[?]` terulang | Cross-check `\cite{}`↔`.bib` sebelum setiap compile |
| Upscale gambar kecil ke A4 | Cover pecah saat cetak | Buat ulang gambar beresolusi tinggi via ChatGPT sesuai layout |

## 12. Roadmap & Milestone

| Milestone | Isi | Status (per chat) |
|-----------|-----|-------------------|
| M1 | PRD + task breakdown + keputusan LLM-only | ✅ Selesai (C1-msg1–6) |
| M2 | Setup Elsevier + makalah METs + Beamer | ✅ Selesai (C1-msg9–26) |
| M3 | Riset multi-AI + 10 rencana + laporan 168 ref | ✅ Selesai (C1-msg29–100) |
| M4 | Unduh 168 referensi, 0 gagal | 🔄 94+1 ok, ±30 gagal (C1-msg101–128) |
| M5 | Draf + `.bib` + revisi Claude (72 ref) | ✅ Selesai (C1-msg129–140) |
| M6 | Konversi IEEE + compile bersih | ✅ Selesai (C1-msg183–190) |
| M7 | Halaman judul + cover + typesetting final | 🔄 Berjalan (C1-msg191–212, C2–C6) |
| M8 (ditunda) | Bangun aplikasi Makalah Ceritas (RISE 1–6) | ⏸️ Non-tujuan fase ini |

## 13. Acceptance Criteria (rilis makalah)

1. `makalah_pancasila_ieee.pdf` 12 halaman, compile tanpa error/warning fatal.
2. 0 sitasi `[?]`; daftar pustaka IEEE lengkap 72 entri; 0 orphan/yatim.
3. Abstrak berjudul **Abstract**, 150–250 kata; **Index Terms** 5–7 frasa.
4. Tabel 1–2 full-width (`table*`), tanpa teks tindih/nyebrang; tanpa nomor baris.
5. Halaman judul: nama panggilan + NIM (vertikal), afiliasi 1×, dosen pengampu, header, footer tugas tengah tanpa tabrakan, logo tampil.
6. Cover image full-halaman terpisah, tidak dihitung sebagai halaman 1.
7. Istilah asing italic; bold hanya heading/label; sitasi `[n]` konsisten.
8. Metadata penulis final (3 nama + NIM + afiliasi + corresponding email) terisi — tanpa placeholder.

## 14. Lampiran

### Lampiran A — Daftar file yang disebut di chat

`TASK_BREAKDOWN.md`, `presentasi.tex`, `ecrc-template.tex`, `elsarticle-template-num.tex`, `makalah_METs.tex`, `references.bib`, `extract_all_urls.py`, `download_all.py`, `retry_failed.py`, `gagal.txt`, `Riset 10 Dimensi Filsafat Pancasila dan Relevansi Kontemporer.docx`, `makalah_pancasila_draft.md`, `pancasila_referensi.bib`, `makalah_pancasila_final/revisi/gabungan/fix/ieee(.tex/.bib/.pdf)`, `pancasila_referensi_final/fix.bib`, `bare_jrnl.tex`, `bare_jrnl_transmag.tex`, `PKN 1.docx`, `Makalah-Pancasila-Revisi-Final-Humanized.docx`, `cover_page.png`, `batavia_.png`/`batavia.png`, `garuda_pancasila.png`, `logo_walisongo.png`, `dema_fsh.png`, `hmj_if.png`.

### Lampiran B — Konflik antar-chat (dua versi)

1. **Acuan `.bib`:** Versi C1: `pancasila_referensi_fix.bib` (benar; 72 cocok). Versi C6: `pancasila_referensi_final.bib` (klaim memori pengguna). Catatan: keduanya ada di chat; cross-check sebelum compile.
2. **Format nama penulis:** Versi awal (C1-msg164–166): nama lengkap + NIM + email corresponding. Versi akhir (C1-msg203–212, C2): panggilan (Salman, Fairus, As'ad) + NIM di samping nama, vertikal.
3. **Cover:** Versi kode (TikZ, C6 awal) vs versi image (C5 + keputusan akhir C6). Catatan: keputusan akhir = image; TikZ ditolak pengguna.

### Lampiran C — Sumber

C1 `https://chat.deepseek.com/share/uu1swa3yr7ugtgx3kn` · C2 `https://chat.deepseek.com/share/027f4tgdrpyi7wt75e` · C3 `https://chat.deepseek.com/share/x9pgajcgj2d6ke4ebb` · C4 `https://chat.deepseek.com/share/r2gls2fvehrrvpufok` · C5 `https://chat.deepseek.com/share/kidbec3ztiugrs0nx4` · C6 `https://chat.deepseek.com/share/t0rcrajn3a8y2d15pi`

---

## 15. Glossary (otomatis dari istilah chat — FASE 3)

| Istilah | Arti dalam konteks chat |
|---------|-------------------------|
| Makalah Ceritas | Platform asisten penulisan makalah akademik (PRD awal C1) |
| RISE 1–6 | Kelompok fitur di roadmap gambar pengguna (isi gambar tak terekstrak — PD-04) |
| LLM-only | Pengerjaan tanpa kontributor manusia; pengguna kontrol, LLM eksekusi |
| Staged Prompting / Human-in-the-Loop | Kerja bertahap dengan pengguna sebagai pengontrol mutu |
| elsarticle / IEEEtran | Kelas dokumen LaTeX Elsevier / IEEE |
| BibTeX / `.bib` | Sistem + file daftar pustaka (`\cite{}` ↔ entri) |
| Sitasi yatim / orphan reference | Sitasi tanpa padanan `.bib` (atau sebaliknya) |
| `[?]` | Sitasi gagal render (BibTeX gagal / `.bib` tak ditemukan) |
| `table*` | Tabel selebar penuh di dokumen dua kolom |
| `\linenumbers` | Nomor baris (1000+ di draf; wajib hapus di final) |
| `\thanks{}` / `\IEEEpubid` / `\markboth` | Catatan kaki judul / ID publikasi footer / header berjalan |
| `\IEEEPARstart` | Drop cap (huruf awal besar) paragraf pembuka IEEE |
| PRISMA 2020 | Protokol studi literatur sistematis (identifikasi–skrining–eligibilitas–inklusi) |
| Smart Citations | Fitur Scite: sitasi diklasifikasi mendukung/menyebut/membantah |
| Deep Research (LeapSpace/Gemini) | Riset multi-langkah berbasis ratusan sumber |
| Monodualisme / monopluralisme | Konsep ontologi manusia Pancasila (Notonagoro/Pristiwiyanto) |
| *Empty signifier* / *agonizing Pancasila* | Kritik post-foundational Kim 2024 |
| SINTA / Scopus Q1–Q2 | Indeks jurnal nasional / internasional (kriteria korpus) |
| login-wall / paywall | Pembatas unduhan (ResearchGate, Academia.edu, Taylor & Francis) |
| tlmgr / TeX Live 2026 | Manajer paket / distribusi LaTeX yang dipakai |

## 16. Dependency Matrix (otomatis dari FR — FASE 3)

Dibaca: baris diblokir oleh kolom (×). FR Sedang tanpa ketergantungan dikosongkan.

| FR | diblokir oleh → | FR-01 | FR-02 | FR-04 | FR-05 | FR-06 | FR-07 | FR-08 |
|----|-----------------|-------|-------|-------|-------|-------|-------|-------|
| FR-02 | Workflow LLM-only | × | — | | | | | |
| FR-04 | Riset multi-AI | | × | — | | | | |
| FR-05 | Unduhan 168 | | | × | — | | | |
| FR-06 | Draf + `.bib` | | | × | (× parsial: 7 inti cukup untuk mulai) | — | | |
| FR-07 | Revisi Claude | | | | | × | — | |
| FR-08 | Konversi IEEE | | | | | | × | — |
| FR-09 | Halaman judul final | | | | | | | × |
| FR-10 | Tabel & sitasi rapi | | | | | | | × |
| FR-11 | Cover profesional | | | | | | | × |
| FR-12 | Typesetting IEEE | | | | | | × | × |
| FR-03 | Setup Elsevier | × | | | | | | |
| FR-13 | Abstrak "Abstract" | | | | | | | × |
| FR-14 | docx→tex | | | | | | | × |

Rantai kritis: FR-01 → FR-02 → FR-04 → FR-06 → FR-07 → FR-08 → FR-09/10/11/12. FR-05 paralel (pemblokir parsial FR-06).

## 17. User Stories (FR prioritas Tinggi — FASE 3)

| ID | User Story |
|----|------------|
| US-01 (FR-01) | Sebagai pengguna, saya ingin PRD + task breakdown dalam `.md`, agar tim OpenCode bisa mengeksekusi per modul. |
| US-02 (FR-02) | Sebagai pengguna, saya ingin tahapan LLM-only yang terkontrol, agar output LLM tidak "ngawur". |
| US-03 (FR-03) | Sebagai mahasiswa, saya ingin template Elsevier terinstal + contoh terkompilasi, agar bisa langsung menulis makalah. |
| US-04 (FR-04) | Sebagai peneliti, saya ingin prompt siap pakai per AI tool, agar riset multi-AI bisa dijalankan sekarang juga. |
| US-05 (FR-05) | Sebagai pengguna, saya ingin 168 referensi terunduh otomatis (0 gagal), agar korpus lengkap tanpa kerja manual. |
| US-06 (FR-06) | Sebagai penulis, saya ingin draf 7 bagian + `.bib` terverifikasi, agar naskah bisa disusun di SciSpace. |
| US-07 (FR-07) | Sebagai penulis, saya ingin revisi Claude yang konsisten (72/72, abstrak ~230 kata), agar siap format final. |
| US-08 (FR-08) | Sebagai penulis, saya ingin konversi IEEE yang terkompilasi bersih, agar layout rapi standar jurnal. |
| US-09 (FR-09) | Sebagai mahasiswa, saya ingin halaman judul (nama+NIM+afiliasi+dosen+footer) rapi tak nabrak, agar memenuhi syarat tugas. |

## 18. Open Questions (USULAN — diputuskan manusia, FASE 3)

| ID | Pertanyaan | Konteks chat |
|----|------------|--------------|
| OQ-01 | xelatex vs lualatex untuk cover bergambar — mana standar final? | C6-msg111–135 |
| OQ-02 | Bisakah cover di-generate murni via pdflatex? | C6-msg135 |
| OQ-03 | Cover via code vs desain image — keputusan final? (pengguna menolak TikZ, perlu konfirmasi) | C6-msg55–125, PD-08 |
| OQ-04 | Instalasi/paket/font apa yang masih kurang di mesin pengguna? | C6-msg67–75 |
| OQ-05 | 10 rencana riset: gas eksekusi atau perbaiki dulu? | C1-msg95 |
| OQ-06 | Bagaimana mencapai 0 gagal unduh untuk 23 file ResearchGate? | C1-msg111–118 |
| OQ-07 | File HTML mana yang wajib dikonversi ke PDF? | C1-msg121–128 |
| OQ-08 | Bagaimana Claude mengakses direktori file secara langsung? | C1-msg133–136 |
| OQ-09 | Judul final makalah (opsi bermakna sama) — pilih yang mana? | C1-msg191, C6-msg43 |
| OQ-10 | Target angka NFR (NFR-01–NFR-07) — nilai resmi? | §6 kolom Target |

## 19. Out of Scope

> Status: FINAL (divalidasi 2026-09-13, Gap 7). Sebelumnya "USULAN — perlu validasi manusia, FASE 3".

Fitur/pekerjaan berikut eksplisit TIDAK termasuk dalam scope PRD v1.0:

1. **Data lampiran eksternal** (PD-01) — 92 file DOCX/PDF/TXT/CSV/TEX tidak bisa diakses via share API; hanya tersedia di device pemilik chat (OS-03).
2. **Thinking blocks** (PD-02) — 188 blok (~733K char) = proses internal AI, bukan keputusan produk (OS-04).
3. **Cabang pruned** (PD-03) — 29 pesan kosong + cabang eksperimen = duplikat, di luar ringkasan.
4. **Implementasi konkret RISE 1–6** — roadmap ada, tapi development belum dimulai; pembangunan aplikasi web Makalah Ceritas eksplisit ditunda (NG-01, OS-01).
5. **Multi-user collaboration** — single-user authoring tool untuk v1.0.
6. **Auto-translate** — tidak direncanakan untuk v1.0.
7. **Custom template builder** — user hanya bisa pakai template yang tersedia (IEEE, Elsevier).
8. **Riset primer/survei baru** — hanya literatur + data sekunder yang ada (korpus 2015–2026 + survei existing) (OS-02).
9. **Bypass login-wall/paywall otomatis** — manual ber-akun saja, di luar skope (OS-05, etika NFR-06).
10. **Desain cover programatik TikZ** — di luar skope karena cover image diputuskan final (PD-08, OS-06; NG-03).
