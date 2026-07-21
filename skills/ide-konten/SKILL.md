---
name: ide-konten
description: Bikin ide konten (Threads/X/Facebook) dari link yang user kasih — link metrik/insight dan link hasil riset sendiri (post, thread, grup FB). Menjalankan agen ide-konten yang mengunjungi tiap link via Claude Browser (browser bawaan Claude Desktop), mengutip temuan sebagai bukti, lalu menghasilkan daftar ide konten (BUKAN brief lengkap, bukan rencana posting) sebagai artifact Claude. User yang posting sendiri. Gunakan saat user bilang "kasih ide konten", "bikinin ide konten dari link ini", "dari riset aku ini gimana", "lihat metrik ini kasih ide", atau kasih link dan minta ide konten.
---

# Ide Konten dari Link

Skill ini mendelegasikan ke agen `ide-konten`. Beda dengan skill `marketing-organik`: skill ini TIDAK riset mandiri (agen tidak cari grup/keyword sendiri) — semua sumber datang dari link yang user kasih. Outputnya juga cuma ide konten, bukan brief 30 hari.

## Langkah

1. **Cek `brands/` dulu**: kalau ada profil persona (`brands/<slug>/persona.md`) yang cocok dengan brand/akun user, baca dan sertakan isinya ke prompt agen — hook & bahasa WAJIB mengikuti profil itu (persona kata ganti, kata terlarang, contoh gaya asli). Kalau belum ada profil, tawarkan singkat jalankan skill `audit-persona` dulu (tidak blocking — user boleh skip).
2. Kumpulkan dari user: **daftar link** (link metrik/insight, dan/atau link hasil riset sendiri — post FB, thread Threads, tweet X, dll). Kalau user belum kasih link sama sekali, minta dulu — skill ini tidak jalan tanpa link. Info produk (nama, target, harga) opsional, tanya singkat kalau relevan tapi jangan blocking.
3. Jalankan Agent tool dengan `subagent_type: "ide-konten"`. Masukkan semua link + info produk (kalau ada) + isi profil persona (kalau ada) + path repo ini ke prompt agen, supaya file ditulis ke `briefs/`.
4. Agen akan buka tiap link lewat Claude Browser (browser bawaan Claude Desktop), baca isinya, kutip metrik/temuan penting sebagai bukti, lalu tulis daftar ide ke `briefs/ide-konten-<produk>-<tanggal>.md`.
5. Setelah agen selesai, **publikasikan sebagai artifact Claude**: baca file markdown ide. **Sebelum menulis HTML, baca `${CLAUDE_PLUGIN_ROOT}/artifact-style.md`** dan ikuti design system-nya: gaya koran ala artikel NYT — SELALU terang (putih polos, jangan dark mode), kolom teks sempit 600px, headline serif Georgia besar & tebal, deck abu, byline sans kecil, item dipisah garis tipis. Layout mengikuti pola "Ide konten" di panduan itu: tiap ide satu item bergaris — label kecil "IDE 01 · THREADS", hook sebagai kalimat serif menonjol, alasan (dikaitkan ke temuan/kutipan sumbernya), dan sumbernya (link asal). (Kalau file panduan tidak ketemu, tetap pakai prinsipnya: putih flat, serif Georgia 18px untuk headline+body, sans Franklin/Arial kecil untuk label, hitam-abu tanpa warna.)
6. Sampaikan ke user: URL artifact + lokasi file + jumlah ide yang dihasilkan. Ingatkan: ini ide doang, user yang posting. Bahasa Indonesia. Kalau publish artifact gagal, kasih file .md saja.

## Catatan

- Read-only: agen tidak posting, komen, like, atau join apa pun — cuma baca.
- Kalau ada link yang minta login atau keblokir, agen catat dan lanjut ke link berikutnya.
- Output HANYA ide konten — bukan rencana 30 hari, bukan peta pasar (itu tugas skill `marketing-organik`).
