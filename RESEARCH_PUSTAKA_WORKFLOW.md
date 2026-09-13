# Alur Research Pustaka — Ekstraksi dari 6 Chat DeepSeek

> Diekstrak dari `raw/C1.json` s/d `raw/C6.json` (total 376 pesan: C1=212, C2=12, C3=2, C4=2, C5=10, C6=138)
> Tanggal ekstraksi: 2026-09-13
> Metode: grep case-insensitive level pesan pada field `data.biz_data.messages[].content`; jangkar = `Cx-msg<message_id>`
> Cross-check: `memory/chat_memory.md` + `memory/chat_memory.json`

## 1. Ringkasan Alur

Alur research pustaka **hanya ada di C1**. C2–C6 adalah iterasi LaTeX/layout/cover (tidak ada alur research baru).

```
[Fase 0 Ideasi] DeepSeek (orkestrator) + LeapSpace brainstorming
      -> [Fase 1 Cari] Perplexity Academic (15 ref) + LeapSpace 4 prompt (Deep Research p1&p4, Copilot p2&p3)
      -> [Fase 2 Validasi] Consensus (Consensus Meter, 20 artikel) + Elicit (tabel ekstraksi / Agen / PRISMA)
      -> [Fase 3 Peta] Semantic Scholar (Ask-this-paper, TL;DR) + Research Rabbit + Connected Papers + Scite (supporting/contrasting/mentioning)
      -> [Fase 4 Dalam] Gemini Deep Research (10 dimensi, 30+ sumber) — SEMPAT TERTUNDA (server penuh)
      -> [Fase 5 Tulis] SciSpace (AI Writer + template Elsevier + Citation Generator) + Claude (penulisan/revisi) + DeepSeek operasional (sintesis)
      -> [Fase 6 Eksekusi] OpenCode (skrip extract/download/retry, compile pdflatex->bibtex->pdflatex x2)
```

Keputusan arsitektur (C1-msg30): *"Kita **skip dulu** pembuatan aplikasi web (Next.js/Prisma) ... langsung fokus ke **'Penerapan Praktis'** ... dengan **DeepSeek sebagai 'Orkestrator'**"*.

## 2. Tool yang Digunakan

