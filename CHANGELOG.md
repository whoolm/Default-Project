# CHANGELOG

> Semua perubahan file dicatat di sini (tanggal UTC, file, alasan). Bahasa Indonesia.

## 2026-09-13 — Baseline v1.0-prd

- `raw/C1–C6.json`: fetch awal via `api/v0/share/content` (fetch HTML terhalang WAF). Alasan: data mentah.
- `raw/C1–C6.html`: stub penjelasan WAF. Alasan: folder `raw/` lengkap per spek.
- `raw/errors.log`: catatan WAF + status 6/6 sukses. Alasan: audit fetch.
- `extracted/C1–C6.json`: ekstraksi role/content/timestamp + metadata. Alasan: basis semua dokumen.
- `memory/chat_memory.json` + `memory/chat_memory.md`: memori terstruktur 6 chat. Alasan: konsolidasi.
- `PRD.md`, `ALGORITMA_RESEARCH.md`, `TRACEABILITY.md` (TR-01–TR-20): dokumen awal. Alasan: deliverable utama.

## 2026-09-13 — Hardening (FASE 1: audit)

- `AUDIT_REPORT.md` (baru): hasil validasi raw JSON, diff memory→PRD (M-01–M-08), integritas traceability, review errors.log. Alasan: FASE 1.
- `PENDING_DECISIONS.md` (baru): PD-01–PD-13 (verifikasi manusia, konflik, asumsi). Alasan: FASE 1.5.
- `CHANGELOG.md` (baru, file ini): pencatatan perubahan. Alasan: aturan global #2.

## 2026-09-13 — Hardening (FASE 2: reframe)

- `ALGORITMA_RESEARCH.md` → `METODOLOGI_RESEARCH.md` (rename; 138 baris < 200 → **tanpa split** sesuai aturan). Alasan: nama lama menyesatkan (tak ada algoritma ML di chat).
- `METODOLOGI_RESEARCH.md`: tambah header disclaimer + ganti judul. Alasan: kejujuran metodologi.
- `PRD.md`: referensi silang `ALGORITMA_RESEARCH.md` → `METODOLOGI_RESEARCH.md`. Alasan: cegah link mati.
- `MANIFEST.md` (baru): daftar file + status. Alasan: FASE 2.

## 2026-09-13 — Hardening (FASE 3: PRD)

- `PRD.md`: tambah kolom Target `[PERLU TARGET ANGKA]` di NFR-01–07; tambah §15 Glossary, §16 Dependency Matrix, §17 User Stories (US-01–09), §18 Open Questions (OQ-01–10), §19 Out of Scope usulan (OS-01–06). Tanpa FR baru, tanpa angka NFR. Alasan: FASE 3.

## 2026-09-13 — Hardening (FASE 4: traceability v2)

- `TRACEABILITY.md`: tulis ulang v1 (20 TR tanpa jangkar) → v2 (69 TR atomik + chat_id/message_index/raw_message_id/status/test_method; 54 confirmed, 13 inferred, 2 conflicting). Alasan: FASE 4 + temuan audit §3.
- `TRACEABILITY.csv` (baru): ekspor 69 baris, 12 kolom. Alasan: FASE 4.
- Skrip generator satu-pakai: `%TEMP%\opencode\gen_tr.py` (69 jangkar terverifikasi isi+role vs raw). Alasan: reproduksibilitas audit.

## 2026-09-13 — Hardening (FASE 5: rekonsiliasi)

- `PENDING_DECISIONS.md`: tambah §D Tabel Rekonsiliasi K-01–K-13 (9 OPEN + 4 RIWAYAT; konflik|opsi|argumen|dampak; tanpa keputusan). Alasan: FASE 5.

## 2026-09-13 — Siap eksekusi (FASE 6)

- `README.md`, `CONTRIBUTING.md`, `ROADMAP.md`, `.gitignore` (baru). Alasan: FASE 6.
- Git: `init` + commit `v1.0-prd baseline` + tag `v1.0-prd` (hanya file deliverable PRD, lihat daftar di pesan commit). Alasan: FASE 6.
