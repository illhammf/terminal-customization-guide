# 03 — PowerShell & Oh My Posh

Panduan ini membahas cara mengubah tampilan Windows PowerShell menjadi terminal yang lebih modern, berwarna, dan nyaman digunakan untuk aktivitas development.

Kustomisasi menggunakan Oh My Posh sebagai prompt engine, Meslo Nerd Font sebagai font terminal, serta konfigurasi JSON untuk mengatur tampilan prompt.

Panduan ini menggunakan Windows 11, PowerShell 5.1, dan Visual Studio Code.

## 1. Mengenal Oh My Posh

Oh My Posh merupakan prompt engine yang memungkinkan pengguna mengubah tampilan terminal melalui konfigurasi tema.

Beberapa informasi yang dapat ditampilkan:

- Username dan hostname.
- Direktori aktif.
- Git branch dan status repository.
- Durasi eksekusi perintah.
- Ikon dan simbol khusus.
- Warna dan tampilan prompt.
- Transient Prompt.

Dokumentasi resmi:

https://ohmyposh.dev/

Repository GitHub:

https://github.com/JanDeDobbeleer/oh-my-posh

## 2. Persiapan

Pastikan beberapa kebutuhan berikut sudah tersedia:

- Windows 10/11.
- Windows PowerShell 5.1 atau PowerShell 7.
- Windows Terminal atau Visual Studio Code.
- Windows Package Manager (winget).
- Git.

### Memeriksa versi PowerShell

Buka PowerShell dan jalankan:

```powershell
$PSVersionTable.PSVersion
```

Contoh hasil:

```text
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      26100  9818
```

### Memeriksa lokasi PowerShell Profile

Jalankan:

```powershell
$PROFILE
```

Contoh hasil:

```text
C:\Users\HP\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```

File tersebut merupakan tempat menyimpan konfigurasi yang dijalankan ketika PowerShell dimulai.

## 3. Instalasi Oh My Posh

Oh My Posh dapat diinstal menggunakan Windows Package Manager.

Jalankan PowerShell:

```powershell
winget install JanDeDobbeleer.OhMyPosh --source winget
```

Tunggu sampai proses instalasi selesai.

### Memeriksa instalasi

Jalankan:

```powershell
oh-my-posh version
```

Contoh hasil:

```text
32.0.0
```

Jika perintah belum dikenali setelah instalasi, tutup dan buka kembali PowerShell agar perubahan PATH dapat diterapkan.

Dokumentasi instalasi:

https://ohmyposh.dev/docs/installation/windows

## 4. Instalasi Meslo Nerd Font

Nerd Font menyediakan karakter dan ikon tambahan yang digunakan oleh berbagai tema terminal.

Dalam panduan ini, kita menggunakan Meslo Nerd Font.

Jalankan:

```powershell
oh-my-posh font install meslo
```

Jika berhasil, akan muncul informasi bahwa font Meslo telah terinstal.

Oh My Posh menyediakan beberapa varian font, seperti:

- MesloLGL Nerd Font
- MesloLGL Nerd Font Mono
- MesloLGS Nerd Font
- MesloLGS Nerd Font Mono
- MesloLGM Nerd Font

Untuk konfigurasi ini, gunakan keluarga font `MesloLGS NF` jika tersedia pada sistem.

### Mengatur font Windows Terminal

1. Buka Windows Terminal.
2. Masuk ke Settings.
3. Pilih profil PowerShell.
4. Buka Appearance.
5. Cari Font face.
6. Pilih MesloLGS NF.
7. Simpan perubahan.

### Mengatur font Visual Studio Code

Buka Settings menggunakan:

```text
CTRL + ,
```

Cari pengaturan:

```text
Terminal › Integrated: Font Family
```

Isi dengan:

```text
MesloLGS NF
```

Alternatifnya, tambahkan ke User Settings JSON:

```json
{
  "terminal.integrated.fontFamily": "MesloLGS NF"
}
```

Restart terminal setelah mengubah font.

Dokumentasi font:

https://ohmyposh.dev/docs/installation/fonts

## 5. Mencoba Tema Oh My Posh

Sebelum membuat konfigurasi sendiri, kita dapat mencoba tema bawaan.

