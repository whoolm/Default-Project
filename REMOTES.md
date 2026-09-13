# REMOTES — Backup Repositories

| Repo | URL | Branch | Tag Terakhir | Status Push |
|---|---|---|---|---|
| Default-Project (parent) | https://github.com/whoolm/Default-Project | master | milestone-v1.0 | ❌ BELUM — repo belum ada di GitHub (`remote: Repository not found`), butuh dibuat manual oleh @whoolm |
| template-ieee | https://github.com/whoolm/template-ieee | master | template-v2.0 | ❌ BELUM — remote belum di-set + repo belum ada, butuh dibuat manual |
| template-elsevier | https://github.com/whoolm/template-elsevier | master | elsevier-v1.1 | ❌ BELUM — remote belum di-set + repo belum ada, butuh dibuat manual |

Backup terakhir (percobaan): 2026-09-13

## Catatan Gap 6 (2026-09-13)

- `gh` CLI TIDAK tersedia di Windows ini (`gh: command not found`), sehingga repo tidak bisa dibuat otomatis.
- Remote parent SUDAH di-set (`origin → https://github.com/whoolm/Default-Project.git`) tetapi `git push -u origin master --tags` gagal dengan `remote: Repository not found`.
- Remote nested (template-ieee, template-elsevier) BELUM di-set; `git remote -v` kosong.
- Branch aktif adalah `master` (bukan `main` seperti di instruksi) — push harus pakai `master`.
- Tag lama TIDAK dimodifikasi (aturan global §4): `v1.0-prd`, `template-v2.0`, `decisions-v1.0`, `workflow-v1.0`, `milestone-v1.0` tetap.

## Tindak lanjut untuk @whoolm (manual)

1. Buka https://github.com/new — buat 3 repo private kosong:
   - `whoolm/Default-Project`
   - `whoolm/template-ieee`
   - `whoolm/template-elsevier`
   - JANGAN centang "Add README / .gitignore / license" (biar push bersih).
2. Setelah itu jalankan dari PowerShell:
   ```powershell
   cd "C:\Users\USER\Documents\Default Project"
   git push -u origin master --tags
   cd template-ieee
   git remote add origin https://github.com/whoolm/template-ieee.git
   git push -u origin master --tags
   cd ..
   cd template-elsevier
   git remote add origin https://github.com/whoolm/template-elsevier.git
   git push -u origin master --tags
   cd ..
   ```
3. Update tabel Status Push di file ini menjadi ✅ + tanggal backup sukses.
