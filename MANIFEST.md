# MANIFEST — Daftar File Repo

> Status: refresh 2026-09-13 (pasca-decisions + audit Fase A–C + template Elsevier; tag `milestone-v1.0`). Lihat `CHANGELOG.md` untuk riwayat.

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
| `AUDIT_REPORT_2.md` | Hasil audit Fase A–C (repo health + Elsevier + verifikasi IEEE) | ✅ 2026-09-13 |
| `PENDING_DECISIONS.md` | PD-01–PD-13 + tabel rekonsiliasi (diputus 2026-09-13, lihat `DECISIONS.md`) | ✅ CLOSED |
| `DECISIONS.md` | 26 keputusan final K/PD + NFR terukur (tag `decisions-v1.0`) | ✅ 2026-09-13 |
| `CONTEXT.md` | Briefing AI agent (orientasi proyek, baca dulu sebelum task) | ✅ 2026-09-13 |
| `WORKFLOW.md` | SOP lengkap (tag `workflow-v1.0`) | ✅ 2026-09-13 |
| `PROMPTS.md` | Prompt siap pakai 1–9 (paper baru, update, optimasi, audit, Elsevier) | ✅ 2026-09-13 |
| `PDF_OPTIMIZATION.md` | Log optimasi PDF 10.44 → 0.65 MB (-93.8%, strategi S1) | ✅ 2026-09-13 |
| `CHANGELOG.md` | Catatan semua perubahan file | ✅ berjalan |
| `MANIFEST.md` | File ini | ✅ |
| `.gitignore` | Exclude `template-ieee/`, `template-elsevier/`, `arsip/`, artefak LaTeX, `*.pdf` kecuali final | ✅ |
| `makalah_pancasila_ieee.tex` | Source LaTeX makalah final (IEEEtran journal, 2 kolom) | ✅ final |
| `makalah_pancasila_ieee.pdf` | Makalah final (19 hlm, 0.65 MB pasca-optimasi) | ✅ final |
| `makalah_pancasila_draft.md` | Draft markdown makalah | ✅ |
| `pancasila_referensi_fix.bib` | Daftar pustaka final (72 key, 0 orphan/0 unused) | ✅ final |
| `cover_page.png` | Cover original (5.66 MB, 2487×3508) | ✅ |
| `cover_page_opt.jpg` | Cover optimized 518 KB (dipakai PDF final) | ✅ |
| `batavia_.png` | Gambar pendukung makalah | ✅ |
| `dema_fsh.png` | Gambar pendukung makalah | ✅ |
| `garuda_pancasila.png` | Gambar pendukung makalah | ✅ |
| `hmj_if.png` | Gambar pendukung makalah | ✅ |
| `logo_walisongo.png` | Logo UIN Walisongo (pendukung makalah/cover) | ✅ |
| `memory/chat_memory.json` | Memori terstruktur 6 chat (JSON) | ✅ |
| `memory/chat_memory.md` | Memori terstruktur 6 chat (tabel Markdown) | ✅ |
| `extracted/C1–C6.json` | Transkrip terstruktur per chat (skema id/url/title/messages/metadata) | ✅ |
| `raw/C1–C6.json` | Respons API mentah per share URL | ✅ |
| `raw/C1–C6.html` | Stub (fetch HTML terhalang WAF; data via JSON) — di-exclude dari git | ⚠️ lokal saja |
| `raw/errors.log` | Log fetch (6/6 sukses, NOTE WAF) | ✅ |
| `template-ieee/` | Nested repo template IEEE (tag `template-v2.0`; di-ignore parent) | ✅ nested |
| `template-elsevier/` | Nested repo template Elsevier konversi dari IEEE (tag `elsevier-v1.1`; di-ignore parent) | ✅ nested |
| `tests/regression-2026-09-13/` | Smoke test baseline template-ieee v2.0 (NFR-05 PASS; .tex/.bib/.pdf + SMOKE_REPORT/DURATION/START/END) | ✅ 2026-09-13 |
