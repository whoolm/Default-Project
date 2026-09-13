# CONTRIBUTING — Cara Update PRD & Traceability

## Prinsip (tak bisa ditawar)

1. Jangan mengarang. Tanpa bukti di `extracted/C*.json` → tulis `TIDAK_TERSEDIA`.
2. Jangan memutuskan konflik (lihat `PENDING_DECISIONS.md`) — catat dua versi.
3. Setiap perubahan file → catat di `CHANGELOG.md` (tanggal, file, alasan).

## Menambah/mengubah requirement

1. Cari bukti pesan di `extracted/C*.json`; catat `chat_id` + `message_index` (1-based) + `raw_message_id`.
2. Tambah baris di `PRD.md` §5 (ID FR-xx berikutnya) + User Story di §17 + dependensi di §16.
3. Tambah TR baru di `TRACEABILITY.md` **dan** `TRACEABILITY.csv` (12 kolom sama; status: confirmed/inferred/conflicting).
4. Update `ROADMAP.md` bila prioritas berubah; update `CHANGELOG.md`.

## Mengubah status PENDING_DECISIONS

- Hanya manusia. Ubah `OPEN` → `DECIDED: <keputusan + tanggal>`, lalu eksekusi dampaknya (PRD/TR/code) + catat di `CHANGELOG.md`.

## Menambah chat sumber baru (C7+)

1. Simpan respons API ke `raw/C7.json` (+ stub `raw/C7.html` bila perlu).
2. Ekstrak ke `extracted/C7.json` (skema sama: id/url/title/messages/metadata).
3. Tambah entri `memory/chat_memory.json` + baris `memory/chat_memory.md`.
4. Tambah TR + update PRD/AUDIT sesuai dampak; catat semua di `CHANGELOG.md`.

## Git

- Commit kecil per dokumen; tag `vX.Y-<nama>` tiap baseline disetujui manusia.
- Jangan commit `raw/*.html` (stub lokal) dan `.env` (lihat `.gitignore`).
