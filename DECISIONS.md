# DECISIONS — Log Keputusan Proyek

> Setiap keputusan punya: ID, keputusan, alasan, tanggal, sumber (chat/konteks).
> Diputuskan manusia 13 Sep 2026. Sumber awal: `PENDING_DECISIONS.md` (26 item: K-01 s/d K-13 + PD-01 s/d PD-13).

## Keputusan Final

### K-01 — Acuan .bib
- **Status:** DECIDED
- **Keputusan:** Pakai `pancasila_referensi_fix.bib`
- **Alasan:** 72/72 sitasi cocok; `final` kehilangan `gumilanghudaefi` + ada `bengbeng` yatim
- **Tanggal:** 13 Sep 2026
- **Sumber:** C1-msg187 (perbandingan fix vs final); konsisten dengan PD-06

### K-02 — Format nama penulis
- **Status:** DECIDED
- **Keputusan:** Nama panggilan + NIM vertikal (satu penulis per baris)
- **Alasan:** Permintaan eksplisit pengguna (C1-msg203) + anti-nabrak/tabrakan (C2-msg9); konsisten dengan PD-07
- **Tanggal:** 13 Sep 2026
- **Sumber:** C1-msg203, C2-msg9

### K-03 — Penempatan NIM
- **Status:** DECIDED
- **Keputusan:** Samping nama (di author block)
- **Alasan:** Permintaan pengguna (C1-msg203); footnote `\thanks` dinilai "terlalu bawah" (C6-msg12); bawah abstrak = duplikasi (C1-msg206)
- **Tanggal:** 13 Sep 2026
- **Sumber:** C1-msg203, C1-msg206, C6-msg12

### K-04 — Penempatan dosen pembimbing
- **Status:** DECIDED
- **Keputusan:** Halaman judul (author block)
- **Alasan:** Permintaan akhir pengguna (C1-msg203); opsi Ucapan Terima Kasih hanya usulan saat krisis (C1-msg210)
- **Tanggal:** 13 Sep 2026
- **Sumber:** C1-msg203, C1-msg210

### K-05 — Cover: kode vs image
- **Status:** DECIDED
- **Keputusan:** Image full-page
- **Alasan:** Pengguna menolak TikZ ("gamau tikzzzz", C6-msg125); image stabil; konsisten dengan PD-08
- **Tanggal:** 13 Sep 2026
- **Sumber:** C5-msg1, C6-msg125

### K-06 — Gaya abstrak
- **Status:** DECIDED
- **Keputusan:** Ala Elsevier (`Abstract` bold + em-dash)
- **Alasan:** Permintaan pengguna ("jelek banget posisinya", C1-msg193); konsisten dengan PD-09
- **Tanggal:** 13 Sep 2026
- **Sumber:** C1-msg193

### K-07 — Engine kompilasi
- **Status:** DECIDED
- **Keputusan:** `pdflatex`
- **Alasan:** Simpel tanpa TikZ/fontspec (jalur C5 final); xelatex/lualatex hanya relevan untuk cover programatik yang sudah ditolak
- **Tanggal:** 13 Sep 2026
- **Sumber:** C5, C6-msg133–135

### K-08 — Angka unduhan definitif
- **Status:** DECIDED
- **Keputusan:** Catat rentang 91–94; untuk metrik pakai 91
- **Alasan:** Inkonsistensi internal chat ("94 berhasil" C1-msg110 vs "91 file + 1 retry" C1-msg114); angka konservatif 91 untuk FR-05; konsisten dengan PD-05
- **Tanggal:** 13 Sep 2026
- **Sumber:** C1-msg110–114

