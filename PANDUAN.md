# Klyn — panduan rilis gratis (web + APK Android)

Total biaya: Rp0. Tidak perlu Node.js, Android Studio, atau terminal.

Isi folder ini:
- `index.html` — aplikasi Klyn lengkap (sudah jadi PWA)
- `manifest.webmanifest` — nama, ikon, dan warna aplikasi saat dipasang di HP
- `sw.js` — service worker, supaya Klyn bisa dipasang dan tetap jalan offline
- `icons/` — ikon aplikasi (Lolo di latar teal)
- `.nojekyll` — file kosong, wajib ikut diunggah (file tersembunyi, pastikan tidak hilang saat ekstrak zip)

---

## Langkah 1 — Terbitkan versi web di GitHub Pages (±15 menit)

1. Buat akun di github.com kalau belum punya.
2. Klik **New repository**. Nama: `klyn`. Pilih **Public** (GitHub Pages gratis hanya untuk repo publik). Centang **Add a README file**, lalu **Create repository**.
3. Di halaman repo, klik **Add file → Upload files**. Seret SEMUA isi folder ini (termasuk folder `icons` dan file `.nojekyll`), lalu klik **Commit changes**.
   - Kalau `.nojekyll` tidak ikut karena tersembunyi: klik **Add file → Create new file**, beri nama `.nojekyll`, biarkan kosong, lalu commit.
4. Buka **Settings → Pages**. Di **Build and deployment**, pilih **Source: Deploy from a branch**, **Branch: main**, folder **/ (root)**, lalu **Save**.
5. Tunggu 1–3 menit. Link Klyn akan muncul di halaman yang sama, formatnya: `https://USERNAME.github.io/klyn/`

## Langkah 2 — Uji di HP Android (±10 menit)

1. Buka link tadi di **Chrome** di HP.
2. Menu titik tiga → **Tambahkan ke layar utama** / **Instal aplikasi**.
3. Buka Klyn dari layar utama. Coba:
   - Onboarding sampai selesai, izinkan notifikasi.
   - Satu sesi penuh (mode demo: 25 menit selesai dalam 25 detik).
   - Keluar ke aplikasi lain lalu kembali dalam 5 detik → sesi lanjut.
   - Keluar lebih dari 10 detik → sesi gagal, Lolo sedih.
   - Matikan internet, tutup, buka lagi → Klyn tetap jalan.

## Langkah 3 — Buat APK Android dengan PWABuilder (±15 menit)

1. Buka **pwabuilder.com**, tempel link Klyn dari Langkah 1, klik **Start**.
2. Setelah analisis selesai, klik **Package for stores**, lalu pilih **Android**.
3. Isi Package ID, misalnya `io.github.USERNAME.klyn`. Pengaturan lain boleh dibiarkan default. Klik **Generate** lalu unduh file zip-nya.
4. Di dalam zip ada file `.apk` (untuk dipasang langsung) dan `.aab` (khusus Play Store, tidak perlu). **Simpan juga file signing key dan catatan password dari zip itu** di tempat aman.
5. Kirim `.apk` ke HP, buka, lalu izinkan **Instal aplikasi tidak dikenal** saat diminta.

Catatan: di APK hasil PWABuilder, bagian atas layar mungkin menampilkan bilah alamat kecil. Itu normal jika file verifikasi domain (`assetlinks.json`) tidak dipasang. Untuk portfolio, ini boleh dibiarkan.

## Langkah 4 — Bagikan APK lewat GitHub Releases (±5 menit)

1. Di repo `klyn`, klik **Releases → Create a new release**.
2. Tag: `v1.0`. Judul: `Klyn v1.0`. Seret file `.apk` ke kotak lampiran, lalu **Publish release**.
3. Link unduhan APK sekarang bisa ditaruh di portfolio.

---

## Batasan yang perlu diketahui

- **Menekan tombol power saat sesi = dianggap keluar app.** Versi web tidak bisa membedakan layar dikunci dengan pindah aplikasi. Sebagai gantinya, Klyn menjaga layar tetap menyala selama sesi, jadi layar tidak mati sendiri.
- **Notifikasi "Lolo memanggilmu"** hanya muncul jika izin notifikasi diberikan dan Klyn sudah dipasang dari layar utama.
- **Data tersimpan di HP/browser masing-masing.** Menghapus data Chrome atau uninstall akan menghapus progres.
- **Mode demo aktif secara default** supaya pengunjung portfolio bisa menyelesaikan sesi dengan cepat. Bisa dimatikan di Profil.

## Memperbarui Klyn nanti

Ubah file di repo (atau unggah ulang `index.html`), tunggu 1–3 menit. Kalau mengubah file selain `index.html`, naikkan versi di baris pertama `sw.js` (`klyn-v1` → `klyn-v2`) supaya HP mengambil versi terbaru. APK dari PWABuilder ikut ter-update otomatis karena isinya memuat link web yang sama.
