---
name: montase
description: Sutradara Shorts vertikal — hook 3 detik, reveal, payoff — plus resep ffmpeg buat motong, gabung, dan bakar caption langsung di HP.
channel: api
metadata:
  author: Jono
  version: "1"
---

# Video Shorts

Dua bagian: (A) naskah, (B) edit dasar di HP.

## A. Naskah: hook dulu, reveal belakangan

Format: vertikal 9:16, 18–22 detik, Bahasa Indonesia santai.

Setiap naskah punya 3 beat, urutan wajib:

1. **Hook (3 detik pertama): pertanyaan + tebakan.** Buka dengan pertanyaan
   yang bikin penonton menebak, BUKAN dengan jawaban. Contoh: "Kenapa X bisa
   Y, padahal Z?"
2. **Reveal + mekanisme.** Jawab singkat dengan mekanisme yang BISA
   divisualkan — satu klaim per adegan. Tiap klaim harus bisa ditunjukkan
   gambarnya, bukan cuma diucapkan.
3. **Payoff / ending loop.** Tutup dengan kalimat yang nyambung ke pertanyaan
   pembuka ("Jadi, masih percaya [mitos awal]?") agar penonton replay.

### Bank formula hook (rotasi, jangan monoton)

1. Myth-busting: "Selama ini kita kira [X]... ternyata [Y]!"
2. "Kukira hoax, ternyata beneran: [fakta]. Kok bisa?"
3. "Stop [kebiasaan umum]! Ini faktanya."
4. "[A] atau [B]? Jawabannya bikin kaget."
5. "Kenapa nggak ada yang bahas [X]?"
6. "Katanya [X]. Beneran?"
7. "Dulu kita percaya [X]. Sampai [fakta] kebongkar."

### Verifikasi fakta sebelum naskah dikunci

- Setiap klaim harus punya sumber yang bisa disebut. Satu klaim tanpa sumber
  = naskah belum kunci.
- Jangan mengarang angka, tahun, atau nama peneliti. Bedakan fakta vs
  analogi: analogi boleh menyederhanakan, tidak boleh mengubah mekanisme.

### Judul & hashtag

- Judul: formula myth-busting ("Selama Ini Ternyata [X]!") + " #Shorts".
- Deskripsi: 1–2 kalimat + cantumkan SUMBER FAKTA (nama publikasi/peneliti).
- Hashtag 8–10, yang paling relevan di depan.

## B. Edit dasar dengan ffmpeg di HP

Install dulu kalau belum ada: `apk add ffmpeg` (di dalam shell aplikasi).

```bash
# Potong 0:05–0:20
ffmpeg -i in.mp4 -ss 5 -to 20 -c copy out.mp4

# Resize/crop ke vertikal 1080x1920 (center-crop)
ffmpeg -i in.mp4 -vf "scale=1080:1920:force_original_aspect_ratio=increase,crop=1080:1920" -c:a copy out.mp4

# Gabung 2 klip (buat dulu list.txt berisi: file 'a.mp4' / file 'b.mp4')
ffmpeg -f concat -safe 0 -i list.txt -c copy gabung.mp4

# Bakar caption dari file .srt
ffmpeg -i in.mp4 -vf "subtitles=cap.srt:force_style='FontName=DejaVu Sans,FontSize=22,PrimaryColour=&HFFFFFF,OutlineColour=&H80000000,BorderStyle=1,Outline=2,MarginV=120'" -c:a copy out.mp4

# Cek hasil: durasi, resolusi, fps
ffprobe -v error -show_entries format=duration -show_entries stream=width,height,r_frame_rate -of default=noprint_wrappers=1 out.mp4
```

Aturan: normalisasi dulu (fps dan resolusi sama) sebelum digabung. Jangan
klaim video jadi sebelum `ffprobe` + tonton hasilnya.
