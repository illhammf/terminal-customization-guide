# Terminal Wallpapers Collection

Folder ini merupakan bagian dari proyek **Terminal Customization Guide** yang digunakan untuk menyimpan koleksi wallpaper atau gambar latar belakang terminal.

Wallpaper dapat digunakan untuk mempercantik tampilan Windows Terminal, khususnya ketika menggunakan fitur background image dan transparansi.

Koleksi ini disediakan sebagai materi pendukung agar pengguna dapat mencoba berbagai tampilan terminal sesuai preferensi masing-masing.

---

## Daftar Isi

- [1. Tentang Wallpapers](#1-tentang-wallpapers)
- [2. Tujuan](#2-tujuan)
- [3. Struktur Folder](#3-struktur-folder)
- [4. Kategori Wallpaper](#4-kategori-wallpaper)
- [5. Cara Menggunakan Wallpaper](#5-cara-menggunakan-wallpaper)
- [6. Pengaturan Tampilan](#6-pengaturan-tampilan)
- [7. Panduan Menambahkan Wallpaper](#7-panduan-menambahkan-wallpaper)
- [8. Ketentuan Penggunaan](#8-ketentuan-penggunaan)

---

## 1. Tentang Wallpapers

Wallpaper merupakan gambar yang digunakan sebagai latar belakang aplikasi terminal.

Pada Windows Terminal, pengguna dapat mengatur gambar latar belakang melalui pengaturan profil terminal.

Dengan menggunakan wallpaper yang sesuai, tampilan terminal dapat dibuat lebih menarik tanpa mengurangi fungsi utamanya sebagai tempat menjalankan perintah.

Folder ini menyediakan tempat terorganisasi untuk menyimpan gambar yang digunakan dalam proses kustomisasi tersebut.

## 2. Tujuan

Folder `wallpapers/` dibuat untuk:

- Menyediakan koleksi wallpaper untuk Windows Terminal.
- Mengelompokkan gambar berdasarkan kategori.
- Memberikan pilihan tampilan bagi pengguna.
- Menjadi referensi visual dalam tutorial.
- Memudahkan pengguna menerapkan background image.
- Menyimpan gambar yang memang boleh dibagikan melalui repository.

Wallpaper bersifat opsional. Pengguna tetap dapat mengikuti seluruh tutorial tanpa harus menggunakan gambar latar belakang.

---

## 3. Struktur Folder

Struktur direktori yang direncanakan:

```text
wallpapers/
│
├── README.md
│
├── nature/
│   ├── forest.jpg
│   └── mountain.jpg
│
├── abstract/
│   └── dark-abstract.jpg
│
└── minimal/
    └── dark-gradient.jpg
```

Setiap kategori memiliki fungsi berbeda agar pengguna dapat menemukan gambar dengan lebih mudah.

---

## 4. Kategori Wallpaper

### 4.1 Nature

Kategori ini berisi wallpaper bertema alam, seperti hutan, pegunungan, dan pemandangan alam lainnya.

Contoh penggunaan:
- Tampilan terminal dengan nuansa hutan.
- Background pemandangan pegunungan.
- Wallpaper alam dengan warna gelap.

### 4.2 Abstract

Kategori ini berisi gambar dengan pola dan bentuk abstrak.

Contoh penggunaan:
- Pola geometris.
- Desain abstrak dengan warna gelap.
- Efek visual dengan kombinasi warna.

### 4.3 Minimal

Kategori ini berisi wallpaper dengan desain sederhana dan tidak terlalu ramai.

Contoh penggunaan:
- Gradient gelap.
- Background polos dengan sedikit variasi warna.
- Desain minimalis.

**Catatan:** Nama kategori merupakan pengelompokan yang direncanakan. Isi koleksi akan bertambah secara bertahap.

---

## 5. Cara Menggunakan Wallpaper

Untuk menggunakan wallpaper pada Windows Terminal, ikuti langkah berikut:

1. Pilih wallpaper dari folder yang tersedia.
2. Salin gambar ke lokasi penyimpanan pada perangkat.
3. Buka Windows Terminal.
4. Masuk ke Settings.
5. Pilih profil terminal yang ingin dikustomisasi.
6. Buka bagian Appearance.
7. Atur gambar latar belakang menggunakan lokasi file wallpaper.
8. Sesuaikan transparansi dan posisi gambar.
9. Simpan perubahan.

Pastikan lokasi gambar yang digunakan sudah benar.

---

## 6. Pengaturan Tampilan

Windows Terminal menyediakan beberapa properti untuk mengatur tampilan background image.

Contoh konfigurasi:

```json
{
    "backgroundImage": "C:\\Users\\Username\\Pictures\\Terminal\\forest.jpg",
    "backgroundImageOpacity": 0.15,
    "backgroundImageAlignment": "center",
    "backgroundImageStretchMode": "uniformToFill"
}
```

Penjelasan:

| Properti | Fungsi |
|---|---|
| `backgroundImage` | Menentukan lokasi file wallpaper |
| `backgroundImageOpacity` | Mengatur tingkat transparansi gambar |
| `backgroundImageAlignment` | Mengatur posisi gambar |
| `backgroundImageStretchMode` | Mengatur cara gambar menyesuaikan ukuran terminal |

Nilai pada contoh tersebut dapat disesuaikan dengan kebutuhan.

**Penting:** Konfigurasi di atas merupakan potongan properti profil Windows Terminal, bukan keseluruhan file `settings.json`. Gabungkan ke profil yang ingin digunakan.

---

## 7. Panduan Menambahkan Wallpaper

Pengguna yang ingin menambahkan wallpaper baru dapat mengikuti aturan berikut.

### 7.1 Format Gambar

Format yang disarankan:

- JPG
- JPEG
- PNG
- WebP

### 7.2 Resolusi

Gunakan gambar dengan resolusi yang cukup tinggi agar tetap terlihat baik ketika terminal diperbesar.

### 7.3 Penamaan File

Gunakan nama yang sederhana dan mudah dipahami.

Contoh:

```text
forest.jpg
mountain.jpg
dark-abstract.jpg
dark-gradient.jpg
```

Hindari nama yang tidak menjelaskan isi gambar seperti:

```text
image1.jpg
new-wallpaper.png
final-image-2.jpg
```

### 7.4 Pengelompokan

Masukkan gambar ke kategori yang sesuai.

Contohnya, wallpaper bertema hutan dimasukkan ke:

```text
nature/forest.jpg
```

Sedangkan wallpaper dengan desain geometris dimasukkan ke:

```text
abstract/dark-abstract.jpg
```

---

## 8. Ketentuan Penggunaan

Beberapa hal yang perlu diperhatikan:

1. Gunakan gambar yang dibuat sendiri atau memiliki izin penggunaan dan distribusi.
2. Jangan mengunggah gambar yang melanggar hak cipta.
3. Usahakan ukuran file tetap wajar.
4. Gunakan nama file yang deskriptif.
5. Hindari gambar yang terlalu ramai sehingga mengganggu keterbacaan teks terminal.
6. Pastikan setiap gambar ditempatkan pada kategori yang sesuai.
7. Sertakan sumber atau informasi lisensi jika diperlukan.

---

## Referensi

- [Windows Terminal Documentation](https://learn.microsoft.com/windows/terminal/)
- [Windows Terminal Appearance Settings](https://learn.microsoft.com/windows/terminal/customize-settings/profile-appearance)

---

**Bagian dari:** [Terminal Customization Guide](../../README.md)

Koleksi wallpaper ini akan dikembangkan secara bertahap sebagai bagian dari dokumentasi kustomisasi terminal.