| Tool | Fungsi | Chat Asal | Kutipan (dipangkas, verbatim) |
|---|---|---|---|
| LeapSpace | Brainstorming terstruktur + Deep Research; database Scopus + ScienceDirect; sintesis s.d. 300 sumber | C1-msg40 | *"LeapSpace ... Brainstorming terstruktur, eksplorasi analogi ... Menggunakan database Scopus + ScienceDirect"* |
| LeapSpace Deep Research | Laporan multi-langkah + trust card; bisa multi-round follow-up | C1-msg44 | *"bisa ... menghasilkan 'laporan riset multi-langkah yang komprehensif' ... mensintesis hingga 300 sumber ... trust card"* (terjemahan dari teks Mandarin di pesan tsb) |
| Perplexity (Academic/Pro) | Pencarian literatur awal cepat + sitasi + link; 15 referensi awal | C1-msg30 | *"Buka Perplexity, aktifkan mode **'Academic'** ... Prompt: 'Cari 15 artikel ilmiah terbaru (2021-2026) ... Berikan DOI, judul, dan ringkasan'"* |
| Consensus | Validasi konsensus ilmiah; Consensus Meter atas 20 artikel (Yes/No/Possibly); Study Snapshots; Pro Analysis | C1-msg60 | *"Consensus ... mengakses lebih dari **200 juta paper** dari ... Semantic Scholar ... Consensus Meter ... **20 artikel** ... label Yes/No/Possibly"* |
| Elicit | Cari paper + ekstraksi tabel (metodologi, populasi, temuan); Agen Penelitian; Tinjauan sistematis PRISMA 2020 | C1-msg64, C1-msg66 | *"Elicit ... mengekstrak informasi penting ke dalam **tabel** (misal: metodologi, populasi, temuan)"* (C1-msg64); *"'Tinjauan sistematis' ... mengikuti standar **PRISMA 2020**"* (C1-msg66) |
| Semantic Scholar | Pencarian akademik + Ask-this-paper + TL;DR; sumber database Consensus/Connected Papers | C1-msg64, C1-msg70 | *"fitur **'Ask This Paper'** ... TL;DR otomatis"* (C1-msg64); temuan demokrasi/aksiologi/NASAKOM di C1-msg70 |
| Research Rabbit | Visual citation graph (Spotify for papers); Similar/Earlier/Later; 50 seed gratis; integrasi Zotero | C1-msg72 | *"**Visual Citation Graph** ... **Similar / Earlier / Later Works** ... **Zotero Integration**"* |
| Connected Papers | Grafik 1 seed paper; co-citation + bibliographic coupling; Prior/Derivative works; 5 grafik gratis | C1-msg74 | *"membangun grafik visual dari ... **satu paper seed** ... **co-citation** ... **bibliographic coupling** ... **Prior Works** / **Derivative Works**"* |
| Scite | Smart Citations: supporting / contrasting / mentioning | C1-msg78 | *"**'Smart Citations'** ... 1. **Mendukung (Supporting)** 2. **Membantah (Contrasting)** 3. **Menyebut (Mentioning)**"* |
| SciSpace | Penulisan all-in-one + template Elsevier + Citation Generator (DOI) + AI Writer/Copilot | C1-msg80, C1-msg82 | *"platform penulisan akademik all-in-one ... template jurnal ... **Citation Generator** ... dari DOI/URL/ISBN"* (C1-msg80) |
| Gemini Deep Research | Laporan komprehensif 10 dimensi, min. 30 sumber Scopus/SINTA 1-2 (2015–2026) | C1-msg90, C1-msg94 | *"**10 RENCANA RISET UNTUK GEMINI DEEP RESEARCH**"* (C1-msg90); *"PROMPT GABUNGAN ... mencakup 10 dimensi ... minimal 30 sumber"* (C1-msg94) |
| DeepSeek | Orkestrator operasional + sintesis bahan LeapSpace+Perplexity | C1-msg30, C1-msg58 | *"dengan **DeepSeek sebagai 'Orkestrator'** (pusat kontrol operasional)"* (C1-msg30) |
| Claude | Inti penulisan/revisi + LaTeX (elsarticle) + academic tone | C1-msg32 | *"**Claude (Saya)** ... Saya tulis langsung file `makalah.tex`, `references.bib` ... **siap compile**"* |
| OpenCode | Eksekusi: skrip extract/download/retry + compile + konversi Elsevier->IEEE | C1-msg84, C1-msg110 | *"skrip `extract_all_urls.py` / `download_all.py`"*, *"Total Referensi: 168"* (C1-msg110) |
| Julius AI | TIDAK_TERPAKAI (hanya disebut sekali sebagai opsi analisis data, tanpa tindak lanjut) | C1-msg63 | *"Julius AI: Asisten AI untuk analisis data ..."* — tidak ada prompt/output |
| Mendeley / EndNote / DOAJ / scholar.google / "Leap Space" (spasi) | TIDAK_TERSEDIA di chat (0 hit) | — | Mendeley disebut 1x hanya sebagai analogi SciSpace (C1-msg80); EndNote/DOAJ/scholar.google/"Leap Space" = 0 hit |

Catatan koreksi jangkar: pesan user *"kita ambil praktisnya dulu ... consensus+leapspace+perplexity ... gemini ... deepseek"* = **C1-msg29** (bukan msg28; msg28 adalah pesan asisten tentang tech stack Next.js/Prisma).

## 3. Urutan Langkah (Step-by-Step)

### Langkah 1 — Ideasi & Pemetaan Topik
- **Tool:** DeepSeek (orkestrator) + LeapSpace brainstorming
- **Query/Keyword:** Topik user C1-msg33: *"Pancasila sebagai Sistem Filsafat dan Ideologi Negara ... ontologis, epistemologis, aksiologis ... Perbandingan ... (Liberalisme, Komunisme)"*
- **Output:** 5 pertanyaan riset + 10 kata kunci + struktur makalah (rencana di C1-msg30 Fase 0)
- **Chat asal:** C1-msg29, C1-msg30, C1-msg33

### Langkah 2 — Pencarian Literatur Awal (Perplexity)
- **Tool:** Perplexity Academic/Pro
- **Query:** *"Cari 15 artikel ilmiah terbaru (2021-2026) tentang [TOPIC], fokus pada [aspek spesifik]. Berikan DOI, judul, dan ringkasan 1 paragraf per artikel."* (C1-msg30)
- **Output:** 15 referensi awal (5 filsafat + 3 liberalisme + 4 komunisme + 3 global — rekap di C1-msg58)
- **Chat asal:** C1-msg30, C1-msg58

