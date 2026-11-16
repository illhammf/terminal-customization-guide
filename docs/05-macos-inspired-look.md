# 05 — macOS Inspired Terminal Look

Panduan ini membahas cara mengubah tampilan terminal Windows agar memiliki nuansa seperti terminal macOS.

Kustomisasi meliputi background gelap, transparansi Acrylic, gambar latar belakang, warna terminal, dan pengaturan tampilan jendela.

Pengaturan utama menggunakan Windows Terminal, sedangkan Visual Studio Code memiliki pengaturan tampilan tersendiri.

## 1. Mengenal Windows Terminal

Windows Terminal merupakan aplikasi terminal modern dari Microsoft yang mendukung berbagai shell dalam satu aplikasi.

Beberapa shell yang dapat digunakan:

- Windows PowerShell.
- PowerShell 7.
- Command Prompt.
- Ubuntu melalui WSL.
- Git Bash.

Windows Terminal menyediakan beberapa fitur visual:

- Custom background image.
- Acrylic transparency.
- Custom color schemes.
- Font customization.
- Tab customization.
- Profile-specific appearance.

Dokumentasi resmi:

https://learn.microsoft.com/windows/terminal/

## 2. Membuka Windows Terminal Settings

Buka Windows Terminal, kemudian:

1. Klik ikon panah di samping tab.
2. Pilih Settings.
3. Pilih profil PowerShell atau Ubuntu.
4. Masuk ke bagian Appearance.

Kita dapat mengatur tampilan setiap profil secara terpisah.

Alternatifnya, gunakan shortcut:

```text
CTRL + SHIFT + ,
```

Shortcut tersebut membuka file `settings.json` Windows Terminal.

## 3. Mengatur Background Hitam

Untuk mendapatkan tampilan terminal yang minimalis, kita dapat menggunakan background hitam atau hitam kebiruan.

Buka:

```text
Windows Terminal → Settings → Profiles → PowerShell → Appearance
```

Atur warna background sesuai preferensi.

Contoh warna:

```text
#080B10
```

Warna tersebut memberikan kesan gelap dengan sedikit nuansa biru.

Jika menggunakan `settings.json`, pengaturannya dapat ditulis seperti berikut:

```json
{
  "background": "#080B10",
  "foreground": "#F5F5F5"
}
```

Background dapat dikombinasikan dengan warna teks yang terang agar tetap mudah dibaca.

## 4. Mengaktifkan Acrylic Transparency

Acrylic merupakan efek transparansi dengan latar belakang buram yang dapat membuat Windows Terminal terlihat lebih modern.

Untuk mengaktifkannya:

1. Buka Windows Terminal Settings.
2. Pilih profil PowerShell.
3. Masuk ke Appearance.
4. Aktifkan Acrylic material.
5. Sesuaikan opacity.

Alternatif melalui `settings.json`:

```json
{
  "useAcrylic": true,
  "opacity": 85
}
```

Penjelasan:

| Properti | Fungsi |
|---|---|
| `useAcrylic` | Mengaktifkan atau menonaktifkan efek Acrylic |
| `opacity` | Mengatur tingkat opasitas jendela |

Nilai opacity yang lebih rendah membuat tampilan lebih transparan.

Sebagai contoh:

- `100`: sepenuhnya opaque.
- `85`: sedikit transparan.
- `70`: lebih transparan.
- `50`: sangat transparan.

Untuk tampilan yang tetap nyaman dibaca, gunakan nilai sekitar 80–90 sebagai titik awal.

**Catatan:** Acrylic membutuhkan dukungan sistem dan dapat tidak aktif dalam kondisi tertentu, misalnya ketika Windows menggunakan mode penghemat daya.

## 5. Menggunakan Background Image

Windows Terminal mendukung gambar sebagai latar belakang profil terminal.

Fitur ini memungkinkan kita menggunakan wallpaper bertema alam, hutan, pegunungan, atau gambar gelap lainnya.

Siapkan gambar dalam format:

- PNG.
- JPG.
- GIF.

Simpan gambar di folder yang mudah ditemukan.

Contoh lokasi:

```text
C:\Users\HP\Pictures\Terminal\forest.jpg
```

Kemudian buka `settings.json` dan tambahkan konfigurasi pada profil yang ingin diubah:

```json
{
  "backgroundImage": "C:\\Users\\HP\\Pictures\\Terminal\\forest.jpg",
  "backgroundImageOpacity": 0.15,
  "backgroundImageAlignment": "center",
  "backgroundImageStretchMode": "uniformToFill"
}
```

Penjelasan:

| Properti | Fungsi |
|---|---|
| `backgroundImage` | Lokasi gambar |
| `backgroundImageOpacity` | Transparansi gambar |
| `backgroundImageAlignment` | Posisi gambar |
| `backgroundImageStretchMode` | Cara gambar menyesuaikan ukuran jendela |

Beberapa pilihan alignment:

- `center`
- `top`
- `bottom`
- `left`
- `right`
- `topLeft`
- `topRight`
- `bottomLeft`
- `bottomRight`

Beberapa pilihan stretch mode:

- `none`
- `fill`
- `uniform`
- `uniformToFill`

Untuk gambar wallpaper, `uniformToFill` dapat digunakan agar gambar mengisi area terminal.

**Tips:** Gunakan gambar yang tidak terlalu ramai dan atur opacity rendah agar teks terminal tetap terlihat jelas.

## 6. Menggabungkan Background dan Acrylic

Kita dapat menggabungkan background image dengan Acrylic.

Contoh konfigurasi:

