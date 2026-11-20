# Ayo Belajar Huruf & Angka!

Game anak untuk belajar huruf besar A–Z, huruf kecil a–z, angka 0–9, dan menyusun kata (Bahasa Indonesia).
Situs statis tanpa build — langsung jalan di Vercel. Sudah berupa PWA: bisa dipasang di layar utama HP dan dimainkan tanpa internet.

## Isi folder

| File | Fungsi |
|---|---|
| `index.html` | Seluruh game (HTML + CSS + JS dalam satu file) |
| `manifest.webmanifest` | Data aplikasi (nama, ikon, warna) agar bisa "Instal aplikasi" |
| `sw.js` | Service worker: menyimpan game agar bisa dimainkan offline |
| `icons/` | Ikon aplikasi (192, 512, maskable, Apple, favicon) |
| `vercel.json` | Pengaturan Vercel (header cache service worker, manifest, keamanan) |

Tidak ada `package.json` dan tidak perlu `npm install` — Vercel otomatis menyajikannya sebagai situs statis.

## Cara 1 — Lewat GitHub (disarankan)

1. Buat repository baru di GitHub, misalnya `belajar-huruf`.
2. Upload semua isi folder ini (termasuk folder `icons`) ke repository itu.
   - Lewat web: di repository → **Add file → Upload files** → seret semua file → **Commit changes**.
   - Atau lewat terminal:
     ```bash
     git init
     git add .
     git commit -m "Game belajar huruf"
     git branch -M main
     git remote add origin https://github.com/USERNAME/belajar-huruf.git
     git push -u origin main
     ```
3. Buka https://vercel.com/new → **Import** repository `belajar-huruf`.
4. Pengaturan biarkan default:
   - Framework Preset: **Other**
   - Build Command: *(kosong)*
   - Output Directory: *(kosong)*
5. Klik **Deploy**. Selesai — alamatnya seperti `https://belajar-huruf.vercel.app`.

Setiap kali Anda push perubahan ke GitHub, Vercel otomatis memperbarui situsnya.

## Cara 2 — Lewat Vercel CLI (tanpa GitHub)

Butuh Node.js terpasang.

```bash
cd belajar-huruf
npx vercel login        # sekali saja, login akun Vercel
npx vercel --prod       # deploy; jawab pertanyaan dengan Enter (default)
```

## Coba di komputer sebelum deploy (opsional)

```bash
npx serve .
```
Lalu buka `http://localhost:3000`.

## Setelah online

- **Pasang di HP**: buka alamat Vercel di Chrome (Android) atau Safari (iPhone), lalu ketuk tombol **📲 Pasang** di menu utama
  (atau menu browser → *Instal aplikasi* / *Tambah ke Layar Utama*).
- **Suara bicara** bekerja lebih baik di sini dibanding di dalam aplikasi lain. Gunakan tombol **🔊 Tes Suara** untuk mengecek.

## Mengubah game

Edit `index.html`, lalu **naikkan versi** di baris pertama `sw.js`:

```js
const VERSION = 'belajar-huruf-v2';   // ganti v1 → v2, v3, dst.
```

Ini memastikan HP yang sudah memasang game mengambil versi terbaru.
