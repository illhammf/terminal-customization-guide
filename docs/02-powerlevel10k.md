# 02 — Powerlevel10k

Powerlevel10k merupakan tema Zsh yang dirancang untuk memberikan tampilan terminal yang menarik, responsif, dan mudah dikustomisasi.

Tema ini menyediakan berbagai fitur, seperti informasi Git, direktori aktif, waktu eksekusi perintah, Instant Prompt, dan Transient Prompt.

Panduan ini menggunakan Ubuntu melalui WSL dan Oh My Zsh sebagai framework.

## 1. Mengenal Powerlevel10k

Powerlevel10k adalah tema untuk Zsh yang berfokus pada kecepatan, fleksibilitas, dan kemudahan konfigurasi.

Beberapa fitur yang tersedia:

- Configuration Wizard.
- Informasi Git branch dan status repository.
- Tampilan direktori aktif.
- Informasi waktu eksekusi perintah.
- Instant Prompt.
- Transient Prompt.
- Dukungan Nerd Font.
- Kustomisasi warna dan simbol.

Repository resmi:

https://github.com/romkatv/powerlevel10k

## 2. Persiapan

Sebelum memasang Powerlevel10k, pastikan beberapa kebutuhan berikut sudah tersedia:

- WSL 2.
- Ubuntu.
- Zsh.
- Oh My Zsh.
- Git.
- Meslo Nerd Font.

Periksa pengguna aktif:

```bash
whoami
```

Periksa lokasi home:

```bash
echo $HOME
```

Periksa versi Zsh:

```bash
zsh --version
```

**Penting:** Instalasi harus dilakukan menggunakan user biasa yang ingin menggunakan tema tersebut.

Jangan menjalankan instalasi dari akun root jika tujuanmu adalah mengubah tampilan terminal user biasa.

## 3. Instalasi Powerlevel10k

Pastikan Oh My Zsh sudah tersedia.

