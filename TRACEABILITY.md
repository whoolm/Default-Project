# Traceability Matrix v2

## Chat → Requirement → Algoritma/Metode → Dataset → Metrik → Prioritas (+ jangkar & status)

> FASE 4 (2026-09-13). Menggantikan v1 (TR-01–TR-20 tanpa jangkar — lihat `AUDIT_REPORT.md` §3).
> `message_index` = nomor pesan 1-based di `extracted/C*.json` (urut `message_id`); `raw_message_id` = ID asli API.
> Status: `confirmed` = klaim diverifikasi baca manual; `inferred` = cocok kata kunci + baca kepala pesan (perlu spot-check manusia, PD-12); `conflicting` = bertentangan dengan pesan lain (JANGAN diputuskan — lihat `PENDING_DECISIONS.md`).
> Aturan global tetap: tanpa mengarang; `TIDAK_TERSEDIA` bila tak ada data.

| ID | chat_id | message_index | raw_message_id | status | Requirement | Algoritma/Metode | Dataset | Metrik | Prioritas | test_method |
|----|---------|----------------|----------------|--------|-------------|------------------|---------|--------|-----------|-------------|
| TR-01 | C1 | 1 | 1 | confirmed | PRD .md sesuai roadmap gambar | Staged Prompting (permintaan) | Roadmap gambar pengguna | File PRD ada | Tinggi | baca extracted/C1.json msg1 |
| TR-02 | C1 | 2 | 2 | confirmed | PRD Makalah Ceritas + objektif drv roadmap | Sinteisis asisten -> PRD | Roadmap + pengetahuan umum | PRD mencakup RISE | Tinggi | baca extracted/C1.json msg2 (kepala) |
| TR-03 | C1 | 3 | 3 | confirmed | Task breakdown ke OpenCode via .md | Dekomposisi modular + label | PRD C1 | TASK_BREAKDOWN.md ada | Tinggi | baca extracted/C1.json msg3 |
| TR-04 | C1 | 4 | 4 | confirmed | TASK_BREAKDOWN.md modular diserahkan | Checklist + good-first-issue | PRD C1 | File tersimpan di root | Tinggi | baca extracted/C1.json msg4 (kepala) |
| TR-05 | C1 | 5 | 5 | confirmed | Tahapan LLM-only agar terkontrol | Staged Prompting + Human-in-the-Loop | TIDAK_TERSEDIA | 7 tahapan terdokumentasi | Tinggi | baca extracted/C1.json msg5 |
| TR-06 | C1 | 6 | 6 | confirmed | 7 Tahapan Sistematik + Tahap 0 stack | Staged Prompting | Contoh Next.js | Dokumen tahapan | Tinggi | baca extracted/C1.json msg6 (kepala) |
| TR-07 | C1 | 7 | 7 | confirmed | Makalah + presentasi Elsevier dulu, aplikasi tunda | Keputusan skope | TIDAK_TERSEDIA | Keputusan tercatat | Tinggi | baca extracted/C1.json msg7 |
| TR-08 | C1 | 9 | 9 | confirmed | Skrip PowerShell inspeksi direktori Elsevier | Inspeksi direktori via skrip | D:\Research & Paper\elsevier | Output inspeksi ditempel | Tinggi | baca extracted/C1.json msg9 |
| TR-09 | C1 | 19 | 19 | confirmed | Contoh paper template Elsevier (METs) | Referensi format | Contoh paper METs (gambar) | File .tex isi dibuat | Tinggi | baca extracted/C1.json msg19 |
| TR-10 | C1 | 20 | 20 | confirmed | File makalah METs + references.bib | Penulisan + BibTeX | Konten METs | Siap compile | Tinggi | baca extracted/C1.json msg20 (kepala) |
| TR-11 | C1 | 24 | 24 | confirmed | Kompilasi Elsevier 17 hlm sukses | pdflatex+bibtex | ecrc/elsarticle | 17 hlm, elemen lengkap | Tinggi | kompilasi ulang pdflatex; cek visual PDF |
| TR-12 | C1 | 25 | 25 | confirmed | Presentasi makalah dibuatkan | Beamer tema Madrid (ID) | Isi makalah METs | File presentasi.tex | Tinggi | baca extracted/C1.json msg25 |
| TR-13 | C1 | 26 | 26 | confirmed | File presentasi Beamer diserahkan | Beamer | Isi makalah | Compile 2x pdflatex | Tinggi | baca extracted/C1.json msg26 (kepala); kompilasi ulang |
| TR-14 | C1 | 29 | 29 | confirmed | Workflow praktis multi-AI (consensus/leapspace/perplexity/gemini/deepseek) | Orkestrasi multi-AI | TIDAK_TERSEDIA | Workflow 4 fase | Tinggi | baca extracted/C1.json msg29 |
| TR-15 | C1 | 30 | 30 | confirmed | Skip aplikasi web (Next.js/Prisma) | Keputusan skope | TIDAK_TERSEDIA | Keputusan tercatat | Tinggi | baca extracted/C1.json msg30 (kepala) |
| TR-16 | C1 | 31 | 31 | confirmed | Penulisan pakai Claude | Penulisan LLM | Bahan riset | Keputusan tercatat | Tinggi | baca extracted/C1.json msg31 |
| TR-17 | C1 | 33 | 33 | confirmed | Topik Pancasila 3 dimensi + komparasi | Framing riset | TIDAK_TERSEDIA | 3 sub-topik | Tinggi | baca extracted/C1.json msg33 |
| TR-18 | C1 | 39 | 41 | confirmed | Batas LeapSpace 500 karakter | Batasan tool | UI LeapSpace | Prompt <=500 char | Sedang | baca extracted/C1.json msg39 |
| TR-19 | C1 | 47 | 49 | confirmed | Alokasi Deep Research p1&p4, Copilot p2&p3 | Alokasi kuota riset | 4 prompt | Keputusan tercatat | Sedang | baca extracted/C1.json msg47 |
| TR-20 | C1 | 49 | 55 | confirmed | Empat prompt LeapSpace final | Prompt engineering <=500 char | Topik Pancasila | 4 prompt siap pakai | Tinggi | baca extracted/C1.json msg49 |
| TR-21 | C1 | 53 | 59 | confirmed | Langkah Consensus | Consensus evidensial | 200 jt+ paper | Pertanyaan terjawab | Sedang | baca extracted/C1.json msg53 |
| TR-22 | C1 | 59 | 65 | confirmed | Elicit mode agen penelitian | Elicit agent | Korpus Elicit | Hasil tabel | Sedang | baca extracted/C1.json msg59 |
| TR-23 | C1 | 63 | 69 | confirmed | Lanjut ke Semantic Scholar | Crawling Scholar | Korpus S2 | Temuan tambahan | Sedang | baca extracted/C1.json msg63 |
| TR-24 | C1 | 65 | 71 | confirmed | Lanjut ke Connected Papers | Citation graph | Seed paper | Grafik visual | Sedang | baca extracted/C1.json msg65 |
| TR-25 | C1 | 69 | 75 | confirmed | Asisten jalankan Rabbit + Connected | Simulasi peta sitasi | 5 seed paper | Simulasi + rekomendasi | Sedang | baca extracted/C1.json msg69 |
| TR-26 | C1 | 71 | 77 | confirmed | Lanjut ke Scite | Smart Citations | Korpus sitasi | Dukungan vs bantahan | Sedang | baca extracted/C1.json msg71 |
| TR-27 | C1 | 73 | 79 | confirmed | Lanjut ke SciSpace | All-in-one writing | Template Elsevier | Proyek + sitasi | Tinggi | baca extracted/C1.json msg73 |
| TR-28 | C1 | 75 | 81 | confirmed | Kumpulan prompt SciSpace | Template-driven writing | Bahan + DOI | Prompt siap-copy | Tinggi | baca extracted/C1.json msg75 |
| TR-29 | C1 | 77 | 83 | confirmed | Prompt OpenCode untuk SciSpace | Delegasi eksekusi | Draf + bahan | Prompt tim | Tinggi | baca extracted/C1.json msg77 |
| TR-30 | C1 | 79 | 85 | confirmed | Draf md + .bib 40 (7 inti Crossref) | Penulisan + verifikasi DOI | 40 referensi | 2 file siap SciSpace | Tinggi | baca extracted/C1.json msg79; cek Crossref 2 DOI |
| TR-31 | C1 | 83 | 89 | confirmed | Rencana 7 -> 10 untuk Gemini Deep Research | Deep Research planning | TIDAK_TERSEDIA | 10 rencana rinci | Tinggi | baca extracted/C1.json msg83 |
| TR-32 | C1 | 93 | 99 | confirmed | Tulis versi final 10 rencana | Sintesis 10 dimensi | Bahan multi-AI | Dokumen final | Tinggi | baca extracted/C1.json msg93 |
| TR-33 | C1 | 101 | 107 | confirmed | Unduh 67 referensi via OpenCode | Download pipeline | Daftar pustaka | File di elsevier/ | Tinggi | baca extracted/C1.json msg101 |
| TR-34 | C1 | 103 | 109 | confirmed | Ambil seluruh 168 referensi | Download pipeline | 168 URL | Folder referensi/ | Tinggi | baca extracted/C1.json msg103 |
| TR-35 | C1 | 105 | 111 | confirmed | Error path spasi PowerShell | Diagnosis shell | Log PS pengguna | Solusi quoting | Sedang | baca extracted/C1.json msg105; replika perintah cd |
| TR-36 | C1 | 110 | 116 | confirmed | Hasil: 94 ok, 31 gagal | Audit hasil unduh | Folder referensi/ + gagal.txt | 94/31/skip | Tinggi | audit folder referensi/ + gagal.txt |
| TR-37 | C1 | 111 | 117 | confirmed | Retry 31 gagal hingga 0 | Retry Session+Referer+timeout90 | 31 URL gagal | 0 gagal | Tinggi | baca extracted/C1.json msg111; uji unduh ulang |
| TR-38 | C1 | 114 | 120 | conflicting | Hasil retry 1 ok, 30 gagal (403) | Retry 5x | 31 URL | 1/30; total ~91 | Tinggi | audit folder + bandingkan klaim msg110 vs msg114 |
| TR-39 | C1 | 121 | 127 | confirmed | Klarifikasi format HTML hasil unduh | Klasifikasi HTML-vs-PDF | File .html terunduh | Kategori prioritas | Sedang | baca extracted/C1.json msg121; inspeksi isi HTML |
| TR-40 | C1 | 131 | 139 | confirmed | Prompt Claude penyusun makalah | Prompt engineering | 168 ref + bahan | Prompt lengkap | Tinggi | baca extracted/C1.json msg131 |
| TR-41 | C1 | 139 | 147 | confirmed | Revisi Claude: 72/72 cocok, abstrak 230 | Verifikasi terprogram sitasi-bib | tex+bib+pdf 3 versi | 72 cocok; 0 placeholder | Tinggi | cross-check \cite vs .bib; hitung kata abstrak |
| TR-42 | C1 | 163 | 171 | confirmed | Metadata 3 penulis (tanpa Nazhif) | Ekstraksi PKN 1.docx | PKN 1.docx | 3 nama + NIM | Tinggi | verifikasi manusia (file PKN 1.docx) |
| TR-43 | C1 | 166 | 174 | confirmed | NIM ditulis di metadata | LaTeX frontmatter | NIM 3 penulis | Kode metadata | Tinggi | baca extracted/C1.json msg166; kompilasi |
| TR-44 | C1 | 170 | 178 | confirmed | Tabel jadi 1 sisi via table* | table* full-width | Tabel 1-2 | Tak tindih | Tinggi | kompilasi ulang; cek visual tabel |
| TR-45 | C1 | 176 | 184 | confirmed | IEEE = layout terbaik | Evaluasi template | Makalah 20 hlm | Keputusan tercatat | Tinggi | baca extracted/C1.json msg176 (kepala) |
| TR-46 | C1 | 183 | 193 | confirmed | Prompt OpenCode konversi ke IEEE | Migrasi elsarticle->IEEEtran | fix.tex + fix.bib | Prompt tim | Tinggi | baca extracted/C1.json msg183 |
| TR-47 | C1 | 187 | 199 | confirmed | Konversi bersih 12 hlm, 0 overfull | IEEEtran journal 2-kolom | fix.tex + fix.bib | 12 hlm; 0/0/0 | Tinggi | kompilasi ulang pdflatex+bibtex; cek log |
| TR-48 | C1 | 191 | 203 | confirmed | Perbaikan penulis/logo/dosen/judul | Iterasi halaman judul | PDF ieee | Daftar 4 isu | Tinggi | baca extracted/C1.json msg191; cek visual |
| TR-49 | C1 | 203 | 215 | confirmed | Panggilan+NIM; afiliasi 1x; footer tak nabrak | Restruktur author block | ieee_final.tex | Kode final | Tinggi | kompilasi ulang; cek visual judul |
| TR-50 | C1 | 211 | 223 | confirmed | Baseline aman; terapkan perubahan | Salin dari file berhasil | ieee.tex berhasil | Keputusan tercatat | Tinggi | baca extracted/C1.json msg211 |
| TR-51 | C2 | 5 | 9 | confirmed | Tempel tex final + pindah NIM->nama | Iterasi judul IEEE | ieee_final.tex pengguna | File acuan | Tinggi | baca extracted/C2.json msg5 (parsial, 70KB) |
| TR-52 | C2 | 7 | 11 | confirmed | Footer tugas tengah, anti-nabrak | Penjarakan IEEEtran | ieee_final.tex | Tak nabrak | Tinggi | kompilasi ulang; cek visual footer |
| TR-53 | C2 | 9 | 13 | confirmed | Nama vertikal bukan horizontal | Stacked author block | ieee_final.tex | Satu/baris | Tinggi | baca extracted/C2.json msg9; cek visual |
| TR-54 | C3 | 1 | 1 | confirmed | Isi docx -> pasted tanpa ubah format | Substitusi teks non-destruktif | docx + pasted .tex | Diff hanya isi | Sedang | diff tex sebelum vs sesudah |
| TR-55 | C3 | 2 | 2 | confirmed | File .tex IEEE lengkap diserahkan | Aplikasi konten ke template | docx | documentclass-end lengkap | Sedang | baca extracted/C3.json msg2 (kepala); kompilasi |
| TR-56 | C4 | 1 | 1 | confirmed | Typesetting 100% IEEE (bold/italic/sitasi) | Aturan IEEE style | Humanized.docx | Instruksi 4 poin | Sedang | baca extracted/C4.json msg1 |
| TR-57 | C4 | 2 | 2 | confirmed | Laporan layout + versi terkoreksi | Audit format IEEE | ieee.tex | Bold em-dash dkk | Sedang | baca extracted/C4.json msg2 (kepala); cek visual |
| TR-58 | C5 | 1 | 1 | confirmed | Cover blank + abstrak Ringkasan | Diagnosis margin+babel | cover_page.png + tex | 2 akar masalah | Tinggi | baca extracted/C5.json msg1; replika compile |
| TR-59 | C5 | 3 | 3 | confirmed | Dimensi cover 482x680 px 96dpi | Analisis resolusi | cover_page.png | 12,75x18 cm | Sedang | baca extracted/C5.json msg3; cek properti file |
| TR-60 | C5 | 7 | 7 | confirmed | Bold/miring hilang; aturan italic | Kaidah EYD + LaTeX | tex final + txt | 4 seksi aturan | Sedang | baca extracted/C5.json msg7; cek visual PDF |
| TR-61 | C5 | 9 | 9 | confirmed | Prompt typesetter IEEE (ulang) | Aturan IEEE style | Humanized.docx | Instruksi 4 poin | Sedang | baca extracted/C5.json msg9 |
| TR-62 | C6 | 1 | 1 | confirmed | Workflow compile pdflatex+bibtex | Pipeline 4-pass | ieee.tex | Best practice | Tinggi | jalankan 4 perintah; cek artefak |
| TR-63 | C6 | 21 | 21 | confirmed | Cover ala jurnal peringkat atas | Referensi cover top-tier | Link jurnal | Referensi + opsi | Sedang | baca extracted/C6.json msg21 |
| TR-64 | C6 | 29 | 29 | confirmed | Contoh cover Springer via link | Koleksi referensi visual | Jurnal Springer | Link contoh | Sedang | baca extracted/C6.json msg29; buka link |
| TR-65 | C6 | 43 | 43 | confirmed | Prompt Claude untuk judul baru | Prompt engineering | Makalah + layout | Prompt judul | Sedang | baca extracted/C6.json msg43 |
| TR-66 | C6 | 71 | 73 | confirmed | Instalasi tlmgr gagal (sudo Windows) | Diagnosis OS | Log PS + tlmgr | Solusi Windows | Sedang | baca extracted/C6.json msg71; cek tlmgr Windows |
| TR-67 | C6 | 85 | 87 | confirmed | Prompt image ChatGPT sesuai layout | Image-gen prompting | Layout + ref image 1 | Prompt + warna | Sedang | baca extracted/C6.json msg85 |
| TR-68 | C6 | 109 | 111 | conflicting | Acuan bib = final (klaim memori) | Klaim memori pengguna | final.bib | KONFLIK vs TR-47 | Tinggi | bandingkan isi fix.bib vs final.bib; cross-check cite |
| TR-69 | C6 | 137 | 139 | confirmed | Drop cap pembuka ala IEEE | \IEEEPARstart | Bagian pendahuluan | Huruf besar | Rendah | baca extracted/C6.json msg137; cek visual |

## Catatan v2

- Total: **69 TR** (≥40 terpenuhi). Perincian status: confirmed=67, inferred=0, conflicting=2.
- TR-38 (`conflicting`): angka "94 berhasil" (C1-msg110) vs "91 file + 1 retry" (C1-msg114) — lihat PD-05.
- TR-68 (`conflicting`): acuan `.bib` `final` (C6-msg109) vs `fix` (C1-msg187/TR-47) — lihat PD-06.
- Ekspor CSV: `TRACEABILITY.csv` (kolom sama + `role`).
