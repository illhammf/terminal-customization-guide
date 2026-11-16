# Troubleshooting: Mengatasi Masalah Terminal

Dokumen ini berisi panduan untuk mengatasi berbagai masalah yang mungkin muncul ketika melakukan kustomisasi terminal Windows, PowerShell, WSL, Zsh, Oh My Zsh, Powerlevel10k, Oh My Posh, dan Visual Studio Code.

Panduan ini disusun berdasarkan masalah yang umum ditemui selama proses instalasi dan konfigurasi.

Tujuannya adalah membantu pengguna memahami penyebab masalah dan memperbaikinya secara bertahap.

---

## Daftar Isi

1. [Masalah pada WSL dan Ubuntu](#1-masalah-pada-wsl-dan-ubuntu)
2. [Masalah pada Zsh dan Oh My Zsh](#2-masalah-pada-zsh-dan-oh-my-zsh)
3. [Masalah pada Powerlevel10k](#3-masalah-pada-powerlevel10k)
4. [Masalah pada PowerShell dan Oh My Posh](#4-masalah-pada-powershell-dan-oh-my-posh)
5. [Masalah pada Windows Terminal](#5-masalah-pada-windows-terminal)
6. [Masalah pada VS Code](#6-masalah-pada-vs-code)
7. [Tips Sebelum Memperbaiki Error](#7-tips-sebelum-memperbaiki-error)

---

## 1. Masalah pada WSL dan Ubuntu

### 1.1 WSL Tidak Bisa Dibuka

**Gejala:**

Ketika menjalankan Ubuntu, terminal tidak terbuka atau menampilkan pesan kesalahan.

**Penyebab yang mungkin:**

- WSL belum terpasang dengan benar.
- Distribusi Ubuntu belum terinstal.
- WSL sedang mengalami masalah.

**Cara memeriksa:**

Buka PowerShell, kemudian jalankan:

```powershell
wsl --status
```

Untuk melihat daftar distribusi Linux yang tersedia:

```powershell
wsl --list --verbose
```

**Solusi:**

Jika Ubuntu tersedia, coba jalankan secara langsung:

```powershell
wsl -d Ubuntu
```

Jika distribusi belum tersedia, instal Ubuntu melalui petunjuk resmi Microsoft dan Ubuntu.

### 1.2 Perintah Berjalan pada User yang Salah

**Gejala:**

Konfigurasi yang sudah dibuat tidak muncul ketika membuka terminal seperti biasanya.

Contohnya, tema Zsh sudah dipasang, tetapi ketika membuka Ubuntu sebagai pengguna biasa, tampilannya masih sama seperti sebelumnya.

**Penyebab:**

Linux memisahkan direktori konfigurasi setiap pengguna.

Contohnya:

| Pengguna | Direktori Home |
|---|---|
| Root | `/root` |
| User biasa | `/home/ilhamfirmansyah` |

Artinya, konfigurasi yang dibuat di `/root` tidak otomatis berlaku untuk pengguna biasa.

**Cara memeriksa:**

Jalankan:

```bash
whoami
```

Kemudian:

```bash
echo $HOME
```

Perintah pertama menunjukkan pengguna yang sedang aktif. Perintah kedua menunjukkan direktori Home pengguna tersebut.

**Solusi:**

Pastikan instalasi dan konfigurasi dilakukan pada pengguna yang memang digunakan sehari-hari.

Jangan langsung menyalin konfigurasi dari `/root` ke direktori pengguna biasa tanpa memahami isi dan kepemilikannya.

---

## 2. Masalah pada Zsh dan Oh My Zsh

### 2.1 Perintah `zsh` Tidak Ditemukan

**Gejala:**

Terminal menampilkan pesan:

```text
zsh: command not found
```

**Penyebab:**

Zsh belum terpasang atau instalasinya belum selesai.

**Solusi:**

Pada Ubuntu, jalankan:

```bash
sudo apt update
sudo apt install zsh -y
```

Setelah instalasi selesai, periksa versinya:

```bash
zsh --version
```

Jika berhasil, terminal akan menampilkan informasi versi Zsh.

### 2.2 Oh My Zsh Tidak Terpasang

**Gejala:**

Folder `.oh-my-zsh` tidak ditemukan atau konfigurasi Oh My Zsh tidak berjalan.

**Cara memeriksa:**

```bash
ls -la ~/.oh-my-zsh
```

Jika folder tersebut tidak ditemukan, kemungkinan Oh My Zsh belum terpasang pada pengguna yang sedang aktif.

**Solusi:**

Ikuti petunjuk instalasi dari dokumentasi resmi Oh My Zsh:

https://ohmyz.sh/

Setelah instalasi selesai, periksa kembali:

```bash
ls -la ~/.oh-my-zsh
```

### 2.3 Tema Zsh Tidak Muncul

**Gejala:**

Tema yang sudah dipilih tidak berubah ketika membuka terminal.

**Penyebab yang mungkin:**

- Nama tema pada `.zshrc` salah.
- Tema belum terpasang.
- Konfigurasi belum dimuat ulang.
- Pengaturan dilakukan pada akun pengguna yang berbeda.

**Cara memeriksa:**

Buka konfigurasi Zsh:

```bash
nano ~/.zshrc
```

Cari bagian:

```bash
ZSH_THEME="nama-tema"
```

Pastikan nama tema sesuai dengan tema yang digunakan.

Jika menggunakan Powerlevel10k, contohnya:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Setelah memastikan konfigurasinya benar, muat ulang:

```bash
source ~/.zshrc
```

---

## 3. Masalah pada Powerlevel10k

### 3.1 Tema Powerlevel10k Tidak Ditemukan

**Gejala:**

Terminal menampilkan pesan bahwa tema `powerlevel10k` tidak ditemukan.

**Penyebab:**

Folder Powerlevel10k belum berada di lokasi tema khusus Oh My Zsh.

**Cara memeriksa:**

```bash
ls ~/.oh-my-zsh/custom/themes/
```

Pastikan terdapat folder:

```text
powerlevel10k
```

**Solusi:**

Jika belum ada, pasang Powerlevel10k menggunakan perintah:

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Kemudian pastikan `.zshrc` menggunakan:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Muat ulang konfigurasi:

```bash
source ~/.zshrc
```

### 3.2 Ikon Berubah Menjadi Kotak atau Simbol Aneh

**Gejala:**

Tampilan prompt menunjukkan kotak kosong, tanda tanya, atau simbol yang tidak sesuai.

**Penyebab:**

Font terminal belum mendukung karakter khusus yang digunakan Powerlevel10k.

**Solusi:**

1. Instal font Meslo Nerd Font atau MesloLGS NF pada Windows.
2. Buka pengaturan Windows Terminal.
3. Pilih profil Ubuntu yang digunakan.
4. Buka bagian Appearance.
5. Ubah Font face menjadi `MesloLGS NF`.
6. Simpan pengaturan.
7. Tutup dan buka kembali terminal.

**Catatan:**

Font harus terpasang pada Windows, bukan hanya di dalam Ubuntu WSL.

### 3.3 Konfigurasi Powerlevel10k Tidak Muncul

**Gejala:**

Terminal tidak menampilkan pengaturan Powerlevel10k atau konfigurasi sebelumnya tidak diterapkan.

**Cara memeriksa:**

```bash
ls -la ~/.p10k.zsh
```

File `.p10k.zsh` digunakan untuk menyimpan konfigurasi tampilan Powerlevel10k.

**Solusi:**

Jika file tersebut tersedia, jalankan:

```bash
source ~/.zshrc
```

Jika ingin mengatur ulang tampilan, jalankan:

```bash
p10k configure
```

Ikuti pertanyaan konfigurasi yang muncul sampai selesai.

---

## 4. Masalah pada PowerShell dan Oh My Posh

### 4.1 Perintah `oh-my-posh` Tidak Dikenali

**Gejala:**

PowerShell menampilkan pesan:

```text
oh-my-posh : The term 'oh-my-posh' is not recognized
```

**Penyebab yang mungkin:**

- Oh My Posh belum terinstal.
- PATH belum diperbarui.
- Terminal masih menggunakan sesi lama.

**Solusi:**

Periksa apakah Oh My Posh sudah terpasang:

```powershell
oh-my-posh version
```

Jika belum terpasang, instal melalui Windows Package Manager:

```powershell
winget install JanDeDobbeleer.OhMyPosh --source winget
```

Setelah instalasi selesai, tutup PowerShell dan buka kembali.

Kemudian periksa ulang:

```powershell
oh-my-posh version
```

### 4.2 Tema Oh My Posh Tidak Berubah

**Gejala:**

PowerShell masih menampilkan prompt standar meskipun konfigurasi tema sudah dibuat.

**Penyebab:**

Perintah inisialisasi Oh My Posh belum dimasukkan ke profil PowerShell atau belum dijalankan.

**Solusi:**

Jalankan perintah berikut:

```powershell
oh-my-posh init pwsh --config "$HOME\macos-theme.omp.json" | Invoke-Expression
```

Jika tema berhasil muncul, masukkan perintah yang sama ke profil PowerShell agar otomatis dijalankan setiap kali terminal dibuka.

Periksa lokasi profil:

```powershell
$PROFILE
```

### 4.3 File Konfigurasi JSON Mengalami Error

**Gejala:**

Oh My Posh menampilkan pesan seperti:

```text
CONFIG PARSE ERROR
```

**Penyebab yang mungkin:**

- Ada tanda koma yang tidak sesuai.
- Tanda kurung kurawal tidak berpasangan.
- Tanda kutip tidak lengkap.
- Struktur JSON salah.

**Cara memeriksa:**

Jalankan:

```powershell
Get-Content "$HOME\macos-theme.omp.json" -Raw | ConvertFrom-Json
```

Jika tidak muncul error, berarti sintaks JSON dapat dibaca oleh PowerShell.

Namun, perlu diingat bahwa pemeriksaan ini hanya memeriksa format JSON. Belum tentu seluruh konfigurasi sudah sesuai dengan struktur yang dibutuhkan Oh My Posh.

**Solusi:**

Periksa kembali file konfigurasi dan cocokkan strukturnya dengan dokumentasi resmi:

https://ohmyposh.dev/docs/

### 4.4 Folder dengan Nama yang Memiliki Spasi Tidak Bisa Dibuka

**Gejala:**

Ketika menjalankan:

```powershell
cd Belajar Dart
```

PowerShell menampilkan error karena nama folder dianggap sebagai beberapa argumen.

**Penyebab:**

Nama folder memiliki spasi sehingga perlu ditulis menggunakan tanda kutip.

**Solusi:**

Gunakan:

```powershell
cd "Belajar Dart"
```

Atau gunakan alamat lengkap:

```powershell
cd "C:\Dokumen\Belajar Dart"
```

**Tips:**

Gunakan tombol `Tab` untuk membantu melengkapi nama folder secara otomatis.

---

## 5. Masalah pada Windows Terminal

### 5.1 Background Image Tidak Muncul

**Gejala:**

Gambar latar belakang tidak tampil meskipun lokasi file sudah dimasukkan ke pengaturan.

**Penyebab yang mungkin:**

- Lokasi file gambar salah.
- Nama file atau ekstensi tidak sesuai.
- Pengaturan dimasukkan ke profil terminal yang berbeda.
- Format JSON mengalami kesalahan.

**Solusi:**

Pastikan file gambar memang tersedia pada lokasi yang ditentukan.

Contoh:

```json
"backgroundImage": "C:\\Users\\HP\\Pictures\\Terminal\\forest.jpg"
```

Perhatikan bahwa karakter `\\` digunakan untuk menuliskan backslash di dalam JSON.

Pastikan juga properti gambar dimasukkan ke profil Windows Terminal yang sedang digunakan.

### 5.2 Efek Transparan Tidak Berfungsi

**Gejala:**

Terminal tidak terlihat transparan meskipun pengaturan Acrylic sudah diaktifkan.

**Penyebab yang mungkin:**

- Efek Acrylic tidak didukung dalam kondisi sistem tertentu.
- Pengaturan transparansi belum disimpan.
- Efek transparansi dibatasi oleh sistem atau kebijakan perangkat.

**Solusi:**

Periksa pengaturan profil Windows Terminal:

```json
"useAcrylic": true,
"opacity": 85
```

Kemudian simpan dan buka kembali terminal.

Jika tetap tidak berfungsi, coba gunakan transparansi tanpa Acrylic atau periksa pengaturan sistem Windows.

**Catatan:**

Tampilan Acrylic dapat dipengaruhi oleh kondisi perangkat dan lingkungan Windows. Jadi, tidak semua perangkat akan menampilkan efek yang sama.

---

## 6. Masalah pada VS Code

### 6.1 Terminal Tidak Menggunakan Font yang Dipilih

**Gejala:**

Font di editor sudah berubah, tetapi terminal masih menggunakan font sebelumnya.

**Penyebab:**

Pengaturan font editor dan terminal merupakan dua pengaturan yang berbeda.

**Solusi:**

Buka User Settings (JSON), kemudian pastikan terdapat pengaturan:

```json
"terminal.integrated.fontFamily": "MesloLGS NF"
```

Simpan perubahan dan buat terminal baru.

### 6.2 Terminal Tidak Bisa Membuka Ubuntu

**Gejala:**

Profil terminal WSL tidak muncul atau Ubuntu tidak bisa dijalankan dari VS Code.

**Solusi:**

Pastikan WSL dapat dijalankan melalui PowerShell:

```powershell
wsl -d Ubuntu
```

Jika berhasil, buka Command Palette di VS Code menggunakan:

```text
Ctrl + Shift + P
```

Cari perintah:

```text
Terminal: Select Default Profile
```

Pilih profil Ubuntu atau WSL yang tersedia.

### 6.3 Panel Terminal Tidak Terlihat

**Gejala:**

Terminal tiba-tiba menghilang dari bagian bawah VS Code.

**Penyebab:**

Panel terminal mungkin hanya disembunyikan, bukan dihapus.

**Solusi:**

Tekan:

```text
Ctrl + J
```

Shortcut tersebut digunakan untuk menampilkan atau menyembunyikan panel bawah VS Code.

Untuk membuka terminal baru, gunakan:

```text
Ctrl + Shift + `
```

### 6.4 Background Image Tidak Bisa Dipasang pada Terminal VS Code

**Gejala:**

Pengguna ingin memasang wallpaper atau efek Acrylic seperti Windows Terminal, tetapi pengaturan tersebut tidak bekerja di terminal bawaan VS Code.

**Penjelasan:**

Terminal terintegrasi VS Code memiliki sistem pengaturan tampilan sendiri. Pengaturan background image dan Acrylic milik Windows Terminal tidak otomatis berlaku di dalam VS Code.

**Solusi:**

Gunakan pengaturan warna terminal melalui `workbench.colorCustomizations` dan sesuaikan font, ukuran teks, serta warna prompt.

Jika ingin menggunakan wallpaper dan Acrylic, gunakan aplikasi Windows Terminal.

---

## 7. Tips Sebelum Memperbaiki Error

Ketika menemukan masalah, jangan langsung menghapus konfigurasi atau menginstal ulang semua komponen.

Lakukan pemeriksaan secara bertahap.

### 7.1 Periksa Versi Program

Beberapa perintah yang dapat digunakan:

**PowerShell:**

```powershell
$PSVersionTable
```

```powershell
oh-my-posh version
```

**Ubuntu / WSL:**

```bash
zsh --version
```

```bash
git --version
```

### 7.2 Periksa Pengguna yang Sedang Aktif

Pada Ubuntu atau WSL:

```bash
whoami
```

```bash
echo $HOME
```

Pastikan konfigurasi dibuat pada akun yang benar.

### 7.3 Periksa Lokasi File Konfigurasi

Contoh lokasi konfigurasi:

| Komponen | Lokasi |
|---|---|
| Zsh | `~/.zshrc` |
| Powerlevel10k | `~/.p10k.zsh` |
| Oh My Zsh | `~/.oh-my-zsh` |
| PowerShell Profile | `$PROFILE` |
| Oh My Posh Config | `$HOME\macos-theme.omp.json` |
| VS Code Settings | User Settings (JSON) |

### 7.4 Jangan Menghapus Konfigurasi Sebelum Membuat Cadangan

Sebelum mengubah file konfigurasi, buat salinannya terlebih dahulu.

Contoh pada Ubuntu:

```bash
cp ~/.zshrc ~/.zshrc.backup
```

Contoh pada PowerShell:

```powershell
Copy-Item $PROFILE "$PROFILE.backup"
```

Jika terjadi kesalahan, cadangan tersebut dapat digunakan untuk mengembalikan konfigurasi sebelumnya.

---

## Penutup

Masalah saat melakukan kustomisasi terminal merupakan hal yang wajar, terutama ketika baru pertama kali menggunakan WSL, Zsh, Powerlevel10k, PowerShell, dan Oh My Posh.

Hal terpenting adalah memahami penyebab masalah sebelum melakukan perubahan.

Jika satu langkah belum berhasil, periksa kembali pesan error dan konfigurasi yang digunakan. Hindari mengubah banyak pengaturan sekaligus agar lebih mudah menemukan sumber masalah.

**Referensi resmi:**

- WSL: https://learn.microsoft.com/windows/wsl/
- Oh My Zsh: https://ohmyz.sh/
- Powerlevel10k: https://github.com/romkatv/powerlevel10k
- Oh My Posh: https://ohmyposh.dev/docs/
- Windows Terminal: https://learn.microsoft.com/windows/terminal/
- Visual Studio Code: https://code.visualstudio.com/docs

---

**Dokumentasi berikutnya:** [Kembali ke Dokumentasi Utama](../README.md)