# Smoke Test Report — Gap 1 + NFR-05

Tanggal: Minggu, 13 September 2026
Template: template-ieee (template-v2.0)
Target NFR-05: ≤ 120 menit

## Hasil
- Waktu setup + isi + compile: ±1,95 menit (START 11:50:05 → END 11:52:01)
- PDF: 4 halaman (1 cover + 3 konten), 97.775 byte (~95,5 KB) — `smoke-test-ieee/template_ieee.pdf`
- Errors: 0 (`grep "^!"` pada `template_ieee.log` kosong)
- Undefined cites: 0 (tidak ada `undefined`/`Citation undefined` di log)
- Overfull `\hbox`: 0
- Sisa placeholder `<<...>>`: 0
- Tabel: OK (booktabs 3 kolom, `tab:smoke`, tidak overflow)
- Cover: OK (halaman 1 full-page via cabang `\IfFileExists`, tanpa error)
- Sitasi: `[1]` (`contoh_artikel_jurnal`) dan `[2]` (`contoh_buku`) ter-render; `\bibcite` 1–2 terdaftar di `.aux`; sitasi rentang `[1],[2]` di Kesimpulan ter-render

## Status NFR-05: ✅ PASS

Durasi ±1,95 menit ≪ batas 120 menit (margin ~60×).

## Temuan (kalau ada)
- PDF jadi 4 halaman, bukan ~2 halaman: konten dummy (abstrak ~150 kata + 5 section 1–2 paragraf + tabel + gambar) mengisi ~3 halaman konten + 1 halaman cover. Bukan cacat template — volume dummy saja yang sedikit berlebih.
- Gambar uji memakai ulang `cover_page.png` bawaan template (33 KB) sehingga tidak perlu berkas gambar tambahan; pada naskah riil tinggal diganti file gambar sesungguhnya.
- Perintah duration satu-baris dari penugasan (`Get-Content ... | Get-Date`) gagal di PowerShell 5.1 (`Get-Date` tidak menerima pipeline input); durasi dihitung via `$start` sesi + `New-TimeSpan`, hasil identik.
- Struktur template tidak perlu diubah: tidak ada paket yang ditambah, tidak ada definisi baru — murni pengisian placeholder.

## Rekomendasi
- Tidak ada update template yang mendesak dari hasil smoke test ini.
- Opsional: tambahkan catatan 1 baris di `README_TEMPLATE.md` bahwa gambar `\includegraphics` cukup ditaruh sefolder dengan `.tex` (terbukti bekerja tanpa konfigurasi path).
- Opsional: contoh perhitungan durasi NFR-05 yang kompatibel PowerShell 5.1 (hindari `| Get-Date`, pakai `[datetime](Get-Content ...)`).
