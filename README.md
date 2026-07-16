# marketing-agent-indo

Plugin Claude Code untuk **riset pasar organik & brief marketing berbahasa Indonesia**.

Susah marketing produk? Plugin ini menjalankan agen yang riset grup Facebook & Threads lewat [Claude in Chrome](https://claude.com/chrome), memetakan di mana target pasarmu berkumpul dan apa keluhan mereka, lalu menghasilkan brief marketing organik yang bisa langsung dieksekusi — dipublikasikan sebagai artifact Claude (halaman interaktif yang bisa di-share via link).

## Instalasi

Di Claude Code, jalankan:

```
/plugin marketplace add opencraftdev/marketing-agent-indo
/plugin install marketing-organik@marketing-agent-indo
```

## Cara pakai

Minta secara natural, misalnya:

> "Saya susah marketing produk kopi literan saya, target anak kantoran Jakarta, harga 45rb. Tolong riset dan buatkan brief."

Yang terjadi:

1. Agen `marketing-organik` buka Chrome kamu, riset grup Facebook & Threads dengan beberapa kata kunci (kategori produk, masalah yang diselesaikan, istilah target pasar).
2. Hasilnya ditulis ke `briefs/brief-<produk>-<tanggal>.md`: peta pasar (grup mana yang ramai), pain points + kutipan asli calon pembeli, **rencana aksi 30 hari**, dan **5–10 ide konten agar produk naik**.
3. Brief dipublikasikan sebagai **artifact Claude** — halaman interaktif di claude.ai, bisa dibuka dari mana saja dan di-share.
4. Riset **read-only** — agen tidak posting, komen, atau join grup atas nama kamu.

Selain itu ada skill `ide-konten`: kasih link (metrik/insight atau hasil riset kamu sendiri di FB/Threads/X), agen buka tiap link, ambil screenshot sebagai bukti, dan kasih **daftar ide konten** untuk Threads/X/Facebook — bukan brief lengkap, kamu yang posting sendiri.

Ada juga skill `cari-komunitas`: kasih produk kamu (deskripsi atau link), agen cari **grup Facebook** tempat target pasarmu ngumpul, nilai tiap grup (anggota, aktivitas, boleh promosi atau tidak), **auto-join grup rekomendasi** (maks 5 per run, pakai akun FB kamu), lalu kasih daftar komunitas + status join. Lebih ringan dari `marketing-organik` — tanpa brief 30 hari. Pastikan sudah login Facebook di Chrome-nya.

## Isi plugin

| Komponen | Fungsi |
|---|---|
| Agent `marketing-organik` | Riset browser mandiri (cari grup/keyword sendiri) + tulis brief 30 hari |
| Skill `marketing-organik` | Pemicu: kumpulkan info produk, jalankan agen, publish artifact |
| Agent `ide-konten` | Kunjungi link yang dikasih user + screenshot + tulis daftar ide konten |
| Skill `ide-konten` | Pemicu: kumpulkan link dari user, jalankan agen, publish artifact |
| Agent `cari-komunitas` | Cari grup FB dari info produk + nilai kelayakan + auto-join maks 5 grup |
| Skill `cari-komunitas` | Pemicu: tanya produk (deskripsi/link), jalankan agen, publish artifact |

## Syarat

- Ekstensi [Claude in Chrome](https://claude.com/chrome) aktif, dan sudah login Facebook/Threads di Chrome tersebut.
- Untuk artifact: sesi Claude Code login via `/login` (plan Pro/Max/Team/Enterprise), CLI v2.1.183+. Kalau tidak, brief tetap tersedia sebagai file `.md`.

## Lisensi

MIT
