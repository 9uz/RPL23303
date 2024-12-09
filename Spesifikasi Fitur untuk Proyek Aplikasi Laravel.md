1. Sistem Autentikasi Pengguna (Login, Registrasi, dan Verifikasi)
Prosentase Nilai: 15%
Fitur:
	 - Pengguna dapat mendaftar akun dengan menggunakan email dan password.
	 - Pengguna dapat login menggunakan email dan password yang sudah terdaftar.
	 - Reset password: Pengguna dapat mengatur ulang password melalui email verifikasi.
	 - Autentikasi dua faktor (opsional): Menambahkan lapisan keamanan dengan verifikasi melalui kode yang dikirimkan ke email atau aplikasi otentikasi.
	 - Verifikasi email: Pengguna yang baru mendaftar harus memverifikasi email mereka sebelum dapat menggunakan aplikasi.
	 - Penggunaan Laravel: Gunakan Laravel Breeze, Laravel Jetstream, atau Laravel Fortify untuk menangani autentikasi pengguna secara standar.

2. CRUD (Create, Read, Update, Delete) untuk Data Utama
Prosentase Nilai: 20%
Fitur:
	- Pengguna dapat menambahkan, melihat, memperbarui, dan menghapus data dari sistem (misalnya, data pengguna, produk, artikel, atau entitas lain sesuai dengan konteks proyek).
	- Halaman admin untuk mengelola data (opsional): Admin dapat melakukan CRUD terhadap entitas-entitas tertentu (misalnya, manajemen pengguna, manajemen konten).
	- Penggunaan Laravel: Implementasikan menggunakan Eloquent ORM, Controllers, dan Routes untuk mengelola operasi CRUD. Gunakan Form Request Validation untuk memastikan data valid.

3. API Endpoints untuk Integrasi dengan Frontend
Prosentase Nilai: 20%
Fitur:
	- RESTful API untuk mengakses data, dengan minimal tiga endpoint utama (misalnya, GET, POST, PUT/PATCH, DELETE) untuk mengelola entitas utama (misalnya, produk, pengguna, artikel).
	- Gunakan API Resources untuk merender data dalam format JSON yang terstruktur dan konsisten.
	- Endpoint Pagination untuk menampilkan daftar data (misalnya, produk atau artikel dalam jumlah besar).
	- Implementasikan fitur filtering dan sorting untuk menampilkan data sesuai kriteria yang diminta.
	- Autentikasi API: Penggunaan token berbasis JWT atau OAuth untuk mengamankan endpoint API.
	- Penggunaan Laravel: Gunakan RBAC untuk autentikasi API dan pengelolaan token. Gunakan API Resource untuk format output data.

4. Validasi Input dan Keamanan
Prosentase Nilai: 10%
Fitur:
	- Validasi input untuk formulir pengguna, memastikan bahwa semua data yang dikirim valid (misalnya, validasi email, password, nomor telepon).
	- Proteksi CSRF: Gunakan token CSRF untuk melindungi aplikasi dari serangan Cross-Site Request Forgery.
	- Keamanan Password: Gunakan bcrypt atau hash untuk meng-hash password dan menghindari penyimpanan password secara plaintext.
	- Proteksi XSS dan SQL Injection: Pastikan input yang diberikan oleh pengguna divalidasi dan disaring untuk menghindari serangan.
	- Penggunaan Laravel: Gunakan Form Request Validation, Laravel's built-in validation rules, dan fitur keamanan seperti middleware CSRF.

5. Sistem Manajemen Hak Akses (RBAC - Role-Based Access Control)
Prosentase Nilai: 15%
    Fitur:
   - Admin: Akses penuh ke semua fitur dan data.
   - Pengguna Biasa: Akses terbatas pada data pribadi mereka (misalnya, melihat profil dan mengedit data mereka sendiri).
   - Role Management: Admin dapat membuat, memperbarui, dan menghapus peran pengguna serta menetapkan hak akses sesuai dengan peran yang ditentukan.
   - Penggunaan Laravel: Gunakan Laravel Policies dan Gates untuk mengelola akses berdasarkan peran dan izin pengguna.