### K-09 — Judul final makalah
- **Status:** DECIDED
- **Keputusan:** Judul existing di `makalah_pancasila_ieee.tex`: "Pancasila sebagai Sistem Filsafat: Tinjauan Ontologi, Epistemologi, dan Aksiologi serta Relevansinya di Era Disrupsi Digital"
- **Alasan:** 10 opsi Claude bermakna sama (C1-msg191, C6-msg43); pertahankan judul yang sudah terpakai di naskah final
- **Tanggal:** 13 Sep 2026
- **Sumber:** C1-msg191, C6-msg43, `makalah_pancasila_ieee.tex` (blok `\title`)

### K-10 — 67 vs 168 referensi (RIWAYAT)
- **Status:** RIWAYAT — JANGAN DIUBAH
- **Keputusan:** 168 (diputuskan C1-msg103)
- **Alasan:** Arsip; sudah diputuskan di chat
- **Tanggal:** diputuskan di chat (dicatat 13 Sep 2026)
- **Sumber:** C1-msg103

### K-11 — Cover dihitung halaman? (RIWAYAT)
- **Status:** RIWAYAT — JANGAN DIUBAH
- **Keputusan:** Tidak; hal.1 = judul/abstrak (diputuskan C6-msg33)
- **Alasan:** Arsip; sudah diputuskan di chat
- **Tanggal:** diputuskan di chat (dicatat 13 Sep 2026)
- **Sumber:** C6-msg33

### K-12 — "Ringkasan" vs "Abstract" (RIWAYAT)
- **Status:** RIWAYAT — JANGAN DIUBAH
- **Keputusan:** "Abstract" (diputuskan C5)
- **Alasan:** Arsip; sudah diputuskan di chat
- **Tanggal:** diputuskan di chat (dicatat 13 Sep 2026)
- **Sumber:** C5

### K-13 — Tabel sempit vs `table*` (RIWAYAT)
- **Status:** RIWAYAT — JANGAN DIUBAH
- **Keputusan:** `table*` (diputuskan C1-msg170)
- **Alasan:** Arsip; sudah diputuskan di chat
- **Tanggal:** diputuskan di chat (dicatat 13 Sep 2026)
- **Sumber:** C1-msg170

### PD-01 — Isi 92 lampiran
- **Status:** DECIDED (ABAIKAN — di luar skope)
- **Keputusan:** Abaikan
- **Alasan:** Isi file tidak ada di API share; hanya pemilik chat yang punya file asli; di luar skope (lihat OS-03 di PRD)
- **Tanggal:** 13 Sep 2026
- **Sumber:** Keputusan manusia 13 Sep 2026

### PD-02 — 188 thinking blocks
- **Status:** DECIDED (ABAIKAN — proses internal)
- **Keputusan:** Abaikan
- **Alasan:** Thinking block = proses internal, bukan keputusan final
- **Tanggal:** 13 Sep 2026
- **Sumber:** Keputusan manusia 13 Sep 2026

### PD-03 — Pesan kosong + cabang pruned
- **Status:** DECIDED (ABAIKAN — duplikat)
- **Keputusan:** Abaikan (anggap duplikat)
- **Alasan:** Respons final cabang pruned hilang dari share; diasumsikan duplikat
- **Tanggal:** 13 Sep 2026
- **Sumber:** Keputusan manusia 13 Sep 2026

### PD-04 — Isi gambar paste (21× image.png + screenshot)
- **Status:** DECIDED (MINTA FILE — opsional, tidak kritis)
- **Keputusan:** Minta file gambar asli; opsional, tidak kritis (RISE 1–6 tetap ditunda)
- **Alasan:** Roadmap RISE 1–6 & screenshot error hanya ada sebagai gambar; tidak kritis untuk fase paper/template/docs
- **Tanggal:** 13 Sep 2026
- **Sumber:** Keputusan manusia 13 Sep 2026

### PD-05 — Angka unduhan "94 berhasil" vs "91+1 retry"
- **Status:** DECIDED (CATAT RENTANG 91–94; metrik pakai 91)
- **Keputusan:** Catat rentang 91–94; untuk metrik pakai 91
- **Alasan:** Inkonsistensi internal C1-msg110–114; angka konservatif untuk FR-05; konsisten dengan K-08
- **Tanggal:** 13 Sep 2026
- **Sumber:** C1-msg110–114; keputusan manusia 13 Sep 2026

