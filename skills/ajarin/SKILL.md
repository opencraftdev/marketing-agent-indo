---
name: ajarin
description: Belajar dari postingan orang lain yang rame — user kasih link post/akun Threads (atau X/FB) yang banyak views, agen buka via Claude Browser (browser bawaan Claude Desktop) lalu bedah KENAPA post itu perform: hook-nya, struktur, bahasa, cara audiens merespons. Hasil pelajaran disimpan ke brands/research/ dan dipresentasikan sebagai artifact. Gunakan saat user bilang "ajarin", "ajarin dari akun ini", "kenapa post ini rame", "bedah post si A", "pelajarin akun ini", atau kasih link post viral dan minta dipelajari.
---

# Ajarin — Bedah Post yang Rame

Skill ini kebalikan dari `audit-persona`: bukan mempelajari gaya user sendiri, tapi **mempelajari post orang lain yang terbukti dapet views** — lalu menarik teori yang bisa dipakai ulang. Output-nya pelajaran (bukan ide konten, bukan profil brand): "post si A rame karena X, ini polanya, ini yang bisa kamu tiru dan ini yang jangan".

## Langkah

1. **Minta link dari user** — skill ini tidak jalan tanpa link. Yang diterima: link post spesifik (yang keliatan rame), atau link profil akun (agen ambil beberapa post teratasnya). Boleh campur, boleh banyak. Tanya singkat juga: user pengen belajar buat brand yang mana (biar pelajaran bisa dikaitkan ke profil di `brands/` kalau ada — tidak blocking).

2. **Jalankan Agent tool** `subagent_type: "ajarin"` dengan semua link + path repo. Agen buka tiap link via Claude Browser (browser bawaan Claude Desktop), baca post + metrik (views/like/reply/repost) + reply-reply teratas, kutip verbatim sebagai bukti, lalu bedah tiap post: hook masuk pola apa, struktur & bahasa gimana, audiens nyantol di bagian mana (keliatan dari reply).

3. Agen tulis hasil ke `brands/research/ajarin-<slug>-<YYYY-MM-DD>.md` (slug = nama akun/topik yang dipelajari).

4. **Publikasikan sebagai artifact Claude**: baca file markdown hasil agen. **Sebelum menulis HTML, baca `${CLAUDE_PLUGIN_ROOT}/artifact-style.md`** dan ikuti design system-nya: gaya koran ala artikel NYT — SELALU terang (putih polos, jangan dark mode), kolom teks sempit 600px, headline serif Georgia besar & tebal, deck abu, byline sans kecil, item dipisah garis tipis. Layout mengikuti pola "Pelajaran" di panduan itu: per post yang dibedah satu item bergaris — kutipan post verbatim sebagai pull quote + metrik sebagai angka besar → bedahan (hook, struktur, bahasa, respons audiens) → "pelajaran yang bisa dipakai" — lalu satu bagian penutup **pola umum lintas post** (teori yang berulang di semua sampel). (Kalau file panduan tidak ketemu, tetap pakai prinsipnya: putih flat, serif Georgia 18px untuk headline+body, sans Franklin/Arial kecil untuk label, hitam-abu tanpa warna.)

5. Sampaikan ke user: URL artifact + lokasi file + berapa post yang dibedah. Ingatkan: pelajaran ini makin tajam kalau digabung dengan `audit-persona` — profil brand user yang sudah ada bisa di-update pakai temuan ini (misal tingkat keberanian hook atau format yang mau ditiru), tinggal jalankan `audit-persona` mode update.

## Catatan

- Read-only: agen tidak posting, komen, like, follow, atau join apa pun.
- Yang dipelajari adalah **pola & teori** — bukan nyontek kalimat. Pelajaran harus berbentuk "kenapa ini kerja", bukan "copy kalimat ini".
- Kalau link minta login / keblokir, agen catat dan lanjut ke link berikutnya.
- Beda skill: `ajarin` = belajar dari orang lain; `audit-persona` = memotret diri sendiri; `ide-konten` = bikin ide dari link metrik/riset. Ketiganya nyimpen ke tempat beda dan saling melengkapi.
