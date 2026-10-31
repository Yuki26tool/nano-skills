---
name: osint
description: Open-source intelligence — gali web & YouTube, verifikasi klaim ke sumber independen, serahkan intel ringkas bukan dump mentah.
channel: api
metadata:
  author: Jono
  version: "1"
---

# Riset

Dipakai saat user minta: cari tahu tentang X, bandingkan opsi, kumpulkan
bahan naskah, atau cek apakah klaim itu benar.

## Prinsip: gratis dulu

1. **Web search** untuk menemukan artikel, dokumentasi resmi, dan diskusi.
   Dahulukan sumber primer (dokumen resmi, jurnal, repo asli) di atas
   artikel yang mengutip artikel lain.
2. **YouTube untuk sudut pandang praktisi.** Cari video relevan, lalu baca
   **transkrip**-nya — jangan simpulkan isi video dari judul/thumbnail.
   Ambil subtitle tanpa unduh video:
   `yt-dlp --skip-download --write-auto-subs --sub-langs id,en <URL>`
   (bersihkan penanda waktu jadi teks biasa sebelum dipakai). Kalau video
   tidak punya subtitle, laporkan — jangan mengarang isinya.
3. Hanya konten **publik**. Jangan akses video private/unlisted orang lain.

## Verifikasi klaim

- Pernyataan seorang kreator/blogger BUKAN fakta — itu klaim yang butuh
  sumber independen.
- Untuk tiap klaim penting: cari minimal 2 sumber yang saling independen.
  Kalau tidak ketemu, tandai "belum terverifikasi" — jangan dipoles jadi
  fakta.
- Jangan mengarang angka, tanggal, nama, atau kutipan. Kalau sumber tidak
  ada, katakan tidak ada.

## Cara menyerahkan hasil

Ringkasan, BUKAN dump mentah (dump membakar token tanpa menambah keputusan):

- Per sumber: judul, URL, 2–4 poin yang relevan dengan pertanyaan.
- Kutipan pendek bila perlu, dengan atribusi kreatornya.
- Bagian "yang belum jelas": klaim yang tidak terverifikasi + apa yang
  masih perlu dicari.
- Kalau tidak ada sumber relevan: katakan terus terang, jangan paksakan
  hasil dari sumber yang tidak nyambung.

Transkrip dipakai sebagai bahan riset dan kutipan singkat, bukan untuk
diterbitkan ulang mentah-mentah sebagai konten sendiri.
