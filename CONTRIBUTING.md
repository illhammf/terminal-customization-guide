# Contributing Guide

Terima kasih telah tertarik untuk berkontribusi pada **Terminal Customization Guide**!

Proyek ini dikembangkan sebagai panduan terbuka untuk membantu pengguna mempelajari dan mengustomisasi lingkungan terminal, khususnya Windows Terminal, PowerShell, WSL Ubuntu, Zsh, Oh My Zsh, Powerlevel10k, Oh My Posh, dan Visual Studio Code.

Kami menyambut kontribusi dari siapa saja, baik pemula maupun developer berpengalaman.

Kontribusi dapat berupa perbaikan dokumentasi, penambahan konfigurasi, penambahan wallpaper, perbaikan kesalahan, maupun ide pengembangan lainnya.

---

## Daftar Isi

- [1. Tentang Kontribusi](#1-tentang-kontribusi)
- [2. Jenis Kontribusi](#2-jenis-kontribusi)
- [3. Sebelum Berkontribusi](#3-sebelum-berkontribusi)
- [4. Persiapan Repository](#4-persiapan-repository)
- [5. Alur Kontribusi](#5-alur-kontribusi)
- [6. Panduan Penulisan Dokumentasi](#6-panduan-penulisan-dokumentasi)
- [7. Panduan Menambahkan Konfigurasi](#7-panduan-menambahkan-konfigurasi)
- [8. Panduan Menambahkan Wallpaper dan Screenshot](#8-panduan-menambahkan-wallpaper-dan-screenshot)
- [9. Standar Commit](#9-standar-commit)
- [10. Pull Request](#10-pull-request)
- [11. Melaporkan Bug dan Memberikan Saran](#11-melaporkan-bug-dan-memberikan-saran)
- [12. Code of Conduct](#12-code-of-conduct)

---

## 1. Tentang Kontribusi

Terminal Customization Guide merupakan proyek dokumentasi yang bertujuan membantu pengguna membangun lingkungan terminal yang lebih nyaman, menarik, dan sesuai kebutuhan.

Kami percaya bahwa dokumentasi yang baik dapat berkembang melalui kolaborasi.

Karena itu, setiap kontribusi yang relevan dan bermanfaat sangat dihargai.

## 2. Jenis Kontribusi

Ada beberapa bentuk kontribusi yang dapat dilakukan.

### 2.1 Perbaikan Dokumentasi

Contohnya:

- Memperbaiki kesalahan penulisan.
- Memperjelas langkah instalasi.
- Menambahkan penjelasan perintah terminal.
- Memperbaiki tutorial yang kurang lengkap.
- Menambahkan solusi untuk masalah yang sering ditemui.

### 2.2 Penambahan Konfigurasi

Contohnya:

- Menambahkan tema Oh My Posh.
- Menambahkan konfigurasi Zsh.
- Menambahkan contoh pengaturan Windows Terminal.
- Menambahkan konfigurasi warna VS Code.
- Menambahkan konfigurasi terminal lainnya.

### 2.3 Penambahan Wallpaper

Contohnya:

- Menambahkan wallpaper bertema alam.
- Menambahkan desain abstrak.
- Menambahkan wallpaper minimalis.
- Menambahkan variasi background terminal.

Pastikan gambar yang dibagikan memiliki izin penggunaan dan distribusi yang sesuai.

### 2.4 Penambahan Screenshot

Contohnya:

- Screenshot hasil konfigurasi PowerShell.
- Screenshot terminal Ubuntu dengan Powerlevel10k.
- Screenshot Windows Terminal dengan Acrylic.
- Screenshot terminal terintegrasi VS Code.

### 2.5 Pelaporan Bug

Jika menemukan kesalahan pada tutorial, konfigurasi, atau struktur repository, silakan buat laporan agar dapat diperiksa dan diperbaiki.

---

## 3. Sebelum Berkontribusi

Sebelum mulai melakukan perubahan, perhatikan beberapa hal berikut:

1. Pastikan kontribusi sesuai dengan tujuan proyek.
2. Periksa apakah materi yang ingin ditambahkan sudah tersedia.
3. Gunakan bahasa yang jelas dan mudah dipahami.
4. Hindari menambahkan file yang tidak berkaitan dengan proyek.
5. Pastikan konfigurasi sudah diperiksa sebelum dibagikan.
6. Jangan mengunggah password, API key, token, atau informasi pribadi.
7. Gunakan gambar dan aset yang memiliki izin distribusi.

Jika ingin mengusulkan perubahan besar, sebaiknya diskusikan terlebih dahulu melalui GitHub Issues.

---

## 4. Persiapan Repository

Untuk mulai berkontribusi, beberapa perangkat berikut disarankan:

- Git
- GitHub Account
- Visual Studio Code atau editor lainnya
- Windows Terminal
- PowerShell atau WSL Ubuntu sesuai kebutuhan kontribusi

### 4.1 Fork Repository

Jika ingin berkontribusi melalui GitHub:

1. Buka repository utama.
2. Klik tombol **Fork**.
3. Pilih akun GitHub milikmu.
4. Tunggu hingga repository hasil fork selesai dibuat.

### 4.2 Clone Repository

Buka terminal, kemudian jalankan:

```bash
git clone https://github.com/illhammf/terminal-customization-guide.git
```

Ganti `illhammf` dengan username GitHub milikmu.

Masuk ke direktori repository:

```bash
cd terminal-customization-guide
```

### 4.3 Buat Branch Baru

Sebaiknya gunakan branch terpisah untuk setiap perubahan.

Contoh:

```bash
git checkout -b docs/update-zsh-guide
```

Nama branch dapat disesuaikan dengan jenis kontribusi.

Contoh lainnya:

```bash
git checkout -b feat/add-new-wallpaper
```

```bash
git checkout -b fix/powershell-config
```

---

## 5. Alur Kontribusi

Secara umum, alur kontribusi dalam proyek ini adalah:

```text
Fork Repository
       |
       v
Clone Repository
       |
       v
Buat Branch Baru
       |
       v
Lakukan Perubahan
       |
       v
Periksa Hasil Perubahan
       |
       v
Commit Perubahan
       |
       v
Push ke GitHub
       |
       v
Buat Pull Request
       |
       v
Review dan Diskusi
       |
       v
Kontribusi Diterima
```

### 5.1 Lakukan Perubahan

Kerjakan perubahan sesuai tujuan branch yang dibuat.

Usahakan satu branch hanya berfokus pada satu kelompok perubahan agar proses pemeriksaan lebih mudah.

### 5.2 Periksa Perubahan

Sebelum melakukan commit, periksa file yang berubah:

```bash
git status
```

Lihat detail perubahan:

```bash
git diff
```

Pastikan tidak ada file yang tidak sengaja ikut ditambahkan.

### 5.3 Commit Perubahan

Jika sudah sesuai, tambahkan perubahan:

```bash
git add .
```

Buat commit:

```bash
git commit -m "docs: improve terminal installation guide"
```

### 5.4 Push ke GitHub

Kirim branch ke repository hasil fork:

```bash
git push origin nama-branch
```

Setelah berhasil, lanjutkan dengan membuat Pull Request melalui GitHub.

---

## 6. Panduan Penulisan Dokumentasi

Dokumentasi merupakan bagian utama dari proyek ini.

Karena itu, setiap tutorial diharapkan memiliki struktur yang jelas dan mudah diikuti.

### 6.1 Gunakan Bahasa yang Mudah Dipahami

Hindari penjelasan yang terlalu teknis tanpa memberikan konteks.

Jika menggunakan istilah teknis, sertakan penjelasan singkat.

### 6.2 Sertakan Langkah yang Jelas

Tutorial sebaiknya memiliki:

- Tujuan penggunaan.
- Persyaratan instalasi.
- Langkah-langkah konfigurasi.
- Contoh perintah.
- Penjelasan hasil.
- Solusi jika terjadi masalah.
- Referensi resmi jika diperlukan.

### 6.3 Gunakan Markdown

Gunakan format Markdown agar dokumentasi konsisten dan mudah dibaca di GitHub.

Contoh:

```markdown
# Judul Tutorial

## Persyaratan

Penjelasan kebutuhan instalasi.

## Langkah Instalasi

```bash
sudo apt update
```

## Hasil

Penjelasan hasil konfigurasi.
```

### 6.4 Sertakan Referensi

Jika tutorial menggunakan informasi dari dokumentasi resmi atau sumber eksternal, sertakan tautannya.

Utamakan dokumentasi resmi dari pengembang aplikasi.

---

## 7. Panduan Menambahkan Konfigurasi

File konfigurasi disimpan di dalam direktori `configs/`.

Contoh struktur:

```text
configs/
│
├── powershell/
├── vscode/
└── zsh/
```

Ketika menambahkan konfigurasi baru:

1. Tempatkan file pada kategori yang sesuai.
2. Gunakan nama file yang deskriptif.
3. Pastikan format file valid.
4. Tambahkan komentar atau penjelasan jika diperlukan.
5. Sertakan petunjuk penggunaan.
6. Periksa apakah konfigurasi memerlukan aplikasi atau font tambahan.

Jangan mengunggah konfigurasi yang berisi informasi rahasia atau data pribadi.

---

## 8. Panduan Menambahkan Wallpaper dan Screenshot

Materi visual disimpan di dalam direktori `assets/`.

### 8.1 Wallpaper

Wallpaper ditempatkan berdasarkan kategorinya:

```text
assets/wallpapers/
│
├── nature/
├── abstract/
└── minimal/
```

Ketentuan:

- Gunakan gambar yang dibuat sendiri atau memiliki izin distribusi.
- Gunakan nama file yang deskriptif.
- Hindari file duplikat.
- Usahakan ukuran file tetap wajar.
- Tambahkan preview dan deskripsi pada katalog wallpaper.

### 8.2 Screenshot

Screenshot ditempatkan berdasarkan lingkungan terminal:

```text
assets/screenshots/
│
├── powershell/
├── ubuntu-zsh/
├── windows-terminal/
└── vscode/
```

Ketentuan:

- Gunakan screenshot yang relevan.
- Pastikan teks dapat dibaca.
- Hindari menampilkan informasi pribadi.
- Jangan tampilkan password, token, atau kredensial.
- Gunakan format PNG atau JPG.

---

## 9. Standar Commit

Agar riwayat perubahan mudah dibaca, gunakan format pesan commit yang konsisten.

Format:

```text
type: short description
```

Jenis commit yang disarankan:

| Type | Penggunaan |
|---|---|
| `feat` | Menambahkan fitur atau materi baru |
| `docs` | Mengubah atau menambahkan dokumentasi |
| `fix` | Memperbaiki kesalahan |
| `refactor` | Merapikan struktur tanpa mengubah fungsi utama |
| `style` | Perubahan format atau tampilan |
| `chore` | Perubahan pemeliharaan proyek |

Contoh:

```bash
git commit -m "docs: add Powerlevel10k guide"
```

```bash
git commit -m "feat: add new terminal wallpaper"
```

```bash
git commit -m "fix: correct PowerShell configuration"
```

```bash
git commit -m "chore: organize assets directory"
```

---

## 10. Pull Request

Pull Request digunakan untuk mengajukan perubahan dari repository hasil fork ke repository utama.

Sebelum membuat Pull Request, pastikan:

- Perubahan sesuai dengan tujuan proyek.
- Tidak ada file yang tidak relevan.
- Dokumentasi sudah diperiksa.
- File konfigurasi sudah divalidasi.
- Gambar memiliki izin distribusi yang sesuai.
- Pesan commit sudah jelas.

### Informasi Pull Request

Sertakan informasi berikut:

**Judul:** Jelaskan perubahan secara singkat.

**Deskripsi:**
- Apa yang ditambahkan atau diperbaiki?
- Mengapa perubahan tersebut diperlukan?
- File atau direktori apa yang terdampak?
- Apakah diperlukan pengujian tambahan?

Sertakan screenshot jika perubahan berkaitan dengan tampilan terminal.

Setelah Pull Request dibuat, perubahan akan diperiksa sebelum digabungkan.

---

## 11. Melaporkan Bug dan Memberikan Saran

Jika menemukan masalah atau memiliki ide pengembangan, silakan gunakan GitHub Issues.

### Bug Report

Sertakan informasi berikut:

- Judul masalah.
- Sistem operasi yang digunakan.
- Aplikasi dan versi yang digunakan.
- Langkah untuk menghasilkan masalah.
- Pesan error yang muncul.
- Screenshot jika diperlukan.

### Feature Request

Jika ingin mengusulkan fitur atau materi baru, jelaskan:

- Ide yang ingin ditambahkan.
- Tujuan dan manfaatnya.
- Bagian repository yang berkaitan.
- Contoh penerapan jika tersedia.

Laporan yang jelas akan membantu proses pemeriksaan dan pengembangan proyek.

---

## 12. Code of Conduct

Setiap kontributor diharapkan menjaga lingkungan kolaborasi yang positif dan saling menghargai.

Beberapa hal yang perlu diperhatikan:

1. Hargai pendapat dan kontribusi orang lain.
2. Gunakan bahasa yang sopan dan profesional.
3. Berikan kritik yang membangun.
4. Hindari komentar yang menyerang atau merendahkan.
5. Bersikap terbuka terhadap masukan dan perbaikan.
6. Hormati hak cipta dan lisensi materi yang digunakan.

Setiap kontributor memiliki peran dalam menjaga kualitas dan keberlanjutan proyek ini.

---

## Terima Kasih!

Terima kasih telah meluangkan waktu untuk membaca panduan kontribusi ini.

Setiap kontribusi, sekecil apa pun, dapat membantu membuat **Terminal Customization Guide** menjadi sumber belajar yang lebih baik bagi komunitas.

Mari bersama-sama membangun dokumentasi terminal yang terbuka, bermanfaat, dan mudah dipahami.

**Happy Contributing!** 🚀