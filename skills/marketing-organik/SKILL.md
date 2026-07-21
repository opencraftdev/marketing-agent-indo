---
name: marketing-organik
description: Riset pasar organik + brief marketing untuk produk user. Menjalankan agen marketing-organik yang riset grup Facebook dan Threads via Claude Browser (browser bawaan Claude Desktop), lalu menghasilkan brief langkah organik agar produk naik. Gunakan saat user bilang "marketing organik", "riset pasar", "susah marketing produk", "cari pasar di Facebook/Threads", atau "buatkan brief marketing".
---

# Marketing Organik

Skill ini mendelegasikan riset ke agen `marketing-organik`.

## Langkah

1. Kumpulkan dari user (tanya kalau belum disebut): **nama produk, fungsinya, target pembeli, kisaran harga**. Kalau user sudah menyebut semuanya, jangan tanya ulang.
2. Jalankan Agent tool dengan `subagent_type: "marketing-organik"`. Masukkan semua info produk ke dalam prompt agen, plus path repo ini supaya brief ditulis ke folder `briefs/`.
3. Agen akan riset grup Facebook & Threads lewat Claude Browser (browser bawaan Claude Desktop — bukan Chrome user) dan menulis brief ke `briefs/brief-<produk>-<tanggal>.md`.
4. Setelah agen selesai, **publikasikan file brief itu sebagai artifact Claude** (halaman interaktif di claude.ai) dengan judul "Brief Marketing Organik — <Produk>". **Sebelum menulis HTML, baca `${CLAUDE_PLUGIN_ROOT}/artifact-style.md`** dan ikuti design system-nya: gaya koran ala artikel NYT — SELALU terang (putih polos, jangan dark mode), kolom teks sempit 600px, headline serif Georgia besar & tebal, deck abu, byline sans kecil, item dipisah garis tipis. Layout mengikuti pola "Brief marketing" di panduan itu: lead → angka penting → tabel peta pasar → kutipan pain-point → rencana 30 hari & ide sebagai item bergaris. (Kalau file panduan tidak ketemu, tetap pakai prinsipnya: putih flat, serif Georgia 18px untuk headline+body, sans Franklin/Arial kecil untuk label, hitam-abu tanpa warna.)
5. Sampaikan ke user: URL artifact + lokasi file brief + ringkasan temuan utama + 3 aksi pertama yang harus dilakukan minggu ini. Bahasa Indonesia. Kalau publish artifact gagal (belum /login, plan tidak mendukung, atau fitur nonaktif), sampaikan alasannya dan berikan file .md saja.

## Catatan

- Riset bersifat read-only: agen tidak akan posting, komen, atau join grup atas nama user.
- Kalau Facebook/Threads minta login, minta user login manual dulu di panel Claude Browser (sesi loginnya terpisah dari Chrome) lalu jalankan ulang.
