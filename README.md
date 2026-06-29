# 📘 LAPORAN PRAKTIKUM PEMROGRAMAN WEB 2

### CodeIgniter 4, REST API, dan Vue.js 3 SPA

</br>

**Disusun oleh:**

| | |
|---|---|
| **Nama** | M. Iqbal |
| **NIM** | 312410212 |
| **Kelas** | I241B |
| **Mata Kuliah** | Pemrograman Web 2 |
| **Dosen Pengampu** | Agung Nugroho, S.Kom., M.Kom. |
| **Program Studi** | Informatika |
| **Fakultas** | Teknik |
| **Universitas** | Universitas Pelita Bangsa |


## 🛠️ Teknologi yang Digunakan

| Layer | Teknologi |
|---|---|
| Backend | PHP 8.x, CodeIgniter 4, MySQL/MariaDB, RESTful API |
| Frontend | HTML5, CSS3, JavaScript ES6, Vue.js 3, Vue Router, Axios |
| Tools | VS Code, XAMPP, Composer, Git, GitHub, Postman |

---

## Langkah-langkah Praktikum

### 1. Persiapan
Sebelum memulai menggunakan Framework Codeigniter, perlu dilakukan konfigurasi pada webserver. Beberapa ekstensi PHP perlu diaktifkan untuk kebutuhan pengembangan Codeigniter 4.

Berikut beberapa ekstensi yang perlu diaktifkan:
- **php-json** ekstension untuk bekerja dengan JSON
- **php-mysqlnd** native driver untuk MySQL
- **php-xml** ekstension untuk bekerja dengan XML
- **php-intl** ekstensi untuk membuat aplikasi multibahasa
- **libcurl** (opsional), jika ingin pakai Curl

Untuk mengaktifkan ekstensi tersebut, melalui **XAMPP Control Panel**, pada bagian Apache klik **Config -> PHP.ini**

<img width="1115" height="645" alt="image" src="https://github.com/user-attachments/assets/e8ba8d46-1a25-4032-9fc2-628af1d4bee7" />


Pada bagian extension, hilangkan tanda ; (titik koma) pada ekstensi yang akan diaktifkan. Kemudian simpan kembali filenya dan restart Apache web server.

<img width="976" height="625" alt="image" src="https://github.com/user-attachments/assets/2dc4ac2b-0957-4ce0-9402-3c7f1fb2442d" />

---

### 2. Instalasi Codeigniter 4
Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara manual dan menggunakan composer. Pada praktikum ini kita menggunakan cara manual.

- Unduh **Codeigniter** dari website https://codeigniter.com/download
- Extrak file zip Codeigniter ke direktori **htdocs/lab11_ci**
- Ubah nama direktori **framework-4.x.xx** menjadi **ci4**
- Buka browser dengan alamat http://localhost/lab11_ci/ci4/public/

<img width="1919" height="924" alt="Cuplikan layar 2026-03-29 221700" src="https://github.com/user-attachments/assets/9809f4d1-24c0-4b6a-9b97-4a16846c9647" />

---

### 3. Menjalankan CLI (Command Line Interface)
Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk mengakses CLI buka terminal/command prompt.

Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat **(xampp/htdocs/lab11_ci/ci4/)**

Perintah yang dapat dijalankan untuk memanggil CLI Codeigniter adalah:

```
php spark
```

<img width="954" height="997" alt="Cuplikan layar 2026-03-29 222247" src="https://github.com/user-attachments/assets/524e8d54-2012-49ea-afdc-1cfdc5a68e97" />

---

### 4. Mengaktifkan Mode Debugging
Codeigniter 4 menyediakan fitur **debugging** untuk memudahkan developer untuk mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program.

Secara default fitur ini belum aktif. Ketika terjadi error pada aplikasi akan ditampilkan pesan kesalahan **"Whoops!"** yang tidak informatif.

<img width="1919" height="704" alt="image" src="https://github.com/user-attachments/assets/6942d15e-c076-4983-bfd0-9cf7e54e4e86" />
Untuk mengaktifkan mode debugging:
- Ubah nama file **env** menjadi **.env**
- Buka file tersebut dan ubah nilai variable **CI_ENVIRONMENT** menjadi **development**

```
CI_ENVIRONMENT = development
```

<img width="532" height="178" alt="image" src="https://github.com/user-attachments/assets/b5b360e3-8d90-4c71-a1a3-0a1b6777e75b" />

Setelah mode debugging aktif, pesan error akan ditampilkan lebih detail seperti **ParseError** beserta nama file dan nomor baris yang menyebabkan error.

<img width="488" height="311" alt="image" src="https://github.com/user-attachments/assets/ca63867d-4ea5-42de-beb1-cc227b67f3c8" />


---

### 5. Struktur Direktori
Untuk lebih memahami Framework Codeigniter 4 perlu mengetahui struktur direktori dan file yang ada. Buka pada **Windows Explorer** atau dari **Visual Studio Code -> Open Folder**.

<img width="1439" height="847" alt="image" src="https://github.com/user-attachments/assets/39544d74-fa6f-4340-aa46-7b34a272a4e4" />


Terdapat beberapa direktori dan file yang perlu dipahami fungsi dan kegunaannya:

- **.github** - folder untuk konfigurasi repo github
- **app** - folder yang berisi kode dari aplikasi yang dikembangkan
- **public** - folder yang berisi file yang bisa diakses oleh publik
- **tests** - folder yang berisi kode untuk melakukan testing dengan PHPunit
- **vendor** - folder yang berisi library yang dibutuhkan oleh aplikasi
- **writable** - folder yang berisi file yang ditulis oleh aplikasi

Sedangkan file-file yang berada pada root direktori CI:
- **.env** - file yang berisi variabel environment
- **.gitignore** - file yang berisi daftar nama file dan folder yang diabaikan Git
- **composer.json** - file JSON yang berisi informasi tentang proyek
- **spark** - program untuk menjalankan server, generate kode, dll

---

### 6. Memahami Konsep MVC
Codeigniter menggunakan konsep MVC (**Model-View-Controller**). MVC merupakan konsep arsitektur yang umum digunakan dalam pengembangan aplikasi. Konsep MVC adalah memisahkan kode program berdasarkan logic proses, data, dan tampilan.

- **Model** - kode program yang berisi pemodelan data (database atau sumber lainnya)
- **View** - kode program yang menangani tampilan user interface
- **Controller** - kode program yang berkaitan dengan logic proses yang menghubungkan antara view dan model

---

### 7. Routing dan Controller
Routing merupakan proses yang mengatur arah atau rute dari request untuk menentukan fungsi/bagian mana yang akan memproses request tersebut.

Router terletak pada file **app/Config/Routes.php**

Contoh route untuk halaman home:
```php
$routes->get('/', 'Home::index');
```

#### Membuat Route Baru
Tambahkan kode berikut di dalam **Routes.php**:

```php
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
```

Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan:

```
php spark routes
```

<img width="1713" height="409" alt="image" src="https://github.com/user-attachments/assets/4463e363-920a-4346-826a-f5772d3f1f93" />


Ketika route diakses tanpa Controller yang sesuai, akan muncul error 404.

<img width="593" height="367" alt="image" src="https://github.com/user-attachments/assets/c05505ea-5c3d-418f-ad1f-a8fcaf686a9b" />

---

