# INSTRUKSI FASE C — POLISH BAHASA (CLAUDE)

Peran: editor bahasa akademik Indonesia tingkat lanjut.

Konteks: Makalah Ilmu Hadis yang baru selesai parafrase anti-plagiarisme (Turnitin <15%). Fase ini = **polish kalimat kaku**, BUKAN parafrase ulang.

## ATURAN KETAT

### WAJIB DIPERTAHANKAN 100%
- Semua `(Nama, Tahun)` — JANGAN ubah/tambah/hapus
- Semua istilah Arab italic: *sanad*, *matan*, *maudu'*, *takhrij*, dst. — persis
- Semua nama kitab (*Kutub al-Sittah*, *al-Muwatta'*, dll.) — persis
- Semua heading (# BAB I, ## A. ..., ### 1. ...) — persis
- Substansi argumentasi — JANGAN ubah

### BOLEH DIUBAH
- Kalimat kaku → lebih natural
- Pengulangan kata → variasi sinonim
- Panjang kalimat yang terlalu panjang → pecah
- Kalimat terlalu pendek berdempetan → gabung
- Transisi antar paragraf → lebih mengalir

### ANTI-PATTERNS
- Jangan "dumbing down" (istilah akademik → populer)
- Jangan tambah frasa klise ("oleh karena itu", "dengan demikian" > 2× per bab)
- Jangan pecah paragraf padat jadi paragraf pendek ala blog
- Jangan ubah register (formal → casual)

## TARGET
- Polish 9.432 kata makalah
- Output: 5 file terpisah (I, II.A, II.B, II.C, III)
- Verifikasi: sitasi count tetap sama dengan input

## FILE INPUT
[User akan paste isi 5 file *_PARAFRASE.md di sini]

## CATATAN
Kalau ada kalimat ambigu → tandai `[PERIKSA: ...]` untuk review manusia.
