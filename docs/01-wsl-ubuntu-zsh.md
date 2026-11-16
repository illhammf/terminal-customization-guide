\# 01 — WSL Ubuntu \& Zsh



Panduan ini membahas persiapan lingkungan Linux menggunakan Windows Subsystem for Linux (WSL), instalasi Ubuntu, Zsh, dan Oh My Zsh.



Tujuannya adalah membangun lingkungan terminal yang nyaman untuk aktivitas development sebelum melanjutkan ke kustomisasi Powerlevel10k.



\## 1. Persiapan WSL



\### Apa itu WSL?



Windows Subsystem for Linux (WSL) memungkinkan pengguna menjalankan lingkungan Linux secara langsung di Windows tanpa harus menggunakan virtual machine tradisional.



Dalam panduan ini, kita menggunakan:



\- Windows 10/11

\- WSL 2

\- Ubuntu

\- Zsh

\- Oh My Zsh



\### Memeriksa WSL



Buka PowerShell Windows dan jalankan:



```powershell

wsl --status

```



Untuk melihat distribusi Linux yang tersedia:



```powershell

wsl --list --verbose

```



Pastikan Ubuntu menggunakan WSL 2.



Jika belum terpasang, instal Ubuntu melalui PowerShell:



```powershell

wsl --install -d Ubuntu

```



Ikuti proses konfigurasi awal Ubuntu sampai selesai.



\## 2. Memperbarui Ubuntu



Buka terminal Ubuntu, kemudian perbarui daftar paket:



```bash

sudo apt update

```



Perbarui paket yang sudah terinstal:



```bash

sudo apt upgrade -y

```



Instal beberapa kebutuhan dasar:



```bash

sudo apt install zsh git curl wget -y

```



Periksa instalasi:



```bash

zsh --version

git --version

curl --version

```



\## 3. Mengenal Root dan User Biasa



Linux memiliki sistem pengguna yang berbeda, termasuk root dan user biasa.



\*\*Root\*\*



Root merupakan akun administrator dengan hak akses penuh terhadap sistem Linux.



\*\*User biasa\*\*



User biasa merupakan akun yang digunakan untuk aktivitas sehari-hari, seperti mengelola project, menjalankan Git, dan menggunakan berbagai tools development.



Sebaiknya konfigurasi terminal sehari-hari dilakukan menggunakan user biasa.



Periksa pengguna aktif:



```bash

whoami

```



Periksa direktori home:



```bash

echo $HOME

```



Periksa informasi akun:



```bash

getent passwd "$USER"

```



Contoh hasil:



```text

ilhamfirmansyah:x:1000:1000:,,,:/home/ilhamfirmansyah:/usr/bin/zsh

```



Perhatikan bahwa konfigurasi milik root dan user biasa berada di direktori home yang berbeda.



```text

/root/

├── .zshrc

└── .oh-my-zsh/



/home/username/

├── .zshrc

└── .oh-my-zsh/

```



Jangan mencampurkan konfigurasi kedua akun tersebut.



\## 4. Instalasi Zsh



Zsh merupakan shell alternatif yang menyediakan berbagai fitur tambahan untuk pengalaman bekerja di terminal.



Instalasi:



```bash

sudo apt install zsh -y

```



Periksa versi:



```bash

zsh --version

```



Contoh:



```text

zsh 5.9 (x86\_64-ubuntu-linux-gnu)

```



\### Mengatur Zsh sebagai Default Shell



Jalankan:



```bash

chsh -s "$(command -v zsh)"

```



Setelah itu, tutup sesi terminal dan buka kembali Ubuntu.



Jika perubahan belum diterapkan, periksa shell akun:



```bash

getent passwd "$USER"

```



Pastikan bagian terakhir menunjukkan lokasi Zsh, misalnya:



```text

/usr/bin/zsh

```



\## 5. Instalasi Oh My Zsh



Oh My Zsh merupakan framework untuk mengelola konfigurasi Zsh, tema, dan plugin.



Dokumentasi resmi:



https://ohmyz.sh/



Pastikan kamu menjalankan instalasi menggunakan user biasa, bukan root.



