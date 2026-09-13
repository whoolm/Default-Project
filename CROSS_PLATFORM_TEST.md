# Cross-Platform Test Report

Tanggal: 2026-09-13
Metode: cek WSL + inventarisasi skrip build

## Hasil

| Template | Platform | Status | Catatan |
|---|---|---|---|
| template-ieee | WSL/Ubuntu | SKIP | Tidak ada distro Linux di WSL — hanya `docker-desktop` (Stopped). `build.sh` belum diuji. |
| template-elsevier | WSL/Ubuntu | SKIP | Sama — `build.sh` belum diuji. |
| template-ieee | Windows (PowerShell) | ✅ | `build.ps1` + `Makefile` ada; template-ieee lulus compile Windows (tag `template-v2.0`, 0 error per BUILD_TEST.md). |
| template-elsevier | Windows (PowerShell) | ✅ | `build.ps1` + `Makefile` ada; PDF `template_elsevier.pdf` (168 KB) ter-build di Windows. |

## Detail WSL

```
wsl --list --verbose
* docker-desktop Stopped 2
```

Tidak ada distro Ubuntu/Debian yang running. Menjalankan `wsl bash -c ... ./build.sh`
tidak dimungkinkan tanpa install distro terlebih dahulu.

## File build yang tersedia (belum diuji di Linux)

- `template-ieee/build.sh` ✅ ada
- `template-elsevier/build.sh` ✅ ada
- Keduanya juga punya `build.ps1` + `Makefile` untuk Windows.

## Rekomendasi

- Test manual di Linux/macOS direkomendasikan sebelum klaim cross-platform:
  `chmod +x build.sh && ./build.sh` di tiap template, verifikasi PDF muncul.
- Opsional: install distro WSL (`wsl --install -d Ubuntu`) lalu jalankan ulang test ini.
- Tidak ada indikasi `build.sh` rusak — hanya berstatus NOT TESTED, bukan FAILED.