### Langkah 3 — Brainstorming & Deep Research (LeapSpace, 4 prompt)
- **Tool:** LeapSpace; prompt 1 & 4 = Deep Research, prompt 2 & 3 = Copilot (keputusan user C1-msg49)
- **Query:** 4 prompt ±480–490 karakter (verbatim di §4; sumber C1-msg55)
- **Kendala:** *"Maximum 500 characters allowed"* (C1-msg41); tanya-jawab Deep Research 1 vs 4 prompt (C1-msg43, C1-msg47)
- **Output:** 4 laporan (filosofis, liberalisme, komunisme, global-digital)
- **Chat asal:** C1-msg40, C1-msg41, C1-msg44, C1-msg49, C1-msg55, C1-msg57, C1-msg58

### Langkah 4 — Validasi Konsensus (Consensus)
- **Tool:** Consensus (Consensus Meter + Study Snapshots + Pro Analysis/Deep Search)
- **Query:** Pertanyaan Ya/Tidak, cth. *"Apakah Pancasila dapat dikategorikan sebagai sistem filsafat yang koheren?" → 85% Yes* (contoh ilustratif di C1-msg60, bukan hasil ukur real)
- **Output:** 3 laporan + gauge konsensus (disebut di rekap C1-msg84: *"Consensus → 3 laporan dengan Consensus Meter"*)
- **Chat asal:** C1-msg60, C1-msg61, C1-msg84

### Langkah 5 — Ekstraksi Terstruktur (Elicit)
- **Tool:** Elicit (Cari makalah / Mengobrol / Ekstrak data / Agen penelitian / Laporan / Tinjauan sistematis PRISMA)
- **Query:** 4 prompt Agen (EN, verbatim di C1-msg68; ringkas di §4); cth. *"What are the main critiques of Pancasila as a state ideology ...?"* (C1-msg64)
- **Output:** 2 laporan Agen Penelitian (rekap C1-msg84)
- **Chat asal:** C1-msg64, C1-msg66, C1-msg68, C1-msg84

### Langkah 6 — Pemetaan Sitasi (Semantic Scholar + Research Rabbit + Connected Papers + Scite)
- **Tool:** Semantic Scholar → Research Rabbit → Connected Papers → Scite (urutan sesuai C1-msg63 list user + panduan asisten)
- **Query:** Seed paper: Latif 2018, Madung 2016, dsb. (simulasi grafik di C1-msg76)
- **Output:** Tabel temuan tambahan (C1-msg70) + simulasi 5 grafik seed (C1-msg76) + analisis supporting/contrasting (C1-msg78)
- **Chat asal:** C1-msg63, C1-msg70, C1-msg72, C1-msg74, C1-msg76, C1-msg77 (user: *"lanjut ke scite aja"*), C1-msg78, C1-msg79 (user: *"lanjut ke scispace"*)

### Langkah 7 — Penulisan & Referensi (SciSpace + Claude + DeepSeek)
- **Tool:** SciSpace (Citation Generator via DOI) + Claude (draf) + DeepSeek (sintesis)
- **Query:** Prompt setup + impor 40 DOI (daftar di C1-msg82); 7 inti terverifikasi Crossref: latif2018, madung2016, duha2022, kim2024, pristiwiyanto2021, madungmere2021, ulumhamida2018 (C1-msg85)
- **Output:** `makalah_pancasila_draft.md` (7 bagian) + `pancasila_referensi.bib` (7 lengkap + 33 `@misc` minimal-DOI) — C1-msg85
- **Chat asal:** C1-msg80, C1-msg82, C1-msg84, C1-msg85, C1-msg86, C1-msg88

### Langkah 8 — Deep Research Komprehensif (Gemini — tertunda lalu jalan)
- **Tool:** Gemini Deep Research
- **Query:** 7 → 10 rencana riset (C1-msg90) → versi rinci (C1-msg92) → 1 prompt gabungan 10 dimensi (C1-msg94); evaluasi kelayakan 10 rencana (C1-msg102)
- **Kendala:** *"gemini lagi server penuh, kita coba nanti"* (C1-msg63); evaluasi: rencana 7 (Gen Z) *"butuh effort"* data survei (C1-msg102)
- **Output:** Laporan "Riset 10 Dimensi" (.docx, 168 entri "Karya yang dikutip" — C1-msg110)
- **Chat asal:** C1-msg61, C1-msg63, C1-msg90, C1-msg92, C1-msg94, C1-msg102, C1-msg110

