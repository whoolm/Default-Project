# PENDING DECISIONS — Butuh Judgment Manusia

> Semua item diputuskan 13 Sep 2026. Lihat DECISIONS.md untuk detail.
> Aturan: OpenCode TIDAK memutuskan. Manusia memilih; OpenCode mengeksekusi hasilnya dan mencatat di `CHANGELOG.md`.
> Status awal: semua `OPEN`. Format status: `OPEN | DECIDED: <keputusan + tanggal>`.

## A. Verifikasi Manusia (TIDAK_TERSEDIA yang mungkin sebenarnya ada)

| ID | Item | Kenapa butuh manusia | Opsi | Status |
|----|------|----------------------|------|--------|
| PD-01 | Isi 92 lampiran (DOCX/PDF/TXT/CSV/TEX) — baru nama file yang tercatat | Isi file tidak ada di API share; hanya pemilik chat yang punya file asli | Abaikan / unggah manual / anggap di luar skope | DECIDED 13 Sep 2026: ABAIKAN (di luar skope) |
| PD-02 | 188 thinking blocks (±733K char) — belum dibaca | Mungkin berisi keputusan/argumen yang tak muncul di jawaban final | Abaikan / ringkas bertahap / prioritaskan pesan cabang kosong | DECIDED 13 Sep 2026: ABAIKAN (proses internal) |
| PD-03 | 29 pesan assistant-kosong + 12+4+2 cabang pruned | Respons final cabang tersebut hilang dari share | Abaikan (anggap duplikat) / minta pemilik ekspor ulang | DECIDED 13 Sep 2026: ABAIKAN (duplikat) |
| PD-04 | Isi gambar paste (21× `image.png` + screenshot lain) | Roadmap RISE 1–6 & screenshot error hanya ada sebagai gambar | Minta file gambar asli untuk dibaca manual | DECIDED 13 Sep 2026: MINTA FILE (opsional, tidak kritis) |
| PD-05 | Angka unduhan: "94 berhasil" vs "91 file" vs "+1 retry" (C1-msg110–114) | Inkonsistensi internal chat; angka definitif tak bisa ditentukan otomatis | Tetapkan angka resmi / catat rentang | DECIDED 13 Sep 2026: CATAT RENTANG 91–94 (metrik pakai 91) |

## B. Konflik Antar-Chat (diperdalam di FASE 5 — JANGAN putuskan di sini)

| ID | Konflik | Opsi | Dampak jika salah pilih | Status |
|----|---------|------|-------------------------|--------|
| PD-06 | Acuan `.bib`: `pancasila_referensi_fix.bib` (C1) vs `pancasila_referensi_final.bib` (C6-msg109) | fix / final / gabung manual | Sitasi `[?]` + pustaka kosong terulang | DECIDED 13 Sep 2026: fix.bib |
| PD-07 | Format nama penulis: lengkap+NIM (awal) vs panggilan+NIM horizontal vs vertikal (akhir) | lengkap / panggilan-horizontal / panggilan-vertikal | Halaman judul ditolak pembimbing/jurnal | DECIDED 13 Sep 2026: panggilan+NIM vertikal |
| PD-08 | Cover: kode programatik (TikZ) vs image | image (keputusan pengguna tercatat) / TikZ ulang | Cover blank vs upkeep berat — pengguna sudah menolak TikZ, butuh konfirmasi final | DECIDED 13 Sep 2026: image |
| PD-09 | Abstrak: gaya IEEE (`Ringkasan—`) vs ala Elsevier (`Abstract` bold) | Elsevier (keputusan tercatat) / bawaan IEEE | Inkonsistensi dengan template jurnal target | DECIDED 13 Sep 2026: gaya Elsevier |

## C. Asumsi OpenCode (mohon validasi)

| ID | Asumsi | Jika salah | Status |
|----|--------|------------|--------|
| PD-10 | M-01–M-08 (temuan audit) TIDAK dijadikan FR baru sepihak — hanya User Stories/Open Questions | Jika seharusnya FR, manusia perlu menambahkannya eksplisit | DECIDED 13 Sep 2026: VALIDASI BENAR |
| PD-11 | Urutan `message_id` = urutan kronologis dialog (basis jangkar traceability v2) | Jangkar `message_index` bisa meleset pada cabang pruned | DECIDED 13 Sep 2026: VALIDASI BENAR |
| PD-12 | Jangkar berstatus `inferred` (pencocokan kata kunci) dianggap cukup untuk v2; `confirmed` hanya untuk yang dibaca manual | Standar bukti traceability bisa kurang kuat untuk audit formal | DECIDED 13 Sep 2026: TERIMA untuk v2 (13 inferred; upgrade nanti) |
| PD-13 | Target NFR ([PERLU TARGET ANGKA]) diisi manusia nanti; PRD tetap rilis tanpa angka | Persetujuan PRD tanpa NFR terukur | DECIDED 13 Sep 2026: ISI 6 NFR terukur (lihat DECISIONS.md) |

