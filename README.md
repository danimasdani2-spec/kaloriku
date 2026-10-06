# kaloriku

Aplikasi web penghitung kalori dari foto piring makan. Foto piring → AI menganalisis → keluar estimasi kalori, protein, karbohidrat, lemak, natrium, rincian tiap makanan, bahan utama, dan cara masak.

Bisa di-install di HP (PWA). Data tersimpan lokal di browser masing-masing.

## Fitur

- 📷 **Scan foto piring** — analisis AI otomatis (kalori + gizi lengkap)
- 🌾 **Bahan utama** — AI menandai bahan pengganti yang tidak umum (misal kue coklat pakai oat, bukan tepung terigu)
- 📝 **Keterangan manual** — tambah info sendiri di bawah foto agar analisis lebih tepat
- 🎯 **Target berat badan** — rekomendasi kalori harian otomatis (±0,5 kg/minggu)
- 📈 **Grafik** — grafik berat badan & kalori 7 hari
- 🏃 **Aktivitas** — catat olahraga (lari, sepeda, jalan, gym, dll), kalori terbakar mengurangi hitungan harian
- 💾 **Backup / import** — pindah HP via file JSON
- 🔄 **Update otomatis** — aplikasi menawarkan update sendiri saat ada versi baru
- ❤️ **Dukung** — info donasi di menu Pengaturan

## AI yang dipakai

- **Gemini** (utama) — bisa isi sampai **3 API key**, otomatis bergantian jika satu habis kuotanya / error. Jika semua gagal, dicoba ulang 3x saat server sibuk (503).
- **Groq** (cadangan) — dipakai otomatis jika semua key Gemini gagal.

API key diisi di menu Pengaturan (ikon ⋮ kanan atas) dan tersimpan **hanya di browser HP masing-masing** — tidak dikirim ke mana pun selain API resmi Google/Groq. Ada panduan langkah-demi-langkah untuk pemula di dalam aplikasi.

## Menjalankan

File statis biasa, tidak perlu build:

```bash
cd kaloriku
python -m http.server 8000
# buka http://localhost:8000 di browser
```

Untuk akses dari HP lain: gunakan `ngrok http 8000`, atau upload ke hosting (cPanel) — sudah termasuk `manifest.json` + `sw.js` agar bisa di-install sebagai PWA (butuh HTTPS).

## Struktur

| File | Fungsi |
|---|---|
| `index.html` | Seluruh aplikasi (satu file) |
| `manifest.json` | Konfigurasi PWA |
| `sw.js` | Service worker (offline + update) |
| `version.json` | Nomor versi untuk cek update otomatis |
| `icon-192.png` / `icon-512.png` | Ikon aplikasi |
| `CARA-PAKAI.txt` | Panduan pemakaian (Indonesia) |

## Lisensi

MIT — bebas dipakai, diubah, dan disebarkan.
