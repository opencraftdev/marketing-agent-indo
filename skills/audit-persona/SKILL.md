---
name: audit-persona
description: Audit persona brand/user sebelum bikin konten — interview mendalam (tujuan, target audiens, gaya bahasa, batasan) plus analisis gaya bahasa dari link post terakhir user via Claude in Chrome. Hasilnya profil brand di folder brands/ yang dipakai skill lain (ide-konten) biar konten konsisten sama suara user. Gunakan saat user bilang "audit persona", "kenalan dulu sama brand aku", "pelajari gaya bahasa aku", "bikin profil brand", atau saat mau bikin konten tapi belum ada profil di brands/.
---

# Audit Persona Brand

Skill ini bikin **profil brand** lewat interview + analisis post asli user, lalu simpan ke `brands/<slug>/persona.md`. Profil ini jadi sumber kebenaran untuk skill lain: `ide-konten` wajib baca profil ini (kalau ada) supaya hook & bahasa yang dihasilkan cocok sama suara user — bukan bahasa marketing generik.

## Langkah

1. **Cek dulu `brands/`**: kalau sudah ada profil untuk brand yang dimaksud, tanya user mau update atau bikin baru. Jangan menimpa tanpa konfirmasi.

2. **Interview ronde 1 — identitas & tujuan** (pakai AskUserQuestion, sekali panggil maks 4 pertanyaan):
   - Nama brand/akun + apa yang dijual/ditawarkan (produk, jasa, atau personal brand)?
   - Tujuan utama konten: bangun audiens / cari klien / jualan langsung / dokumentasi belajar?
   - Siapa target pembacanya (sespesifik mungkin: UMKM? developer? ibu rumah tangga?)
   - Platform utama & frekuensi posting realistis?

3. **Interview ronde 2 — gaya bahasa & batasan**:
   - Persona bahasa: "gue/lu" santai, "aku/kamu" netral, atau "saya/Anda" formal? (WAJIB dikunci satu, jangan campur)
   - Seberapa berani: main aman & ramah, atau boleh hot take / kontradiksi yang mancing diskusi?
   - Kata/topik yang DILARANG (misal: jargon kantoran, janji berlebihan, topik sensitif)?
   - Ada idola gaya konten? (akun yang user pengen "mirip kayak dia")

4. **Minta link post terakhir** (opsional tapi sangat dianjurkan): minta 1–5 link post asli user (Threads/X/FB/IG). Kalau user kasih, jalankan Agent tool `subagent_type: "audit-persona"` dengan semua link + path repo — agen buka tiap link via Claude in Chrome, baca teksnya, dan ekstrak pola bahasa asli user (kata khas, panjang kalimat, kebiasaan emoji/slang, struktur post). Kalau user tidak punya post sama sekali, lewati — tandai profil sebagai "belum ada sampel tulisan".

5. **Tulis profil** ke `brands/<slug>/persona.md` (slug = nama brand kebab-case). Struktur:

   ```markdown
   # Persona — <Nama Brand>
   Terakhir diaudit: <tanggal>

   ## Identitas
   (apa brand ini, apa yang ditawarkan, tujuan konten)

   ## Target audiens
   (siapa, apa masalah mereka, di mana mereka nongkrong)

   ## Suara & gaya bahasa
   - Persona: gue/lu | aku/kamu | saya/Anda
   - Nada: (santai/berani/hangat/teknis — dari jawaban interview)
   - Kata & kebiasaan khas: (dari analisis post asli — kata favorit, emoji, panjang post)
   - DILARANG: (kata/gaya/topik terlarang)

   ## Contoh gaya asli
   (kutip 2–3 potongan post asli user apa adanya — ini kalibrasi paling penting)

   ## Arah konten
   (idola gaya, tingkat keberanian hook, platform & frekuensi)
   ```

6. **Konfirmasi ke user**: tunjukkan ringkasan profil, tanya ada yang mau dikoreksi. Simpan revisi kalau ada. Kasih tahu: mulai sekarang `ide-konten` otomatis pakai profil ini.

## Catatan

- Interview jangan robotik — kalau jawaban user sudah menjawab pertanyaan berikutnya, jangan tanya ulang.
- Agen link read-only: tidak posting/komen/like, cuma baca & screenshot.
- Satu brand = satu folder di `brands/`. User boleh punya banyak brand.
- Profil boleh di-update kapan pun dengan menjalankan skill ini lagi (mode update: cuma tanya yang berubah).
- Saat update, cek juga `brands/research/` (hasil skill `ajarin`): kalau ada pelajaran dari post orang lain yang relevan, tawarkan ke user untuk dimasukkan ke bagian "Arah konten" profil (misal pola hook yang mau ditiru).
