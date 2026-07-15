---
name: marketing-organik
description: Riset pasar organik + brief marketing untuk produk user. Menjalankan agen marketing-organik yang riset grup Facebook dan Threads via Claude in Chrome, lalu menghasilkan brief langkah organik agar produk naik. Gunakan saat user bilang "marketing organik", "riset pasar", "susah marketing produk", "cari pasar di Facebook/Threads", atau "buatkan brief marketing".
---

# Marketing Organik

Skill ini mendelegasikan riset ke agen `marketing-organik`.

## Langkah

1. Kumpulkan dari user (tanya kalau belum disebut): **nama produk, fungsinya, target pembeli, kisaran harga**. Kalau user sudah menyebut semuanya, jangan tanya ulang.
2. Jalankan Agent tool dengan `subagent_type: "marketing-organik"`. Masukkan semua info produk ke dalam prompt agen, plus path repo ini supaya brief ditulis ke folder `briefs/`.
3. Agen akan riset grup Facebook & Threads lewat Claude in Chrome (browser "PC Gaming Raka") dan menulis brief ke `briefs/brief-<produk>-<tanggal>.md`.
4. Setelah agen selesai, sampaikan ke user: lokasi file brief + ringkasan temuan utama + 3 aksi pertama yang harus dilakukan minggu ini. Bahasa Indonesia.

## Catatan

- Riset bersifat read-only: agen tidak akan posting, komen, atau join grup atas nama user.
- Kalau Facebook/Threads minta login di browser user, minta user login manual dulu lalu jalankan ulang.
