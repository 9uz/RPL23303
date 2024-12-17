1. Sistem Autentikasi Pengguna (Login, Registrasi, dan Verifikasi)
Prosentase Nilai: 15%
Fitur:
	1. Pengguna dapat mendaftar akun dengan menggunakan email dan password.
  	2. Pengguna dapat login menggunakan email dan password yang sudah terdaftar.
   	3. Reset password: Pengguna dapat mengatur ulang password melalui email verifikasi.
   	4.  Autentikasi dua faktor (opsional): Menambahkan lapisan keamanan dengan verifikasi melalui kode yang dikirimkan ke email atau aplikasi otentikasi.
   	5.  Verifikasi email: Pengguna yang baru mendaftar harus memverifikasi email mereka sebelum dapat menggunakan aplikasi.
   	6.  Penggunaan Laravel: Gunakan Laravel Breeze, Laravel Jetstream, atau Laravel Fortify untuk menangani autentikasi pengguna secara standar.

2. CRUD (Create, Read, Update, Delete) untuk Data Utama
Prosentase Nilai: 20%
Fitur:
	1. Pengguna dapat menambahkan, melihat, memperbarui, dan menghapus data dari sistem (misalnya, data pengguna, produk, artikel, atau entitas lain sesuai dengan konteks proyek).
 	2. Halaman admin untuk mengelola data (opsional): Admin dapat melakukan CRUD terhadap entitas-entitas tertentu (misalnya, manajemen pengguna, manajemen konten).
 	3. Penggunaan Laravel: Implementasikan menggunakan Eloquent ORM, Controllers, dan Routes untuk mengelola operasi CRUD. Gunakan Form Request Validation untuk memastikan data valid.

3. API Endpoints untuk Integrasi dengan Frontend
Prosentase Nilai: 20%
Fitur:
	1. RESTful API untuk mengakses data, dengan minimal tiga endpoint utama (misalnya, GET, POST, PUT/PATCH, DELETE) untuk mengelola entitas utama (misalnya, produk, pengguna, artikel).
 	2. Gunakan API Resources untuk merender data dalam format JSON yang terstruktur dan konsisten.
 	3. Endpoint Pagination untuk menampilkan daftar data (misalnya, produk atau artikel dalam jumlah besar).
 	4. Implementasikan fitur filtering dan sorting untuk menampilkan data sesuai kriteria yang diminta.
 	5. Autentikasi API: Penggunaan token berbasis JWT atau OAuth untuk mengamankan endpoint API.
 	6. Penggunaan Laravel: Gunakan RBAC untuk autentikasi API dan pengelolaan token. Gunakan API Resource untuk format output data.

4. Validasi Input dan Keamanan
Prosentase Nilai: 10%
Fitur:
	1. Validasi input untuk formulir pengguna, memastikan bahwa semua data yang dikirim valid (misalnya, validasi email, password, nomor telepon).
 	2. Proteksi CSRF: Gunakan token CSRF untuk melindungi aplikasi dari serangan Cross-Site Request Forgery.
 	3. Keamanan Password: Gunakan bcrypt atau hash untuk meng-hash password dan menghindari penyimpanan password secara plaintext.
 	4. Proteksi XSS dan SQL Injection: Pastikan input yang diberikan oleh pengguna divalidasi dan disaring untuk menghindari serangan.
 	5. Penggunaan Laravel: Gunakan Form Request Validation, Laravel's built-in validation rules, dan fitur keamanan seperti middleware CSRF.

5. Sistem Manajemen Hak Akses (RBAC - Role-Based Access Control)
Prosentase Nilai: 15%
    Fitur:
   1. Admin: Akses penuh ke semua fitur dan data.
   2. Pengguna Biasa: Akses terbatas pada data pribadi mereka (misalnya, melihat profil dan mengedit data mereka sendiri).
   3. Role Management: Admin dapat membuat, memperbarui, dan menghapus peran pengguna serta menetapkan hak akses sesuai dengan peran yang ditentukan.
   4. Penggunaan Laravel: Gunakan Laravel Policies dan Gates untuk mengelola akses berdasarkan peran dan izin pengguna.

