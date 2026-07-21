---
name: cari-komunitas
description: Cari komunitas (grup Facebook) tempat target pasar produk user berkumpul. Menjalankan agen cari-komunitas yang mencari grup FB via Claude Browser (browser bawaan Claude Desktop) berdasarkan produk (deskripsi atau link), menilai kelayakan tiap grup (member, aktivitas, boleh promosi atau tidak), auto-join grup rekomendasi (maks 5 per run), lalu menghasilkan daftar komunitas + status join sebagai artifact Claude — BUKAN brief 30 hari, bukan ide konten. Gunakan saat user bilang "cari komunitas", "cari grup FB", "di mana pasar produkku ngumpul", "komunitas buat jualan produk ini".
---

# Cari Komunitas Facebook

Skill ini mendelegasikan ke agen `cari-komunitas`. Beda dengan skill `marketing-organik`: skill ini HANYA mencari komunitas Facebook dan menilai kelayakannya — tanpa brief 30 hari, tanpa peta Threads, tanpa ide konten. Lebih ringan dan cepat.

## Langkah

1. Tanya dulu ke user: **produk apa yang mau dijual/dipasarkan?** Terima dua bentuk: **deskripsi** (nama, fungsi, target pembeli, harga) atau **link produk** (marketplace, landing page, post sosmed). Kalau user sudah menyebut di pesannya, jangan tanya ulang. Ingatkan singkat: pastikan sudah login Facebook di panel Claude Browser (browser bawaan Claude Desktop — sesi loginnya terpisah dari Chrome) — kalau belum, agen akan berhenti dan minta login manual.
2. Jalankan Agent tool dengan `subagent_type: "cari-komunitas"`. Masukkan deskripsi/link produk ke prompt agen, plus path repo ini supaya hasil ditulis ke folder `briefs/`.
3. Agen akan cek login FB, cari grup dengan beberapa kata kunci via Claude Browser, nilai tiap grup (member, aktivitas, aturan promosi), **auto-join maksimal 5 grup prioritas** (sisanya masuk daftar join manual), lalu tulis daftar ke `briefs/komunitas-<produk>-<tanggal>.md`.
4. Setelah agen selesai, **publikasikan sebagai artifact Claude** dengan judul "Komunitas Facebook — <Produk>". **Sebelum menulis HTML, baca `${CLAUDE_PLUGIN_ROOT}/artifact-style.md`** dan ikuti design system-nya: gaya koran ala artikel NYT — SELALU terang (putih polos, jangan dark mode), kolom teks sempit 600px, headline serif Georgia besar & tebal, deck abu, byline sans kecil, item dipisah garis tipis. Layout mengikuti pola "Daftar komunitas" di panduan itu: lead + angka penting (grup ditemukan/joined/menunggu) → tabel komunitas (nama, anggota, aktivitas, aturan promosi, link, status join) → bagian status join (joined / menunggu approval / perlu join manual). (Kalau file panduan tidak ketemu, tetap pakai prinsipnya: putih flat, serif Georgia 18px untuk headline+body, sans Franklin/Arial kecil untuk label, hitam-abu tanpa warna.)
5. Sampaikan ke user: URL artifact + lokasi file + grup mana yang sudah di-join, mana yang menunggu approval, dan mana yang perlu di-join manual (dan kenapa). Bahasa Indonesia. Kalau publish artifact gagal (belum /login, plan tidak mendukung), kasih file .md saja. Kalau agen berhenti karena FB belum login, sampaikan itu dan minta user login di panel Claude Browser lalu jalankan ulang.

## Catatan

- Agen **join grup atas nama akun user** (maks 5 per run untuk hindari deteksi spam FB). Selain join: tidak posting, komen, atau like.
- Grup dengan pertanyaan screening yang butuh info pribadi tidak di-join otomatis — masuk daftar join manual.
- Output HANYA daftar komunitas + status join — brief lengkap itu tugas skill `marketing-organik`, ide konten itu tugas skill `ide-konten`.
