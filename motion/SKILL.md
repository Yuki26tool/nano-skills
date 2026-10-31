---
name: motion
description: Sutradara motion-graphics vertikal — tulis scene HTML+GSAP 1080x1920 yang deterministik, siap render. Aturan zona, timeline, dan teks layar.
channel: api
metadata:
  author: Jono
  version: "1"
---

# Motion Graphics

Bikin scene motion-graphics vertikal 9:16 (untuk Shorts) sebagai SATU file
`index.html` mandiri + GSAP. Render final dikerjakan Jono (pipeline
open-edit di VM) — skill ini mengurus naskah visual dan kodenya.

## Kapan dipakai

User minta scene motion graphic / diagram animasi untuk video vertikal.

## Aturan scene (wajib)

- Canvas **1080x1920**. Satu file HTML mandiri: GSAP lokal, font sistem
  saja, tanpa gambar dari internet (bentuk CSS/SVG saja).
- **Satu master timeline GSAP** yang deterministik: tanpa `Math.random()`,
  tanpa `Date.now()`. Animasi yang sama setiap diputar.
- Expose **`window.__seek(t)`** (loncat ke detik t) dan
  **`window.__duration`** (total detik). Ini kontrak dengan renderer.
- Semua kata di layar HARUS dari brief user. Jangan menambah teks sendiri.

## Zona layar (jangan langgar)

- **520px bawah**: area caption — KOSONGKAN, jangan taruh elemen penting.
- **Kanan atas (x ≥ 820, y ≤ 260)**: area logo — KOSONGKAN.
- Tidak ada elemen yang menutupi teks elemen lain.

## Struktur kerja

1. Terima brief: topik, klaim per adegan, durasi tiap adegan (dari
   voiceover), gaya visual.
2. Tulis `index.html`: satu adegan = satu segmen timeline; transisi antar
   segmen simpel (fade/slide).
3. Cek: buka di browser, jalankan `__seek()` di beberapa titik — tiap
   detik harus render benar (tidak ada elemen hilang/lompat).
4. Serahkan file + catatan durasi ke Jono untuk render final. Jangan klaim
   video jadi sebelum render + QC frame.

## Prinsip visual

- Satu ide per layar. Kalau adegan menjelaskan 3 hal, pecah jadi 3 layar.
- Gerakan punya tujuan (menunjukkan mekanisme), bukan dekorasi.
- Kontras teks: pastikan terbaca di layar HP kecil.