6. Sistem Pengelolaan Data (Soft Delete dan Archiving)
Prosentase Nilai: 10%
    Fitur:
   - Aplikasi harus menyediakan:  fitur yang diminta dalam deskripsi proyek atau dokumen persyaratan fungsional.
   - Soft Delete: Pengguna atau admin dapat menghapus data, tetapi data tersebut masih bisa dipulihkan (misalnya, menggunakan Laravel’s SoftDeletes).
   - Arsip Data: Pengguna dapat memindahkan data tertentu ke arsip tanpa benar-benar menghapusnya.
   - Penggunaan Laravel: Gunakan fitur SoftDeletes yang disediakan oleh Eloquent.

7. Seeding dan Data Factory untuk Pengujian
Prosentase Nilai: 5%
    Fitur:
    - Gunakan database seeding dan data factory untuk mengisi database dengan data dummy yang berguna selama pengembangan dan pengujian.
    - Seeding untuk beberapa entitas utama, seperti pengguna, produk, atau postingan.
    - Penggunaan Laravel: Gunakan DatabaseSeeder dan Factory untuk membuat data dummy. Pastikan seeding berfungsi dengan baik di database pengembangan.

8. Pengujian dan Penjaminan Kualitas
Prosentase Nilai: 10%
    Fitur:
    - Tulis pengujian unit untuk memastikan fungsi aplikasi bekerja sesuai harapan (misalnya, pengujian model, controller, atau validasi).
    - Pengujian fungsional untuk memverifikasi bahwa API dan fitur utama berjalan dengan baik.
    - Pengujian keamanan: Verifikasi bahwa aplikasi aman dari potensi ancaman umum, seperti SQL Injection dan XSS.
    - Penggunaan Laravel: Gunakan Laravel PHPUnit untuk menulis pengujian unit dan fitur. Gunakan Laravel Dusk untuk pengujian end-to-end berbasis browser.

9. Antarmuka Pengguna (UI/UX) yang Responsif
Prosentase Nilai: 5%
    Fitur:
    - Desain antarmuka pengguna yang responsif yang dapat menyesuaikan dengan berbagai ukuran layar (desktop, tablet, smartphone).
    - Gunakan framework CSS seperti Bootstrap atau Tailwind CSS untuk memastikan antarmuka yang modern dan responsif.
    - Fitur navigasi yang intuitif dan mudah digunakan (misalnya, menu dropdown, tombol aksi, dan breadcrumb).
    - Penggunaan Laravel: Implementasi dengan Blade Templating Engine dan Tailwind CSS atau Bootstrap untuk memastikan pengalaman pengguna yang baik di berbagai perangkat.

10. Deployment dan Pengelolaan Proyek- Fitur Laravel yang Lanjut 
Prosentase Nilai: 10%
    Fitur:
    - Dokumentasi: Apakah ada dokumentasi yang jelas dan lengkap tentang cara menjalankan dan menggunakan aplikasi? Ini bisa mencakup instruksi instalasi, cara konfigurasi, serta penjelasan struktur proyek dan fitur.
    - Presentasi: Apakah kelompok dapat menjelaskan dengan baik proyek mereka? Kemampuan untuk menjelaskan bagaimana mereka mengimplementasikan fitur dan solusi masalah teknis.
    - Distribusi pekerjaan proyek : bagaimana team melakukan distribusi pekerjaan
    - Proyek dapat dideploy ke platform hosting seperti Heroku, DigitalOcean, atau Laravel Forge.
    - Automasi deploy: Gunakan alat seperti GitHub Actions atau CI/CD pipeline untuk mendeploy aplikasi secara otomatis.
    - Proyek menggunakan version control (Git) untuk melacak perubahan dan kolaborasi tim.
    - Penggunaan Laravel: Siapkan file .env untuk konfigurasi dan pastikan aplikasi dapat berjalan dengan lancar di server.


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