### Langkah 9 — Unduh Massal + Kompilasi (OpenCode)
- **Tool:** OpenCode (skrip Python + pdflatex→bibtex→pdflatex×2)
- **Query:** N/A (eksekusi file)
- **Output:** 168 URL diekstrak; hasil unduh dilaporkan bertahap (94 ok, 31 gagal dst. — lihat `memory/chat_memory.md`; angka final bervariasi antar pesan, jangan dikutip sebagai metrik tunggal tanpa konteks)
- **Chat asal:** C1-msg106–C1-msg110+ (skrip di C1-msg110)

## 4. Query/Keyword yang Dipakai

### 4.1 Empat prompt LeapSpace (verbatim user, C1-msg55, ±480–490 char)

| # | Fokus | Query (verbatim, dipangkas 400 char) | Mode |
|---|---|---|---|
| P1 | Filosofis (onto-epis-aksio) | *"Pancasila sebagai sistem filsafat. Analisis ontologis, epistemologis, aksiologis. Bagaimana tiga dimensi ini saling terkait ... perbandingan dengan ... (Plato, Hegel, Marx) ... hubungan hierarkis antar sila. Berikan sumber dari jurnal terakreditasi."* | Deep Research |
| P2 | vs Liberalisme | *"Bandingkan Pancasila dengan liberalisme dalam hal: konsep kebebasan individu, peran negara, hak asasi manusia, dan demokrasi. Mana yang lebih menekankan musyawarah ... Sertakan kritik Pancasila terhadap liberalisme. Berikan referensi jurnal internasional dan nasional."* | Copilot |
| P3 | vs Komunisme | *"Bandingkan Pancasila dengan komunisme dalam hal: kepemilikan pribadi, kolektivitas, peran negara, dan pandangan tentang ketuhanan. Apa titik temu dan perbedaan mendasar? Mengapa Pancasila disebut sebagai 'jalan tengah'? Sertakan sumber dari jurnal terindeks SINTA atau Scopus."* | Copilot |
| P4 | Global & digital | *"Relevansi Pancasila di era globalisasi dan digital. Tantangan utama dari nilai asing (liberalisme, kapitalisme, sekularisme). Bagaimana Pancasila sebagai ideologi terbuka dapat berdialog dengan nilai global tanpa kehilangan identitas? Sertakan studi kasus atau data terkini."* | Deep Research |

Pembagian mode diputuskan user di **C1-msg49**: *"prompt 1-4 tetap di leapspace dulu, cuman prompt 1 & 4 pake deep research, sedangkan prompt 2 & 3 menggunakan copilot saja"*.

### 4.2 Prompt Elicit Agen (verbatim asisten, C1-msg68, EN)

1. *"Pancasila as a philosophical system: analyze its ontology ..., epistemology ..., and axiology .... How are these three dimensions interconnected? Include critiques from contemporary scholarship."*
2. *"Compare Pancasila and liberalism in terms of: (1) individual freedom vs social responsibility, (2) the role of the state, (3) human rights, (4) democracy. ...?"*
3. *"Compare Pancasila and communism in terms of: (1) private property vs collective ownership, (2) the role of the state, (3) views on religion/theology, (4) individualism vs collectivism. Why is Pancasila often described as a 'middle way'? ...?"*
4. Relevansi global-digital + studi kasus/data terbaru (lihat C1-msg68 penuh).

Prompt tunggal contoh (C1-msg64): *"Comparative studies between Pancasila and liberalism/communism in terms of individual rights, state role, and religious values. Extract methodology, key findings, and theoretical framework."*

### 4.3 Prompt Gemini (10 dimensi, C1-msg90/92/94)

Ontologi vs Barat+Timur; epistemologi vs rasionalisme/empirisme/hermeneutika; aksiologi vs Rawls/Sen-Nussbaum/Fraser; kritik hierarki-piramidal; vs liberalisme; vs komunisme/NASAKOM; globalisasi Gen-Z; ekonomi digital; kritik HAM/agama/post-foundational; sintesis + research gaps. Syarat di prompt gabungan (C1-msg94): *"minimal 30 sumber dari jurnal Scopus dan SINTA 1-2 (2015-2026)"* + matriks perbandingan + celah riset.

### 4.4 Prompt Perplexity / Consensus / Semantic Scholar