Kemudian jalankan perintah berikut:

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"
```

Perintah tersebut akan mengunduh Powerlevel10k ke direktori tema kustom Oh My Zsh.

Lokasi instalasi secara default:

```text
~/.oh-my-zsh/custom/themes/powerlevel10k
```

### Memeriksa instalasi

Jalankan:

```bash
ls -la "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"
```

Jika direktori tersebut berisi file tema, instalasi sudah berhasil.

**Catatan:** Jika direktori Powerlevel10k sudah tersedia, jangan melakukan clone ulang. Periksa instalasi yang ada terlebih dahulu.

## 4. Mengaktifkan Powerlevel10k

Buka file konfigurasi:

```bash
nano ~/.zshrc
```

Cari bagian:

```bash
ZSH_THEME="robbyrussell"
```

Ganti menjadi:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Pastikan hanya ada satu konfigurasi `ZSH_THEME` yang aktif.

Simpan perubahan, kemudian muat ulang konfigurasi:

```bash
source ~/.zshrc
```

Jika wizard konfigurasi tidak muncul secara otomatis, jalankan:

```bash
p10k configure
```

## 5. Instalasi Meslo Nerd Font

Powerlevel10k merekomendasikan Meslo Nerd Font untuk menampilkan simbol, ikon, dan karakter khusus dengan benar.

Repository dan dokumentasi:

https://github.com/romkatv/powerlevel10k

### Mengunduh font

Untuk pengguna WSL, font perlu dipasang pada Windows sebagai sistem host karena terminal WSL menggunakan font yang disediakan oleh aplikasi terminal Windows.

Pilihan font yang direkomendasikan:

- MesloLGS NF Regular.
- MesloLGS NF Bold.
- MesloLGS NF Italic.
- MesloLGS NF Bold Italic.

Ikuti petunjuk instalasi font pada dokumentasi resmi Powerlevel10k.

### Mengatur font pada Windows Terminal

Setelah font terpasang:

1. Buka Windows Terminal.
2. Masuk ke Settings.
3. Pilih profil Ubuntu.
4. Buka Appearance.
5. Cari Font face.
6. Pilih MesloLGS NF.
7. Simpan pengaturan.

Jika menggunakan VS Code, pengaturan font terminal dapat dilakukan melalui:

```json
{
  "terminal.integrated.fontFamily": "MesloLGS NF"
}
```

Tutup dan buka kembali terminal setelah mengganti font.

## 6. Configuration Wizard

Setelah Powerlevel10k aktif, jalankan:

```bash
p10k configure
```

Wizard akan menampilkan beberapa pertanyaan untuk menentukan tampilan terminal.

Pilihan yang muncul dapat berbeda tergantung versi dan konfigurasi yang digunakan.

### Tahapan konfigurasi

**1. Character appearance**

Wizard akan meminta pengguna mengidentifikasi karakter atau simbol yang ditampilkan.

Pilih jawaban yang sesuai dengan simbol yang terlihat.

**2. Character Set**

Biasanya tersedia pilihan:

- Unicode.
- ASCII.

Pilih Unicode jika terminal sudah mendukung karakter dan font yang direkomendasikan.

**3. Prompt Style**

Pilih gaya prompt sesuai preferensi.

Beberapa gaya memiliki tampilan minimalis, sedangkan gaya lainnya menampilkan informasi lebih lengkap.

**4. Prompt Colors**

Pilih kombinasi warna yang paling sesuai dengan tampilan terminal yang diinginkan.

**5. Transient Prompt**

Fitur ini menyederhanakan prompt sebelumnya setelah sebuah perintah dijalankan.

Fitur tersebut membantu menjaga riwayat terminal tetap rapi.

**6. Instant Prompt**

Fitur ini membantu mempercepat tampilan awal Zsh ketika terminal dibuka.

Pilih mode yang sesuai dengan kebutuhan.

Setelah semua pertanyaan selesai, Powerlevel10k akan menyimpan konfigurasi.

## 7. Mengenal File .p10k.zsh

Powerlevel10k menyimpan pengaturan prompt dalam file:

```text
~/.p10k.zsh
```

File tersebut dibuat oleh Configuration Wizard.

Periksa keberadaannya:

```bash
ls -la ~/.p10k.zsh
```

Untuk mengubah pengaturan secara manual:

```bash
nano ~/.p10k.zsh
```

Beberapa pengaturan yang dapat dikustomisasi:

- Warna prompt.
- Informasi direktori.
- Informasi Git.
- Ikon dan simbol.
- Posisi elemen prompt.
- Tampilan waktu eksekusi.

Setelah melakukan perubahan, muat ulang konfigurasi:

```bash
source ~/.zshrc
```

## 8. Mengenal Instant Prompt

Instant Prompt merupakan fitur Powerlevel10k yang membantu menampilkan prompt lebih cepat ketika Zsh dijalankan.

Fitur ini berguna ketika konfigurasi Zsh memiliki banyak plugin atau proses inisialisasi yang membutuhkan waktu.

Pengaturannya dapat dilakukan melalui:

```bash
p10k configure
```

Secara otomatis, konfigurasi Instant Prompt dapat ditambahkan ke bagian awal `~/.zshrc`.

Contoh konfigurasi:

```bash
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi
```

Letakkan blok tersebut dekat bagian atas `~/.zshrc`.

**Perhatian:** Perintah yang membutuhkan input pengguna, seperti konfirmasi atau permintaan password, harus dijalankan sebelum blok Instant Prompt.

Jika muncul peringatan akibat output selama inisialisasi, periksa konfigurasi Zsh sebelum mengubah mode Instant Prompt.

## 9. Mengenal Transient Prompt

Transient Prompt merupakan fitur untuk menyederhanakan prompt lama setelah perintah selesai dijalankan.

Tanpa Transient Prompt, setiap perintah dapat mempertahankan informasi prompt lengkap.

Dengan Transient Prompt, riwayat perintah menjadi lebih ringkas sehingga lebih mudah dibaca.

Aktifkan melalui:

```bash
p10k configure
```

Pilih pengaturan Transient Prompt yang tersedia pada wizard.

Fitur ini juga dapat dikombinasikan dengan prompt dua baris untuk mendapatkan tampilan terminal yang lebih nyaman.

## 10. Troubleshooting

### A. Repository tidak ditemukan ketika clone

Contoh kesalahan:

```text
fatal: repository 'https://github.com/' not found
```

Penyebabnya adalah URL Git yang digunakan tidak menunjuk ke repository Powerlevel10k.

Gunakan URL lengkap:

```bash
https://github.com/romkatv/powerlevel10k.git
```

### B. Powerlevel10k tidak muncul

Periksa konfigurasi tema:

```bash
grep '^ZSH_THEME=' ~/.zshrc
```

Pastikan hasilnya:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Periksa direktori tema:

```bash
ls ~/.oh-my-zsh/custom/themes/powerlevel10k
```

Jika direktori tersedia, coba muat ulang:

```bash
source ~/.zshrc
```

### C. File .p10k.zsh tidak ditemukan

Periksa:

```bash
ls -la ~/.p10k.zsh
```

Jika belum tersedia, jalankan:

```bash
p10k configure
```

Wizard akan membantu membuat konfigurasi baru.

### D. Ikon tidak tampil dengan benar

Pastikan:

- Meslo Nerd Font sudah terpasang pada Windows.
- Profil Ubuntu menggunakan font yang benar.
- Terminal sudah dibuka ulang.
- Character Set menggunakan Unicode jika didukung.

### E. Powerlevel10k terpasang di akun root

Periksa pengguna aktif:

```bash
whoami
```

Periksa direktori home:

```bash
echo $HOME
```

Jika kamu menggunakan user biasa, instalasi seharusnya berada di:

```text
/home/username/.oh-my-zsh/custom/themes/powerlevel10k
```

Bukan:

```text
/root/.oh-my-zsh/custom/themes/powerlevel10k
```

Konfigurasi root dan user biasa harus dikelola secara terpisah.

## 11. Hasil Akhir

Setelah mengikuti panduan ini, pengguna diharapkan sudah memiliki:

- Powerlevel10k terpasang pada Oh My Zsh.
- Tema Powerlevel10k aktif.
- Meslo Nerd Font terpasang.
- Konfigurasi prompt melalui wizard.
- Instant Prompt yang sudah dikonfigurasi.
- Transient Prompt sesuai preferensi.

Terminal sekarang sudah memiliki tampilan yang lebih informatif dan dapat dikustomisasi sesuai kebutuhan.

## 12. Referensi

- Powerlevel10k GitHub: https://github.com/romkatv/powerlevel10k
- Powerlevel10k Installation: https://github.com/romkatv/powerlevel10k#installation
- Powerlevel10k Configuration: https://github.com/romkatv/powerlevel10k#configuration
- Oh My Zsh: https://ohmyz.sh/
- Zsh Documentation: https://zsh.sourceforge.io/Doc/

---

**Previous:** [01 — WSL Ubuntu & Zsh](01-wsl-ubuntu-zsh.md)

**Next:** [03 — PowerShell & Oh My Posh](03-powershell-oh-my-posh.md)