Contohnya:

```powershell
oh-my-posh init pwsh --config pure | Invoke-Expression
```

Perintah tersebut mengaktifkan tema `pure` untuk sesi PowerShell saat ini.

Tema ini dapat digunakan sebagai pengujian awal sebelum membuat konfigurasi custom.

Untuk melihat hasilnya, jalankan beberapa perintah:

```powershell
pwd
git status
```

## 6. Membuat Tema Custom

Oh My Posh mendukung konfigurasi tema menggunakan format JSON.

Dalam panduan ini, kita membuat tema bernama:

```text
macos-theme.omp.json
```

Tema ini menggunakan kombinasi warna yang terinspirasi dari tampilan terminal macOS dan Powerlevel10k.

### Membuat file konfigurasi

Simpan file konfigurasi dengan nama:

```text
macos-theme.omp.json
```

Lokasi yang digunakan dalam contoh ini:

```text
C:\Users\HP\macos-theme.omp.json
```

### Isi konfigurasi

Gunakan konfigurasi berikut:

```json
{
  "$schema": "https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/schema.json",
  "version": 4,
  "final_space": true,
  "transient_prompt": {
    "foreground": "#00FF87",
    "background": "transparent",
    "template": "\n❯ ",
    "newline": true
  },
  "blocks": [
    {
      "type": "prompt",
      "alignment": "left",
      "segments": [
        {
          "type": "session",
          "style": "plain",
          "foreground": "#00FF87",
          "template": "{{ .UserName }} "
        },
        {
          "type": "path",
          "style": "plain",
          "foreground": "#00D7FF",
          "template": "{{ .Path }} "
        },
        {
          "type": "git",
          "style": "plain",
          "foreground": "#A6E22E",
          "template": "{{ .HEAD }}{{ if .Working.Changed }} *{{ end }} "
        }
      ]
    },
    {
      "type": "prompt",
      "alignment": "left",
      "newline": true,
      "segments": [
        {
          "type": "text",
          "style": "plain",
          "foreground": "#00FF87",
          "template": "❯ "
        }
      ]
    }
  ]
}
```

### Penjelasan konfigurasi

**1. Schema**

```json
"$schema": "https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/schema.json"
```

Menunjukkan schema konfigurasi Oh My Posh.

**2. Version**

```json
"version": 4
```

Menentukan versi struktur konfigurasi yang digunakan.

**3. Final Space**

```json
"final_space": true
```

Mengatur perilaku spasi akhir pada prompt.

**4. Session Segment**

```json
{
  "type": "session",
  "foreground": "#00FF87",
  "template": "{{ .UserName }} "
}
```

Menampilkan username dengan warna hijau.

**5. Path Segment**

```json
{
  "type": "path",
  "foreground": "#00D7FF",
  "template": "{{ .Path }} "
}
```

Menampilkan direktori aktif menggunakan warna cyan.

**6. Git Segment**

```json
{
  "type": "git",
  "foreground": "#A6E22E",
  "template": "{{ .HEAD }}{{ if .Working.Changed }} *{{ end }} "
}
```

Menampilkan Git branch dan tanda ketika terdapat perubahan pada working tree.

**7. Prompt Segment**

```json
{
  "type": "text",
  "foreground": "#00FF87",
  "template": "❯ "
}
```

Menampilkan simbol prompt berwarna hijau.

**8. Transient Prompt**

```json
"transient_prompt": {
  "foreground": "#00FF87",
  "background": "transparent",
  "template": "\n❯ ",
  "newline": true
}
```

Mengatur tampilan prompt sebelumnya agar lebih sederhana dan memiliki jarak kosong sebelum simbol prompt.

Kombinasi `newline` dan karakter `\n` digunakan untuk menghasilkan jarak tambahan pada tampilan riwayat perintah.

## 7. Mengaktifkan Tema Custom

Setelah file JSON selesai dibuat, jalankan:

```powershell
oh-my-posh init pwsh --config "$HOME\macos-theme.omp.json" | Invoke-Expression
```

Jika konfigurasi berhasil dibaca, prompt akan berubah sesuai tema yang dibuat.

### Menguji prompt

Coba beberapa perintah:

