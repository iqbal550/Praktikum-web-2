# Praktikum Pemrograman Web 2

## CodeIgniter 4, REST API, dan Vue.js SPA


**Nama:** M. Iqbal

**NIM:** 312410212

**Kelas:** I241B

**Mata Kuliah:** Pemrograman Web 2

**Dosen Pengampu:** Agung Nugroho S.KOM.,M.KOM.

---

# 📖 Deskripsi Repository

Repository ini berisi kumpulan hasil Praktikum Pemrograman Web 2 menggunakan Framework CodeIgniter 4 dan Vue.js yang dilaksanakan selama 14 pertemuan.

Materi praktikum mencakup:

* Framework CodeIgniter 4
* MVC (Model View Controller)
* CRUD Database
* View Layout dan View Cell
* Authentication & Authorization
* Pagination dan Search
* Relasi Database
* Upload File
* AJAX
* REST API
* Vue.js
* Vue Router
* SPA (Single Page Application)
* Navigation Guards
* Token Authentication
* Axios Interceptors

---

# 🛠️ Teknologi yang Digunakan

## Backend

* PHP 8.x
* CodeIgniter 4
* MySQL/MariaDB
* RESTful API

## Frontend

* HTML5
* CSS3
* Bootstrap 5
* JavaScript ES6
* Vue.js 3
* Vue Router
* Axios

## Tools

* Visual Studio Code
* XAMPP
* Composer
* Git
* GitHub
* Postman

---

# 📂 Struktur Project

```bash
project/
│
├── app/
│   ├── Controllers/
│   ├── Models/
│   ├── Views/
│   ├── Filters/
│   └── Config/
│
├── public/
│   ├── assets/
│   ├── uploads/
│   └── index.php
│
├── writable/
│
├── database/
│   └── db_web2.sql
│
├── frontend/
│   ├── components/
│   ├── views/
│   ├── router/
│   ├── services/
│   └── app.js
│
└── README.md
```

---

# 📑 Daftar Praktikum

---

## Praktikum 1

### Framework CodeIgniter 4

### Tujuan

* Memahami konsep Framework
* Memahami pola MVC
* Instalasi CodeIgniter 4

### Materi

* Instalasi Composer
* Instalasi CI4
* Routing dasar
* Controller
* View

<img width="1897" height="1137" alt="image" src="https://github.com/user-attachments/assets/9f7f7477-c487-453f-b7a3-95ad73e3db40" />

Berhasil membuat aplikasi CodeIgniter pertama menggunakan konsep MVC.

---

## Praktikum 2

### CRUD Menggunakan CodeIgniter 4

### Tujuan

* Memahami Model
* Membuat CRUD Data

### Materi

* Create
* Read
* Update
* Delete

### Hasil

Berhasil membuat manajemen data artikel menggunakan database MySQL.

---

## Praktikum 3

### View Layout dan View Cell

### Tujuan

* Membuat template halaman
* Menggunakan komponen modular

### Materi

* Layout Template
* Extend View
* Section
* View Cell

### Hasil

Tampilan website menjadi lebih terstruktur dan reusable.

---

## Praktikum 4

### Modul Login dan Authentication

### Tujuan

* Membuat sistem login
* Menerapkan filter keamanan

### Materi

* Session
* Login
* Logout
* Filter

### Hasil

Berhasil membuat autentikasi pengguna dan pembatasan akses halaman.

---

## Praktikum 5

### Pagination dan Search

### Tujuan

* Menampilkan data secara bertahap
* Menambahkan fitur pencarian

### Materi

* Pagination
* Query Search

### Hasil

Data dapat dicari dan ditampilkan per halaman.

---

## Praktikum 6

### Relasi Tabel dan Query Builder

### Tujuan

* Memahami relasi database

### Materi

* One-to-Many
* Join Table
* Query Builder

### Hasil

Data kategori dan artikel dapat saling terhubung.

---

## Praktikum 7