### 8. Membuat Controller
Buat file baru dengan nama **Page.php** pada direktori **app/Controllers/**:

```php
<?php

namespace App\Controllers;

class Page extends BaseController
{
    public function about()
    {
        return view('about', [
            'title'   => 'Halaman About',
            'content' => 'Ini adalah halaman about yang menjelaskan tentang isi halaman ini.'
        ]);
    }

    public function contact()
    {
        return view('contact', [
            'title'   => 'Halaman Contact',
            'content' => 'Ini adalah halaman contact. Silakan hubungi kami.'
        ]);
    }

    public function faqs()
    {
        return view('faqs', [
            'title'   => 'Halaman FAQ',
            'content' => 'Ini adalah halaman FAQ berisi pertanyaan yang sering ditanyakan.'
        ]);
    }
}
```

<img width="654" height="180" alt="image" src="https://github.com/user-attachments/assets/c4c94f7a-5aba-4981-aab1-eeee1594d8c3" />


---

### 9. Membuat View
Buat file baru dengan nama **about.php** pada direktori **app/Views/**:

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
</head>
<body>
    <h1><?= $title; ?></h1>
    <hr>
    <p><?= $content; ?></p>
</body>
</html>
```

<img width="910" height="360" alt="image" src="https://github.com/user-attachments/assets/fb6e6e4f-6abb-4450-a26e-11ea3770cd8f" />

---

### 10. Membuat Layout Web dengan CSS
Pada Codeigniter 4, file yang menyimpan asset CSS dan JavaScript terletak pada direktori **public**.

Buat file **style.css** pada direktori **public/**.

Kemudian buat folder **template** pada direktori **app/Views/** dan buat file **header.php** dan **footer.php**.

#### File app/Views/template/header.php
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
    <link rel="stylesheet" href="<?= base_url('/style.css');?>">
</head>
<body>
    <div id="container">
        <header>
            <h1>Layout Sederhana</h1>
        </header>
        <nav>
            <a href="<?= base_url('/');?>" class="active">Home</a>
            <a href="<?= base_url('/artikel');?>">Artikel</a>
            <a href="<?= base_url('/about');?>">About</a>
            <a href="<?= base_url('/contact');?>">Kontak</a>
        </nav>
        <section id="wrapper">
            <section id="main">
```

#### File app/Views/template/footer.php
```php
            </section>
            <aside id="sidebar">
                <div class="widget-box">
                    <h3 class="title">Widget Header</h3>
                    <ul>
                        <li><a href="#">Widget Link</a></li>
                        <li><a href="#">Widget Link</a></li>
                    </ul>
                </div>
                <div class="widget-box">
                    <h3 class="title">Widget Text</h3>
                    <p>Vestibulum lorem elit, iaculis in nisl volutpat, malesuada tincidunt arcu.</p>
                </div>
            </aside>
        </section>
        <footer>
            <p>&copy; 2021 - Universitas Pelita Bangsa</p>
        </footer>
    </div>
</body>
</html>
```


Kemudian ubah file **app/Views/about.php** menjadi:

```php
<?= $this->include('template/header'); ?>
<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>
<?= $this->include('template/footer'); ?>
```

<img width="852" height="616" alt="image" src="https://github.com/user-attachments/assets/052e6f2f-c6e7-4e48-a771-765cb1ce57ce" />


<img width="790" height="377" alt="image" src="https://github.com/user-attachments/assets/ee4e11b9-9ae5-407f-a013-5d24a308b0a9" />



---

## Pertanyaan dan Tugas
Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga semua link pada navigasi header dapat menampilkan tampilan dengan layout yang sama.

**Jawaban:**
Membuat view untuk halaman **contact.php** dan **faqs.php** dengan menggunakan template header dan footer yang sama, serta mengupdate method `contact()` dan `faqs()` pada Controller Page untuk memanggil view yang sesuai.

<img width="950" height="743" alt="image" src="https://github.com/user-attachments/assets/0b98e60a-3c8d-465f-b28f-e20edc0629b5" />


<img width="955" height="737" alt="image" src="https://github.com/user-attachments/assets/d900a687-c29a-4e03-87c1-57db9c0dbddd" />

---

## Hasil Akhir
Tampilan akhir website dengan layout lengkap:
- Header dengan judul "Layout Sederhana"
- Navigasi menu (Home, Artikel, About, Kontak)
- Konten utama di bagian kiri
- Sidebar dengan Widget Header dan Widget Text di bagian kanan 
- Footer di bagian bawah


# PRAKTIKUM 2: Framework Lanjutan (CRUD)

---

## Langkah-langkah Praktikum

### 1. Persiapan Database
Untuk memulai membuat aplikasi CRUD sederhana, yang perlu disiapkan adalah database server menggunakan MySQL. Pastikan MySQL Server sudah dapat dijalankan melalui XAMPP.

#### Membuat Database
```sql
CREATE DATABASE lab_ci4;
```

#### Membuat Tabel Artikel
```sql
CREATE TABLE artikel (
    id INT(11) auto_increment,
    judul VARCHAR(200) NOT NULL,
    isi TEXT,
    gambar VARCHAR(200),
    status TINYINT(1) DEFAULT 0,
    slug VARCHAR(200),
    PRIMARY KEY(id)
);
```

---

### 2. Konfigurasi Koneksi Database
Selanjutnya membuat konfigurasi untuk menghubungkan dengan database server. Konfigurasi dilakukan pada file **.env** dengan menghapus tanda `#` dan mengisi nilai berikut:

```
database.default.hostname = localhost
database.default.database = lab_ci4
database.default.username = root
database.default.password = 
database.default.DBDriver = MySQLi
database.default.DBPrefix =
```

<img width="888" height="302" alt="image" src="https://github.com/user-attachments/assets/04d326da-a040-46d7-b8db-559b484dd34f" />

---

### 3. Membuat Model
Selanjutnya adalah membuat Model untuk memproses data Artikel. Buat file baru pada direktori **app/Models** dengan nama **ArtikelModel.php**:

```php
<?php

namespace App\Models;

use CodeIgniter\Model;

class ArtikelModel extends Model
{
    protected $table = 'artikel';
    protected $primaryKey = 'id';
    protected $useAutoIncrement = true;
    protected $allowedFields = ['judul', 'isi', 'status', 'slug', 'gambar'];
}
```

---

### 4. Membuat Controller Artikel
Buat Controller baru dengan nama **Artikel.php** pada direktori **app/Controllers**:

```php
<?php

namespace App\Controllers;

use App\Models\ArtikelModel;

class Artikel extends BaseController
{
    public function index()
    {
        $title = 'Daftar Artikel';
        $model = new ArtikelModel();
        $artikel = $model->findAll();
        return view('artikel/index', compact('artikel', 'title'));
    }

    public function view($slug)
    {
        $model = new ArtikelModel();
        $artikel = $model->where(['slug' => $slug])->first();

        if (!$artikel)
        {
            throw \CodeIgniter\Exceptions\PageNotFoundException::forPageNotFound();
        }

        $title = $artikel['judul'];
        return view('artikel/detail', compact('artikel', 'title'));
    }

    public function admin_index()
    {
        $title = 'Daftar Artikel';
        $model = new ArtikelModel();
        $artikel = $model->findAll();
        return view('artikel/admin_index', compact('artikel', 'title'));
    }

    public function add()
    {
        $validation = \Config\Services::validation();
        $validation->setRules(['judul' => 'required']);
        $isDataValid = $validation->withRequest($this->request)->run();

        if ($isDataValid)
        {
            $artikel = new ArtikelModel();
            $artikel->insert([
                'judul' => $this->request->getPost('judul'),
                'isi'   => $this->request->getPost('isi'),
                'slug'  => url_title($this->request->getPost('judul')),
            ]);
            return redirect()->to('/admin/artikel');
        }

        $title = "Tambah Artikel";
        return view('artikel/form_add', compact('title'));
    }

    public function edit($id)
    {
        $artikel = new ArtikelModel();

        $validation = \Config\Services::validation();
        $validation->setRules(['judul' => 'required']);
        $isDataValid = $validation->withRequest($this->request)->run();

        if ($isDataValid)
        {
            $artikel->update($id, [
                'judul' => $this->request->getPost('judul'),
                'isi'   => $this->request->getPost('isi'),
            ]);
            return redirect()->to('/admin/artikel');
        }

        $data = $artikel->where('id', $id)->first();
        $title = "Edit Artikel";
        return view('artikel/form_edit', compact('title', 'data'));
    }

    public function delete($id)
    {
        $artikel = new ArtikelModel();
        $artikel->delete($id);
        return redirect()->to('/admin/artikel');
    }
}
```

---

### 5. Membuat View Index Artikel
Buat direktori baru dengan nama **artikel** pada direktori **app/Views**, kemudian buat file baru dengan nama **index.php**:

```php
<?= $this->include('template/header'); ?>

<?php if($artikel): foreach($artikel as $row): ?>
<article class="entry">
    <h2><a href="<?= base_url('/artikel/' . $row['slug']);?>"><?= $row['judul']; ?></a></h2>
    <img src="<?= base_url('/gambar/' . $row['gambar']);?>" alt="<?= $row['judul']; ?>">
    <p><?= substr($row['isi'], 0, 200); ?></p>
</article>
<hr class="divider" />
<?php endforeach; else: ?>
<article class="entry">
    <h2>Belum ada data.</h2>
</article>
<?php endif; ?>

<?= $this->include('template/footer'); ?>
```

Selanjutnya buka browser dengan mengakses url `http://localhost/lab11_ci/ci4/public/artikel`

<img width="1918" height="766" alt="image" src="https://github.com/user-attachments/assets/1329ee4b-d91a-41c2-bcf5-db88395b1f09" />

---

### 6. Menambahkan Data Artikel
Tambahkan beberapa data pada database agar dapat ditampilkan datanya dengan menjalankan query berikut di phpMyAdmin:

```sql
INSERT INTO artikel (judul, isi, slug) VALUES
('Artikel pertama', 'Lorem Ipsum adalah contoh teks atau dummy dalam industri percetakan dan penataan huruf atau typesetting. Lorem Ipsum telah menjadi standar contoh teks sejak tahun 1500an, saat seorang tukang cetak yang tidak dikenal mengambil sebuah kumpulan teks dan mengacaknya untuk menjadi sebuah buku contoh huruf.', 'artikel-pertama'),
('Artikel kedua', 'Tidak seperti anggapan banyak orang, Lorem Ipsum bukanlah teks-teks yang diacak. Ia berakar dari sebuah naskah sastra latin klasik dari era 45 sebelum masehi, hingga bisa dipastikan usianya telah mencapai lebih dari 2000 tahun.', 'artikel-kedua');
```

Refresh kembali browser, sehingga akan ditampilkan hasilnya.

<img width="1919" height="746" alt="image" src="https://github.com/user-attachments/assets/9bd4b193-e751-443a-a0e1-26d3885e5d4f" />

---

### 7. Membuat Tampilan Detail Artikel
Tambahkan fungsi baru pada Controller Artikel dengan nama **view()** (sudah ada di Controller di atas).

Buat view baru untuk halaman detail dengan nama **app/Views/artikel/detail.php**:

```php
<?= $this->include('template/header'); ?>

<article class="entry">
    <h2><?= $artikel['judul']; ?></h2>
    <img src="<?= base_url('/gambar/' . $artikel['gambar']);?>" alt="<?= $artikel['judul']; ?>">
    <p><?= $artikel['isi']; ?></p>
</article>

<?= $this->include('template/footer'); ?>
```

Tambahkan routing untuk artikel detail di **app/Config/Routes.php**:

```php
$routes->get('/artikel/(:any)', 'Artikel::view/$1');
```

<img width="1919" height="730" alt="image" src="https://github.com/user-attachments/assets/fafba2f1-0bc7-4e95-b2df-683c5ccc0e7b" />

---

### 8. Membuat Menu Admin
Menu admin adalah untuk proses CRUD data artikel. Tambahkan method **admin_index()** pada Controller Artikel (sudah ada di Controller di atas).

Buat file **admin_index.php** pada direktori **app/Views/artikel/**:

```php
<?= $this->include('template/admin_header'); ?>

<table class="table">
    <thead>
        <tr>
            <th>ID</th>
            <th>Judul</th>
            <th>Status</th>
            <th>Aksi</th>
        </tr>
    </thead>
    <tbody>
        <?php if($artikel): foreach($artikel as $row): ?>
        <tr>
            <td><?= $row['id']; ?></td>
            <td>
                <b><?= $row['judul']; ?></b>
                <p><small><?= substr($row['isi'], 0, 50); ?></small></p>
            </td>
            <td><?= $row['status']; ?></td>
            <td>
                <a class="btn" href="<?= base_url('/admin/artikel/edit/' . $row['id']);?>">Ubah</a>
                <a class="btn btn-danger" onclick="return confirm('Yakin menghapus data?');" href="<?= base_url('/admin/artikel/delete/' . $row['id']);?>">Hapus</a>
            </td>
        </tr>
        <?php endforeach; else: ?>
        <tr>
            <td colspan="4">Belum ada data.</td>
        </tr>
        <?php endif; ?>
    </tbody>
    <tfoot>
        <tr>
            <th>ID</th>
            <th>Judul</th>
            <th>Status</th>
            <th>Aksi</th>
        </tr>
    </tfoot>
</table>

<?= $this->include('template/admin_footer'); ?>
```

Tambahkan routing untuk menu admin di **app/Config/Routes.php**:

```php
$routes->group('admin', function($routes) {
    $routes->get('artikel', 'Artikel::admin_index');
    $routes->add('artikel/add', 'Artikel::add');
    $routes->add('artikel/edit/(:any)', 'Artikel::edit/$1');
    $routes->get('artikel/delete/(:any)', 'Artikel::delete/$1');
});
```

Akses menu admin dengan url `http://localhost/lab11_ci/ci4/public/admin/artikel`

<img width="962" height="614" alt="image" src="https://github.com/user-attachments/assets/240a200f-b9ab-47cf-b57f-5b0929be518b" />

---

### 9. Menambah Data Artikel (Form Add)
Buat view untuk form tambah dengan nama **form_add.php** pada direktori **app/Views/artikel/**:

```php
<?= $this->include('template/admin_header'); ?>

<h2><?= $title; ?></h2>
<form action="" method="post">
    <p>
        <label>Judul</label><br>
        <input type="text" name="judul" style="width:100%; padding:8px;">
    </p>
    <p>
        <label>Isi Artikel</label><br>
        <textarea name="isi" cols="50" rows="10" style="width:100%; padding:8px;"></textarea>
    </p>
    <p>
        <input type="submit" value="Kirim" class="btn btn-large">
    </p>
</form>

<?= $this->include('template/admin_footer'); ?>
```

<img width="1919" height="727" alt="image" src="https://github.com/user-attachments/assets/59bff7be-eedd-4998-8820-8758701eea65" />
---

### 10. Mengubah Data Artikel (Form Edit)
Buat view untuk form edit dengan nama **form_edit.php** pada direktori **app/Views/artikel/**:

```php
<?= $this->include('template/admin_header'); ?>

<h2><?= $title; ?></h2>
<form action="" method="post">
    <p>
        <label>Judul</label><br>
        <input type="text" name="judul" value="<?= $data['judul'];?>" style="width:100%; padding:8px;">
    </p>
    <p>
        <label>Isi Artikel</label><br>
        <textarea name="isi" cols="50" rows="10" style="width:100%; padding:8px;"><?= $data['isi'];?></textarea>
    </p>
    <p>
        <input type="submit" value="Kirim" class="btn btn-large">
    </p>
</form>

<?= $this->include('template/admin_footer'); ?>
```

<img width="1914" height="829" alt="image" src="https://github.com/user-attachments/assets/b08031b8-2874-4133-a531-c6630fd9b2a7" />

---

Setelah menambah satu artikel

<img width="963" height="661" alt="image" src="https://github.com/user-attachments/assets/36b9fea3-b001-4636-aa56-b343d7544ddf" />

---

### 11. Menghapus Data Artikel
Fungsi hapus data sudah ada pada method **delete()** di Controller Artikel. Ketika tombol **Hapus** diklik, akan muncul konfirmasi "Yakin menghapus data?" sebelum data dihapus dari database.

Salah satu Data Yang sudah dihapus
<img width="1907" height="625" alt="image" src="https://github.com/user-attachments/assets/d600d0d0-3667-4717-82ef-926559a56179" />

---

## Hasil Akhir Praktikum 2

Fitur CRUD yang berhasil dibuat:
- **Read** - Menampilkan daftar artikel di halaman publik
- **Read Detail** - Menampilkan detail artikel saat judul diklik
- **Create** - Form tambah artikel baru di halaman admin
- **Update** - Form edit artikel yang sudah ada
- **Delete** - Hapus artikel dengan konfirmasi


<img width="1919" height="730" alt="image" src="https://github.com/user-attachments/assets/fafba2f1-0bc7-4e95-b2df-683c5ccc0e7b" />

<img width="962" height="614" alt="image" src="https://github.com/user-attachments/assets/240a200f-b9ab-47cf-b57f-5b0929be518b" />

<img width="1919" height="727" alt="image" src="https://github.com/user-attachments/assets/59bff7be-eedd-4998-8820-8758701eea65" />



# PRAKTIKUM 3: View Layout dan View Cell

## Langkah-langkah Praktikum

### 1. Persiapan
Pada praktikum sebelumnya kita telah menggunakan template layout dengan konsep parsial atau memecah bagian template menjadi beberapa bagian untuk kemudian di include pada view yang lain.

Praktikum kali ini kita akan menggunakan konsep **View Layout** dan **View Cell** untuk memudahkan dalam penggunaan layout.

Tambahkan field **created_at** pada tabel artikel di database:

```sql
ALTER TABLE artikel ADD COLUMN created_at DATETIME DEFAULT CURRENT_TIMESTAMP;
```

---

### 2. Membuat Layout Utama
Buat folder **layout** di dalam **app/Views/**, kemudian buat file **main.php** di dalam folder layout:

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title ?? 'My Website' ?></title>
    <link rel="stylesheet" href="<?= base_url('/style.css');?>">
</head>
<body>
    <div id="container">
        <header>
            <h1>Layout Sederhana</h1>
        </header>
        <nav>
            <a href="<?= base_url('/');?>" class="active">Home</a>
            <a href="<?= base_url('/artikel');?>">Artikel</a>
            <a href="<?= base_url('/about');?>">About</a>
            <a href="<?= base_url('/contact');?>">Kontak</a>
        </nav>
        <section id="wrapper">
            <section id="main">
                <?= $this->renderSection('content') ?>
            </section>
            <aside id="sidebar">
                <?= view_cell('App\\Cells\\ArtikelTerkini::render') ?>
                <div class="widget-box">
                    <h3 class="title">Widget Header</h3>
                    <ul>
                        <li><a href="#">Widget Link</a></li>
                        <li><a href="#">Widget Link</a></li>
                    </ul>
                </div>
                <div class="widget-box">
                    <h3 class="title">Widget Text</h3>
                    <p>Vestibulum lorem elit, iaculis in nisl volutpat, malesuada tincidunt arcu.</p>
                </div>
            </aside>
        </section>
        <footer>
            <p>&copy; 2021 - Universitas Pelita Bangsa</p>
        </footer>
    </div>
</body>
</html>
```

---

### 3. Modifikasi File View
Ubah file **app/Views/about.php** agar sesuai dengan layout baru:

```php
<?= $this->extend('layout/main') ?>

<?= $this->section('content') ?>
<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>
<?= $this->endSection() ?>
```

Lakukan hal yang sama untuk file **contact.php**, **faqs.php**, dan **artikel/index.php**.

---

### 4. Membuat Class View Cell
View Cell adalah fitur yang memungkinkan pemanggilan tampilan dalam bentuk komponen yang dapat digunakan ulang.

Buat folder **Cells** di dalam **app/**, kemudian buat file **ArtikelTerkini.php**:

```php
<?php

namespace App\Cells;

use App\Models\ArtikelModel;

class ArtikelTerkini
{
    public function render()
    {
        $model = new ArtikelModel();
        $artikel = $model->orderBy('created_at', 'DESC')->limit(5)->findAll();
        return view('components/artikel_terkini', ['artikel' => $artikel]);
    }
}
```

---

### 5. Membuat View untuk View Cell
Buat folder **components** di dalam **app/Views/**, kemudian buat file **artikel_terkini.php**:

```php
<div class="widget-box">
    <h3 class="title">Artikel Terkini</h3>
    <ul>
        <?php foreach ($artikel as $row): ?>
        <li><a href="<?= base_url('/artikel/' . $row['slug']) ?>"><?= $row['judul'] ?></a></li>
        <?php endforeach; ?>
    </ul>
</div>
```

---

### 6. Hasil Akhir
Refresh browser dan akses halaman:
```
localhost/lab11_ci/ci4/public/about
```

<img width="1714" height="761" alt="image" src="https://github.com/user-attachments/assets/4a7f7bce-62e6-4672-8898-b18739f43877" />
---

## Pertanyaan dan Tugas

**1. Apa manfaat utama dari penggunaan View Layout dalam pengembangan aplikasi?**

View Layout memungkinkan kita membuat template tampilan yang konsisten di semua halaman. Cukup ubah satu file layout, semua halaman yang menggunakannya akan ikut berubah. Ini membuat kode lebih efisien, terstruktur, dan mudah dipelihara.

**2. Jelaskan perbedaan antara View Cell dan View biasa.**

View biasa dipanggil langsung dari Controller dan menampilkan seluruh halaman. Sedangkan View Cell adalah komponen kecil yang bisa dipanggil dari dalam View manapun secara mandiri, memiliki logika sendiri untuk mengambil data, dan dapat digunakan ulang di berbagai halaman tanpa harus melewati Controller.

---

# Praktikum 4 - Modul Login CodeIgniter 4

Praktikum ini membahas pembuatan modul login menggunakan Framework CodeIgniter 4, mencakup konsep Auth dan Filter.

---

## 1. Membuat Tabel User

Jalankan query berikut di MySQL:

```sql
CREATE TABLE user (
  id INT(11) auto_increment,
  username VARCHAR(200) NOT NULL,
  useremail VARCHAR(200),
  userpassword VARCHAR(200),
  PRIMARY KEY(id)
);
```

---

## 2. Membuat Model

Buat file `app/Models/UserModel.php`:

```php
<?php
namespace App\Models;
use CodeIgniter\Model;

class UserModel extends Model
{
    protected $table = 'user';
    protected $primaryKey = 'id';
    protected $useAutoIncrement = true;
    protected $allowedFields = ['username', 'useremail', 'userpassword'];
}
```

---

## 3. Membuat Controller User

Buat file `app/Controllers/User.php` dengan dua method utama:

- `index()` → menampilkan daftar user
- `login()` → memproses login (cek email & password, set session)
- `logout()` → menghapus session dan redirect ke halaman login

---

## 4. Membuat View Login

Buat folder `app/Views/user/` lalu buat file `login.php` berisi form dengan field **email** dan **password**, serta tampilan pesan flash error jika login gagal.

---

## 5. Membuat Database Seeder

Buat seeder untuk data dummy user:

```bash
php spark make:seeder UserSeeder
```

Isi `app/Database/Seeds/UserSeeder.php` dengan data admin, lalu jalankan:

```bash
php spark db:seed UserSeeder
```

Kredensial default: `admin@email.com` / `admin123`

---

## 6. Menambahkan Auth Filter

Buat file `app/Filters/Auth.php` untuk mengecek session `logged_in`. Jika belum login, redirect ke `/user/login`.

Daftarkan filter di `app/Config/Filters.php`:

```php
'auth' => App\Filters\Auth::class
```

---

## 7. Konfigurasi Routes

Buka `app/Config/Routes.php`, terapkan filter `auth` pada grup route admin:

```php
$routes->group('admin', ['filter' => 'auth'], function($routes) {
    $routes->get('artikel', 'Artikel::admin_index');
    // ...
});
```

---

## Screenshot

<img width="1919" height="649" alt="image" src="https://github.com/user-attachments/assets/1654c1cb-928e-465b-9d14-963fb3cd31b6" />

---

# Praktikum 5 - Pagination dan Pencarian

---

## Langkah 1 - Modifikasi Controller untuk Pagination

Buka file `app/Controllers/Artikel.php`, cari method `admin_index()` dan ubah kodenya menjadi seperti berikut:

```php
public function admin_index()
{
    $title = 'Daftar Artikel';
    $model = new ArtikelModel();
    $data = [
        'title'   => $title,
        'artikel' => $model->paginate(10), // batasi 10 data per halaman
        'pager'   => $model->pager,
    ];
    return view('artikel/admin_index', $data);
}
```

> **Keterangan:**
> - `findAll()` diganti dengan `paginate(10)` agar data dibatasi 10 per halaman
> - Ditambahkan `'pager' => $model->pager` untuk mengirim navigasi halaman ke view

---

## Langkah 2 - Modifikasi Controller untuk Pencarian

Masih di file `app/Controllers/Artikel.php`, ubah kembali method `admin_index()` menjadi:

```php
public function admin_index()
{
    $title = 'Daftar Artikel';
    $q     = $this->request->getVar('q') ?? '';
    $model = new ArtikelModel();
    $data  = [
        'title'   => $title,
        'q'       => $q,
        'artikel' => $model->like('judul', $q)->paginate(10),
        'pager'   => $model->pager,
    ];
    return view('artikel/admin_index', $data);
}
```

> **Keterangan:**
> - Ditambahkan `$q` untuk menangkap kata kunci dari form pencarian
> - `->like('judul', $q)` untuk memfilter artikel berdasarkan judul
> - `'q' => $q` dikirim ke view agar kata kunci tetap tampil setelah submit

---

## Langkah 3 - Modifikasi View Admin Index

Buka file `app/Views/artikel/admin_index.php` dan ubah seluruh isinya menjadi:

```php
<?= $this->include('template/admin_header'); ?>

<h2><?= $title; ?></h2>

<div style="margin-bottom: 15px; display: flex; gap: 10px;">
    <form method="get" style="display: flex; gap: 10px; width: 100%;">
        <input type="text" name="q" value="<?= $q; ?>" 
               placeholder="Cari artikel..." 
               style="padding: 8px 12px; border: 1px solid #ccc; border-radius: 4px; width: 300px; font-size: 14px;">
        <input type="submit" value="🔍 Cari" 
               style="padding: 8px 20px; background-color: #1a6fc4; color: white; border: none; border-radius: 4px; cursor: pointer; font-size: 14px;">
    </form>
</div>

<table class="table" border="1" cellpadding="8" cellspacing="0" style="width: 100%;">
    <thead>
        <tr>
            <th>ID</th>
            <th>Judul</th>
            <th>Status</th>
            <th>Aksi</th>
        </tr>
    </thead>
    <tbody>
        <?php if($artikel): foreach($artikel as $row): ?>
        <tr>
            <td><?= $row['id']; ?></td>
            <td><b><?= $row['judul']; ?></b><br>
                <small><?= substr($row['isi'], 0, 100); ?>...</small>
            </td>
            <td><?= $row['status']; ?></td>
            <td>
                <a href="<?= base_url('/admin/artikel/edit/'. $row['id']); ?>">Edit</a> |
                <a href="<?= base_url('/admin/artikel/delete/'. $row['id']); ?>" 
                   onclick="return confirm('Yakin ingin menghapus?')">Hapus</a>
            </td>
        </tr>
        <?php endforeach; else: ?>
        <tr>
            <td colspan="4" style="text-align: center;">Belum ada data</td>
        </tr>
        <?php endif; ?>
    </tbody>
</table>

<div style="margin-top: 15px; display: flex; justify-content: center;">
    <?= $pager->only(['q'])->links(); ?>
</div>

<?= $this->include('template/admin_footer'); ?>
```

> **Keterangan:**
> - Form pencarian ditambahkan sebelum tabel
> - `$pager->only(['q'])->links()` ditambahkan setelah tabel agar keyword ikut terbawa saat pindah halaman

---

## Hasil Pagination

Buka url: `http://localhost/lab11_ci/ci4/public/index.php/admin/artikel`

<img width="1600" height="760" alt="image" src="https://github.com/user-attachments/assets/6fa3edb7-3035-4af9-a326-04dd1e75eaa2" />
---

## Hasil Pencarian

Masukkan kata kunci pada form pencarian, lalu klik tombol **Cari**.

<img width="1919" height="496" alt="image" src="https://github.com/user-attachments/assets/d683f0fb-b46a-4037-9dcf-0e010bd2dd85" />

---

## Kesimpulan

Pada praktikum ini telah berhasil dibuat fitur:
- **Pagination** — data artikel ditampilkan maksimal 10 per halaman dengan navigasi halaman di bawah tabel
- **Pencarian** — data artikel dapat difilter berdasarkan judul menggunakan form pencarian, dan keyword tetap terbawa saat pindah halaman


---

# Praktikum 6 - Relasi Tabel dan Query Builder

---

## Langkah 1 - Membuat Tabel Kategori

Buka **phpMyAdmin** → pilih database `lab_ci4` → klik tab **SQL** → jalankan query berikut:

```sql
CREATE TABLE kategori (
    id_kategori INT(11) AUTO_INCREMENT,
    nama_kategori VARCHAR(100) NOT NULL,
    slug_kategori VARCHAR(100),
    PRIMARY KEY (id_kategori)
);
```

<img width="957" height="466" alt="image" src="https://github.com/user-attachments/assets/3cd507e1-5bb5-4c7f-865d-18355e074142" />

---

## Langkah 2 - Menambah Kolom id_kategori pada Tabel Artikel

Masih di tab **SQL**, jalankan query berikut untuk menambahkan foreign key:

```sql
ALTER TABLE artikel
ADD COLUMN id_kategori INT(11),
ADD CONSTRAINT fk_kategori_artikel
FOREIGN KEY (id_kategori) REFERENCES kategori(id_kategori);
```

<img width="951" height="317" alt="image" src="https://github.com/user-attachments/assets/57dacdad-aec6-4075-9a17-6dbe45de3e40" />

---

## Langkah 3 - Menambah Data Kategori

Jalankan query berikut untuk mengisi data kategori:

```sql
INSERT INTO kategori (nama_kategori, slug_kategori) VALUES
('Framework', 'framework'),
('Database', 'database'),
('Pemrograman Web', 'pemrograman-web');
```

---

## Langkah 4 - Membuat Model Kategori

Buat file baru **`app/Models/KategoriModel.php`** dengan isi:

```php
<?php

namespace App\Models;

use CodeIgniter\Model;

class KategoriModel extends Model
{
    protected $table = 'kategori';
    protected $primaryKey = 'id_kategori';
    protected $useAutoIncrement = true;
    protected $allowedFields = ['nama_kategori', 'slug_kategori'];
}
```

---

## Langkah 5 - Modifikasi ArtikelModel

Buka **`app/Models/ArtikelModel.php`** dan ganti seluruh isinya:

```php
<?php

namespace App\Models;

use CodeIgniter\Model;

class ArtikelModel extends Model
{
    protected $table = 'artikel';
    protected $primaryKey = 'id';
    protected $useAutoIncrement = true;
    protected $allowedFields = ['judul', 'isi', 'status', 'slug', 'gambar', 'id_kategori'];

    public function getArtikelDenganKategori()
    {
        return $this->db->table('artikel')
            ->select('artikel.*, kategori.nama_kategori')
            ->join('kategori', 'kategori.id_kategori = artikel.id_kategori')
            ->get()
            ->getResultArray();
    }
}
```

---

## Langkah 6 - Modifikasi Controller Artikel

Buka **`app/Controllers/Artikel.php`** dan ganti seluruh isinya:

```php
<?php

namespace App\Controllers;

use App\Models\ArtikelModel;
use App\Models\KategoriModel;

class Artikel extends BaseController
{
    public function index()
    {
        $title = 'Daftar Artikel';
        $model = new ArtikelModel();
        $artikel = $model->getArtikelDenganKategori();
        return view('artikel/index', compact('artikel', 'title'));
    }

    public function admin_index()
    {
        $title = 'Daftar Artikel (Admin)';
        $model = new ArtikelModel();
        $q = $this->request->getVar('q') ?? '';
        $kategori_id = $this->request->getVar('kategori_id') ?? '';

        $builder = $model->db->table('artikel')
            ->select('artikel.*, kategori.nama_kategori')
            ->join('kategori', 'kategori.id_kategori = artikel.id_kategori', 'left');

        if ($q != '') {
            $builder->like('artikel.judul', $q);
        }

        if ($kategori_id != '') {
            $builder->where('artikel.id_kategori', $kategori_id);
        }

        $kategoriModel = new KategoriModel();

        $data = [
            'title'       => $title,
            'q'           => $q,
            'kategori_id' => $kategori_id,
            'artikel'     => $builder->get()->getResultArray(),
            'pager'       => null,
            'kategori'    => $kategoriModel->findAll(),
        ];

        return view('artikel/admin_index', $data);
    }

    public function add()
    {
        $kategoriModel = new KategoriModel();
        $data['kategori'] = $kategoriModel->findAll();
        $data['title'] = "Tambah Artikel";

        if ($this->request->getMethod() == 'post' && $this->validate([
            'judul'       => 'required',
            'id_kategori' => 'required',
        ])) {
            $model = new ArtikelModel();
            $model->insert([
                'judul'       => $this->request->getPost('judul'),
                'isi'         => $this->request->getPost('isi'),
                'slug'        => url_title($this->request->getPost('judul')),
                'id_kategori' => $this->request->getPost('id_kategori'),
            ]);
            return redirect()->to('/admin/artikel');
        }

        return view('artikel/form_add', $data);
    }

    public function edit($id)
    {
        $model = new ArtikelModel();
        $kategoriModel = new KategoriModel();

        $data['artikel']  = $model->find($id);
        $data['kategori'] = $kategoriModel->findAll();
        $data['title']    = "Edit Artikel";

        if ($this->request->getMethod() == 'post' && $this->validate([
            'judul'       => 'required',
            'id_kategori' => 'required',
        ])) {
            $model->update($id, [
                'judul'       => $this->request->getPost('judul'),
                'isi'         => $this->request->getPost('isi'),
                'id_kategori' => $this->request->getPost('id_kategori'),
            ]);
            return redirect()->to('/admin/artikel');
        }

        return view('artikel/form_edit', $data);
    }

    public function delete($id)
    {
        $model = new ArtikelModel();
        $model->delete($id);
        return redirect()->to('/admin/artikel');
    }

    public function view($slug)
    {
        $model = new ArtikelModel();
        $artikel = $model->where('slug', $slug)->first();

        if (!$artikel) {
            throw \CodeIgniter\Exceptions\PageNotFoundException::forPageNotFound();
        }

        $title = $artikel['judul'];
        return view('artikel/detail', compact('artikel', 'title'));
    }
}
```

---

## Langkah 7 - Modifikasi View

### admin_index.php
Buka **`app/Views/artikel/admin_index.php`** dan sesuaikan tampilannya dengan menambahkan kolom Kategori dan dropdown filter kategori.

### form_add.php
Buka **`app/Views/artikel/form_add.php`** dan tambahkan dropdown pilihan kategori:

```php
<?= $this->include('template/admin_header'); ?>

<h2><?= $title; ?></h2>

<form action="" method="post">
    <p>
        <label for="judul">Judul</label>
        <input type="text" name="judul" id="judul" required>
    </p>
    <p>
        <label for="isi">Isi</label>
        <textarea name="isi" id="isi" cols="50" rows="10"></textarea>
    </p>
    <p>
        <label for="id_kategori">Kategori</label>
        <select name="id_kategori" id="id_kategori" required>
            <?php foreach($kategori as $k): ?>
            <option value="<?= $k['id_kategori']; ?>"><?= $k['nama_kategori']; ?></option>
            <?php endforeach; ?>
        </select>
    </p>
    <p><input type="submit" value="Kirim" class="btn btn-large"></p>
</form>

<?= $this->include('template/admin_footer'); ?>
```

### form_edit.php
Buka **`app/Views/artikel/form_edit.php`** dan tambahkan dropdown kategori:

```php
<?= $this->include('template/admin_header'); ?>

<h2><?= $title; ?></h2>

<form action="" method="post">
    <p>
        <label for="judul">Judul</label>
        <input type="text" name="judul" value="<?= $artikel['judul']; ?>" id="judul" required>
    </p>
    <p>
        <label for="isi">Isi</label>
        <textarea name="isi" id="isi" cols="50" rows="10"><?= $artikel['isi']; ?></textarea>
    </p>
    <p>
        <label for="id_kategori">Kategori</label>
        <select name="id_kategori" id="id_kategori" required>
            <?php foreach($kategori as $k): ?>
            <option value="<?= $k['id_kategori']; ?>" <?= ($artikel['id_kategori'] == $k['id_kategori']) ? 'selected' : ''; ?>>
                <?= $k['nama_kategori']; ?>
            </option>
            <?php endforeach; ?>
        </select>
    </p>
    <p><input type="submit" value="Kirim" class="btn btn-large"></p>
</form>

<?= $this->include('template/admin_footer'); ?>
```

---

## Langkah 8 - Update Data Artikel Lama

Karena artikel lama belum memiliki kategori, update melalui **phpMyAdmin** → tab **SQL**:

```sql
UPDATE artikel SET id_kategori = 1 WHERE id = 1;
UPDATE artikel SET id_kategori = 3 WHERE id = 2;
UPDATE artikel SET id_kategori = 2 WHERE id = 3;
```

---

## Hasil Daftar Artikel dengan Kategori

Buka url: `http://localhost/lab11_ci/ci4/public/index.php/admin/artikel`

<img width="1512" height="837" alt="image" src="https://github.com/user-attachments/assets/28882e17-cf91-4de1-bc8b-a1fe2116c0d2" />


---

## Hasil Filter Kategori

Pilih salah satu kategori dari dropdown lalu klik Cari.

<img width="1240" height="565" alt="image" src="https://github.com/user-attachments/assets/367b1fb9-6631-4f8d-ba87-aacc0c356e8e" />


---

## Hasil Tambah Artikel dengan Kategori

Klik menu **Tambah Artikel**, pastikan dropdown kategori muncul.

<img width="1210" height="688" alt="image" src="https://github.com/user-attachments/assets/b775192f-cccb-424e-9f7c-fc57de71cfc9" />

---

## Hasil Edit Artikel dengan Kategori

Klik **Edit** pada salah satu artikel, pastikan dropdown kategori muncul dan terisi sesuai kategori artikel.

<img width="1203" height="682" alt="image" src="https://github.com/user-attachments/assets/a291db95-04ed-4615-9a0d-adb0ac5329d9" />

---

## Kesimpulan

Pada praktikum ini telah berhasil dibuat:
- **Relasi One-to-Many** antara tabel `kategori` dan tabel `artikel`
- **Query Builder dengan JOIN** untuk mengambil data artikel beserta nama kategorinya
- **Filter berdasarkan kategori** pada halaman admin artikel
- **Form tambah dan edit artikel** dengan pilihan kategori

---

# Praktikum 7 - Upload File Gambar

---

## Langkah 1 - Membuat Folder untuk Menyimpan Gambar

Buat folder baru di dalam folder `public` untuk menyimpan gambar yang diupload:

```
C:\Xampp\htdocs\lab11_ci\ci4\public\gambar
```

Atau bisa lewat CMD:

```bash
mkdir "C:\Xampp\htdocs\lab11_ci\ci4\public\gambar"
```

---

## Langkah 2 - Modifikasi Method add() di Controller Artikel

Buka file **`app/Controllers/Artikel.php`**, cari method `add()` dan ubah kodenya menjadi:

```php
public function add()
{
    $kategoriModel = new KategoriModel();
    $data['kategori'] = $kategoriModel->findAll();
    $data['title'] = "Tambah Artikel";

    if ($this->request->getMethod() == 'post') {
        $file = $this->request->getFile('gambar');

        if ($file && $file->isValid() && !$file->hasMoved()) {
            $file->move(ROOTPATH . 'public/gambar');
            $namaGambar = $file->getName();
        } else {
            $namaGambar = '';
        }

        $model = new ArtikelModel();
        $model->insert([
            'judul'       => $this->request->getPost('judul'),
            'isi'         => $this->request->getPost('isi'),
            'slug'        => url_title($this->request->getPost('judul')),
            'id_kategori' => $this->request->getPost('id_kategori'),
            'gambar'      => $namaGambar,
        ]);
        return redirect()->to('/admin/artikel');
    }

    return view('artikel/form_add', $data);
}
```

> **Keterangan:**
> - `$this->request->getFile('gambar')` → mengambil file yang diupload
> - `$file->move(ROOTPATH . 'public/gambar')` → memindahkan file ke folder gambar
> - `$file->getName()` → mengambil nama file untuk disimpan di database

---

## Langkah 3 - Modifikasi View form_add.php

Buka file **`app/Views/artikel/form_add.php`** dan ubah seluruh isinya:

```php
<?= $this->include('template/admin_header'); ?>

<h2><?= $title; ?></h2>

<form action="" method="post" enctype="multipart/form-data">
    <?= csrf_field(); ?>
    <p>
        <label for="judul">Judul</label>
        <input type="text" name="judul" id="judul" required>
    </p>
    <p>
        <label for="isi">Isi</label>
        <textarea name="isi" id="isi" cols="50" rows="10"></textarea>
    </p>
    <p>
        <label for="id_kategori">Kategori</label>
        <select name="id_kategori" id="id_kategori" required>
            <?php foreach($kategori as $k): ?>
            <option value="<?= $k['id_kategori']; ?>"><?= $k['nama_kategori']; ?></option>
            <?php endforeach; ?>
        </select>
    </p>
    <p>
        <label for="gambar">Gambar</label>
        <input type="file" name="gambar" id="gambar">
    </p>
    <p><input type="submit" value="Kirim" class="btn btn-large"></p>
</form>

<?= $this->include('template/admin_footer'); ?>
```

> **Keterangan:**
> - `enctype="multipart/form-data"` → wajib ditambahkan agar form bisa mengirim file
> - `<?= csrf_field(); ?>` → token keamanan untuk mencegah CSRF attack
> - `<input type="file" name="gambar">` → input untuk memilih file gambar

---

## Hasil Form Tambah Artikel dengan Upload Gambar

Buka url: `http://localhost/lab11_ci/ci4/public/index.php/admin/artikel/add`

<img width="1514" height="896" alt="image" src="https://github.com/user-attachments/assets/44e72c07-ffbb-4829-86f7-6544a0d0f352" />


---

## Hasil Setelah Menambah Artikel dengan Gambar

Isi form tambah artikel, pilih gambar dari komputer, lalu klik **Kirim**. Artikel baru akan muncul di daftar artikel.

> 📸 **[SCREENSHOT DAFTAR ARTIKEL SETELAH BERHASIL MENAMBAH ARTIKEL BARU DI SINI]**

---

## Hasil Gambar Tersimpan di Folder

Cek folder `public/gambar` untuk memastikan gambar berhasil tersimpan.

> 📸 **[SCREENSHOT FOLDER public/gambar YANG BERISI FILE GAMBAR DI SINI]**

---

## Kesimpulan

Pada praktikum ini telah berhasil dibuat fitur:
- **Upload File Gambar** pada form tambah artikel
- File gambar tersimpan di folder `public/gambar`
- Nama file gambar tersimpan di database pada kolom `gambar`
- Form menggunakan `enctype="multipart/form-data"` agar bisa mengirim file

---

# Praktikum 8 - AJAX

---

## Apa itu AJAX?

AJAX (Asynchronous JavaScript and XML) adalah kumpulan teknik pengembangan web yang memungkinkan aplikasi web memperbarui dan menampilkan data dari server tanpa harus melakukan reload halaman secara keseluruhan. Hal ini membuat aplikasi web terasa lebih responsif dan dinamis.

**Cara Kerja AJAX:**
1. Pengguna melakukan aksi di halaman web (klik tombol, isi form, dll)
2. JavaScript membuat request HTTP ke server
3. Server memproses request dan mengambil data dari database
4. Server mengirim respon dalam format JSON
5. JavaScript memperbarui tampilan halaman tanpa reload

---

## Langkah 1 - Menambahkan Library jQuery

Download jQuery dari **https://jquery.com/download/** lalu simpan file dengan nama `jquery-3.6.0.min.js`.

Buat folder dan salin file jQuery ke dalamnya:

```bash
mkdir ci4\public\assets\js
```

Salin file `jquery-3.6.0.min.js` ke:

```
C:\Xampp\htdocs\lab11_ci\ci4\public\assets\js\
```

<img width="1875" height="162" alt="image" src="https://github.com/user-attachments/assets/947636dc-9829-4fa6-b869-dddc306bb4df" />


---

## Langkah 2 - Membuat AJAX Controller

Buat file baru **`app/Controllers/AjaxController.php`** dengan isi:

```php
<?php

namespace App\Controllers;

use CodeIgniter\Controller;
use App\Models\ArtikelModel;

class AjaxController extends Controller
{
    public function index()
    {
        return view('ajax/index');
    }

    public function getData()
    {
        $model = new ArtikelModel();
        $data = $model->findAll();
        return $this->response->setJSON($data);
    }

    public function delete($id)
    {
        $model = new ArtikelModel();
        $model->delete($id);
        $data = [
            'status' => 'OK'
        ];
        return $this->response->setJSON($data);
    }
}
```

> **Keterangan:**
> - `getData()` mengambil semua data artikel dan mengirimkannya dalam format JSON
> - `delete()` menghapus artikel berdasarkan id dan mengirimkan status OK dalam format JSON

---

## Langkah 3 - Menambahkan Route

Buka **`app/Config/Routes.php`** dan tambahkan route berikut sebelum group admin:

```php
$routes->get('/ajax', 'AjaxController::index');
$routes->get('/ajax/getData', 'AjaxController::getData');
$routes->delete('/ajax/delete/(:num)', 'AjaxController::delete/$1');
```

---

## Langkah 4 - Membuat View AJAX

Buat folder baru **`app/Views/ajax/`** lalu buat file **`index.php`** di dalamnya dengan isi:

```php
<?= $this->include('template/header'); ?>

<h1>Data Artikel</h1>

<table id="artikelTable" border="1" cellpadding="8" cellspacing="0" style="width: 100%;">
    <thead>
        <tr>
            <th>ID</th>
            <th>Judul</th>
            <th>Status</th>
            <th>Aksi</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td colspan="4" style="text-align: center;">Loading data...</td>
        </tr>
    </tbody>
</table>

<script src="<?= base_url('assets/js/jquery-3.6.0.min.js') ?>"></script>
<script>
$(document).ready(function() {

    function showLoadingMessage() {
        $('#artikelTable tbody').html('<tr><td colspan="4" style="text-align:center;">Loading data...</td></tr>');
    }

    function loadData() {
        showLoadingMessage();
        $.ajax({
            url: "<?= base_url('ajax/getData') ?>",
            method: "GET",
            dataType: "json",
            success: function(data) {
                var tableBody = "";
                for (var i = 0; i < data.length; i++) {
                    var row = data[i];
                    tableBody += '<tr>';
                    tableBody += '<td>' + row.id + '</td>';
                    tableBody += '<td>' + row.judul + '</td>';
                    tableBody += '<td>' + row.status + '</td>';
                    tableBody += '<td>';
                    tableBody += '<a href="<?= base_url('admin/artikel/edit/') ?>' + row.id + '" style="padding:5px 10px;background:#42a5f5;color:white;border-radius:4px;text-decoration:none;margin-right:5px;">Edit</a>';
                    tableBody += '<a href="#" class="btn-delete" data-id="' + row.id + '" style="padding:5px 10px;background:#ef5350;color:white;border-radius:4px;text-decoration:none;">Delete</a>';
                    tableBody += '</td>';
                    tableBody += '</tr>';
                }
                $('#artikelTable tbody').html(tableBody);
            },
            error: function() {
                $('#artikelTable tbody').html('<tr><td colspan="4" style="text-align:center;">Gagal memuat data.</td></tr>');
            }
        });
    }

    loadData();

    $(document).on('click', '.btn-delete', function(e) {
        e.preventDefault();
        var id = $(this).data('id');
        if (confirm('Apakah Anda yakin ingin menghapus artikel ini?')) {
            $.ajax({
                url: "<?= base_url('ajax/delete/') ?>" + id,
                method: "DELETE",
                success: function(data) {
                    alert('Artikel berhasil dihapus!');
                    loadData();
                },
                error: function(jqXHR, textStatus, errorThrown) {
                    alert('Error: ' + textStatus + ' ' + errorThrown);
                }
            });
        }
    });

});
</script>

<?= $this->include('template/footer'); ?>
```

> **Keterangan:**
> - `loadData()` fungsi untuk mengambil data dari server menggunakan AJAX dan menampilkannya di tabel tanpa reload halaman
> - `showLoadingMessage()` menampilkan pesan loading saat data sedang diambil
> - `.btn-delete` tombol hapus yang menggunakan AJAX untuk menghapus artikel tanpa reload halaman

---

## Hasil Halaman AJAX

Buka url: `http://localhost/lab11_ci/ci4/public/index.php/ajax`

<img width="593" height="328" alt="image" src="https://github.com/user-attachments/assets/fc97797b-e16e-479c-8687-c15303862e08" />
*

---

## Hasil Hapus Data dengan AJAX

Klik tombol **Delete** pada salah satu artikel, konfirmasi penghapusan, dan data akan terhapus tanpa reload halaman.

**Notifikasi Delete**
<img width="1606" height="754" alt="image" src="https://github.com/user-attachments/assets/8070649c-123d-4b78-ae22-78b3d92cfe6f" />


**Setelah Data dihapus**
<img width="1503" height="689" alt="image" src="https://github.com/user-attachments/assets/2f0c3d4f-b67c-4689-99b2-cd2f746ac876" />

## Kesimpulan

Pada praktikum ini telah berhasil dibuat:
- **AJAX Controller** untuk menangani request AJAX dari browser
- **Fitur load data** menggunakan AJAX tanpa reload halaman
- **Fitur hapus data** menggunakan AJAX tanpa reload halaman
- **Library jQuery** digunakan untuk mempermudah proses AJAX

---

# Praktikum 9 - Implementasi AJAX Pagination dan Search

---

## Langkah 1 - Modifikasi Controller admin_index()

Buka **`app/Controllers/Artikel.php`**, cari method `admin_index()` dan ubah kodenya menjadi:

```php
public function admin_index()
{
    $title = 'Daftar Artikel (Admin)';
    $model = new ArtikelModel();
    $q = $this->request->getVar('q') ?? '';
    $kategori_id = $this->request->getVar('kategori_id') ?? '';
    $page = $this->request->getVar('page') ?? 1;

    $builder = $model->db->table('artikel')
        ->select('artikel.*, kategori.nama_kategori')
        ->join('kategori', 'kategori.id_kategori = artikel.id_kategori', 'left');

    if ($q != '') {
        $builder->like('artikel.judul', $q);
    }

    if ($kategori_id != '') {
        $builder->where('artikel.id_kategori', $kategori_id);
    }

    $artikel = $model->paginate(10, 'default', $page);
    $pager = $model->pager;

    $data = [
        'title'       => $title,
        'q'           => $q,
        'kategori_id' => $kategori_id,
        'artikel'     => $builder->get()->getResultArray(),
        'pager'       => $pager,
    ];

    if ($this->request->isAJAX()) {
        return $this->response->setJSON($data);
    } else {
        $kategoriModel = new KategoriModel();
        $data['kategori'] = $kategoriModel->findAll();
        return view('artikel/admin_index', $data);
    }
}
```

> **Keterangan:**
> - `$page` mengambil nomor halaman dari request, default ke halaman 1
> - `paginate(10, 'default', $page)` menerapkan pagination dengan nomor halaman yang diberikan
> - `isAJAX()` memeriksa apakah request yang datang adalah AJAX
> - Jika AJAX → kembalikan data dalam format JSON
> - Jika bukan AJAX → tampilkan view seperti biasa

---

## Langkah 2 - Modifikasi View admin_index.php

Buka **`app/Views/artikel/admin_index.php`** dan ubah seluruh isinya. Perubahan utama yang dilakukan:

- Menghapus tabel statis dan menggantinya dengan `<div id="article-container">` yang akan diisi oleh AJAX
- Menambahkan `<div id="pagination-container">` untuk pagination yang dirender oleh AJAX
- Menambahkan `<div id="loading">` sebagai indikator loading
- Menambahkan kode jQuery untuk melakukan request AJAX

```php
<?= $this->include('template/admin_header'); ?>

<h2><?= $title; ?></h2>

<div style="margin-bottom: 15px;">
    <form id="search-form" style="display: flex; gap: 10px; flex-wrap: wrap; align-items: center;">
        <input type="text" name="q" id="search-box" value="<?= $q; ?>"
               placeholder="Cari judul artikel..."
               style="padding: 8px 12px; border: 1px solid #ccc; border-radius: 4px; font-size: 14px;">
        <select name="kategori_id" id="category-filter"
                style="padding: 8px 12px; border: 1px solid #ccc; border-radius: 4px; font-size: 14px;">
            <option value="">Semua Kategori</option>
            <?php foreach ($kategori as $k): ?>
            <option value="<?= $k['id_kategori']; ?>" <?= ($kategori_id == $k['id_kategori']) ? 'selected' : ''; ?>>
                <?= $k['nama_kategori']; ?>
            </option>
            <?php endforeach; ?>
        </select>
        <input type="submit" value=" Cari"
               style="padding: 8px 20px; background-color: #1a6fc4; color: white; border: none; border-radius: 4px; cursor: pointer;">
    </form>
</div>

<div id="loading" style="display:none; text-align:center; padding:20px; color:#1a6fc4; font-weight:bold;">
     Loading data...
</div>
<div id="article-container"></div>
<div id="pagination-container" style="margin-top: 15px; display: flex; justify-content: center;"></div>

<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script>
$(document).ready(function() {
    const articleContainer = $('#article-container');
    const paginationContainer = $('#pagination-container');
    const searchForm = $('#search-form');
    const searchBox = $('#search-box');
    const categoryFilter = $('#category-filter');
    const loading = $('#loading');

    const fetchData = (url) => {
        loading.show();
        articleContainer.hide();
        paginationContainer.hide();

        $.ajax({
            url: url,
            type: 'GET',
            dataType: 'json',
            headers: { 'X-Requested-With': 'XMLHttpRequest' },
            success: function(data) {
                renderArticles(data.artikel);
                loading.hide();
                articleContainer.show();
                paginationContainer.show();
            },
            error: function() {
                loading.hide();
                articleContainer.html('<p style="color:red; text-align:center;">Gagal memuat data.</p>');
                articleContainer.show();
            }
        });
    };

    const renderArticles = (articles) => {
        let html = '<table border="1" cellpadding="8" cellspacing="0" style="width:100%;">';
        html += '<thead style="background:#1a6fc4; color:white;"><tr><th>ID</th><th>Judul</th><th>Kategori</th><th>Status</th><th>Aksi</th></tr></thead><tbody>';

        if (articles.length > 0) {
            articles.forEach(article => {
                html += `<tr>
                    <td>${article.id}</td>
                    <td><b>${article.judul}</b><br><small>${article.isi.substring(0, 80)}...</small></td>
                    <td>${article.nama_kategori}</td>
                    <td>${article.status == 1 ? 'Aktif' : 'Draft'}</td>
                    <td>
                        <a href="<?= base_url('admin/artikel/edit/') ?>${article.id}" style="padding:5px 10px;background:#42a5f5;color:white;border-radius:4px;text-decoration:none;margin-right:5px;">✏️ Edit</a>
                        <a href="<?= base_url('admin/artikel/delete/') ?>${article.id}" onclick="return confirm('Yakin menghapus?');" style="padding:5px 10px;background:#ef5350;color:white;border-radius:4px;text-decoration:none;"> Hapus</a>
                    </td>
                </tr>`;
            });
        } else {
            html += '<tr><td colspan="5" style="text-align:center;">Tidak ada data.</td></tr>';
        }

        html += '</tbody></table>';
        articleContainer.html(html);
    };

    searchForm.on('submit', function(e) {
        e.preventDefault();
        const q = searchBox.val();
        const kategori_id = categoryFilter.val();
        fetchData(`<?= base_url('admin/artikel') ?>?q=${q}&kategori_id=${kategori_id}`);
    });

    categoryFilter.on('change', function() {
        searchForm.trigger('submit');
    });

    fetchData('<?= base_url('admin/artikel') ?>');
});
</script>

<?= $this->include('template/admin_footer'); ?>
```

---

## Hasil Halaman Admin Artikel dengan AJAX

Buka url: `http://localhost/lab11_ci/ci4/public/index.php/admin/artikel`

<img width="1919" height="728" alt="image" src="https://github.com/user-attachments/assets/447c5d44-802f-4a71-8ef2-09f37bfa8956" />

---

## Hasil Pencarian dengan AJAX

Ketik kata kunci di form pencarian dan klik **Cari**, data akan difilter tanpa reload halaman.

<img width="1188" height="506" alt="image" src="https://github.com/user-attachments/assets/e4200122-1695-45ad-919d-a3dc9ea2e899" />

<img width="1181" height="571" alt="image" src="https://github.com/user-attachments/assets/82b16d98-ad2e-446a-a3b2-469a74bfae82" />


---

## Hasil Filter Kategori dengan AJAX

Pilih kategori dari dropdown, data akan langsung difilter tanpa reload halaman.

<img width="1183" height="503" alt="image" src="https://github.com/user-attachments/assets/a6ee703b-0c8c-4cd1-951e-2a26462a7524" />

<img width="1187" height="569" alt="image" src="https://github.com/user-attachments/assets/df9fcfc6-26a2-42b8-a45b-9af99de80f15" />

---

## Kesimpulan

Pada praktikum ini telah berhasil diimplementasikan:
- **AJAX Load Data** — data artikel dimuat otomatis menggunakan AJAX tanpa reload halaman
- **AJAX Search** — pencarian artikel tanpa reload halaman menggunakan AJAX
- **AJAX Filter Kategori** — filter berdasarkan kategori tanpa reload halaman
- **Loading Indicator** — indikator loading saat data sedang diambil dari server
- **isAJAX() check** — controller dapat membedakan request AJAX dan request biasa
EOF


# PRAKTIKUM 10

<img width="1445" height="1012" alt="image" src="https://github.com/user-attachments/assets/2b7dcb56-f51d-4b1f-baf8-7b22f3f60c8a" />

<img width="1444" height="971" alt="image" src="https://github.com/user-attachments/assets/8f01f741-6c70-4e3f-95b5-e4344ebe06f4" />

<img width="1441" height="1004" alt="image" src="https://github.com/user-attachments/assets/4cfd5be1-ac5d-43c0-a389-2f6494e2546d" />

<img width="1443" height="1010" alt="image" src="https://github.com/user-attachments/assets/4f4fc4d5-501f-4004-a33c-eec29e68500f" />

<img width="1443" height="1006" alt="image" src="https://github.com/user-attachments/assets/eb61d102-7602-4cbb-b28c-ae4aebf64291" />


# Praktikum 10 - REST API

---

## Apa itu REST API?

REST (Representational State Transfer) adalah salah satu desain arsitektur API yang berisi aturan untuk membuat web service. REST API bisa diakses atau dihubungkan dengan aplikasi lain dan biasanya mengirim/menerima data dalam format JSON.

**Cara kerja REST API:**
- **REST Server** → bertindak sebagai penyedia data
- **REST Client** → membuat HTTP request ke server menggunakan URI
- Server memberikan response dalam format **JSON**

---

## Langkah 1 - Install Postman

Download dan install Postman dari **https://www.postman.com/downloads/**

Postman digunakan sebagai REST Client untuk testing REST API.

<img width="1914" height="879" alt="image" src="https://github.com/user-attachments/assets/a83cb5e7-3fd6-4236-903e-9cbf9bed8a46" />

---

## Langkah 2 - Membuat REST Controller

Buat file baru **`app/Controllers/Post.php`** dengan isi:

```php
<?php

namespace App\Controllers;

use CodeIgniter\RESTful\ResourceController;
use CodeIgniter\API\ResponseTrait;
use App\Models\ArtikelModel;

class Post extends ResourceController
{
    use ResponseTrait;

    public function index()
    {
        $model = new ArtikelModel();
        $data['artikel'] = $model->orderBy('id', 'DESC')->findAll();
        return $this->respond($data);
    }

    public function create()
    {
        $model = new ArtikelModel();
        $data = [
            'judul' => $this->request->getVar('judul'),
            'isi'   => $this->request->getVar('isi'),
        ];
        $model->insert($data);
        $response = [
            'status'   => 201,
            'error'    => null,
            'messages' => [
                'success' => 'Data artikel berhasil ditambahkan.'
            ]
        ];
        return $this->respondCreated($response);
    }

    public function show($id = null)
    {
        $model = new ArtikelModel();
        $data = $model->where('id', $id)->first();
        if ($data) {
            return $this->respond($data);
        } else {
            return $this->failNotFound('Data tidak ditemukan.');
        }
    }

    public function update($id = null)
    {
        $model = new ArtikelModel();
        $data = [
            'judul' => $this->request->getVar('judul'),
            'isi'   => $this->request->getVar('isi'),
        ];
        $model->update($id, $data);
        $response = [
            'status'   => 200,
            'error'    => null,
            'messages' => [
                'success' => 'Data artikel berhasil diubah.'
            ]
        ];
        return $this->respond($response);
    }

    public function delete($id = null)
    {
        $model = new ArtikelModel();
        $data = $model->where('id', $id)->first();
        if ($data) {
            $model->delete($id);
            $response = [
                'status'   => 200,
                'error'    => null,
                'messages' => [
                    'success' => 'Data artikel berhasil dihapus.'
                ]
            ];
            return $this->respondDeleted($response);
        } else {
            return $this->failNotFound('Data tidak ditemukan.');
        }
    }
}
```

> **Keterangan 5 method:**
> - `index()` → menampilkan semua data artikel
> - `create()` → menambahkan data baru
> - `show()` → menampilkan data spesifik berdasarkan ID
> - `update()` → mengubah data berdasarkan ID
> - `delete()` → menghapus data berdasarkan ID

---

## Langkah 3 - Menambahkan Route

Buka **`app/Config/Routes.php`** dan tambahkan baris berikut **di luar** group admin:

```php
$routes->resource('post');
```

Satu baris ini akan menghasilkan banyak endpoint sekaligus:

| Method | Route | Fungsi |
|--------|-------|--------|
| GET | /post | Tampilkan semua data |
| GET | /post/new | Form tambah data |
| POST | /post | Simpan data baru |
| GET | /post/{id} | Tampilkan data spesifik |
| GET | /post/{id}/edit | Form edit data |
| PUT/PATCH | /post/{id} | Update data |
| DELETE | /post/{id} | Hapus data |

---

## Langkah 4 - Testing dengan Postman

### GET - Menampilkan Semua Data
- Method: **GET**
- URL: `http://localhost/lab11_ci/ci4/public/index.php/post`
- Klik **Send**

<img width="1445" height="1012" alt="image" src="https://github.com/user-attachments/assets/2b7dcb56-f51d-4b1f-baf8-7b22f3f60c8a" />

---

### GET - Menampilkan Data Spesifik
- Method: **GET**
- URL: `http://localhost/lab11_ci/ci4/public/index.php/post/2`
- Klik **Send**

<img width="1444" height="971" alt="image" src="https://github.com/user-attachments/assets/8f01f741-6c70-4e3f-95b5-e4344ebe06f4" />

---

### POST - Menambah Data Baru
- Method: **POST**
- URL: `http://localhost/lab11_ci/ci4/public/index.php/post`
- Tab **Body** → pilih **x-www-form-urlencoded**
- Isi Key dan Value:

| Key | Value |
|-----|-------|
| judul | Artikel Baru via API |
| isi | Ini isi artikel yang ditambahkan melalui REST API |

- Klik **Send**

<img width="1441" height="1004" alt="image" src="https://github.com/user-attachments/assets/4cfd5be1-ac5d-43c0-a389-2f6494e2546d" />

---

### PUT - Mengubah Data
- Method: **PUT**
- URL: `http://localhost/lab11_ci/ci4/public/index.php/post/2`
- Tab **Body** → pilih **x-www-form-urlencoded**
- Isi Key dan Value:

| Key | Value |
|-----|-------|
| judul | Judul yang Diubah via API |
| isi | Isi artikel yang sudah diubah via API |

- Klik **Send**

<img width="1443" height="1010" alt="image" src="https://github.com/user-attachments/assets/4f4fc4d5-501f-4004-a33c-eec29e68500f" />

---

### DELETE - Menghapus Data
- Method: **DELETE**
- URL: `http://localhost/lab11_ci/ci4/public/index.php/post/2`
- Klik **Send**

<img width="1443" height="1006" alt="image" src="https://github.com/user-attachments/assets/eb61d102-7602-4cbb-b28c-ae4aebf64291" />

---

## Kesimpulan

Pada praktikum ini telah berhasil dibuat:
- **REST Controller** dengan 5 method (index, create, show, update, delete)
- **Route Resource** yang menghasilkan banyak endpoint sekaligus
- **Testing API** menggunakan Postman untuk semua method HTTP (GET, POST, PUT, DELETE)
- Data dikirim dan diterima dalam format **JSON**


# PRAKTIKUM 11  VueJS
---

## Langkah-langkah Praktikum

### 1. Apa itu VueJS?

VueJS merupakan sebuah framework JavaScript untuk membangun aplikasi web atau tampilan interface website agar lebih interaktif. VueJS dapat digunakan untuk membangun aplikasi berbasis user interface, seperti halaman web, aplikasi mobile, dan aplikasi desktop.

Framework ini menawarkan berbagai fitur seperti:
- **Reactive data binding** — data yang berubah otomatis memperbarui tampilan
- **Component-based architecture** — membangun UI dari komponen-komponen kecil
- **Tools untuk membangun aplikasi skalabel**

Library VueJS berfokus pada **view layer** sehingga mudah diimplementasikan dan diintegrasikan dengan library lain seperti Axios untuk HTTP request.

Dokumentasi lengkap: https://vuejs.org/guide/introduction

---

### 2. Persiapan

Untuk praktikum ini kita menggunakan cara **manual** dengan CDN (tanpa npm).

Library yang dibutuhkan:

**Library VueJS 3:**
```html
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
```

**Library Axios (untuk call REST API):**
```html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

---

### 3. Struktur Direktori

Buat project baru dengan struktur file dan direktori seperti berikut di dalam folder **htdocs**:

```
lab11_vuejs/
│   index.html
└───assets/
    ├───css/
    │       style.css
    └───js/
            app.js
```

>  Folder `lab11_vuejs` berada **sejajar** dengan folder `lab11_ci` di dalam htdocs, bukan di dalamnya.

```
htdocs/
├── lab11_ci/        ← Backend CI4 (REST API)
└── lab11_vuejs/     ← Frontend VueJS (project ini)
```

---

### 4. Mengaktifkan CORS pada CI4

Karena frontend VueJS dan backend CI4 berada di path yang berbeda, perlu mengaktifkan CORS agar request dari VueJS bisa diterima oleh API CI4.

Buka file **app/Config/Filters.php** pada project CI4, tambahkan CORS pada bagian `$globals` dan `$filters`:

```php
public array $globals = [
    'before' => [
        'cors',
        // 'csrf',  // dinonaktifkan agar tidak konflik dengan Axios
    ],
    'after' => [
        'cors',
    ],
];

public array $filters = [
    'cors' => [
        'before' => ['post', 'post/*'],
        'after'  => ['post', 'post/*'],
    ],
];
```

>  CSRF perlu dinonaktifkan karena Axios mengirim request tanpa CSRF token.

---

### 5. Menyiapkan Controller Post.php pada CI4

Pastikan **Post.php** pada CI4 sudah mendukung pembacaan **JSON body** dari Axios, karena Axios PUT/POST mengirim data dalam format JSON, bukan form-data.

Perubahan utama pada method `create()` dan `update()`:

```php
// Baca JSON body dari Axios
$json = $this->request->getJSON(true);

$data = [
    'judul'  => $json['judul']  ?? $this->request->getVar('judul'),
    'isi'    => $json['isi']    ?? $this->request->getVar('isi'),
    'status' => $json['status'] ?? $this->request->getVar('status') ?? 0,
];
```

>  Field `status` juga ditambahkan karena form VueJS mengirim data status artikel (Draft/Publish).

---

### 6. Membuat File index.html

Buat file **index.html** pada root folder `lab11_vuejs`. File ini berisi struktur tampilan menggunakan VueJS 3.

Fitur yang ada pada halaman ini:
- Tabel daftar artikel yang diambil dari REST API
- Tombol **Tambah Data** untuk menambah artikel baru
- Tombol **Edit** untuk mengubah artikel
- Tombol **Hapus** dengan konfirmasi sebelum menghapus
- Modal form untuk tambah dan ubah data
- Notifikasi sukses/error otomatis

```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Frontend VueJS - Daftar Artikel</title>
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
  <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
  <link rel="stylesheet" href="assets/css/style.css">
</head>
<body>
  <div id="app">
    <h1>Daftar Artikel</h1>
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Judul</th>
          <th>Status</th>
          <th>Aksi</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(row, index) in artikel" :key="row.id">
          <td>{{ row.id }}</td>
          <td>{{ row.judul }}</td>
          <td>{{ statusText(row.status) }}</td>
          <td>
            <a href="#" @click.prevent="edit(row)">Edit</a>
            <a href="#" @click.prevent="hapus(index, row)">Hapus</a>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
  <script src="assets/js/app.js"></script>
</body>
</html>
```

<img width="1919" height="562" alt="image" src="https://github.com/user-attachments/assets/ff213db2-8301-4f51-8f16-a848ad9bb1ad" />


---

### 7. Membuat File app.js

Buat file **assets/js/app.js**. File ini berisi logika aplikasi VueJS termasuk semua operasi CRUD menggunakan Axios.

Tentukan URL API REST endpoint sesuai lokasi CI4:

```js
const apiUrl = 'http://localhost/lab11_ci/ci4/public'
```

**Fungsi-fungsi utama:**

**loadData()** — Mengambil semua artikel dari API (GET):
```js
loadData() {
    axios.get(apiUrl + '/post')
        .then(response => {
            this.artikel = response.data.artikel
        })
        .catch(error => console.log(error))
}
```

**tambah()** — Membuka form kosong untuk tambah data baru:
```js
tambah() {
    this.showForm  = true
    this.formTitle = 'Tambah Data'
    this.formData  = { id: null, judul: '', isi: '', status: 0 }
}
```

**edit(data)** — Membuka form dengan data yang dipilih untuk diubah:
```js
edit(data) {
    this.showForm  = true
    this.formTitle = 'Ubah Data'
    this.formData  = { id: data.id, judul: data.judul, isi: data.isi, status: data.status }
}
```

**saveData()** — Menyimpan data baru (POST) atau update data (PUT):
```js
saveData() {
    const promise = this.formData.id
        ? axios.put(apiUrl + '/post/' + this.formData.id, this.formData)
        : axios.post(apiUrl + '/post', this.formData)

    promise.then(() => {
        this.loadData()
        this.showForm = false
    })
}
```

**konfirmasiHapus()** — Menghapus artikel berdasarkan ID (DELETE):
```js
konfirmasiHapus() {
    axios.delete(apiUrl + '/post/' + this.hapusData.id)
        .then(() => {
            this.artikel.splice(this.hapusData.index, 1)
        })
}
```

<img width="1919" height="562" alt="image" src="https://github.com/user-attachments/assets/ff213db2-8301-4f51-8f16-a848ad9bb1ad" />

---

### 8. Menampilkan Data (GET)

Saat halaman pertama kali dibuka, fungsi `loadData()` dipanggil secara otomatis melalui `mounted()`. Data artikel diambil dari endpoint `GET /post` dan ditampilkan dalam bentuk tabel.

```js
mounted() {
    this.loadData()
}
```

<img width="1919" height="562" alt="image" src="https://github.com/user-attachments/assets/ff213db2-8301-4f51-8f16-a848ad9bb1ad" />


---

### 9. Form Tambah Data (POST)

Klik tombol **+ Tambah Data** untuk membuka modal form. Isi judul, isi artikel, dan pilih status (Draft/Publish), kemudian klik **Simpan**.

Data dikirim ke API menggunakan `axios.post()` dengan format JSON.


<img width="1565" height="847" alt="image" src="https://github.com/user-attachments/assets/3956217a-dffc-4da9-9fa0-4acc917f45a0" />

<img width="1496" height="740" alt="image" src="https://github.com/user-attachments/assets/94be43c3-98fb-45f6-979c-4d1632fe8add" />

---

### 10. Form Ubah Data (PUT)

Klik tombol **Edit** pada baris artikel yang ingin diubah. Form akan terbuka dan terisi otomatis dengan data artikel tersebut.

Setelah diubah dan klik **Simpan**, data dikirim ke API menggunakan `axios.put()`.


<img width="1623" height="982" alt="image" src="https://github.com/user-attachments/assets/e1146159-5075-40dc-9f0a-76a95a66c96a" />

<img width="1478" height="804" alt="image" src="https://github.com/user-attachments/assets/2b1204fb-b129-46b9-b10c-a18ac7739f45" />

---

### 11. Hapus Data (DELETE)

Klik tombol **Hapus** pada baris artikel yang ingin dihapus. Akan muncul modal konfirmasi yang menampilkan nama artikel sebelum dihapus.

Jika dikonfirmasi, data dihapus melalui `axios.delete()` dan baris langsung hilang dari tabel tanpa perlu reload halaman.

<img width="1512" height="740" alt="Cuplikan layar 2026-05-29 160931" src="https://github.com/user-attachments/assets/965c3ac1-b49c-489a-b609-4618b74f6f99" />

<img width="1534" height="639" alt="Cuplikan layar 2026-05-29 161102" src="https://github.com/user-attachments/assets/ac64a46e-74f5-4e60-ae91-b06fa18a0bca" />


---

### 12. Hasil Akhir

Tampilan akhir aplikasi frontend VueJS yang terhubung ke REST API CI4:

<img width="1919" height="562" alt="image" src="https://github.com/user-attachments/assets/ff213db2-8301-4f51-8f16-a848ad9bb1ad" />


**Fitur yang berhasil diimplementasikan:**
-  Menampilkan daftar artikel dari REST API (GET)
-  Tambah artikel baru melalui form modal (POST)
-  Ubah artikel yang sudah ada (PUT)
-  Hapus artikel dengan konfirmasi (DELETE)
-  Badge status warna berbeda (Publish = hijau, Draft = kuning)
-  Notifikasi sukses/error otomatis
-  Modal konfirmasi sebelum menghapus
-  Loading spinner saat data sedang dimuat

---

## Pertanyaan dan Tugas

Selesaikan programnya sesuai langkah-langkah yang ada. Improvisasi yang ditambahkan:

1. **Notifikasi otomatis** — muncul saat berhasil/gagal operasi CRUD dan hilang otomatis setelah 3 detik
2. **Modal konfirmasi hapus** — menampilkan nama artikel sebelum dihapus agar tidak salah hapus
3. **Badge status berwarna** — Publish (hijau) dan Draft (kuning) untuk membedakan status secara visual
4. **Loading spinner** — tampil saat data sedang dimuat dari API
5. **Tombol disabled saat proses** — tombol Simpan nonaktif saat sedang mengirim data ke API
6. **Empty state** — pesan khusus saat belum ada artikel
7. **Desain responsif** — tampilan menyesuaikan ukuran layar


# Lab12Web_VueJS - Praktikum 12: VueJS Komponen dan Routing (SPA)

---

## Apa itu Vue Components dan Vue Router?

**Vue Components** adalah elemen UI modular yang bisa digunakan kembali (reusable). Kode dipecah menjadi bagian-bagian terisolasi seperti `Home`, `Artikel`, dan `About` agar lebih bersih dan mudah dikelola.

**Vue Router** adalah library resmi VueJS untuk berpindah halaman di sisi klien tanpa reload browser — inilah yang disebut **Single Page Application (SPA)**.

---

## Langkah-langkah Praktikum

### 1. Tambah Library Vue Router

Tambahkan CDN Vue Router di `index.html` setelah library VueJS:

```html
<script src="https://unpkg.com/vue-router@4/dist/vue-router.global.js"></script>
```
<img width="745" height="773" alt="image" src="https://github.com/user-attachments/assets/0d0c8974-3440-4319-ad99-41c7db9a523e" />


---

### 2. Membuat Komponen Home.js

Buat file `assets/js/components/Home.js` sebagai halaman beranda:

```js
const Home = {
  template: `
    <div class="home-container">
      <h2>Selamat Datang di Portal Admin Artikel</h2>
      <p>Gunakan menu navigasi untuk mengelola data artikel.</p>
    </div>
  `
};
```

<img width="1469" height="727" alt="image" src="https://github.com/user-attachments/assets/e6677a9b-5cf1-4106-9c4d-67f317543a39" />

---

### 3. Membuat Komponen Artikel.js

Pindahkan seluruh logika CRUD dari `app.js` lama ke file baru `assets/js/components/Artikel.js`. Komponen ini berisi `template`, `data()`, dan semua `methods` (loadData, tambah, edit, hapus, saveData).

```js
const Artikel = {
  template: `...`,  // berisi tabel dan modal form
  data() { ... },
  mounted() { this.loadData(); },
  methods: { loadData, tambah, edit, hapus, saveData, statusText }
};
```

<img width="1399" height="732" alt="image" src="https://github.com/user-attachments/assets/4d758df8-6bad-4b41-b580-1114ed87d36f" />

---

### 4. Membuat Komponen About.js (Tugas Tambahan)

Buat file `assets/js/components/About.js` berisi profil singkat:

```js
const About = {
  template: `
    <div class="about-container">
      <h2>About Me</h2>
      <table>
        <tr><td>Nama</td><td>: Alipiani Dwi Putri</td></tr>
        <tr><td>NIM</td><td>: [NIM]</td></tr>
        <tr><td>Kelas</td><td>: [Kelas]</td></tr>
      </table>
    </div>
  `
};
```

<img width="1405" height="803" alt="image" src="https://github.com/user-attachments/assets/6578a95a-86dc-4eed-9f83-2585daed4ea3" />
---

### 5. Konfigurasi Vue Router di app.js

Edit `app.js` untuk mendaftarkan semua rute dan komponen:

```js
const { createApp } = Vue;
const { createRouter, createWebHashHistory } = VueRouter;

const apiUrl = 'http://localhost/lab11_ci/ci4/public';

const routes = [
  { path: '/',        component: Home    },
  { path: '/artikel', component: Artikel },
  { path: '/about',   component: About   },
];

const router = createRouter({
  history: createWebHashHistory(),
  routes
});

const app = createApp({});
app.use(router);
app.mount('#app');
```

<img width="571" height="522" alt="image" src="https://github.com/user-attachments/assets/1bb5a2f9-f3b0-4cbf-8b22-a612d6336289" />

---

### 6. Modifikasi index.html

Ganti isi `index.html` agar menggunakan `<router-link>` untuk navigasi dan `<router-view>` sebagai tempat render komponen:

```html
<nav class="nav-menu">
  <router-link to="/">🏠 Beranda</router-link> |
  <router-link to="/artikel">📋 Kelola Artikel</router-link> |
  <router-link to="/about">👤 About</router-link>
</nav>
<main>
  <router-view></router-view>
</main>

<!-- Urutan script: komponen dulu, baru app.js -->
<script src="assets/js/components/Home.js"></script>
<script src="assets/js/components/Artikel.js"></script>
<script src="assets/js/components/About.js"></script>
<script src="assets/js/app.js"></script>
```

<img width="1469" height="727" alt="image" src="https://github.com/user-attachments/assets/e6677a9b-5cf1-4106-9c4d-67f317543a39" />

---

### 7. Tambahan CSS untuk Navigasi

Tambahkan style berikut di `style.css`:

```css
.nav-menu a {
  text-decoration: none;
  color: #3152d6;
  font-weight: bold;
  padding: 6px 14px;
  border-radius: 6px;
}
/* Aktif otomatis saat route cocok */
.router-link-exact-active {
  background-color: #3152d6;
  color: #ffffff !important;
  border-radius: 6px;
}
```

---

## Hasil Akhir

### Halaman Beranda
<img width="1469" height="727" alt="image" src="https://github.com/user-attachments/assets/e6677a9b-5cf1-4106-9c4d-67f317543a39" />

### Halaman Kelola Artikel
<img width="1399" height="732" alt="image" src="https://github.com/user-attachments/assets/4d758df8-6bad-4b41-b580-1114ed87d36f" />

### Halaman About
<img width="1405" height="803" alt="image" src="https://github.com/user-attachments/assets/6578a95a-86dc-4eed-9f83-2585daed4ea3" />

### Perpindahan Halaman Tanpa Reload
<img width="1469" height="727" alt="image" src="https://github.com/user-attachments/assets/e6677a9b-5cf1-4106-9c4d-67f317543a39" />


---

## Kesimpulan

Dengan Vue Router, aplikasi VueJS dapat berpindah halaman tanpa reload (`createWebHashHistory`) sehingga menjadi **Single Page Application (SPA)**. Setiap fitur dipisahkan ke dalam komponen tersendiri (`Home.js`, `Artikel.js`, `About.js`) sehingga kode lebih modular dan mudah dikelola.
