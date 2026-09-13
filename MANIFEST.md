# MANIFEST — Daftar File Repo

> Status: baseline hardening 2026-09-13. Lihat `CHANGELOG.md` untuk riwayat.

| File | Deskripsi 1 baris | Status |
|------|-------------------|--------|
| `README.md` | Cara navigasi repo (mulai di sini) | ✅ |
| `ROADMAP.md` | Timeline berdasarkan prioritas FR | ✅ |
| `CONTRIBUTING.md` | Cara update PRD/traceability | ✅ |
| `PRD.md` | PRD Makalah Ceritas + makalah Pancasila (§1–§19; NFR tanpa angka) | ✅ baseline |
| `METODOLOGI_RESEARCH.md` | Basis metodologi riset (reframe dari ALGORITMA_RESEARCH.md; 138 baris → tanpa split) | ✅ |
| `TRACEABILITY.md` | Matriks v2: ≥40 TR atomik + chat_id/message_index/status/test_method | ✅ |
| `TRACEABILITY.csv` | Ekspor CSV dari TRACEABILITY.md v2 | ✅ |
| `AUDIT_REPORT.md` | Hasil audit FASE 1 (raw health, gap PRD, integritas traceability) | ✅ |
| `PENDING_DECISIONS.md` | PD-01–PD-13 + tabel rekonsiliasi (butuh manusia, JANGAN diputuskan sepihak) | ⏳ OPEN |
| `CHANGELOG.md` | Catatan semua perubahan file | ✅ berjalan |
| `MANIFEST.md` | File ini | ✅ |
| `.gitignore` | Exclude stub `raw/*.html`, `.env` | ✅ |
| `memory/chat_memory.json` | Memori terstruktur 6 chat (JSON) | ✅ |
| `memory/chat_memory.md` | Memori terstruktur 6 chat (tabel Markdown) | ✅ |
| `extracted/C1–C6.json` | Transkrip terstruktur per chat (skema id/url/title/messages/metadata) | ✅ |
| `raw/C1–C6.json` | Respons API mentah per share URL | ✅ |
| `raw/C1–C6.html` | Stub (fetch HTML terhalang WAF; data via JSON) — di-exclude dari git | ⚠️ lokal saja |
| `raw/errors.log` | Log fetch (6/6 sukses, NOTE WAF) | ✅ |
