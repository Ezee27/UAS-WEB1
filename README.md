## UAS MEMBUAT WEBSITE TENTANG TOKO BURUNG JAYA

---

**Mata Kuliah:** Pemrograman Web 1

**Nama:** Zaenal Maulana Rizki

**NIM:** 312410332

**Kelas:** TI.2A.A.4

**Dosen:** Agung Nugroho, S.Kom., M.Kom.

---

# Toko Burung Jaya

Toko Burung Jaya merupakan aplikasi website penjualan burung yang dibangun menggunakan PHP Native dengan menerapkan arsitektur MVC (Model–View–Controller).
Aplikasi ini menyediakan sistem autentikasi, pengelolaan data burung, pemesanan, transaksi, serta dashboard admin.

Project ini dibuat sebagai bagian dari Ujian Akhir Semester (UAS) mata kuliah Pemrograman Web 1 dan dapat dijalankan pada local server (XAMPP) maupun shared hosting seperti InfinityFree.

---

## Teknologi yang Digunakan

* PHP Native
* MySQL
* CSS
* Apache Web Server
* MVC Architecture
* .htaccess (URL Rewriting)

---

## Struktur Folder Project

Struktur folder berikut disesuaikan dengan isi file ZIP project:

```
TOKO-BURUNG-JAYA/
│
├── app/
│   │
│   ├── views/
│   │   └── user/
│   │       ├── beli.php
│   │       ├── dashboard.php
│   │       ├── history.php
│   │       ├── katalog.php
│   │       └── pemesanan.php
│   │
│   └── core/
│       ├── Controller.php
│       ├── Database.php
│       └── Router.php
│
├── public/
│   │
│   ├── assets/
│   │   ├── css/
│   │   │   └── style.css
│   │   │
│   │   └── images/
│   │       └── elang.jpg
│   │
│   ├── uploads/
│   │   └── burung/
│   │
│   └── index.php
│
├── .htaccess
└── database.sql

```

---

## Konsep MVC yang Digunakan

* Model
  Bertugas mengelola data dan berinteraksi dengan database.
  Lokasi: `app/models/`

* View
  Bertugas menampilkan antarmuka pengguna.
  Lokasi: `app/views/`

* Controller
  Bertugas menghubungkan Model dan View serta mengatur alur logika aplikasi.
  Lokasi: `app/controllers/`

---

## Autentikasi Pengguna (Login dan Register)

### File Terkait

* Controller: `app/controllers/AuthController.php`
* Model: `app/models/User.php`
* View:

  * `app/views/auth/login.php`
  * `app/views/auth/register.php`

### Penjelasan

Fitur autentikasi digunakan untuk mengatur akses pengguna dan admin ke dalam sistem.
Proses login memverifikasi email dan password, kemudian menyimpan data pengguna ke dalam session jika berhasil.

### Contoh Potongan Kode Login

```php
public function login()
{
    $email = $_POST['email'];
    $password = $_POST['password'];

    $user = $this->model('User')->getUserByEmail($email);

    if ($user && password_verify($password, $user['password'])) {
        $_SESSION['user'] = $user;
        header('Location: ' . BASE_URL . '/user/beranda');
    } else {
        header('Location: ' . BASE_URL . '/auth/login');
    }
}
```

### Screenshot Halaman Login

---
<img width="1919" height="1028" alt="image" src="https://github.com/user-attachments/assets/a1a8b0c2-b0c2-4afa-97f3-595a2caa26eb" />

---

---

## Halaman Beranda User

### File Terkait

* View: `app/views/user/beranda.php`

### Penjelasan

Halaman beranda menampilkan daftar burung yang tersedia lengkap dengan gambar, harga, dan tombol untuk melihat detail burung.

### Screenshot Beranda User

---
<img width="1919" height="1029" alt="image" src="https://github.com/user-attachments/assets/267fd35f-d1e7-4060-be06-17ef52610611" />

---

---

## Katalog

### File Terkait

* Controller: `app/controllers/BurungController.php`
* View: `app/views/user/katalog.php`

### Penjelasan

Halaman katalog menampilkan informasi lengkap burung seperti nama, harga, stok, deskripsi, serta gambar burung.

### Screenshot Detail Burung

