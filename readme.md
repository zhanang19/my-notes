# My Notes
Penulisan catatan ini dibuat sebagai pengingat bagi saya dan juga untuk berbagi pengetahuan dengan teman-teman saya. Silahkan buat Issue atau PR jika dirasa ada hal-hal yang kurang atau harus diperbaiki. Terima kasih.

# Table of Contents
1. [PHP Guidelines](#1-php-guidelines)
2. [CodeIgniter Guidelines](#2-codeigniter-guidelines)
3. [Laravel Guidelines](#3-laravel-guidelines)
4. [GIT Guidelines](#4-git-guidelines)

## 1. PHP Guidelines
- Indentasi menggunakan 4 spasi, bukan tab
- Penamaan Class harus menggunakan format `StudlyCaps`
- Penamaan Method harus menggunakan format `CamelCase`
- Penamaan Constant harus menggunakan format `UPPER_CASE`
- Penamaan Variable atau Property harus menggunakan format `camelCase`
- Referensi:
    1. [PSR-0: Autoloading](https://php-fig.org/psr/psr-0)
    2. [PSR-1: Basic Coding Standard](https://php-fig.org/psr/psr-1)
    3. [PSR-2: Coding Style Guide](https://php-fig.org/psr/psr-2)
    4. [PSR-4: Autoloader](https://php-fig.org/psr/psr-4)

## 2. Codeigniter Guidelines
- Penamaan Method harus menggunakan format `snake_case`, hal ini untuk mempermudah default routing dari Codeigniter
- Untuk membuat url tetap bagus dilihat, atur konfigurasi *translate_uri_dashes* di file `application/config/routes.php` menjadi `true`.
    ```
    $route['translate_uri_dashes'] = TRUE;
    ```
- Gunakan kode dibawah untuk membuat *dynamic base url*
    ```
    $base_url = "http://".$_SERVER['HTTP_HOST'];
    $base_url .= str_replace(basename($_SERVER['SCRIPT_NAME']), "", $_SERVER['SCRIPT_NAME']);

    $config['base_url'] = $base_url;
    ```
- Tambahkan kode berikut kedalam file `.htaccess` untuk menghilangkan index.php dari url
    ```
    RewriteEngine on
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule ^(.*)$ index.php/$1 [L]
    ```
- Referensi:
    1. [Dokumentasi Codeigniter](https://codeigniter.com/user_guide/)

## 3. Laravel Guidelines
- Gunakan perintah `php artisan make:controller NamaController -r` untuk membuat [resource controller](https://laravel.com/docs/controllers#resource-controllers)
- Gunakan perintah `php artisan storage:link` untuk membuat [symbolic link](https://en.wikipedia.org/wiki/Symbolic_link) dari folder *storage/app/public* ke folder *public/storage*
- Gunakan perintah `php artisan migrate:fresh --force` saat mode *production*
- Gunakan perintah `php artisan key:generate` untuk menghasilkan app key untuk stabilitas keamanan data pengguna
- Gunakan perintah `php artisan config:clear` dan `php artisan view:clear` setelah melakukan deploy
- Gunakan perintah `php artisan route:cache` untuk optimasi routing dari Laravel.
    > Perintah ini hanya dapat digunakan jika tidak ada self function di dalam file *route*.

- Referensi:
    1. [Dokumentasi Laravel](https://laravel.com/docs)

## 4. GIT Guidelines
- Pakai [Github Desktop](https://desktop.github.com/) untuk mempermudah pekerjaan :)
- File yang seharusnya tidak disertakan ke dalam git:
    > Sertakan file atau direktori ini ke dalam list `.gitignore`
    - file `.env` atau file apapun yang berisi informasi sensitif
    - file `desktop.ini`
    - file `*.log`
    - direktori `vendor`, `bower_components`, `node_modules`, `dist` serta direktori lain yang berisi kumpulan paket
    - direktori `.vscode`, `.idea`
    - direktori yang berisi cache seperti `.tmp`, `temp`, `cache`
- Gunakan perintah `git add -f filename` dan `git commit -m "pesan commit"` untuk menyertakan file yang sudah ada dalam `.gitignore`

    