6. Sistem Pengelolaan Data (Soft Delete dan Archiving)
Prosentase Nilai: 10%
    Fitur:
   1. Aplikasi harus menyediakan:  fitur yang diminta dalam deskripsi proyek atau dokumen persyaratan fungsional.
   2. Soft Delete: Pengguna atau admin dapat menghapus data, tetapi data tersebut masih bisa dipulihkan (misalnya, menggunakan Laravel’s SoftDeletes).
   3. Arsip Data: Pengguna dapat memindahkan data tertentu ke arsip tanpa benar-benar menghapusnya.
   4. Penggunaan Laravel: Gunakan fitur SoftDeletes yang disediakan oleh Eloquent.

7. Seeding dan Data Factory untuk Pengujian
Prosentase Nilai: 5%
    Fitur:
   1. Gunakan database seeding dan data factory untuk mengisi database dengan data dummy yang berguna selama pengembangan dan pengujian.
   2. Seeding untuk beberapa entitas utama, seperti pengguna, produk, atau postingan.
   3. Penggunaan Laravel: Gunakan DatabaseSeeder dan Factory untuk membuat data dummy. Pastikan seeding berfungsi dengan baik di database pengembangan.

8. Pengujian dan Penjaminan Kualitas
Prosentase Nilai: 10%
    Fitur:
   1. Tulis pengujian unit untuk memastikan fungsi aplikasi bekerja sesuai harapan (misalnya, pengujian model, controller, atau validasi).
   2. Pengujian fungsional untuk memverifikasi bahwa API dan fitur utama berjalan dengan baik.
   3. Pengujian keamanan: Verifikasi bahwa aplikasi aman dari potensi ancaman umum, seperti SQL Injection dan XSS.
   4. Penggunaan Laravel: Gunakan Laravel PHPUnit untuk menulis pengujian unit dan fitur. Gunakan Laravel Dusk untuk pengujian end-to-end berbasis browser.

9. Antarmuka Pengguna (UI/UX) yang Responsif
Prosentase Nilai: 5%
    Fitur:
   1. Desain antarmuka pengguna yang responsif yang dapat menyesuaikan dengan berbagai ukuran layar (desktop, tablet, smartphone).
   2. Gunakan framework CSS seperti Bootstrap atau Tailwind CSS untuk memastikan antarmuka yang modern dan responsif.
   3. Fitur navigasi yang intuitif dan mudah digunakan (misalnya, menu dropdown, tombol aksi, dan breadcrumb).
   4. Penggunaan Laravel: Implementasi dengan Blade Templating Engine dan Tailwind CSS atau Bootstrap untuk memastikan pengalaman pengguna yang baik di berbagai perangkat.

10. Deployment dan Pengelolaan Proyek- Fitur Laravel yang Lanjut 
Prosentase Nilai: 10%
    Fitur:
    1. Dokumentasi: Apakah ada dokumentasi yang jelas dan lengkap tentang cara menjalankan dan menggunakan aplikasi? Ini bisa mencakup instruksi instalasi, cara konfigurasi, serta penjelasan struktur proyek dan fitur.
    2. Presentasi: Apakah kelompok dapat menjelaskan dengan baik proyek mereka? Kemampuan untuk menjelaskan bagaimana mereka mengimplementasikan fitur dan solusi masalah teknis.
    3. Distribusi pekerjaan proyek : bagaimana team melakukan distribusi pekerjaan
    4. Proyek dapat dideploy ke platform hosting seperti Heroku, DigitalOcean, atau Laravel Forge.
    5. Automasi deploy: Gunakan alat seperti GitHub Actions atau CI/CD pipeline untuk mendeploy aplikasi secara otomatis.
    6. Proyek menggunakan version control (Git) untuk melacak perubahan dan kolaborasi tim.
    7. Penggunaan Laravel: Siapkan file .env untuk konfigurasi dan pastikan aplikasi dapat berjalan dengan lancar di server.


Fitur	Prosentase Nilai
1. Sistem Autentikasi Pengguna (Login, Registrasi, dan Verifikasi)	15%
2. CRUD (Create, Read, Update, Delete) untuk Data Utama	20%
4. API Endpoints untuk Integrasi dengan Frontend	20%
5. Validasi Input dan Keamanan	10%
6. Sistem Manajemen Hak Akses (RBAC - Role-Based Access Control)	15%
7. Sistem Pengelolaan Data (Soft Delete dan Archiving)	10%
9. Seeding dan Data Factory untuk Pengujian	5%
10. Pengujian dan Penjaminan Kualitas	10%
11. Antarmuka Pengguna (UI/UX) yang Responsif	5%
12. Deployment dan Pengelolaan Proyek - Fitur Laravel yang Lanjut 10%