### Upload File Gambar

### Tujuan

* Upload file ke server

### Materi

* Upload gambar
* Validasi file
* Penyimpanan file

### Hasil

Pengguna dapat menambahkan gambar pada data artikel.

---

## Praktikum 8

### AJAX

### Tujuan

* Memahami komunikasi asynchronous

### Materi

* AJAX Request
* Fetch API
* JSON Response

### Hasil

Data dapat ditampilkan tanpa reload halaman.

---

## Praktikum 9

### AJAX Pagination dan Search

### Tujuan

* Mengoptimalkan User Experience

### Materi

* AJAX Search
* AJAX Pagination

### Hasil

Pencarian dan pagination berjalan secara realtime.

---

## Praktikum 10

### REST API

### Tujuan

* Memahami konsep REST

### Materi

* GET
* POST
* PUT
* DELETE

### Endpoint

```http
GET /api/artikel
POST /api/artikel
PUT /api/artikel/{id}
DELETE /api/artikel/{id}
```

### Hasil

Backend berhasil menyediakan data melalui REST API.

---

## Praktikum 11

### Vue.js

### Tujuan

* Membangun Frontend Modern

### Materi

* Vue Instance
* Data Binding
* Lifecycle

### Hasil

Frontend dapat mengambil data dari API CodeIgniter.

---

## Praktikum 12

### Vue Router dan SPA

### Tujuan

* Membuat Single Page Application

### Materi

* Router
* Component
* Navigation

### Hasil

Aplikasi berjalan tanpa reload halaman.

---

## Praktikum 13

### Authentication dan Navigation Guards

### Tujuan

* Proteksi halaman admin

### Materi

* Login API
* beforeEach()
* Route Protection

### Hasil

Halaman admin hanya dapat diakses pengguna yang login.

---

## Praktikum 14

### Token Authentication dan Axios Interceptors

### Tujuan

* Mengamankan REST API

### Materi

* Bearer Token
* JWT Concept
* Axios Interceptors
* API Security

### Hasil

Frontend dan Backend berkomunikasi secara aman menggunakan token autentikasi.

---

# 🚀 Cara Menjalankan Project

## Clone Repository

```bash
git clone https://github.com/username/repository.git
```

## Masuk Folder Project

```bash
cd repository
```

## Install Dependency

```bash
composer install
```

## Konfigurasi Environment

```bash
cp env .env
```

Sesuaikan konfigurasi database:

```env
database.default.hostname = localhost
database.default.database = web2
database.default.username = root
database.default.password =
database.default.DBDriver = MySQLi
```

## Jalankan Server

```bash
php spark serve
```

Akses:

```text
http://localhost:8080
```

---

# 📊 Kompetensi yang Diperoleh

Setelah menyelesaikan seluruh praktikum, mahasiswa mampu:

✅ Menggunakan Framework CodeIgniter 4
✅ Menerapkan konsep MVC
✅ Membuat CRUD Database
✅ Membuat Authentication System
✅ Mengimplementasikan Pagination dan Search
✅ Mengelola Relasi Database
✅ Mengupload File ke Server
✅ Menggunakan AJAX
✅ Membuat REST API
✅ Mengembangkan Frontend dengan Vue.js
✅ Membangun Single Page Application (SPA)
✅ Mengimplementasikan Navigation Guards
✅ Menggunakan Token Authentication
✅ Mengamankan API menggunakan Axios Interceptors

---

# 📝 Kesimpulan

Praktikum Pemrograman Web 2 memberikan pemahaman mengenai pengembangan aplikasi web modern menggunakan CodeIgniter 4 sebagai Backend dan Vue.js sebagai Frontend. Melalui 14 praktikum yang telah dikerjakan, mahasiswa memperoleh kemampuan dalam membangun aplikasi berbasis MVC, REST API, autentikasi pengguna, serta Single Page Application (SPA) yang aman, responsif, dan sesuai kebutuhan industri saat ini.
