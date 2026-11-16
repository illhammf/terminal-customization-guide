# Terminal Configuration Collection

Folder `configs/` merupakan tempat penyimpanan berbagai contoh file konfigurasi yang digunakan dalam proyek **Terminal Customization Guide**.

Folder ini dibuat agar pengguna tidak perlu menyusun seluruh konfigurasi dari awal. Pengguna dapat mempelajari, menyalin, dan menyesuaikan konfigurasi yang sudah disediakan sesuai kebutuhan masing-masing.

Konfigurasi di dalam folder ini berfokus pada kustomisasi terminal Windows, PowerShell, WSL Ubuntu, Zsh, Oh My Zsh, Powerlevel10k, Oh My Posh, dan Visual Studio Code.

> **Tujuan utama:** Menyediakan contoh konfigurasi yang terstruktur, mudah dipahami, dapat digunakan kembali, dan bisa dikembangkan oleh siapa saja.

---

## Daftar Isi

- [1. Tentang Folder Configs](#1-tentang-folder-configs)
- [2. Struktur Folder](#2-struktur-folder)
- [3. Penjelasan Setiap Konfigurasi](#3-penjelasan-setiap-konfigurasi)
- [4. Cara Menggunakan Konfigurasi](#4-cara-menggunakan-konfigurasi)
- [5. Menyesuaikan Konfigurasi](#5-menyesuaikan-konfigurasi)
- [6. Hal yang Perlu Diperhatikan](#6-hal-yang-perlu-diperhatikan)
- [7. Hubungan dengan Folder Docs](#7-hubungan-dengan-folder-docs)
- [8. Rencana Pengembangan](#8-rencana-pengembangan)
- [9. Kontribusi](#9-kontribusi)

---

## 1. Tentang Folder Configs

Folder `configs/` berfungsi sebagai tempat penyimpanan file konfigurasi yang dapat digunakan untuk mengatur tampilan dan perilaku terminal.

Contohnya:

- Mengatur tampilan prompt PowerShell.
- Mengatur warna dan font terminal VS Code.
- Mengatur tema Zsh menggunakan Oh My Zsh.
- Menggunakan konfigurasi Powerlevel10k.
- Menyediakan konfigurasi tambahan untuk pengembangan terminal di masa mendatang.

Dengan adanya folder ini, pengguna dapat memilih konfigurasi yang dibutuhkan tanpa harus membuat semuanya secara manual.

### Mengapa Folder Ini Dibuat?

Dalam proses kustomisasi terminal, banyak pengaturan yang perlu ditulis secara manual ke dalam file konfigurasi.

Bagi pengguna baru, hal tersebut terkadang membingungkan, terutama jika belum memahami struktur JSON, konfigurasi Zsh, atau pengaturan PowerShell.

Karena itu, folder ini menyediakan contoh konfigurasi yang sudah disusun agar lebih mudah dipelajari dan digunakan.

---

## 2. Struktur Folder

Berikut struktur direktori konfigurasi yang tersedia:

```text
configs/
│
├── powershell/
│   └── macos-theme.omp.json
│
├── vscode/
│   └── settings.example.json
│
├── zsh/
│   └── zshrc.example
│
└── README.md
```

Setiap folder memiliki fungsi masing-masing dan tidak saling menggantikan.

---

## 3. Penjelasan Setiap Konfigurasi

### 3.1 PowerShell

**Lokasi:** `configs/powershell/`

Folder ini menyimpan konfigurasi untuk PowerShell, khususnya penggunaan Oh My Posh.

File yang tersedia:

| File | Fungsi |
|---|---|
| `macos-theme.omp.json` | Konfigurasi tema Oh My Posh dengan tampilan minimalis terinspirasi terminal macOS |

Konfigurasi ini mengatur beberapa bagian tampilan terminal, seperti:

- Informasi pengguna.
- Lokasi direktori aktif.
- Informasi Git.
- Warna teks dan prompt.
- Tampilan prompt setelah perintah sebelumnya dijalankan.

**Cara menggunakannya:**

1. Pastikan Oh My Posh sudah terpasang.
2. Salin `macos-theme.omp.json` ke direktori Home Windows.
3. Jalankan perintah berikut di PowerShell:

```powershell
oh-my-posh init pwsh --config "$HOME\macos-theme.omp.json" | Invoke-Expression
```

Jika tema berhasil muncul, tambahkan perintah tersebut ke profil PowerShell agar konfigurasi aktif secara otomatis ketika terminal dibuka.

Periksa lokasi profil dengan:

```powershell
$PROFILE
```

### 3.2 VS Code

**Lokasi:** `configs/vscode/`

Folder ini menyimpan contoh pengaturan tampilan terminal terintegrasi Visual Studio Code.

File yang tersedia:

| File | Fungsi |
|---|---|
| `settings.example.json` | Contoh pengaturan font, ukuran teks, dan warna terminal VS Code |

Pengaturan yang tersedia meliputi:

- Jenis font terminal.
- Ukuran dan ketebalan teks.
- Tinggi baris.
- Warna latar belakang.
- Warna teks.
- Warna kursor.
- Warna ANSI untuk berbagai keluaran terminal.

**Cara menggunakannya:**

1. Buka Visual Studio Code.
2. Tekan `Ctrl + Shift + P`.
3. Cari `Preferences: Open User Settings (JSON)`.
4. Buka file `settings.example.json` dari repository.
5. Salin pengaturan yang dibutuhkan.
6. Gabungkan ke User Settings (JSON) milik VS Code.
7. Simpan perubahan.

**Penting:** Jangan langsung mengganti seluruh isi `settings.json` jika sudah memiliki konfigurasi pribadi. Gabungkan properti yang diperlukan agar pengaturan sebelumnya tidak hilang.

### 3.3 Zsh

**Lokasi:** `configs/zsh/`

Folder ini menyimpan contoh konfigurasi untuk Zsh dan Oh My Zsh pada lingkungan Linux atau WSL Ubuntu.

File yang tersedia:

| File | Fungsi |
|---|---|
| `zshrc.example` | Contoh konfigurasi utama Zsh |

Konfigurasi ini mencakup:

- Lokasi instalasi Oh My Zsh.
- Pemilihan tema Powerlevel10k.
- Pengaturan plugin Oh My Zsh.
- Pengaturan riwayat perintah.
- Alias untuk mempermudah penggunaan terminal.
- Pemanggilan konfigurasi Powerlevel10k.

**Cara menggunakannya:**

1. Pastikan Zsh sudah terpasang.
2. Pastikan Oh My Zsh sudah terpasang.
3. Jika ingin menggunakan tema Powerlevel10k, pastikan tema tersebut sudah dipasang.
4. Buat cadangan file `.zshrc` yang sudah ada.
5. Buka file `zshrc.example` dan pelajari isinya.
6. Gabungkan pengaturan yang dibutuhkan ke `~/.zshrc`.
7. Muat ulang konfigurasi:

```bash
source ~/.zshrc
```

Jika menggunakan Powerlevel10k, jalankan konfigurasi awal dengan:

```bash
p10k configure
```

**Catatan:** File `zshrc.example` bukan pengganti universal untuk `.zshrc`. Pengguna perlu menyesuaikannya dengan instalasi dan konfigurasi yang sudah dimiliki.

---

## 4. Cara Menggunakan Konfigurasi

Secara umum, penggunaan file di dalam folder `configs/` dapat dilakukan melalui langkah berikut:

### Langkah 1 — Pilih Konfigurasi

Tentukan terlebih dahulu aplikasi atau lingkungan terminal yang ingin dikustomisasi.

Contoh:

- Menggunakan PowerShell? Pilih `powershell/`.
- Menggunakan VS Code? Pilih `vscode/`.
- Menggunakan Ubuntu WSL dengan Zsh? Pilih `zsh/`.

### Langkah 2 — Buka File Konfigurasi

Buka file yang sesuai dengan kebutuhan.

Baca isinya terlebih dahulu agar memahami pengaturan yang akan diterapkan.

### Langkah 3 — Buat Cadangan

Sebelum mengubah konfigurasi yang sudah ada, buat salinannya.

Contoh untuk Zsh:

```bash
cp ~/.zshrc ~/.zshrc.backup
```

Contoh untuk PowerShell:

```powershell
Copy-Item $PROFILE "$PROFILE.backup"
```

### Langkah 4 — Terapkan Konfigurasi

Salin atau gabungkan bagian konfigurasi yang diperlukan ke file konfigurasi masing-masing aplikasi.

Jangan menimpa seluruh file konfigurasi jika di dalamnya terdapat pengaturan pribadi yang masih digunakan.

### Langkah 5 — Muat Ulang Terminal

Setelah perubahan disimpan, muat ulang konfigurasi atau buka terminal baru.

Contohnya:

```bash
source ~/.zshrc
```

Untuk PowerShell, tutup dan buka kembali terminal setelah perubahan profil disimpan.

---

## 5. Menyesuaikan Konfigurasi

Semua file di dalam folder ini merupakan contoh yang boleh dipelajari dan dikembangkan.

Beberapa bagian mungkin perlu disesuaikan dengan perangkat masing-masing.

| Pengaturan | Hal yang Perlu Disesuaikan |
|---|---|
| Font | Pastikan font sudah terpasang di Windows |
| Direktori | Sesuaikan lokasi file dengan perangkat |
| Tema | Gunakan tema yang sudah terinstal |
| Plugin | Pastikan plugin tersedia |
| Warna | Ubah sesuai preferensi |
| Profil terminal | Pastikan konfigurasi diterapkan pada profil yang benar |

Sebagai contoh, pengaturan font berikut:

```json
"terminal.integrated.fontFamily": "MesloLGS NF"
```

dapat diganti jika pengguna menggunakan font lain.

Begitu juga dengan lokasi file konfigurasi Oh My Posh. Lokasi tersebut harus sesuai dengan tempat file disimpan.

---

## 6. Hal yang Perlu Diperhatikan

Sebelum menggunakan konfigurasi, perhatikan beberapa hal berikut:

1. **Periksa kebutuhan aplikasi.** Setiap konfigurasi memiliki aplikasi dan lingkungan yang berbeda.
2. **Buat cadangan.** Jangan langsung mengganti file konfigurasi utama.
3. **Periksa lokasi file.** Pastikan direktori dan nama file sudah sesuai.
4. **Perhatikan hak akses.** Konfigurasi WSL untuk root berbeda dengan konfigurasi pengguna biasa.
5. **Periksa font.** Simbol khusus membutuhkan font yang mendukung karakter tersebut.
6. **Baca dokumentasi.** Jika menemukan error, periksa panduan troubleshooting di folder `docs/`.

Konfigurasi yang tersedia tidak menjamin tampilan akan sama persis pada setiap perangkat. Hasil akhirnya dapat dipengaruhi oleh sistem operasi, versi aplikasi, font, dan pengaturan pengguna.

---

## 7. Hubungan dengan Folder Docs

Folder `configs/` dan `docs/` memiliki fungsi yang saling melengkapi.

| Folder | Fungsi |
|---|---|
| `docs/` | Menjelaskan tutorial, langkah instalasi, dan cara konfigurasi |
| `configs/` | Menyediakan file konfigurasi sebagai contoh penerapan tutorial |

Contohnya, pengguna dapat membaca tutorial PowerShell di folder `docs/`, kemudian mengambil file tema Oh My Posh dari folder `configs/powershell/`.

Dengan demikian, pengguna tidak hanya mendapatkan penjelasan, tetapi juga contoh konfigurasi yang dapat dipelajari dan diterapkan.

---

## 8. Rencana Pengembangan

Folder `configs/` dapat dikembangkan secara bertahap.

Beberapa konfigurasi yang berpotensi ditambahkan:

- Tema Oh My Posh tambahan.
- Contoh konfigurasi Powerlevel10k.
- Konfigurasi Zsh dengan plugin tambahan.
- Contoh profil Windows Terminal.
- Variasi warna terminal.
- Konfigurasi terminal untuk lingkungan pengembangan lainnya.

Penambahan konfigurasi akan dilakukan secara bertahap agar setiap file tetap memiliki fungsi dan dokumentasi yang jelas.

---

## 9. Kontribusi

Kontribusi sangat terbuka bagi siapa saja yang ingin menambahkan atau memperbaiki konfigurasi.

Beberapa bentuk kontribusi yang dapat dilakukan:

- Menambahkan tema terminal baru.
- Memperbaiki konfigurasi yang sudah tersedia.
- Menambahkan komentar penjelas pada file konfigurasi.
- Menambahkan dokumentasi penggunaan.
- Melaporkan konfigurasi yang mengalami masalah.

Pastikan setiap konfigurasi baru disertai penjelasan mengenai fungsi, kebutuhan aplikasi, dan cara penggunaannya.

---

## Referensi

- [Oh My Posh Documentation](https://ohmyposh.dev/docs/)
- [Oh My Zsh](https://ohmyz.sh/)
- [Powerlevel10k](https://github.com/romkatv/powerlevel10k)
- [Visual Studio Code Documentation](https://code.visualstudio.com/docs/)
- [Windows Terminal Documentation](https://learn.microsoft.com/windows/terminal/)

---

**Bagian dari:** [Terminal Customization Guide](../README.md)

Dibuat untuk membantu pengguna mempelajari dan membangun lingkungan terminal yang lebih nyaman, konsisten, dan sesuai kebutuhan masing-masing.