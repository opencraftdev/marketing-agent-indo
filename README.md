# marketing-agent-indo

Agen Claude Code untuk riset pasar organik & brief marketing berbahasa Indonesia.

## Isi

| Komponen | Fungsi |
|---|---|
| Agent `marketing-organik` (`.claude/agents/`) | Riset grup Facebook & Threads via Claude in Chrome, petakan di mana target pasar berkumpul dan apa keluhannya, lalu tulis brief marketing organik ke folder `briefs/` |
| Skill `marketing-organik` (`.claude/skills/`) | Pemicu: kumpulkan info produk dari user lalu jalankan agennya |

## Cara pakai

Buka Claude Code di dalam repo ini, lalu minta secara natural:

> "Saya susah marketing produk kopi literan saya, target anak kantoran Jakarta, harga 45rb. Tolong riset dan buatkan brief."

Yang terjadi:

1. Agen buka Chrome (browser "PC Gaming Raka"), riset grup Facebook & Threads dengan beberapa kata kunci.
2. Hasilnya ditulis ke `briefs/brief-<produk>-<tanggal>.md`: peta pasar, pain points + kutipan asli, rencana aksi 30 hari, dan 5–10 ide konten agar produk naik.
3. Brief dipublikasikan sebagai **artifact Claude** — halaman interaktif di claude.ai yang bisa dibuka dari browser mana pun dan di-share via link.
4. Riset read-only — tidak posting/komen/join grup apa pun.

**Syarat**: ekstensi Claude in Chrome aktif di browser dan sudah login Facebook/Threads. Untuk artifact: sesi Claude Code login via `/login` (plan Pro/Max/Team/Enterprise), CLI v2.1.183+.
