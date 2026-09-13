# Verifikasi DOI (Spot-Check) — Makalah Ilmu Hadis

> Tanggal: 2026-09-13 (update pasca-ekstraksi)
> Sampel: 10 DOI dari PUSTAKA_INTI (35 inti), dicek via `api.crossref.org/works/<DOI>`
> Metode: `urllib` + header User-Agent, cocokkan HTTP 200 = terdaftar Crossref

## Hasil

| # | DOI | Status Crossref | Keterangan |
|---|---|---|---|
| 1 | 10.32350/jitc.161.01 | ✅ terdaftar | M345 — matn criticism |
| 2 | 10.1093/jis/etae049 | ✅ terdaftar | M305 — caliphate thirty years |
| 3 | 10.71039/istifham.v3i3.123 | ✅ terdaftar | M331 — tadwin historiografi |
| 4 | 10.1093/jis/etaf047 | ✅ terdaftar | M357 — sanctity of Madina |
| 5 | 10.33102/jfatwa.vol29n03.597 | ⚠️ 404 di Crossref | M252 — HADITH PRESERVATION; cek manual via situs jurnal sebelum disitasi |
| 6 | 10.35516/jjha.v17i3.434 | ✅ terdaftar | M222 — Al-Bukhari's Sources |
| 7 | 10.1093/llc/fqab092 | ✅ terdaftar | M199 — linguistic features ML |
| 8 | 10.1007/s10462-019-09692-w | ✅ terdaftar | M141 — survey NLP hadith |
| 9 | 10.14421/ajis.2023.611.1-17 | ✅ terdaftar | M233 — contextual criticism |
| 10 | 10.58578/ajisd.v4i3.10228 | ✅ terdaftar | M339 — living hadith + AI |

**Ringkasan:** 9 ✅ / 1 ⚠️ / 0 ❌ (dari 10 sampel — 25 sisanya TIDAK_TERSEDIA verifikasi, wajib cek sebelum disitasi).

**Catatan metode (untuk eksekusi nanti):** untuk setiap DOI, buka
`https://doi.org/<DOI>` (mis. `curl -sI`), cocokkan judul + penulis dengan
entri PUSTAKA_INTI, lalu update status: ✅ verified / ❌ tidak match /
⚠️ tidak bisa cek. Minimal 10 sampel random dari 35 inti.
