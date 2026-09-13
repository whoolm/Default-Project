# PDF_OPTIMIZATION.log — Hybrid PDF Optimization (2026-09-13 UTC)

=== DIAGNOSA ===
PDF size: 10944999 bytes (10.44 MB)
Pages: 19 (aktual via PyMuPDF; bukan 17 seperti estimasi awal)
Images di PDF (pdfimages -list): 1 (satu-satunya)
Largest image: page 1, 2487x3508, RGB, image-enc, 10.3 MB di dalam PDF (ratio 41%)
Largest image path: cover_page.png (5938301 bytes / 5.66 MB di disk, 2487x3508 RGB)
  -> PNG di disk mengembang jadi 10.3 MB saat di-embed (ZIP RGB nyaris tanpa kompresi).
Tools available: pdfimages ADA; python+PIL ADA; PyMuPDF ADA; pdftk/gswin64c/magick TIDAK ADA
Log LaTeX: tidak tersedia di root (sudah dibersihkan saat repo tidy; .tex merujuk cover_page.png baris 51-56)
Penyebab dominan: cover_page (10.3/10.44 MB = ~99% ukuran PDF). Teks/tabel/font vektor: ~0.1 MB.
Keputusan strategi: S1 saja (compress cover). S2/S3 butuh Ghostscript (tidak ada; instalasi butuh izin).
  S4 tidak relevan (font hanya ~0.1 MB). S5 DILARANG tanpa izin eksplisit.
Target: Target_B <= 3 MB.

=== STRATEGI DIEKSEKUSI ===
S1 (compress cover): cover_page.png 5799 KB -> resize 2000x2821 + JPG q85 -> cover_page_opt.jpg 518 KB (-91%).
  .tex: hanya referensi \includegraphics cover_page.png -> cover_page_opt.jpg (baris 51/56).
  Pipeline LENGKAP wajib: pdflatex -> bibtex -> pdflatex x2 (2x pdflatex saja SALAH: .bbl tidak ada
  karena artifacts dibersihkan saat tidy -> bibliografi kosong, 17 hlm/8312 kata/0 sitasi. Terdeteksi
  saat verifikasi kata, diperbaiki dengan bibtex. Pelajaran dicatat di sini.)
S2/S3: TIDAK dijalankan (Ghostscript tidak ada; target sudah terlampaui S1). S5: tidak diminta/tidak dijalankan.

=== AFTER ===
Size: 0.65 MB (10.44 -> 0.65 MB, -93.8%). Target_B <=3 MB: TERCAPAI.
Pages: 19/19 utuh. Kata: 10150/10150 identik. Sitasi [n]: 422/422. Drawings vektor: 12/12.
Teks: vektor (ter-ekstrak, 3376 char hal.2). Error compile: 0. Undefined: 0.
Ketajaman cover (render 150dpi, varians Laplacian): lama 23.3 vs baru 24.0 (setara).
Struktur: 1 image hal.1 (kini JPG), sisanya teks vektor.

=== KEPUTUSAN ===
DITUNDA oleh user (2026-09-13): belum commit, belum rollback. Working tree dibiarkan:
  hasil optimasi aktif + .bak utuh. Untuk commit nanti: hapus *.bak lalu
  git add makalah_pancasila_ieee.pdf makalah_pancasila_ieee.tex cover_page_opt.jpg.
Untuk rollback: Move-Item *.bak ke asli + git checkout makalah_pancasila_ieee.tex.
File staging: M makalah_pancasila_ieee.pdf/tex; untracked: cover_page_opt.jpg (+ .bak x3, hapus setelah putusan).
Opsi: (a) COMMIT skenario A; (b) ROLLBACK skenario B; (c) TERIMA lalu S5 (butuh izin eksplisit).
