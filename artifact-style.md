# Panduan Desain Artifact — Gaya Koran (ala Artikel NYT)

Semua artifact yang dihasilkan plugin ini (brief, daftar komunitas, ide konten, pelajaran ajarin) WAJIB pakai design system ini. Referensinya: halaman artikel The New York Times — bersih, flat, tipografi koran klasik, terlihat seperti artikel premium saat di-share. Ini meniru *pola desainnya* saja — JANGAN pernah pakai nama, logo, atau branding NYT di halaman.

## Prinsip

1. **SELALU TERANG — jangan pernah dark mode.** Latar putih polos `#ffffff`, flat di seluruh halaman (BUKAN kartu kertas di atas latar abu). Jangan pakai `prefers-color-scheme: dark` — di dark mode pun halaman tetap putih seperti koran.
2. **Kolom artikel sempit.** Semua teks di kolom tengah max-width 600px. Elemen lebar (tabel, gambar) boleh melebar sampai 780px, tapi teks tetap 600px — ini ciri khas halaman artikel koran.
3. **Dua keluarga font, peran tegas.**
   - **Serif untuk headline & body** — pengganti Cheltenham/Imperial NYT: `Georgia, "Iowan Old Style", "Times New Roman", serif`. Headline besar (clamp 32–42px), weight 700, line-height rapat 1.15, warna hitam pekat. Body 18px, line-height 1.6.
   - **Sans untuk label, byline, caption, tabel** — pengganti Franklin NYT: `"Franklin Gothic Medium", "Libre Franklin", "Helvetica Neue", Arial, sans-serif`. Selalu kecil (11–14px).
4. **Hampir tanpa warna.** Teks utama `#121212`, sekunder `#5a5a5a`, garis `#e2e2e2`, garis tegas `#121212`. Tidak ada aksen warna, tidak ada latar krem/tint blok — hierarki murni dari tipografi dan garis. Link hitam bergaris bawah.
5. **Anatomi artikel NYT (urutan wajib):** kicker/label section kecil uppercase sans → **headline serif besar** → deck/ringkasan serif light abu (20–22px, line-height 1.4) → byline sans ("Oleh Agen Marketing-Organik" — nama bold) → tanggal sans abu → garis tipis → body.
6. **Pemisah pakai garis, bukan kotak.** Antar item (ide, minggu, post) pakai `border-top: 1px solid #e2e2e2` + spasi — seperti daftar berita NYT. Tidak ada kartu ber-background, tidak ada rounded, tidak ada shadow.
7. **Sub-judul section** = serif bold 22px (seperti subhead artikel NYT), bukan label uppercase besar.
8. **Tanpa hiasan.** Tidak ada emoji dekoratif, ikon, atau gradien. Angka penting ditampilkan sebagai teks serif bold besar dengan label sans kecil.
9. **Responsif.** Tabel dibungkus `overflow-x: auto`; body tidak boleh scroll horizontal.

## CSS dasar (inline-kan di artifact, sesuaikan seperlunya)

