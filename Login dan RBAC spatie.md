# Modul Laravel 11: Integrasi Frontend Modern, Autentikasi, dan RBAC menggunakan spatie/laravel-permission

## Tujuan Pembelajaran
Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:
1. Mengintegrasikan frontend modern ke dalam proyek Laravel 11 menggunakan Laravel Breeze.
2. Mengimplementasikan autentikasi dalam proyek Laravel 11.
3. Menerapkan Role-Based Access Control (RBAC) menggunakan package `spatie/laravel-permission`.
4. Menguji implementasi RBAC menggunakan fitur testing bawaan Laravel.

## Prasyarat
- Pemahaman dasar tentang PHP dan Laravel.
- Pengetahuan tentang HTML, CSS, dan JavaScript.
- Lingkungan pengembangan Laravel 11 yang sudah disiapkan.

## Langkah-langkah

### 1. Instalasi Laravel Breeze
- Buka terminal dan arahkan ke direktori proyek Laravel 11 Anda.
- Jalankan perintah berikut untuk menginstal Laravel Breeze:
  ```
  composer require laravel/breeze --dev
  ```
- Setelah instalasi selesai, jalankan perintah berikut untuk menginstal komponen frontend:
  ```
  php artisan breeze:install

  ```
- Pilih opsi untuk menginstal Livewire sebagai framework frontend.

### 2. Konfigurasi Database
- Buka file `.env` dan konfigurasikan koneksi database sesuai dengan lingkungan Anda.
- Jalankan migrasi database dengan perintah:
  ```
  php artisan migrate
  

  ```

### 3. Instalasi dan Konfigurasi spatie/laravel-permission
- Instal package `spatie/laravel-permission` dengan menjalankan perintah:
  ```
  composer require spatie/laravel-permission
  ```
- Publikasikan file konfigurasi dan migrasi dengan menjalankan perintah:
  ```
  php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
  ```
- Jalankan migrasi untuk membuat tabel yang diperlukan:
  ```
  php artisan migrate
  ```
- Tambahkan trait `HasRoles` pada model `User`:
  ```php
  use Spatie\Permission\Traits\HasRoles;

  class User extends Authenticatable
  {
      use HasRoles;
      // ...
  }
  ```

### 4. Menjalankan Aplikasi
- Jalankan server pengembangan Laravel dengan perintah:
  ```
  php artisan serve
  ```
- Buka browser dan akses aplikasi di `http://localhost:8000`.

### 5. Membuat Peran dan Izin
- Buat peran dan izin menggunakan perintah artisan:
  ```
  php artisan permission:create-role admin
  php artisan permission:create-role user

  php artisan permission:create-permission "view posts"
  php artisan permission:create-permission "create posts"
  ```
- Tetapkan izin ke peran:
  ```php
  $adminRole = Role::findByName('admin');
  $adminRole->givePermissionTo('view posts');
  $adminRole->givePermissionTo('create posts');

  $userRole = Role::findByName('user');
  $userRole->givePermissionTo('view posts');
  ```

### 6. Menerapkan RBAC pada Rute dan Middleware
- Definisikan middleware untuk memeriksa peran pengguna di `app/Http/Kernel.php`:
  ```php
  protected $routeMiddleware = [
      // ...
      'role' => \Spatie\Permission\Middlewares\RoleMiddleware::class,
      'permission' => \Spatie\Permission\Middlewares\PermissionMiddleware::class,
  ];
  ```
- Terapkan middleware pada rute yang sesuai:
  ```php
  Route::middleware(['auth', 'role:admin'])->group(function () {
      // Rute yang hanya dapat diakses oleh pengguna dengan peran 'admin'
      Route::get('/admin', [AdminController::class, 'index']);
  });

  Route::middleware(['auth', 'permission:create posts'])->group(function () {
      // Rute yang hanya dapat diakses oleh pengguna dengan izin 'create posts'
      Route::post('/posts', [PostController::class, 'store']);
  });
  ```

### 7. Pengujian RBAC
- Buat file pengujian untuk RBAC, misalnya `tests/Feature/RbacTest.php`:
  ```php
  <?php

  namespace Tests\Feature;

  use App\Models\User;
  use Illuminate\Foundation\Testing\RefreshDatabase;
  use Spatie\Permission\Models\Role;
  use Spatie\Permission\Models\Permission;
  use Tests\TestCase;

  class RbacTest extends TestCase
  {
      use RefreshDatabase;

      public function testAdminCanAccessAdminDashboard()
      {
          $adminUser = User::factory()->create();
          $adminUser->assignRole('admin');

          $response = $this->actingAs($adminUser)->get('/admin');

          $response->assertStatus(200);
      }

      public function testUserCannotAccessAdminDashboard()
      {
          $regularUser = User::factory()->create();
          $regularUser->assignRole('user');

          $response = $this->actingAs($regularUser)->get('/admin');

          $response->assertStatus(403);
      }

      public function testUserWithCreatePostsPermissionCanCreatePost()
      {
          $user = User::factory()->create();
          $user->givePermissionTo('create posts');

          $response = $this->actingAs($user)->post('/posts', [
              'title' => 'Test Post',
              'content' => 'This is a test post',
          ]);

          $response->assertStatus(201);
      }

      public function testUserWithoutCreatePostsPermissionCannotCreatePost()
      {
          $user = User::factory()->create();

          $response = $this->actingAs($user)->post('/posts', [
              'title' => 'Test Post',
              'content' => 'This is a test post',
          ]);

          $response->assertStatus(403);
      }
  }
  ```
- Jalankan pengujian dengan perintah:
  ```
  php artisan test
  ```

## Kesimpulan
Dalam modul ini, Anda telah mempelajari cara mengintegrasikan frontend modern menggunakan Laravel Breeze, mengimplementasikan autentikasi, menerapkan Role-Based Access Control (RBAC) menggunakan package `spatie/laravel-permission`, dan menguji implementasi RBAC menggunakan fitur testing bawaan Laravel.

Pengujian RBAC memastikan bahwa aturan akses yang ditentukan berfungsi dengan baik dan hanya pengguna dengan peran atau izin yang sesuai yang dapat mengakses rute atau melakukan tindakan tertentu.

Dengan menerapkan pengujian, Anda dapat memastikan integritas dan keamanan aplikasi Laravel Anda serta memastikan bahwa RBAC berfungsi sesuai dengan yang diharapkan.