---
<img width="1912" height="1027" alt="image" src="https://github.com/user-attachments/assets/60e73e52-8a3c-4815-a9e8-4c2a3a03494f" />

---

---

## Beli

### File Terkait

* Controller: `app/controllers/PemesananController.php`
* View: `app/views/user/beli.php`

### Penjelasan

Pengguna dapat melakukan pemesanan burung dengan menentukan jumlah pembelian.
Data pemesanan akan disimpan ke database dan diproses oleh admin.

### Screenshot Halaman beli

---
<img width="1919" height="1026" alt="image" src="https://github.com/user-attachments/assets/3e9f9d85-88a4-4c9a-92db-846259bfda7f" />

---

---

## Pemesanan Burung

### File Terkait

* Controller: `app/controllers/PemesananController.php`
* View: `app/views/user/pemesanan.php`

### Penjelasan

Pengguna dapat melakukan pemesanan burung dengan menentukan jumlah pembelian.
Data pemesanan akan disimpan ke database dan diproses oleh admin.

### Screenshot Halaman Pemesanan

<img width="1919" height="1029" alt="image" src="https://github.com/user-attachments/assets/a57126be-e58f-48d3-a909-1670845fb3fb" />

---

---

## History User

### File Terkait

* Model: `app/models/Pemesanan.php`
* View: `app/views/user/history.php`

### Penjelasan

Halaman transaksi menampilkan riwayat pembelian yang telah dilakukan oleh pengguna.

### Screenshot Halaman Transaksi

---
<img width="1917" height="1018" alt="image" src="https://github.com/user-attachments/assets/08de754e-80b3-4b80-aff1-e7cab5fd65e5" />

---

---

## Dashboard Admin

### File Terkait

* Controller: `app/controllers/AdminController.php`
* View: `app/views/admin/dashboard.php`

### Penjelasan

Dashboard admin digunakan untuk mengelola data sistem seperti data burung, pengguna, pemesanan, dan transaksi.

### Screenshot Dashboard Admin

```
![Dashboard Admin](screenshots/admin-dashboard.png)
```

---

## Manajemen Data Burung (Admin)

### File Terkait

* Controller: `app/controllers/BurungController.php`
* View: `app/views/admin/`

### Penjelasan

Admin dapat melakukan tambah, ubah, dan hapus data burung serta mengunggah gambar burung.

### Screenshot Manajemen Burung

```
![Manajemen Burung](screenshots/admin-burung.png)
```

---

## Routing dan Entry Point

* Entry Point aplikasi:

```
public/index.php
```

* Routing diatur menggunakan file `.htaccess`

```apache
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ public/index.php?url=$1 [QSA,L]
```

---

## Konfigurasi Database

1. Buat database MySQL melalui phpMyAdmin
2. Atur koneksi database pada file:

```
app/core/Database.php
```

3. Sesuaikan host, username, password, dan nama database

---

## Cara Menjalankan di Localhost

1. Simpan project ke dalam folder:

```
htdocs/toko-burung-jaya
```

2. Jalankan Apache dan MySQL
3. Import database
4. Akses melalui browser:

```
http://localhost/toko-burung-jaya/public
```

---

## Cara Menjalankan di Hosting (InfinityFree)

1. Upload seluruh isi project ke folder:

```
htdocs/
```

2. Pastikan tidak ada folder ganda
3. Atur BASE_URL pada file `public/index.php`
4. Atur permission folder `upload/` menjadi 755 atau 777

---

## Kesimpulan

Berdasarkan hasil perancangan dan implementasi aplikasi Toko Burung Jaya, dapat disimpulkan bahwa sistem ini berhasil dibangun menggunakan PHP Native dengan menerapkan konsep MVC secara terstruktur. Pemisahan antara Model, View, dan Controller memudahkan pengelolaan kode serta meningkatkan keterbacaan dan pengembangan aplikasi.

Aplikasi ini telah menyediakan fitur utama sistem penjualan online, mulai dari autentikasi pengguna, pengelolaan data burung, pemesanan, hingga transaksi. Diharapkan aplikasi ini dapat menjadi sarana pembelajaran dalam memahami dasar pengembangan web berbasis PHP dan dapat dikembangkan lebih lanjut di masa mendatang.

---