## D. Tabel Rekonsiliasi (FASE 5 — dikumpulkan, TIDAK diputuskan)

> Kolom: konflik | opsi | argumen (dari chat, dua sisi) | dampak. Status `OPEN` = tunggu manusia; `RIWAYAT` = sudah diputuskan di chat (dicatat agar tak dibuka ulang tanpa alasan).

| # | Konflik | Opsi | Argumen | Dampak | Status |
|---|---------|------|---------|--------|--------|
| K-01 | Acuan `.bib` (PD-06; TR-47 vs TR-68) | Opsi A `fix` / Opsi B `final` | A: 72/72 sitasi cocok, `final` kehilangan `gumilanghudaefi` + punya `bengbeng` yatim (C1-msg187). B: memori pengguna menyebut `final` (C6-msg109) | Salah pilih → sitasi `[?]`, pustaka kosong | DECIDED 13 Sep 2026: `pancasila_referensi_fix.bib` |
| K-02 | Format nama penulis (PD-07) | lengkap+NIM / panggilan+NIM horizontal / panggilan+NIM vertikal | Lengkap = resmi; panggilan = permintaan eksplisit (C1-msg203); vertikal = anti-nabrak (C2-msg9) | Penolakan pembimbing/jurnal | DECIDED 13 Sep 2026: panggilan + NIM vertikal |
| K-03 | Penempatan NIM | `\thanks` footnote / samping nama / bawah abstrak | Footnote = standar IEEE tapi "terlalu bawah" (C6-msg12); samping nama = permintaan (C1-msg203); bawah abstrak = duplikasi (C1-msg206) | Duplikasi/nabrak | DECIDED 13 Sep 2026: samping nama (author block) |
| K-04 | Penempatan dosen pembimbing | Halaman judul / Ucapan Terima Kasih | Judul = permintaan akhir (C1-msg203); Terima Kasih = usulan saat krisis (C1-msg210) | Inkonsistensi versi | DECIDED 13 Sep 2026: halaman judul (author block) |
| K-05 | Cover: kode vs image (PD-08) | TikZ programatik / image | Kode = fleksibel tapi rapuh + pengguna menolak ("gamau tikzzzz", C6-msg125); image = stabil tapi butuh generate + upscale | Cover blank vs upkeep berat | DECIDED 13 Sep 2026: image full-page |
| K-06 | Gaya abstrak (PD-09) | Bawaan IEEE / ala Elsevier | Elsevier = permintaan ("jelek banget posisinya", C1-msg193); bawaan = kompatibilitas template | Inkonsistensi jurnal target | DECIDED 13 Sep 2026: ala Elsevier (`Abstract` bold + em-dash) |
| K-07 | Engine kompilasi | pdflatex / xelatex / lualatex | pdflatex = simpel tanpa TikZ (C5); xelatex/lualatex = font/cover programatik (C6-msg133–135) | Error font/nullfont vs fitur kurang | DECIDED 13 Sep 2026: `pdflatex` |
| K-08 | Angka unduhan definitif (PD-05) | 94 / 91+1 / rentang | "94 berhasil" (C1-msg110) vs "91 file + 1 retry" (C1-msg114) | Metrik FR-05 tak bisa ditutup | DECIDED 13 Sep 2026: rentang 91–94 (metrik pakai 91) |
| K-09 | Judul final makalah | 10 opsi Claude (file `# 10 Pilihan Judul...txt`) | Makna sama, redaksi beda (C1-msg191, C6-msg43) | Identitas naskah | DECIDED 13 Sep 2026: judul existing di `makalah_pancasila_ieee.tex` |
| K-10 (RIWAYAT) | 67 vs 168 referensi | 168 (diputuskan C1-msg103) | — | Arsip; jangan dibuka ulang | RIWAYAT — JANGAN DIUBAH |
| K-11 (RIWAYAT) | Cover dihitung halaman? | Tidak; hal.1 = judul/abstrak (diputuskan C6-msg33) | — | Arsip | RIWAYAT — JANGAN DIUBAH |
| K-12 (RIWAYAT) | "Ringkasan" vs "Abstract" | "Abstract" (diputuskan C5) | — | Arsip | RIWAYAT — JANGAN DIUBAH |
| K-13 (RIWAYAT) | Tabel sempit vs `table*` | `table*` (diputuskan C1-msg170) | — | Arsip | RIWAYAT — JANGAN DIUBAH |
