# Modul Praktikum Web Lanjutan: Routing Kompleks dan MVC Lanjutan

## Capaian Pembelajaran
[Bagian ini tetap sama]

## Durasi
4 jam

## Prasyarat
- Pemahaman dasar tentang HTML, CSS, dan JavaScript
- Pengetahuan dasar tentang konsep MVC dan routing dalam pengembangan web
- Familiar dengan penggunaan framework Laravel (versi 8.x atau lebih baru)
- Komputer dengan sistem operasi Windows, macOS, atau Linux

## Bahan dan Alat yang Digunakan
1. Software:
   - PHP (versi 7.4 atau lebih baru)
   - Composer (versi terbaru)
   - Laravel (versi 8.x atau lebih baru)
   - MySQL (versi 5.7 atau lebih baru) atau MariaDB (versi 10.2 atau lebih baru)
   - Text editor atau IDE (Visual Studio Code, PhpStorm, atau sejenisnya)
   - Web browser modern (Chrome, Firefox, atau Edge)

2. Hardware:
   - Komputer dengan minimal 4GB RAM
   - Koneksi internet yang stabil

3. Akun GitHub (opsional, untuk version control)

## Persiapan Sebelum Praktikum
1. Pastikan semua software yang diperlukan sudah terinstal di komputer Anda.
2. Buat folder baru untuk proyek praktikum ini, misalnya `web-lanjutan-praktikum`.
3. Buka terminal atau command prompt, navigasi ke folder proyek.
4. Jalankan perintah berikut untuk membuat proyek Laravel baru:
   ```
   composer create-project laravel/laravel task-manager
   ```
5. Setelah instalasi selesai, masuk ke direktori proyek:
   ```
   cd task-manager
   ```

## Outline Materi
[Bagian ini tetap sama]

## Rincian Materi dan Instruksi

### 1. Pengenalan Routing Kompleks (30 menit)

Instruksi:
1. Buka file `routes/web.php` di proyek Laravel Anda.
2. Tambahkan route statis untuk halaman beranda:
   ```php
   Route::get('/', function () {
       return view('welcome');
   });
   ```
3. Buat route dinamis dengan parameter untuk menampilkan profil pengguna:
   ```php
   Route::get('/user/{id}', function ($id) {
       return "Profil pengguna dengan ID: " . $id;
   });
   ```
4. Implementasikan grup routing untuk fitur admin:
   ```php
   Route::prefix('admin')->group(function () {
       Route::get('/users', function () {
           return "Daftar pengguna";
       });
       Route::get('/posts', function () {
           return "Daftar post";
       });
   });
   ```
5. Buat middleware sederhana untuk memeriksa otentikasi pengguna:
   ```
   php artisan make:middleware CheckAuth
   ```
   Buka file `app/Http/Middleware/CheckAuth.php` dan tambahkan logika:
   ```php
   public function handle($request, Closure $next)
   {
       if (!auth()->check()) {
           return redirect('login');
       }
       return $next($request);
   }
   ```
   Daftarkan middleware di `app/Http/Kernel.php` dan gunakan pada route:
   ```php
   Route::middleware(['check.auth'])->group(function () {
       // Protected routes here
   });
   ```

### 2. Implementasi MVC Lanjutan (45 menit)

Instruksi:
1. Buat model Task:
   ```
   php artisan make:model Task -m
   ```
   Buka file migrasi yang baru dibuat di `database/migrations` dan definisikan skema:
   ```php
   public function up()
   {
       Schema::create('tasks', function (Blueprint $table) {
           $table->id();
           $table->string('title');
           $table->text('description')->nullable();
           $table->enum('status', ['pending', 'in_progress', 'completed']);
           $table->date('due_date');
           $table->foreignId('user_id')->constrained();
           $table->timestamps();
       });
   }
   ```

2. Buka `app/Models/Task.php` dan definisikan relasi dengan User:
   ```php
   public function user()
   {
       return $this->belongsTo(User::class);
   }
   ```

3. Tambahkan query scope di model Task:
   ```php
   public function scopeStatus($query, $status)
   {
       return $query->where('status', $status);
   }
   ```

4. Buat TaskController:
   ```
   php artisan make:controller TaskController --resource
   ```

5. Implementasikan metode di TaskController. Contoh untuk metode index:
   ```php
   public function index()
   {
       $tasks = Task::with('user')->paginate(10);
       return view('tasks.index', compact('tasks'));
   }
   ```

6. Buat views untuk Task. Buat file `resources/views/tasks/index.blade.php`:
   ```html
   @extends('layouts.app')
   
   @section('content')
       <h1>Daftar Tugas</h1>
       @foreach($tasks as $task)
           <div>
               <h2>{{ $task->title }}</h2>
               <p>Status: {{ $task->status }}</p>
               <p>Due Date: {{ $task->due_date }}</p>
           </div>
       @endforeach
   @endsection
   ```

### 3. Pembuatan Proyek: Aplikasi Manajemen Tugas (2 jam 30 menit)

[Instruksi untuk bagian ini tetap sama, dengan penambahan contoh kode spesifik untuk Laravel]

### 4. Pengujian dan Evaluasi (15 menit)

Instruksi:
1. Jalankan server development Laravel:
   ```
   php artisan serve
   ```
2. Buka browser dan akses `http://localhost:8000`
3. Uji setiap fungsi CRUD yang telah dibuat
4. Pastikan routing berfungsi dengan benar, coba akses route dengan parameter dan route grup
5. Verifikasi bahwa pola MVC diimplementasikan dengan benar, periksa interaksi antara Model, View, dan Controller

## Tugas
[Bagian ini tetap sama]

## Referensi
- [Dokumentasi Resmi Laravel](https://laravel.com/docs)
- [Laracasts - Laravel From Scratch](https://laracasts.com/series/laravel-8-from-scratch)
- "Laravel Up & Running" oleh Matt Stauffer
- "Advanced Web Application Architecture" oleh Matthias Noback

## Penilaian
[Bagian ini tetap sama]