- Perplexity: §3 Langkah 2 (C1-msg30).
- Consensus: pertanyaan Ya/Tidak + filter tahun/jenis studi + ekspor `.bib`/`.ris` (C1-msg30, C1-msg60).
- Semantic Scholar: *"Pancasila and liberalism"* + Ask-this-paper, cth. *"Apa metodologi yang digunakan?"* (C1-msg64).

## 5. Kriteria Inklusi/Eksklusi

Eksplisit di chat:

- Rentang tahun: **2021–2026** (prompt Perplexity, C1-msg30); **2015–2026** (prompt gabungan Gemini, C1-msg94).
- Kualitas sumber: **Scopus dan SINTA 1-2** (C1-msg55 P3; C1-msg94); LeapSpace disebut memakai **Scopus + ScienceDirect** (C1-msg40); Consensus memakai **200+ juta paper peer-review via Semantic Scholar** (C1-msg60); Connected Papers memakai **Semantic Scholar** (C1-msg74).
- Jenis: artikel peer-review; filter tahun + jenis studi di Consensus (C1-msg30); ekstraksi metodologi/populasi/temuan (C1-msg60, C1-msg64).
- TIDAK_TERSEDIA: daftar kriteria eksklusi formal (bahasa, duplikat, full-text) tidak dirumuskan di chat; PRISMA disebut sebagai **standar workflow Elicit** (C1-msg66) tanpa lembar skrining.

## 6. Verifikasi Referensi

- **Crossref API:** 2 DOI inti diverifikasi (Latif 2018, Madung 2016) *"valid dan metadata cocok"* (C1-msg85); 7 inti metadata lengkap + 33 entri `@misc` minimal-DOI wajib dilengkapi via Citation Generator SciSpace sebelum submit (C1-msg85).
- **Cross-check cite↔bib:** target 0 yatim/0 menganggur disebut di memori untuk tahap akhir makalah (bukan di alur research awal) — lihat `memory/chat_memory.md`; tidak ada bukti hitungan ini di pesan research awal, jadi TIDAK_TERSEDIA sebagai hasil langkah research.
- **Scite Smart Citations:** validasi supporting/contrasting/mentioning (C1-msg78).
- **Consensus Meter:** indikasi cepat, *"**bukan** alat meta-analisis formal ... maksimal **20 artikel**"* (C1-msg60) — jangan diklaim sebagai meta-analisis.
- **Evaluasi kelayakan 10 rencana:** 9 tersedia, rencana 7 (Gen Z) butuh effort data survei (C1-msg102).

## 7. Klasifikasi Hasil

- Per **sumber tool**: Perplexity 15 ref (5+3+4+3) dan LeapSpace 4 laporan (C1-msg58); Consensus 3 laporan; Elicit 2 laporan Agen; Semantic Scholar temuan tambahan; Scite analisis kutipan (rekap C1-msg84).
- Per **dimensi makalah**: 7 bagian draf (pendahuluan; tinjauan onto-epis-aksio; vs liberalisme; vs komunisme; jalan tengah + 3 syarat; global-digital; kesimpulan) — C1-msg85.
- Per **grafik sitasi**: Prior / Similar / Derivative (Connected Papers, C1-msg74/76); Similar / Earlier / Later (Research Rabbit, C1-msg72).
- Per **tabel ekstraksi**: metodologi, populasi, temuan, framework (C1-msg64).

## 8. Kendala & Solusi

| Kendala | Solusi / Status | Chat |
|---|---|---|
| LeapSpace maks 500 karakter | 4 prompt dipadatkan ±480–490 char; P1&P4 Deep Research, P2&P3 Copilot | C1-msg41, C1-msg49, C1-msg55 |
| Gemini server penuh | Tunda Gemini; kerjakan Elicit/Semantic Scholar/Rabbit/Papers/Scite/SciSpace dulu | C1-msg63 |
| Consensus disangka meta-analisis | Penegasan: bukan meta-analisis formal, maks 20 artikel, hanya indikasi cepat | C1-msg60 |
| User bingung prompt Consensus/LeapSpace susulan | Asisten petakan ulang peran tiap tool + prompt siap pakai | C1-msg37 (user), C1-msg40 (solusi) |
| User minta "meta analisis + mencari lagi" | Perdalam via Elicit Agen + Semantic Scholar + peta sitasi | C1-msg39 (user), C1-msg64+ (solusi) |
| Fetch massal 40 DOI timeout (Crossref lambat) | 33 entri dibuat minimal-DOI; wajib dilengkapi via Citation Generator | C1-msg85 |
| Unduhan massal 403/login-wall/paywall | Skrip retry + manual; angka gagal bervariasi antar pesan — lihat memori, jangan jadikan metrik tunggal | C1-msg110+, `memory/chat_memory.md` |
| Connected Papers/Rabbit butuh interaksi web | Simulasi grafik 5 seed paper + rekomendasi koleksi | C1-msg76 |
| C2–C6: footer nabrak, nama horizontal, cover blank, "Ringkasan", sitasi `[?]` | Perbaikan LaTeX manual (di luar ruang lingkup research pustaka) | C2–C6 (lihat memori) |

