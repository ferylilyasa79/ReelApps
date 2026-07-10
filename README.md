# Reel — Panduan Install sebagai Aplikasi (PWA)

Folder ini berisi aplikasi Reel yang sudah diubah menjadi **Progressive Web App (PWA)** —
artinya bisa di-*install* jadi aplikasi mandiri di desktop maupun HP, dengan ikon sendiri,
dan bisa dipakai offline (setelah dibuka minimal sekali).

## Kenapa harus di-hosting, tidak cukup buka file langsung?

Browser membatasi fitur "Install App" dan mode offline (service worker) supaya **tidak bisa**
diaktifkan hanya dengan membuka file HTML langsung dari komputer (`file://…`) — ini aturan
keamanan semua browser, bukan batasan dari aplikasi ini. Aplikasi harus diakses lewat alamat
`https://` (atau `http://localhost` saat development) agar fitur install-nya aktif penuh.

Kabar baiknya, meng-hosting file statis seperti ini **gratis dan cepat**. Beberapa pilihan:

### Opsi 1 — GitHub Pages (gratis, permanen)
1. Buat repository baru di GitHub, upload semua isi folder ini (`index.html`, `manifest.webmanifest`, `service-worker.js`, folder `icons/`).
2. Buka *Settings → Pages*, pilih branch `main` dan folder root, simpan.
3. Setelah beberapa menit, aplikasi bisa diakses di `https://namakamu.github.io/nama-repo/`.

### Opsi 2 — Netlify / Vercel / Cloudflare Pages (gratis, drag-and-drop)
1. Buat akun gratis di netlify.com (atau vercel.com / pages.cloudflare.com).
2. Pilih "Deploy manually" / "Import project", lalu seret seluruh folder ini ke area upload.
3. Dalam beberapa detik akan muncul alamat `https://....netlify.app` yang bisa langsung dipakai.

### Opsi 3 — Coba dulu di komputer sendiri (localhost)
Kalau sudah punya Python terpasang, buka terminal di folder ini lalu jalankan:
```
python3 -m http.server 8080
```
Lalu buka `http://localhost:8080` di browser Chrome/Edge.

## Cara install setelah aplikasi online

- **Windows / Mac / Linux (Chrome atau Edge):** buka alamatnya, klik ikon "Install" di pojok
  kanan address bar (atau tombol **Install** di pojok kanan atas aplikasi). Aplikasi akan
  terbuka di jendela sendiri tanpa bar alamat browser, dan muncul di Start Menu / Dock /
  Applications seperti aplikasi biasa.
- **Android (Chrome):** buka alamatnya, akan muncul banner "Tambahkan ke layar utama" secara
  otomatis, atau tap tombol **Install** di aplikasi / menu titik tiga Chrome → "Install app".
- **iPhone / iPad (Safari):** buka alamatnya, tap ikon Bagikan (kotak dengan panah ke atas),
  lalu pilih **"Add to Home Screen"**. iOS tidak punya tombol install otomatis seperti Android/
  Chrome, jadi ini satu-satunya cara di iOS — namun hasilnya sama: ikon aplikasi muncul di
  home screen dan terbuka tanpa bar Safari.

## Tentang fitur "Hubungkan folder otomatis"
Fitur ini memakai File System Access API, yang saat ini **hanya didukung Chrome/Edge/Brave
versi desktop**. Di Android, iOS, dan Safari, fitur ini belum tersedia di browser — gunakan
tombol "File" / "Folder" biasa untuk impor manual di platform tersebut.

## Isi folder
```
index.html              → aplikasi utama
manifest.webmanifest     → metadata PWA (nama, ikon, warna tema)
service-worker.js        → caching offline untuk app shell
icons/                   → ikon aplikasi berbagai ukuran
```