```json
{
  "background": "#080B10",
  "foreground": "#F5F5F5",
  "useAcrylic": true,
  "opacity": 85,

  "backgroundImage": "C:\\Users\\HP\\Pictures\\Terminal\\forest.jpg",
  "backgroundImageOpacity": 0.15,
  "backgroundImageAlignment": "center",
  "backgroundImageStretchMode": "uniformToFill"
}
```

Konfigurasi ini menggunakan gambar latar dengan opacity rendah dan efek Acrylic pada profil terminal.

Pengaturan gambar dan transparansi merupakan properti yang berbeda. Atur keduanya sesuai hasil visual yang diinginkan.

## 7. Mengatur Font Terminal

Agar simbol dari Oh My Posh dapat ditampilkan dengan baik, gunakan font Nerd Font yang sudah dipasang sebelumnya.

Dalam panduan ini:

```text
MesloLGS NF
```

Untuk mengaturnya:

1. Buka Settings.
2. Pilih profil PowerShell.
3. Masuk ke Appearance.
4. Pilih Font face.
5. Pilih MesloLGS NF.

Kamu juga dapat mengatur ukuran font sesuai kenyamanan.

## 8. Mengatur Warna Terminal

Kita dapat menggunakan kombinasi warna yang sama dengan konfigurasi Oh My Posh.

Rekomendasi warna:

| Elemen | Warna |
|---|---|
| Background | `#080B10` |
| Foreground | `#F5F5F5` |
| Green | `#00FF87` |
| Cyan | `#00D7FF` |
| Yellow | `#FFD75F` |
| Blue | `#5F87FF` |
| Magenta | `#D787FF` |
| Red | `#FF5F57` |

Pengaturan ini membantu menciptakan tampilan terminal yang konsisten antara PowerShell dan VS Code.

## 9. Mengatur Tampilan Tab

Windows Terminal juga menyediakan pengaturan tampilan tab.

Beberapa pengaturan yang dapat digunakan:

- Mengatur warna tab.
- Menentukan profil default.
- Mengatur lebar tab.
- Menampilkan atau menyembunyikan title bar.
- Mengatur tampilan tab ketika menggunakan Acrylic.

Contoh konfigurasi global:

```json
{
  "theme": "dark",
  "useAcrylicInTabRow": true,
  "tabWidthMode": "titleLength"
}
```

Pengaturan tersebut berlaku pada tampilan aplikasi Windows Terminal, bukan hanya satu profil.

## 10. Perbedaan Windows Terminal dan VS Code

Meskipun keduanya memiliki terminal, kemampuan visualnya berbeda.

| Fitur | Windows Terminal | VS Code Terminal |
|---|---|---|
| Background color | Ya | Ya |
| Font customization | Ya | Ya |
| Acrylic transparency | Ya | Tidak tersedia sebagai pengaturan profil terminal bawaan |
| Background image | Ya | Tidak tersedia sebagai pengaturan terminal bawaan |
| Oh My Posh | Ya | Ya |
| Powerlevel10k melalui WSL | Ya | Ya |
| Integrated editor | Tidak | Ya |

Windows Terminal lebih fleksibel untuk mengatur tampilan jendela, sedangkan VS Code lebih cocok untuk bekerja langsung dengan project.

## 11. Troubleshooting

### A. Acrylic tidak terlihat

Periksa konfigurasi:

```json
{
  "useAcrylic": true,
  "opacity": 85
}
```

Pastikan juga:

- Windows mendukung efek Acrylic.
- Terminal tidak sedang dalam kondisi penghemat daya yang menonaktifkan efek tersebut.
- Pengaturan Acrylic diaktifkan pada profil yang benar.

Jika menggunakan Remote Desktop atau lingkungan virtual, efek Acrylic mungkin tidak tersedia.

### B. Background image tidak muncul

Periksa kembali lokasi gambar.

Contoh:

```text
C:\Users\HP\Pictures\Terminal\forest.jpg
```

Pastikan path JSON menggunakan double backslash:

```json
"backgroundImage": "C:\\Users\\HP\\Pictures\\Terminal\\forest.jpg"
```

Pastikan file gambar masih tersedia di lokasi tersebut.

### C. Gambar terlalu terang

Turunkan nilai:

```json
"backgroundImageOpacity": 0.10
```

Jika terlalu gelap, tingkatkan nilainya secara bertahap.

### D. Teks terminal sulit dibaca

Coba:

- Mengurangi opacity gambar.
- Menggunakan warna foreground yang lebih terang.
- Memilih background yang lebih gelap.
- Mengurangi transparansi jendela.

### E. Perubahan tidak terlihat

Simpan `settings.json`, kemudian tutup dan buka kembali profil atau jendela Windows Terminal.

## 12. Hasil Akhir

Setelah mengikuti panduan ini, pengguna diharapkan dapat:

- Mengatur background terminal menjadi gelap.
- Mengaktifkan Acrylic transparency.
- Menggunakan gambar sebagai wallpaper terminal.
- Mengatur tingkat transparansi.
- Menggunakan Meslo Nerd Font.
- Menyesuaikan warna terminal.
- Mengatur tampilan tab.
- Membuat tampilan terminal Windows yang terinspirasi macOS.

## 13. Referensi

- Windows Terminal: https://github.com/microsoft/terminal
- Windows Terminal Documentation: https://learn.microsoft.com/windows/terminal/
- Appearance Settings: https://learn.microsoft.com/windows/terminal/customize-settings/appearance
- Profile Appearance: https://learn.microsoft.com/windows/terminal/customize-settings/profile-appearance
- Windows Terminal Tips: https://learn.microsoft.com/windows/terminal/tips-and-tricks

---

**Previous:** [04 — VS Code Terminal](04-vscode-terminal.md)

**Next:** [06 — Troubleshooting](06-troubleshooting.md)