## 9. Template Pustaka (dari Chat)

- File kerja: `makalah_pancasila_draft.md` + `pancasila_referensi.bib` (40 ref: 7 inti + 33 DOI) — C1-msg85; prompt tim OpenCode/SciSpace — C1-msg84, C1-msg88.
- Impor: Citation Generator SciSpace via DOI (daftar 40 DOI di C1-msg82); ekspor Consensus `.bib`/`.ris` (C1-msg30); ekspor Elicit CSV (C1-msg64).
- Format akhir makalah: Elsevier `elsarticle` dulu, lalu konversi IEEE `IEEEtran` + `IEEEtran.bst` (disebut di C1-msg32/82/86; detail konversi di luar dokumen ini).
- Contoh kunci DOI inti: `10.15408/sdi.v25i2.7502` (Latif 2018), `10.18592/khazanah.v13i2.768` (Madung 2016), `10.15294/ijpgc.v1i2.59807` (Duha 2022), `10.1080/13569317.2024.2408230` (Kim 2024), `10.37812/fatawa.v1i2.448` (Pristiwiyanto 2021) — C1-msg82.

## 10. Kutipan Penting (Verbatim, berjangkar)

> *"kita ambil praktisnya dulu aja alias kita ambil langsung ke penerapan llm masing" seperti consensus+leapspace+perplexity untuk search reference, gemini(deep research), dan deepseek untuk operasionalnya"* — C1-msg29 (USER)

> *"Kita **skip dulu** pembuatan aplikasi web (Next.js/Prisma) yang ribet, dan langsung fokus ke **'Penerapan Praktis'** ... dengan **DeepSeek sebagai 'Orkestrator'** (pusat kontrol operasional)"* — C1-msg30 (ASSISTANT)

> *"gini aja prompt 1-4 tetap di leapspace dulu, cuman prompt 1 & 4 pake deep research, sedangkan prompt 2 & 3 menggunakan copilot saja(tetap di leapspace)"* — C1-msg49 (USER)

> *"di leapspace Maximum 500 characters allowed"* — C1-msg41 (USER)

> *"ok tadi kan sudah leapspace, sudah perplexity. lanjut kemana?berikut ini hasil leapspace"* — C1-msg57 (USER)

> *"Consensus adalah **mesin pencari akademik berbasis AI** ... mengakses lebih dari **200 juta paper** dari database Semantic Scholar"* — C1-msg60 (ASSISTANT)

> *"Consensus Meter **bukan** alat meta-analisis formal ... Ia hanya menganalisis maksimal **20 artikel**"* — C1-msg60 (ASSISTANT)

> *"duh gemini lagi server penuh, kita coba nanti.. untuk sekarang kita penuhi kebutuhan dari beberapa ai berikut ini dulu"* — C1-msg63 (USER)

> *"lanjut ke scite aja langsung ya"* — C1-msg77 (USER)

> *"ok scite udah lanjut ke scispace"* — C1-msg79 (USER)

> *"Saya verifikasi 2 DOI inti via Crossref API: Latif 2018 dan Madung 2016 valid dan metadata cocok."* — C1-msg85 (USER, ditempel dari laporan asisten; status: klaim user di chat)

> *"Lakukan deep research komprehensif tentang Pancasila sebagai sistem filsafat dengan mencakup 10 dimensi analisis berikut. ... minimal 30 sumber dari jurnal Scopus dan SINTA 1-2 (2015-2026)."* — C1-msg94 (ASSISTANT, prompt gabungan Gemini)

> *"**Tinjauan sistematis** ... mengikuti standar **PRISMA 2020** untuk systematic review."* — C1-msg66 (ASSISTANT, tentang fitur Elicit)

## Lampiran A — Hit keyword (level pesan, case-insensitive, terverifikasi 2026-09-13)

