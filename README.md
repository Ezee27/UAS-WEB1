UAS
---
Mata Kuliah: Pemograman Web1

Nama: Zaenal Maulana Rizki

Nim: 312410332

Kelas: TI.2A.A.4

Dosen: Agung Nugroho, S.Kom., M.Kom.

---

# 🐦 Toko Burung Jaya

**Toko Burung Jaya** adalah aplikasi web penjualan burung berbasis **PHP Native** yang menerapkan konsep **MVC (Model – View – Controller)**.  
Aplikasi ini memiliki fitur autentikasi, manajemen data burung, pemesanan, transaksi, serta dashboard admin.

Project ini dibuat untuk keperluan **pembelajaran dan tugas perkuliahan**, serta dapat dijalankan di **local server (XAMPP)** maupun **shared hosting (InfinityFree)**.

---

## 🚀 Fitur Aplikasi
### 👤 User
- Registrasi & Login
- Melihat daftar burung
- Melakukan pemesanan
- Melihat riwayat transaksi

### 🛠️ Admin
- Dashboard admin
- Manajemen data burung
- Manajemen pengguna
- Manajemen pemesanan & pembelian
- Melihat data transaksi

---

## 🧩 Teknologi yang Digunakan
- **PHP Native**
- **MySQL**
- **HTML & CSS**
- **Apache (.htaccess)**
- **MVC Architecture**

---

## 📂 Struktur Folder Project
Struktur berikut **sesuai dengan isi file ZIP**:

```

toko-burung-jaya/
│
├── .htaccess
│
├── app/
│   ├── controllers/
│   │   ├── AdminController.php
│   │   ├── AuthController.php
│   │   ├── BurungController.php
│   │   ├── PemesananController.php
│   │   └── UserController.php
│   │
│   ├── models/
│   │   ├── Burung.php
│   │   ├── Transaksi.php
│   │   └── User.php
│   │
│   └── views/
│       ├── admin/
│       │   ├── dashboard.php
│       │   ├── pembelian.php
│       │   ├── pemesanan.php
│       │   └── user.php
│       │
│       ├── auth/
│       │   ├── login.php
│       │   └── register.php
│       │
│       └── user/
│           ├── beranda.php
│           ├── detail_burung.php
│           ├── pemesanan.php
│           └── transaksi.php
│
├── assets/
│   └── css/
│       └── style.css
│
├── upload/
│   └── (file gambar burung)
│
└── public/
└── index.php

```

---

## 🔁 Konsep MVC yang Digunakan
- **Model**  
  Mengelola data dan koneksi database  
  (`app/models/`)

- **View**  
  Tampilan antarmuka pengguna  
  (`app/views/`)

- **Controller**  
  Menghubungkan Model dan View  
  (`app/controllers/`)

---

## ⚙️ Routing & Entry Point
- Entry point aplikasi:
```

public/index.php

````
- Routing diatur menggunakan `.htaccess`

### Isi `.htaccess`
```apache
RewriteEngine On

RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ public/index.php?url=$1 [QSA,L]
````

---

## 🗄️ Konfigurasi Database

1. Buat database MySQL
2. Sesuaikan koneksi database di file:

   ```
   app/core/Database.php
   ```
3. Pastikan:

   * Host
   * Username
   * Password
   * Nama database

---

## 🌐 Cara Menjalankan di Localhost

1. Simpan project di:

   ```
   htdocs/toko-burung-jaya
   ```
2. Jalankan Apache & MySQL (XAMPP)
3. Import database
4. Akses:

   ```
   http://localhost/toko-burung-jaya/public
   ```

---

## 🌍 Cara Hosting di InfinityFree

1. Upload **ISI folder project** ke:

   ```
   htdocs/
   ```
2. Pastikan struktur **tidak dobel folder**
3. Ubah `BASE_URL` di `public/index.php`

   ```php
   define('BASE_URL', 'https://namasitus.infinityfreeapp.com');
   ```
4. Pastikan folder `upload/` memiliki permission:

   ```
   755 atau 777
   ```

---

## 📸 Upload Gambar

* Folder upload:

  ```
  upload/
  ```
---
