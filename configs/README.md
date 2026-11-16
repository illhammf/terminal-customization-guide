# Contoh Konfigurasi

Folder ini berisi contoh konfigurasi yang digunakan dalam panduan kustomisasi terminal.

## Struktur

```text
configs/
├── powershell/
│   └── macos-theme.omp.json
├── vscode/
│   └── settings.example.json
└── zsh/
    └── zshrc.example
```

## Sebelum menggunakan

- Buat salinan cadangan konfigurasi yang sudah ada.
- Baca isi file sebelum menyalin atau menggabungkannya.
- Sesuaikan lokasi file, nama pengguna, dan pilihan font dengan perangkat masing-masing.
- Jangan mengganti seluruh konfigurasi pribadi jika yang dibutuhkan hanya beberapa pengaturan.

## 1. PowerShell — Oh My Posh

File: `powershell/macos-theme.omp.json`

Simpan salinan file ini di direktori Home Windows, lalu sesuaikan lokasi file konfigurasi pada perintah inisialisasi di profil PowerShell.

Contoh perintah untuk mengaktifkannya:

```powershell
oh-my-posh init pwsh --config "$HOME\macos-theme.omp.json" | Invoke-Expression
```

Pastikan Oh My Posh sudah terpasang dan font yang mendukung glyph sudah dipilih pada aplikasi terminal.

## 2. VS Code — Terminal

File: `vscode/settings.example.json`

File ini hanya berisi contoh pengaturan terminal dan warna terminal. Gabungkan properti yang diperlukan ke User Settings (JSON) milik VS Code.

**Penting:** Jangan menimpa seluruh `settings.json` jika sudah memiliki pengaturan lain. Jika objek `workbench.colorCustomizations` sudah ada, gabungkan properti warnanya ke objek tersebut.

Sesuaikan `terminal.integrated.fontFamily` dengan font yang benar-benar sudah terpasang.

## 3. Zsh — Oh My Zsh dan Powerlevel10k

File: `zsh/zshrc.example`

File ini merupakan contoh konfigurasi `.zshrc`, bukan file konfigurasi universal. Periksa konfigurasi lama terlebih dahulu sebelum menggabungkan isinya.

Powerlevel10k harus sudah dipasang pada akun Linux yang sedang digunakan. Jika belum menggunakan Powerlevel10k, ubah nilai `ZSH_THEME` ke tema yang tersedia atau gunakan tema bawaan Oh My Zsh.

Setelah mengubah `.zshrc`, muat ulang dengan:

```bash
source ~/.zshrc
```

## Catatan

Contoh konfigurasi dibuat sebagai titik awal untuk dipelajari dan disesuaikan. Hasil tampilan dapat berbeda tergantung versi aplikasi, font, sistem operasi, dan konfigurasi pengguna.