Metode: satu pesan dihitung 1 hit per keyword bila `content` mengandung keyword (regex case-insensitive). Satu pesan bisa kena >1 keyword.

| Keyword | Pesan-hit | Catatan |
|---|---|---|
| research | 83 | C1, C2, C6 dominan |
| pustaka | 70 | C1–C6 |
| literatur | 58 | C1–C6 |
| PRISMA | 43 | C1–C6 (banyak dari kata "Prisma" ORM di C1 awal + PRISMA metode di akhir) |
| SINTA | 32 | C1–C6 |
| scopus | 29 | C1–C6 |
| garuda | 27 | C1, C5, C6 (sebagian = logo/gambar Garuda, bukan database Garuda — perlu pilah manual) |
| LeapSpace | 24 | C1 saja |
| Consensus | 24 | C1 saja |
| Perplexity | 19 | C1 saja |
| Deep Research | 19 | C1 saja |
| systematic review | 18 | C1 |
| Elicit | 16 | C1 |
| Semantic Scholar | 16 | C1 |
| Gemini | 14 | C1 |
| literature | 12 | C1 |
| database | 12 | C1, C2 |
| Scite | 12 | C1 |
| Research Rabbit | 9 | C1 |
| Connected Papers | 8 | C1 |
| SciSpace | 8 | C1 |
| Zotero | 7 | C1 (integrasi Rabbit + analogi manajer referensi) |
| Copilot | 7 | C1 |
| Google Scholar | 4 | C1 |
| systematic literature | 3 | C1 |
| Crossref | 3 | C1 |
| Mendeley | 2 | C1 (1x analogi SciSpace, 1x daftar) |
| DOAJ | 0 | TIDAK_TERSEDIA |
| EndNote | 0 | TIDAK_TERSEDIA |
| scholar.google | 0 | TIDAK_TERSEDIA |
| "Leap Space" (spasi) | 0 | TIDAK_TERSEDIA (yang dipakai selalu "LeapSpace") |

Total pesan unik menyentuh keyword apapun: **157 dari 376** (C1=110, C6=38, C5=5, C2=2, C3=1, C4=1). Total pesan-hit lintas keyword (satu pesan dihitung per keyword): 579. Angka "86 PRISMA / 48 LeapSpace / 48 Consensus / 38 Perplexity" di versi dokumen sebelumnya adalah hit **level baris Select-String** (case-variant digandakan), bukan level pesan — dicatat sebagai konflik versi (lihat bawah).

## Lampiran B — Konflik vs `memory/chat_memory.md` (dicatat, tidak didamaikan sepihak)

1. **Angka unduhan referensi** (94 ok / 31 gagal / 168 total / 72 disitasi) bervariasi antar pesan C1 dan ringkasan memori. Dokumen ini tidak mengklaim satu angka final; gunakan `memory/chat_memory.md` + log skrip sebagai acuan dan verifikasi ulang folder `referensi/`.
2. **File .bib acuan**: memori C1 menetapkan `pancasila_referensi_fix.bib`; memori C6 menyebut `pancasila_referensi_final.bib`. Keduanya dicatat apa adanya.
3. **Hitungan keyword versi lama** dokumen ini (PRISMA 86, LeapSpace 48, Consensus 48, Perplexity 38) vs hitungan level-pesan terverifikasi di Lampiran A. Perbedaan = metodologi (baris vs pesan + duplikat case-variant).
4. **Jangkar msg versi lama** (mis. LeapSpace C1-msg28/msg36-46, Consensus C1-msg53/54, Elicit C1-msg56-61) memakai **nomor urut tampilan** yang mengabaikan gap `message_id`; versi ini memakai `message_id` mentah (mis. keputusan mode LeapSpace = C1-msg49, sintesis = C1-msg58, Consensus guide = C1-msg60) — verifikasi via `raw/C1.json`.
5. **Contoh "85% Yes" Consensus** (C1-msg60) adalah ilustrasi format gauge, bukan hasil ukur riset.
6. **"garuda"**: sebagian hit C5/C6 merujuk gambar/logo Garuda, bukan portal Garuda — jangan dikutip sebagai database tanpa pilah konteks.
7. **Klaim verifikasi Crossref 2 DOI** berasal dari pesan USER C1-msg85 (tempelan laporan), bukan log API mentah — status bukti: klaim chat, bukan artefak terverifikasi independen.