### PD-06 — Acuan `.bib` fix vs final
- **Status:** DECIDED (fix.bib)
- **Keputusan:** Pakai `pancasila_referensi_fix.bib`
- **Alasan:** Konsisten dengan K-01 (72/72 cocok; `final` cacat)
- **Tanggal:** 13 Sep 2026
- **Sumber:** C1-msg187; keputusan manusia 13 Sep 2026

### PD-07 — Format nama penulis
- **Status:** DECIDED (panggilan+NIM vertikal)
- **Keputusan:** Nama panggilan + NIM vertikal
- **Alasan:** Konsisten dengan K-02 (C1-msg203, C2-msg9)
- **Tanggal:** 13 Sep 2026
- **Sumber:** C1-msg203, C2-msg9; keputusan manusia 13 Sep 2026

### PD-08 — Cover kode vs image
- **Status:** DECIDED (image)
- **Keputusan:** Image full-page
- **Alasan:** Konsisten dengan K-05; pengguna menolak TikZ (C6-msg125)
- **Tanggal:** 13 Sep 2026
- **Sumber:** C5-msg1, C6-msg125; keputusan manusia 13 Sep 2026

### PD-09 — Gaya abstrak IEEE vs Elsevier
- **Status:** DECIDED (gaya Elsevier)
- **Keputusan:** Ala Elsevier (`Abstract` bold + em-dash)
- **Alasan:** Konsisten dengan K-06 (C1-msg193)
- **Tanggal:** 13 Sep 2026
- **Sumber:** C1-msg193; keputusan manusia 13 Sep 2026

### PD-10 — M-01–M-08 bukan FR baru
- **Status:** DECIDED (VALIDASI BENAR)
- **Keputusan:** Validasi benar — M-01–M-08 TIDAK dijadikan FR baru; hanya User Stories/Open Questions
- **Alasan:** Manusia mengonfirmasi asumsi OpenCode
- **Tanggal:** 13 Sep 2026
- **Sumber:** Keputusan manusia 13 Sep 2026

### PD-11 — message_id = kronologi
- **Status:** DECIDED (VALIDASI BENAR)
- **Keputusan:** Validasi benar — urutan `message_id` = urutan kronologis dialog (basis jangkar traceability v2)
- **Alasan:** Manusia mengonfirmasi asumsi OpenCode
- **Tanggal:** 13 Sep 2026
- **Sumber:** Keputusan manusia 13 Sep 2026

### PD-12 — inferred cukup untuk v2
- **Status:** DECIDED (TERIMA untuk v2)
- **Keputusan:** Terima untuk v2 — 13 inferred dianggap cukup; upgrade ke confirmed nanti bila audit formal
- **Alasan:** Manusia menerima standar bukti v2 saat ini
- **Tanggal:** 13 Sep 2026
- **Sumber:** Keputusan manusia 13 Sep 2026

### PD-13 — Target NFR
- **Status:** DECIDED (ISI 6 NFR terukur)
- **Keputusan:** Isi 6 target terukur (lihat tabel NFR Target Angka di bawah); terapkan ke `PRD.md` §6
- **Alasan:** Manusia mengisi angka yang selama ini `[PERLU TARGET ANGKA]`
- **Tanggal:** 13 Sep 2026
- **Sumber:** Keputusan manusia 13 Sep 2026

## NFR Target Angka (PD-13)

| NFR | Target |
|---|---|
| Compile time | ≤ 30 detik |
| PDF size | ≤ 3 MB |
| Visual quality | Vektor, cover ≥ 150 dpi |
| Compile errors | 0 |
| Waktu template→draft | ≤ 2 jam |
| Cross-check sitasi | 100% |
