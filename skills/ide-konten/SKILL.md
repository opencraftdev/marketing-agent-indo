---
name: ide-konten
description: Bikin ide konten (Threads/X/Facebook) dari link yang user kasih — link metrik/insight dan link hasil riset sendiri (post, thread, grup FB). Menjalankan agen ide-konten yang mengunjungi tiap link via Claude in Chrome, mengambil screenshot sebagai bukti, lalu menghasilkan daftar ide konten (BUKAN brief lengkap, bukan rencana posting) sebagai artifact Claude. User yang posting sendiri. Gunakan saat user bilang "kasih ide konten", "bikinin ide konten dari link ini", "dari riset aku ini gimana", "lihat metrik ini kasih ide", atau kasih link dan minta ide konten.
---

# Ide Konten dari Link

Skill ini mendelegasikan ke agen `ide-konten`. Beda dengan skill `marketing-organik`: skill ini TIDAK riset mandiri (agen tidak cari grup/keyword sendiri) — semua sumber datang dari link yang user kasih. Outputnya juga cuma ide konten, bukan brief 30 hari.

## Langkah

1. Kumpulkan dari user: **daftar link** (link metrik/insight, dan/atau link hasil riset sendiri — post FB, thread Threads, tweet X, dll). Kalau user belum kasih link sama sekali, minta dulu — skill ini tidak jalan tanpa link. Info produk (nama, target, harga) opsional, tanya singkat kalau relevan tapi jangan blocking.
2. Jalankan Agent tool dengan `subagent_type: "ide-konten"`. Masukkan semua link + info produk (kalau ada) + path repo ini ke prompt agen, supaya file & screenshot ditulis ke `briefs/`.
3. Agen akan buka tiap link lewat Claude in Chrome (browser "PC Gaming Raka"), baca isinya, ambil screenshot sebagai bukti, lalu tulis daftar ide ke `briefs/ide-konten-<produk>-<tanggal>.md` + screenshot ke `briefs/screenshots/<slug>-<tanggal>/`.
4. Setelah agen selesai, **publikasikan sebagai artifact Claude**: baca file markdown ide + tiap screenshot yang disebut di dalamnya, embed tiap screenshot sebagai data URI (base64) di HTML artifact — jangan link ke path lokal (artifact tidak bisa akses filesystem). Layout: tiap ide jadi kartu — hook/angle, platform yang cocok (Threads/X/Facebook), alasan (dikaitkan ke screenshot/sumbernya), dan sumbernya (link asal).
5. Sampaikan ke user: URL artifact + lokasi file + jumlah ide yang dihasilkan. Ingatkan: ini ide doang, user yang posting. Bahasa Indonesia. Kalau publish artifact gagal, kasih file .md + folder screenshot saja.

## Catatan

- Read-only: agen tidak posting, komen, like, atau join apa pun — cuma lihat & screenshot.
- Kalau ada link yang minta login atau keblokir, agen catat dan lanjut ke link berikutnya.
- Output HANYA ide konten — bukan rencana 30 hari, bukan peta pasar (itu tugas skill `marketing-organik`).
