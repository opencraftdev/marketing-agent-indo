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

## Isi plugin

| Komponen | Fungsi |
|---|---|
| Agent `marketing-organik` | Riset browser + tulis brief |
| Skill `marketing-organik` | Pemicu: kumpulkan info produk, jalankan agen, publish artifact |

## Syarat

- Ekstensi [Claude in Chrome](https://claude.com/chrome) aktif, dan sudah login Facebook/Threads di Chrome tersebut.
- Untuk artifact: sesi Claude Code login via `/login` (plan Pro/Max/Team/Enterprise), CLI v2.1.183+. Kalau tidak, brief tetap tersedia sebagai file `.md`.

## Lisensi

MIT