Jalankan:



```bash

sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

```



Tunggu sampai proses instalasi selesai.



Oh My Zsh akan membuat direktori:



```text

\~/.oh-my-zsh/

```



Serta file konfigurasi:



```text

\~/.zshrc

```



\### Memeriksa Instalasi



Periksa direktori Oh My Zsh:



```bash

ls -la \~/.oh-my-zsh

```



Periksa file konfigurasi:



```bash

ls -la \~/.zshrc

```



Jika kedua lokasi tersebut tersedia, instalasi sudah berhasil.



\*\*Catatan:\*\* Jika Oh My Zsh sudah terpasang, tidak perlu menjalankan instalasi ulang. Langsung gunakan konfigurasi yang tersedia.



\## 6. Mengenal File .zshrc



File `.zshrc` merupakan file konfigurasi utama untuk shell Zsh.



Buka menggunakan Nano:



```bash

nano \~/.zshrc

```



Salah satu bagian penting yang akan ditemukan adalah:



```bash

ZSH\_THEME="robbyrussell"

```



Bagian tersebut menentukan tema yang digunakan Oh My Zsh.



Tema dapat diganti sesuai kebutuhan, termasuk menggunakan Powerlevel10k yang akan dibahas pada dokumentasi berikutnya.



Untuk menyimpan perubahan di Nano:



\- `CTRL + O` untuk menyimpan.

\- Enter untuk mengonfirmasi.

\- `CTRL + X` untuk keluar.



Terapkan konfigurasi:



```bash

source \~/.zshrc

```



\## 7. Perintah Dasar Zsh



Beberapa perintah dasar yang berguna:



| Perintah | Fungsi |

|---|---|

| `pwd` | Melihat direktori aktif |

| `ls` | Melihat isi direktori |

| `ls -la` | Melihat seluruh file termasuk tersembunyi |

| `cd nama-folder` | Masuk ke direktori |

| `cd ..` | Kembali satu tingkat |

| `cd \~` | Menuju direktori home |

| `whoami` | Melihat pengguna aktif |

| `clear` | Membersihkan terminal |

| `source \~/.zshrc` | Memuat ulang konfigurasi Zsh |



\## 8. Troubleshooting



\### Zsh tidak ditemukan



Jika muncul:



```text

zsh: command not found

```



Jalankan:



```bash

sudo apt update

sudo apt install zsh -y

```



\### Oh My Zsh tidak ditemukan



Periksa:



```bash

ls -la \~/.oh-my-zsh

```



Jika direktori belum tersedia, instal Oh My Zsh menggunakan langkah sebelumnya.



\### Konfigurasi tidak berubah



Muat ulang konfigurasi:



```bash

source \~/.zshrc

```



Jika masih bermasalah, periksa apakah kamu sedang menggunakan user yang benar:



```bash

whoami

echo $HOME

```



\### Konfigurasi root dan user berbeda



Periksa lokasi home:



```bash

echo $HOME

```



Jangan mengedit `/root/.zshrc` jika tujuanmu adalah mengubah konfigurasi user biasa.



\## 9. Hasil Akhir



Setelah menyelesaikan panduan ini, lingkungan Linux seharusnya sudah memiliki:



\- WSL 2 dan Ubuntu.

\- Zsh sebagai shell.

\- Oh My Zsh sebagai framework.

\- File konfigurasi `.zshrc`.

\- Lingkungan user biasa yang terpisah dari root.



Selanjutnya, kita akan melakukan kustomisasi tampilan terminal menggunakan Powerlevel10k.



\## 10. Referensi



\- WSL Documentation: https://learn.microsoft.com/windows/wsl/

\- Ubuntu Documentation: https://documentation.ubuntu.com/

\- Zsh Documentation: https://zsh.sourceforge.io/Doc/

\- Oh My Zsh: https://ohmyz.sh/

\- Oh My Zsh GitHub: https://github.com/ohmyzsh/ohmyzsh



\---



\*\*Next:\*\* \[02 — Powerlevel10k](02-powerlevel10k.md)