```css
:root {
  --ink: #121212;      /* teks utama */
  --gray: #5a5a5a;     /* teks sekunder, caption, tanggal */
  --line: #e2e2e2;     /* garis pemisah tipis */
  --line-dark: #121212;/* garis tegas */
}
/* SENGAJA tidak ada blok dark mode — halaman selalu putih seperti koran. */

* { box-sizing: border-box; }
body {
  background: #ffffff;
  color: var(--ink);
  font: 18px/1.6 Georgia, "Iowan Old Style", "Times New Roman", serif;
  margin: 0;
  -webkit-font-smoothing: antialiased;
}
.article { max-width: 600px; margin: 0 auto; padding: 56px 20px 96px; }
.wide { max-width: 780px; margin-left: auto; margin-right: auto; } /* untuk tabel lebar */

/* font sans ala Franklin */
.sans { font-family: "Franklin Gothic Medium", "Libre Franklin", "Helvetica Neue", Arial, sans-serif; }

/* Header artikel */
.kicker {
  font-family: "Franklin Gothic Medium", "Libre Franklin", "Helvetica Neue", Arial, sans-serif;
  font-size: 12px; font-weight: 700; letter-spacing: .08em; text-transform: uppercase;
  margin-bottom: 14px;
}
h1 {
  font-size: clamp(32px, 5.5vw, 42px); line-height: 1.15; font-weight: 700;
  letter-spacing: -0.005em; margin: 0 0 18px;
}
.deck { font-size: 21px; line-height: 1.4; color: var(--gray); font-weight: 400; margin: 0 0 24px; }
.byline {
  font-family: "Franklin Gothic Medium", "Libre Franklin", "Helvetica Neue", Arial, sans-serif;
  font-size: 14px; margin-bottom: 4px;
}
.byline b { font-weight: 700; text-decoration: underline; text-underline-offset: 2px; } /* nama di-underline seperti byline NYT */
.dateline {
  font-family: "Franklin Gothic Medium", "Libre Franklin", "Helvetica Neue", Arial, sans-serif;
  font-size: 13px; color: var(--gray); margin-bottom: 26px;
}
.head-rule { border: none; border-top: 1px solid var(--line); margin: 0 0 32px; }

/* Body & sub-judul */
p { margin: 0 0 22px; }
h2 { font-size: 22px; font-weight: 700; line-height: 1.3; margin: 44px 0 14px; }
h3 { font-size: 18px; font-weight: 700; margin: 26px 0 8px; }
a { color: var(--ink); text-decoration: underline; text-underline-offset: 2px; }

/* Item berulang (ide, minggu, post) — dipisah garis seperti indeks berita */
.item { border-top: 1px solid var(--line); padding: 24px 0 6px; }
.item-label {
  font-family: "Franklin Gothic Medium", "Libre Franklin", "Helvetica Neue", Arial, sans-serif;
  font-size: 12px; font-weight: 700; letter-spacing: .08em; text-transform: uppercase;
  color: var(--gray); margin-bottom: 8px;
}
.item h3 { margin-top: 0; }
.item .src {
  font-family: "Franklin Gothic Medium", "Libre Franklin", "Helvetica Neue", Arial, sans-serif;
  font-size: 12.5px; color: var(--gray); margin-top: 8px;
}

/* Kutipan (pain point / post) — pull quote koran */
blockquote, .quote {
  border-left: 1px solid var(--line-dark);
  margin: 26px 0; padding: 2px 0 2px 22px;
  font-size: 20px; line-height: 1.45; font-style: italic;
}
.quote .who {
  font-style: normal;
  font-family: "Franklin Gothic Medium", "Libre Franklin", "Helvetica Neue", Arial, sans-serif;
  font-size: 12.5px; color: var(--gray); margin-top: 10px;
}

/* Tabel — sans kecil seperti grafik data koran */
.table-wrap { overflow-x: auto; margin: 18px 0 26px; }
table {
  border-collapse: collapse; width: 100%;
  font-family: "Franklin Gothic Medium", "Libre Franklin", "Helvetica Neue", Arial, sans-serif;
  font-size: 13.5px; line-height: 1.45;
}
th {
  text-align: left; font-size: 11px; font-weight: 700; letter-spacing: .06em; text-transform: uppercase;
  color: var(--gray); border-bottom: 1px solid var(--line-dark); padding: 8px 12px 6px; white-space: nowrap;
}
td { border-bottom: 1px solid var(--line); padding: 10px 12px; vertical-align: top; }

/* Angka penting */
.stats { display: flex; gap: 36px; flex-wrap: wrap; margin: 4px 0 26px; }
.stat { font-size: 32px; font-weight: 700; line-height: 1; }
.stat-label {
  font-family: "Franklin Gothic Medium", "Libre Franklin", "Helvetica Neue", Arial, sans-serif;
  font-size: 11px; font-weight: 700; letter-spacing: .06em; text-transform: uppercase;
  color: var(--gray); margin-top: 7px;
}

/* Caption / catatan kecil */
.caption {
  font-family: "Franklin Gothic Medium", "Libre Franklin", "Helvetica Neue", Arial, sans-serif;
  font-size: 12.5px; color: var(--gray); line-height: 1.5;
}
ul, ol { padding-left: 22px; margin: 0 0 22px; }
li { margin-bottom: 8px; }
```

## Pola layout per jenis artifact

Semua dimulai dengan anatomi header artikel: `.kicker` (jenis dokumen, mis. "BRIEF MARKETING ORGANIK") → `h1` judul → `.deck` ringkasan 1–2 kalimat → `.byline` ("Oleh <b>Agen Marketing-Organik</b>") → `.dateline` tanggal → `.head-rule`. Setelah itu:

- **Brief marketing (`marketing-organik`)**: paragraf pembuka seperti lead berita → `.stats` (grup / pain points / ide) → h2 "Peta Pasar" + tabel (`.wide .table-wrap`) → h2 "Pain Points" + deretan `.quote` dengan `.who` → h2 "Rencana 30 Hari" + 4 `.item` (label `MINGGU 1`…) → h2 "Ide Konten" + `.item` per ide → h2 "Catatan" `.caption`.
- **Daftar komunitas (`cari-komunitas`)**: lead → `.stats` (ditemukan / joined / menunggu) → tabel komunitas → h2 "Status Join" tiga sub-daftar dengan `.item-label` (JOINED / MENUNGGU APPROVAL / JOIN MANUAL) → catatan `.caption`.
- **Ide konten (`ide-konten`)**: lead + tabel "Sumber" → tiap ide satu `.item`: `.item-label` "IDE 01 · THREADS", hook sebagai `h3` serif atau `.quote`, alasan 1 paragraf, `.src` sumber.
- **Pelajaran (`ajarin`)**: tiap post satu `.item`: `.quote` kutipan verbatim → metrik sebagai `.stats` kecil → bedahan (hook/struktur/bahasa/respons) sebagai paragraf/daftar → kalimat pelajaran di-bold → penutup h2 "Pola Umum Lintas Post".

## Aturan Artifact tool

- Set `<title>` singkat dan stabil; `favicon` satu emoji tetap per jenis dokumen (emoji favicon boleh — larangan emoji hanya untuk isi halaman).
- Konten halaman langsung (tanpa `<!DOCTYPE>`, `<html>`, `<head>`, `<body>`) sesuai kontrak Artifact tool; CSS di `<style>` inline.
- Tanpa aset eksternal (CSP ketat): font NYT (Cheltenham/Imperial/Franklin) proprietary dan tidak bisa dimuat — stack sistem di atas adalah padanan terdekatnya di semua OS.
- Jangan meniru identitas NYT: tanpa logo, tanpa nama "The New York Times", tanpa masthead — yang ditiru hanya pola tipografi & layout.
