---
name: coding
description: Debug dan kerjakan masalah teknis secara sistematis — investigasi akar masalah dulu sebelum usul perbaikan, dan verifikasi setiap klaim dengan bukti segar, bukan tebakan.
channel: api
metadata:
  author: Jono
  version: "1"
---

# Coding & Debugging Sistematis

Dipakai saat: kode error, aplikasi crash, perintah gagal, perilaku aneh, atau
tugas teknis apa pun yang "harusnya jalan tapi tidak".

## Hukum Besi

```
JANGAN USUL PERBAIKAN SEBELUM AKAR MASALAH DITEMUKAN.
JANGAN KLAIM SELESAI TANPA VERIFIKASI SEGAR.
```

Perbaikan atas gejala tanpa tahu penyebab = gagal. Klaim "beres" tanpa bukti
= tebakan.

## Fase 1: Investigasi akar masalah

SEBELUM menyentuh apa pun:

1. **Baca pesan error sampai habis.** Catat kode, baris, komponen yang
   melaporkan. Jangan lompat melewati error.
2. **Reproduksi.** Bisa dipicu konsisten? Langkah pastinya apa? Kalau tidak
   bisa direproduksi, kumpulkan data dulu — jangan menebak.
3. **Cek perubahan terakhir.** Apa yang berubah sebelum rusak? File diedit?
   Paket diinstall? HP direstart?
4. **Uji per lapisan.** Untuk sistem berlapis (aplikasi → shell → jaringan),
   cek tiap batas: apa masuk vs apa keluar. Temukan DI MANA rusaknya dulu,
   baru pikirkan kenapa.
5. **Lacak ke sumbernya.** Perbaiki di sumber masalah, bukan di gejalanya.

## Fase 2: Satu hipotesis, satu tes

1. Rumuskan SATU hipotesis: "Saya kira X penyebabnya karena Y."
2. Tes dengan perubahan terkecil, satu variabel dalam satu waktu.
3. Berhasil → lanjut. Gagal → hipotesis BARU, jangan menumpuk perbaikan di
   atas yang gagal.
4. Kalau tidak tahu, katakan tidak tahu. Jangan pura-pura.

## Fase 3: Verifikasi sebelum klaim selesai

Sebelum bilang "beres":

1. **IDENTIFIKASI:** cek apa yang membuktikan klaim ini? (contoh: perintah
   jalan tanpa error, file muncul di `ls`, aplikasi terbuka)
2. **JALANKAN:** ceknya dieksekusi sekarang, bukan dari ingatan ("tadi kan
   udah...").
3. **BACA:** seluruh output + kode keluar.
4. **BARU KLAIM:** sertakan buktinya.

## Tanda bahaya — berhenti, kembali ke Fase 1

- "Coba ganti X dulu, lihat nanti"
- "Kayaknya sih X, benerin aja"
- Usul solusi sebelum kumpulkan bukti
- Sudah 3x coba gagal → STOP. Pola gagal berulang = diagnosis salah.
  Diskusikan dengan user sebelum coba lagi.
- Kata "harusnya", "kayaknya", "probably" = tebakan, bukan verifikasi.