```powershell
pwd
git status
git add .
git status
```

Jika sedang berada di dalam repository Git, informasi branch akan muncul pada prompt.

## 8. Mengaktifkan Tema Secara Permanen

Secara default, perintah `Invoke-Expression` yang dijalankan langsung hanya berlaku pada sesi PowerShell saat ini.

Agar tema aktif setiap kali terminal dibuka, kita perlu memasukkannya ke PowerShell Profile.

### Memeriksa lokasi Profile

```powershell
$PROFILE
```

### Membuka Profile

```powershell
notepad $PROFILE
```

Tambahkan konfigurasi berikut:

```powershell
oh-my-posh init pwsh --config "$HOME\macos-theme.omp.json" | Invoke-Expression
```

Simpan file.

Jika terdapat konfigurasi Oh My Posh lama, pastikan tidak ada dua inisialisasi tema yang saling bertabrakan.

### Menguji konfigurasi permanen

Tutup terminal PowerShell yang sedang berjalan.

Kemudian buka terminal baru.

Jika berhasil, tema custom akan langsung aktif tanpa menjalankan perintah inisialisasi secara manual.

## 9. Mengatur Tampilan Terminal Visual Studio Code

Visual Studio Code menyediakan pengaturan untuk mengubah warna, ukuran font, dan tampilan terminal terintegrasi.

Buka User Settings JSON:

```text
CTRL + SHIFT + P
```

Cari:

```text
Preferences: Open User Settings (JSON)
```

Tambahkan pengaturan berikut:

```json
{
  "terminal.integrated.fontFamily": "MesloLGS NF",
  "terminal.integrated.fontSize": 13,
  "terminal.integrated.fontWeight": "normal",
  "terminal.integrated.lineHeight": 1.2,

  "workbench.colorCustomizations": {
    "terminal.background": "#080B10",
    "terminal.foreground": "#F5F5F5",
    "terminalCursor.foreground": "#00FF87",
    "terminal.selectionBackground": "#264F78",

    "terminal.ansiBlack": "#171717",
    "terminal.ansiRed": "#FF5F57",
    "terminal.ansiGreen": "#00FF87",
    "terminal.ansiYellow": "#FFD75F",
    "terminal.ansiBlue": "#5F87FF",
    "terminal.ansiMagenta": "#D787FF",
    "terminal.ansiCyan": "#00D7FF",
    "terminal.ansiWhite": "#FFFFFF",

    "terminal.ansiBrightBlack": "#777777",
    "terminal.ansiBrightRed": "#FF6E67",
    "terminal.ansiBrightGreen": "#5FFF87",
    "terminal.ansiBrightYellow": "#FFFF87",
    "terminal.ansiBrightBlue": "#87AFFF",
    "terminal.ansiBrightMagenta": "#FF87FF",
    "terminal.ansiBrightCyan": "#5FFFFF",
    "terminal.ansiBrightWhite": "#FFFFFF"
  }
}
```

**Catatan:** Jika file Settings JSON sudah memiliki konfigurasi lain, gabungkan properti tersebut. Jangan mengganti seluruh pengaturan yang sudah ada.

Pengaturan di atas mengubah warna terminal terintegrasi, bukan seluruh tema editor.

## 10. Mengenal Navigasi PowerShell

PowerShell memiliki aturan navigasi yang sedikit berbeda dari Bash dan Zsh.

Beberapa perintah dasar:

| Perintah | Fungsi |
|---|---|
| `pwd` | Melihat direktori aktif |
| `ls` | Melihat isi direktori |
| `cd ..` | Naik satu direktori |
| `cd ~` | Menuju home user |
| `cd \` | Menuju root drive aktif |
| `Set-Location` | Berpindah direktori |
| `Clear-Host` | Membersihkan terminal |
| `Get-Location` | Melihat lokasi aktif |

### Masuk ke folder yang memiliki spasi

Misalnya terdapat folder:

```text
C:\Dokumen\Belajar Dart
```

Perintah berikut akan menghasilkan error:

```powershell
cd Belajar Dart
```

Hal tersebut terjadi karena PowerShell membaca `Belajar` dan `Dart` sebagai argumen terpisah.

Gunakan tanda kutip:

```powershell
cd "Belajar Dart"
```

Atau gunakan path lengkap:

```powershell
cd "C:\Dokumen\Belajar Dart"
```

### Menggunakan Tab Autocomplete

PowerShell juga menyediakan fitur autocomplete menggunakan tombol `Tab`.

Contoh:

```powershell
cd Bel
```

Tekan `Tab` sampai nama folder yang diinginkan muncul.

Fitur ini sangat membantu ketika bekerja dengan direktori yang memiliki nama panjang atau mengandung spasi.

## 11. Troubleshooting

### A. Oh My Posh tidak dikenali

Contoh error:

```text
oh-my-posh : The term 'oh-my-posh' is not recognized
```

Periksa instalasi:

```powershell
winget list JanDeDobbeleer.OhMyPosh
```

Jika sudah terpasang, tutup dan buka kembali PowerShell.

Periksa kembali:

```powershell
oh-my-posh version
```

### B. Font tidak menampilkan ikon

Pastikan Meslo Nerd Font sudah terinstal dan dipilih pada pengaturan font terminal.

Periksa kembali:

- Font keluarga yang digunakan.
- Pengaturan font Windows Terminal.
- Pengaturan font VS Code.
- Terminal yang sudah dibuka ulang.

### C. CONFIG PARSE ERROR

Jika muncul:

```text
CONFIG PARSE ERROR
```

Jangan langsung mengubah seluruh konfigurasi.

Lakukan pemeriksaan bertahap.

**1. Periksa keberadaan file**

```powershell
Test-Path "$HOME\macos-theme.omp.json"
```

**2. Periksa validitas JSON**

```powershell
Get-Content "$HOME\macos-theme.omp.json" -Raw | ConvertFrom-Json
```

Jika perintah tersebut berhasil, struktur JSON secara sintaksis dapat dibaca oleh PowerShell.

Namun, validitas JSON belum menjamin seluruh properti didukung oleh Oh My Posh.

**3. Uji rendering tema**

```powershell
oh-my-posh print primary --config "$HOME\macos-theme.omp.json" --shell pwsh
```

**4. Periksa inisialisasi**

```powershell
oh-my-posh init pwsh --config "$HOME\macos-theme.omp.json" | Invoke-Expression
```

Periksa pesan error yang muncul sebelum mengganti konfigurasi.

### D. Tema tidak aktif setelah membuka terminal baru

Periksa isi PowerShell Profile:

```powershell
Get-Content $PROFILE
```

Pastikan terdapat baris:

```powershell
oh-my-posh init pwsh --config "$HOME\macos-theme.omp.json" | Invoke-Expression
```

Periksa juga lokasi file:

```powershell
Test-Path "$HOME\macos-theme.omp.json"
```

### E. Folder dengan spasi tidak dapat dibuka

Gunakan tanda kutip:

```powershell
cd "Nama Folder"
```

Contoh:

```powershell
cd "Belajar Dart"
```

## 12. Hasil Akhir

Setelah mengikuti panduan ini, pengguna diharapkan sudah memiliki:

- Oh My Posh terpasang pada Windows.
- Meslo Nerd Font tersedia.
- Tema custom berbasis JSON.
- PowerShell Profile yang menjalankan Oh My Posh secara otomatis.
- Informasi username, direktori, dan Git branch.
- Transient Prompt dengan jarak tambahan.
- Tampilan terminal VS Code yang lebih gelap dan berwarna.
- Pemahaman navigasi direktori PowerShell.

## 13. Referensi

- Oh My Posh Documentation: https://ohmyposh.dev/docs
- Oh My Posh Windows Installation: https://ohmyposh.dev/docs/installation/windows
- Oh My Posh Fonts: https://ohmyposh.dev/docs/installation/fonts
- Oh My Posh Configuration: https://ohmyposh.dev/docs/configuration/overview
- Oh My Posh Transient Prompt: https://ohmyposh.dev/docs/configuration/transient
- Oh My Posh GitHub: https://github.com/JanDeDobbeleer/oh-my-posh

---

**Previous:** [02 — Powerlevel10k](02-powerlevel10k.md)

**Next:** [04 — VS Code Terminal](04-vscode-terminal.md)