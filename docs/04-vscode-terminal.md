# 04 — VS Code Terminal Customization

Visual Studio Code menyediakan integrated terminal yang memungkinkan pengguna menjalankan berbagai shell langsung dari editor.

Dalam panduan ini, kita akan mengatur tampilan terminal agar lebih nyaman digunakan, terutama ketika bekerja menggunakan PowerShell dan WSL Ubuntu.

## 1. Mengenal Integrated Terminal

Integrated Terminal merupakan terminal bawaan Visual Studio Code yang dapat digunakan tanpa membuka aplikasi terminal secara terpisah.

Beberapa shell yang dapat digunakan:

- Windows PowerShell.
- PowerShell 7.
- Command Prompt.
- Ubuntu melalui WSL.
- Git Bash.

Untuk membuka terminal:

```text
CTRL + `
```

Untuk menampilkan atau menyembunyikan panel bawah:

```text
CTRL + J
```

Perlu diketahui bahwa `CTRL + J` mengatur visibilitas panel, bukan menghapus terminal yang sedang berjalan.

## 2. Membuka User Settings

VS Code menyediakan dua cara untuk mengubah pengaturan.

### Menggunakan Settings UI

1. Buka Visual Studio Code.
2. Tekan `CTRL + ,`.
3. Cari pengaturan yang ingin diubah.
4. Sesuaikan nilainya.

### Menggunakan Settings JSON

Untuk mengatur konfigurasi secara langsung:

1. Tekan `CTRL + SHIFT + P`.
2. Cari `Preferences: Open User Settings (JSON)`.
3. Tambahkan konfigurasi yang diperlukan.

Cara ini memudahkan pengguna mengelola berbagai pengaturan terminal dalam satu file.

## 3. Mengatur Font Terminal

Font merupakan salah satu bagian penting dalam kustomisasi terminal.

Dalam panduan ini, kita menggunakan MesloLGS NF agar ikon dan simbol dari Oh My Posh serta Powerlevel10k dapat ditampilkan dengan benar.

Buka User Settings JSON dan tambahkan:

```json
{
  "terminal.integrated.fontFamily": "MesloLGS NF",
  "terminal.integrated.fontSize": 13,
  "terminal.integrated.fontWeight": "normal",
  "terminal.integrated.lineHeight": 1.2
}
```

Penjelasan:

| Pengaturan | Fungsi |
|---|---|
| `fontFamily` | Menentukan jenis font terminal |
| `fontSize` | Mengatur ukuran teks |
| `fontWeight` | Mengatur ketebalan teks |
| `lineHeight` | Mengatur jarak vertikal antarbaris |

Nilai tersebut dapat disesuaikan dengan ukuran layar dan preferensi masing-masing pengguna.

## 4. Mengatur Warna Terminal

VS Code menyediakan pengaturan warna terminal melalui `workbench.colorCustomizations`.

Kita akan menggunakan kombinasi warna gelap dengan aksen cyan, hijau, kuning, dan putih.

Tambahkan konfigurasi berikut:

```json
{
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

### Penjelasan warna

- Background: hitam kebiruan.
- Foreground: putih terang.
- Cursor: hijau neon.
- Cyan: untuk informasi direktori.
- Green: untuk status dan teks tertentu.
- Yellow: untuk informasi yang perlu diperhatikan.
- Bright colors: memberikan variasi warna yang lebih terang.

**Catatan:** Jika sudah memiliki konfigurasi `workbench.colorCustomizations`, gabungkan properti di atas. Jangan membuat properti yang sama berulang kali dalam satu objek JSON.

## 5. Mengatur PowerShell sebagai Default Terminal

VS Code dapat menggunakan beberapa jenis shell.

Untuk mengatur PowerShell sebagai terminal default:

1. Buka Command Palette menggunakan `CTRL + SHIFT + P`.
2. Cari `Terminal: Select Default Profile`.
3. Pilih PowerShell.
4. Buka terminal baru.

Jika menggunakan Windows PowerShell 5.1, profil biasanya ditampilkan sebagai PowerShell.

## 6. Mengintegrasikan WSL Ubuntu

Selain PowerShell, kita juga dapat menjalankan Ubuntu melalui WSL langsung dari VS Code.

Pastikan WSL sudah terpasang dan Ubuntu dapat dijalankan.

Periksa distribusi WSL melalui PowerShell:

```powershell
wsl --list --verbose
```

Untuk menjalankan Ubuntu:

```powershell
wsl -d Ubuntu
```

Kamu juga dapat membuka folder Linux menggunakan VS Code dari terminal Ubuntu.

Contoh:

```bash
cd ~/perkuliahan
code .
```

Jika ekstensi WSL sudah terpasang, VS Code akan membuka project melalui lingkungan WSL.

### Ekstensi yang diperlukan

Instal ekstensi:

**WSL — Microsoft**

Marketplace:

https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl

Ekstensi ini memungkinkan VS Code terhubung dengan lingkungan Linux melalui WSL.

## 7. Menggunakan Beberapa Terminal

VS Code memungkinkan pengguna membuka beberapa terminal sekaligus.

Beberapa fitur yang tersedia:

| Fitur | Fungsi |
|---|---|
| New Terminal | Membuka terminal baru |
| Split Terminal | Membagi terminal menjadi beberapa panel |
| Kill Terminal | Mengakhiri sesi terminal |
| Select Default Profile | Mengubah shell default |
| Clear Terminal | Membersihkan tampilan terminal |

### Membuka terminal baru

Gunakan shortcut:

```text
CTRL + SHIFT + `
```

### Membuka dan menutup panel terminal

Gunakan:

```text
CTRL + J
```

Shortcut tersebut menampilkan atau menyembunyikan panel bawah.

Jika terminal terlihat menghilang setelah menekan shortcut, cukup tekan kembali `CTRL + J`.

## 8. Mengatur Ukuran Terminal

Ukuran font dan jarak antarbaris dapat diatur melalui User Settings JSON.

Contoh:

```json
{
  "terminal.integrated.fontSize": 13,
  "terminal.integrated.lineHeight": 1.2
}
```

Jika teks terlalu kecil, tingkatkan `fontSize`.

Jika jarak antarbaris terlalu rapat, tingkatkan `lineHeight`.

Sesuaikan dengan kebutuhan agar terminal tetap nyaman dibaca.

## 9. Menggunakan Terminal dengan Oh My Posh

Setelah PowerShell dan Oh My Posh dikonfigurasi, terminal VS Code akan menggunakan tampilan prompt yang sama selama PowerShell Profile sudah mengaktifkan Oh My Posh.

Contoh konfigurasi PowerShell Profile:

```powershell
oh-my-posh init pwsh --config "$HOME\macos-theme.omp.json" | Invoke-Expression
```

Pastikan file tema tersedia:

```powershell
Test-Path "$HOME\macos-theme.omp.json"
```

Jika hasilnya:

```text
True
```

File konfigurasi ditemukan.

Buka terminal PowerShell baru untuk menguji tampilan.

## 10. Troubleshooting

### A. Terminal menghilang setelah menekan CTRL + J

Penyebabnya adalah shortcut tersebut digunakan untuk menyembunyikan panel bawah VS Code.

Solusi:

```text
CTRL + J
```

Tekan kembali shortcut tersebut untuk menampilkan panel.

### B. Ikon terminal tidak tampil dengan benar

Pastikan Meslo Nerd Font sudah terpasang dan dipilih melalui pengaturan:

```json
{
  "terminal.integrated.fontFamily": "MesloLGS NF"
}
```

Kemudian tutup dan buka kembali terminal.

### C. Warna terminal tidak berubah

Periksa kembali:

- File User Settings JSON.
- Struktur JSON.
- Pengaturan warna terminal.
- Apakah ada konfigurasi warna lain yang bertabrakan.

Setelah mengubah pengaturan, buka terminal baru untuk menguji hasilnya.

### D. Ubuntu tidak muncul sebagai profil terminal

Periksa instalasi WSL:

```powershell
wsl --list --verbose
```

Jika Ubuntu tersedia, tetapi belum muncul di daftar profil terminal, periksa instalasi ekstensi WSL dan konfigurasi terminal VS Code.

### E. PowerShell tidak menggunakan tema Oh My Posh

Periksa PowerShell Profile:

```powershell
Get-Content $PROFILE
```

Pastikan inisialisasi Oh My Posh sudah tersedia dan lokasi file tema benar.

## 11. Hasil Akhir

Setelah mengikuti panduan ini, pengguna diharapkan sudah dapat:

- Mengatur font terminal.
- Mengubah warna terminal menjadi gelap.
- Mengatur ukuran dan jarak teks.
- Menggunakan PowerShell sebagai shell default.
- Mengintegrasikan Ubuntu WSL.
- Membuka beberapa sesi terminal.
- Menggunakan Oh My Posh melalui integrated terminal.

Dengan pengaturan tersebut, Visual Studio Code dapat menjadi lingkungan development yang lebih nyaman dan konsisten.

## 12. Referensi

- VS Code Integrated Terminal: https://code.visualstudio.com/docs/terminal/basics
- VS Code Terminal Profiles: https://code.visualstudio.com/docs/terminal/profiles
- VS Code Settings: https://code.visualstudio.com/docs/configure/settings
- VS Code Remote Development: https://code.visualstudio.com/docs/remote/remote-overview
- WSL Documentation: https://learn.microsoft.com/windows/wsl/

---

**Previous:** [03 — PowerShell & Oh My Posh](03-powershell-oh-my-posh.md)

**Next:** [05 — macOS Inspired Look](05-macos-inspired-look.md)