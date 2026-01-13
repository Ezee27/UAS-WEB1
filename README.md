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

### Screenshot Halaman History

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

---
<img width="1919" height="1029" alt="image" src="https://github.com/user-attachments/assets/abdd2440-4781-4024-a309-daa84ff28e30" />

---

---

## Data Burung (Admin)

### File Terkait

* Controller: `app/controllers/BurungController.php`
* View: `app/views/admin/burung.php`

### Penjelasan

Halaman data burung digunakan admin untuk melihat seluruh daftar burung yang tersedia di sistem.
Informasi yang ditampilkan meliputi nama burung, harga, stok, dan gambar.
Dari halaman ini, admin dapat menuju ke fitur tambah dan edit data burung.

### Screenshot Halaman Data Burung

---
<img width="1919" height="1026" alt="image" src="https://github.com/user-attachments/assets/1549dc6e-c6ea-4f61-bb55-a1d2e2322485" />

---

---

## Tambah Data Burung (Admin)

### File Terkait

* Controller: `app/controllers/BurungController.php`
* View: `app/views/admin/tambah.php`

### Penjelasan

Halaman tambah burung digunakan admin untuk menambahkan data burung baru ke dalam sistem.
Admin mengisi form berupa nama burung, harga, stok, deskripsi, serta mengunggah gambar burung.
Data yang berhasil disimpan akan langsung masuk ke database.

### Screenshot Halaman Tambah Burung

---
<img width="1917" height="1020" alt="image" src="https://github.com/user-attachments/assets/368ab0d5-616e-4cfa-b42f-0d828d3fda21" />

---

---

## Edit Data Burung (Admin)

### File Terkait

* Controller: `app/controllers/BurungController.php`
* View: `app/views/admin/edit.php`

### Penjelasan

Halaman edit burung digunakan admin untuk memperbarui data burung yang sudah ada.
Admin dapat mengubah nama burung, harga, stok, serta mengganti gambar burung jika diperlukan.

### Screenshot Halaman Edit Burung

---
<img width="1919" height="1020" alt="image" src="https://github.com/user-attachments/assets/642144f0-c476-43cb-9bc6-d64fb9a6c566" />

---

---

## Data Pembelian (Admin)

### File Terkait

* Controller: `app/controllers/AdminController.php`
* View: `app/views/admin/pembelian.php`

### Penjelasan

Halaman pembelian menampilkan data transaksi pembelian yang telah dilakukan oleh pengguna.
Admin dapat melihat detail pembelian seperti nama user, burung yang dibeli, jumlah, dan total pembayaran.

### Screenshot Halaman Pembelian

---
<img width="1919" height="1025" alt="image" src="https://github.com/user-attachments/assets/a05a4d36-8ae6-47ce-8d0c-5e67724b1b73" />

---

---

## Data Pemesanan (Admin)

### File Terkait

* Controller: `app/controllers/PemesananController.php`
* View: `app/views/admin/pemesanan.php`

### Penjelasan

Halaman pemesanan digunakan admin untuk memantau pesanan yang masuk dari pengguna.
Admin dapat melihat data pesanan serta status pemesanan yang sedang diproses.

### Screenshot Halaman Pemesanan

---

<img width="1919" height="1032" alt="image" src="https://github.com/user-attachments/assets/4c89fdd5-e06f-4fe4-82b8-6987306c496d" />

---

---

## Data Admin dan User

### File Terkait

* Controller: `app/controllers/UserController.php`
* View: `app/views/admin/user.php`

### Penjelasan

Halaman ini digunakan admin untuk melihat data akun yang terdaftar di dalam sistem, baik admin maupun user.
Informasi yang ditampilkan digunakan untuk pengawasan dan manajemen pengguna.

### Screenshot Halaman Data Admin dan User

---
<img width="1908" height="1022" alt="image" src="https://github.com/user-attachments/assets/ec97badf-4ff8-424b-82e8-9839f322423a" />

---

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
4. Atur permission folder `upload/`

---

## Kesimpulan

Berdasarkan hasil perancangan dan implementasi aplikasi Toko Burung Jaya, dapat disimpulkan bahwa sistem ini berhasil dibangun menggunakan PHP Native dengan menerapkan konsep MVC secara terstruktur. Pemisahan antara Model, View, dan Controller memudahkan pengelolaan kode serta meningkatkan keterbacaan dan pengembangan aplikasi.

Aplikasi ini telah menyediakan fitur utama sistem penjualan online, mulai dari autentikasi pengguna, pengelolaan data burung, pemesanan, hingga transaksi. Diharapkan aplikasi ini dapat menjadi sarana pembelajaran dalam memahami dasar pengembangan web berbasis PHP dan dapat dikembangkan lebih lanjut di masa mendatang.

---
