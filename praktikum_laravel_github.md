# Modul Praktikum: Manajemen Proyek Pengembangan Web Laravel dengan GitHub (Tim 3 Orang)

## Tujuan
Modul ini bertujuan untuk memberikan pemahaman dan pengalaman praktis dalam manajemen proyek pengembangan web menggunakan Laravel dan GitHub untuk tim yang terdiri dari 3 orang.

## Alat yang Dibutuhkan
1. Git
2. GitHub account
4. Laravel
5. Composer
6. Text editor atau IDE (contoh: Visual Studio Code)

## Langkah-langkah Praktikum

### 1. Persiapan Proyek dan Repository
   - Pastikan Konfigurasikan Git di Terminal Anda telah sesuai
   ```
   git config –global credential.helper manager-core
   git config --global user.name "your_username"
   git config --global user.email "your_email_address@example.com"
   ```
   - Untuk memeriksa konfigurasi, run:
   ```
     git config --global --list
   ```

#### Anggota 1 (Project Manager):
1. Buat repository baru di GitHub dengan nama "laravel-web-project".
   - Buka GitHub dan login ke akun Anda
   - Klik tombol "+" di pojok kanan atas, pilih "New repository"
   - Beri nama repository "laravel-web-project" (sesuaikan dengan proyek anda)
   - Pilih "Public" untuk visibilitas
   - Jangan Centang "Add a README file"
   - Klik "Create repository"

2. Clone repository ke lokal:
   - Buka terminal
   - Navigasi ke direktori kerja Anda
   - Jalankan perintah:
     ```
     git clone https://github.com/username/laravel-web-project.git
     ```
   - Ganti "username" dengan username GitHub Anda

3. Masuk ke direktori proyek:
   ```
   cd laravel-web-project
   ```

4. Inisialisasi proyek Laravel baru:
   - Pastikan Composer sudah terinstal
   - Jalankan perintah:
   ```
   composer create-project --prefer-dist laravel/laravel .
   ```
   - Tunggu hingga proses instalasi selesai

5. Push kode awal ke GitHub:
   ```
   git add .
   git commit -m "Initial Laravel project setup"
   git push origin main
   ```

6. Buat branch development:
   ```
   git checkout -b development
   git push origin development
   ```
   
7. Tambahkan anggota tim ke repository GitHub:
   - Buka halaman repository di GitHub
   - Klik "Settings" > "Manage access"
   - Klik "Invite a collaborator"
   - Masukkan username atau email anggota tim
   - Pilih role yang sesuai (biasanya "Write")
	

#### Anggota 2 dan 3:
1. Clone repository:
   - Buka terminal
   - Navigasi ke direktori kerja Anda
   - Jalankan perintah:
     ```
     git clone https://github.com/username/laravel-web-project.git
     ```
   - Ganti "username" dengan username GitHub Project Manager

2. Masuk ke direktori proyek:
   ```
   cd laravel-web-project
   ```

3. Checkout ke branch development:
   ```
   git checkout development
   ```

4. Instal dependensi proyek:
   ```
   composer install
   ```

5. Salin file .env.example menjadi .env: 
  linux
   ```
   cp .env.example .env
   ```
    windows
   ```
   copy .env.example .env
   ```

7. Generate application key:
   ```
   php artisan key:generate
   ```


### 2. Pembagian Tugas

- Anggota 1 (Project Manager): Bertanggung jawab atas manajemen proyek, code review, dan integrasi.
- Anggota 2 (Frontend Developer): Fokus pada pengembangan tampilan dan interaksi pengguna.
- Anggota 3 (Backend Developer): Fokus pada pengembangan logika bisnis dan database.

### 3. Workflow Pengembangan

#### Untuk setiap fitur baru, ikuti langkah-langkah berikut:

1. Buat branch baru dari development:
   ```
   git checkout development
   git pull origin development
   git checkout -b feature/nama-fitur
   ```

2. Kerjakan fitur pada branch tersebut.
   - Buka proyek di text editor atau IDE Anda
   - Lakukan perubahan sesuai dengan fitur yang sedang dikembangkan
   - Pastikan untuk mengikuti standar penulisan kode Laravel

3. Commit perubahan secara berkala:
   ```
   git add .
   git commit -m "Deskripsi perubahan"
   ```
   - Contoh commit message yang baik:
     "Add user registration form and validation"

4. Push branch ke GitHub:
   ```
   git push origin feature/nama-fitur
   ```

5. Buat Pull Request dari branch feature ke development di GitHub.
   - Buka repository di GitHub
   - Klik tombol "Pull requests"
   - Klik "New pull request"
   - Pilih branch feature Anda sebagai "compare" dan development sebagai "base"
   - Isi judul dan deskripsi pull request dengan detail
   - Assign reviewer (biasanya Project Manager)
   - Klik "Create pull request"

6. Project Manager melakukan code review.
   - Project Manager akan mereview kode
   - Jika ada komentar atau permintaan perubahan, lakukan perubahan di branch feature Anda
   - Commit dan push perubahan tersebut
   - Pull request akan diperbarui secara otomatis

7. Setelah disetujui, merge Pull Request ke branch development.
   - Setelah review selesai dan disetujui, Project Manager akan merge pull request
   - Branch feature akan digabungkan ke development


### 4. Integrasi dan Deployment

1. Secara berkala, Project Manager akan merge branch development ke main:
   ```
   git checkout main
   git merge development
   git push origin main
   ```

2. Lakukan deployment dari branch main ke server produksi.
   - Siapkan server produksi (misalnya menggunakan DigitalOcean, AWS, atau Heroku)
   - Konfigurasi server web (Nginx atau Apache) dan PHP
   - Set up database production
   - Clone repository di server:
     ```
     git clone https://github.com/username/laravel-web-project.git
     ```
   - Checkout ke branch main:
     ```
     git checkout main
     ```
   - Instal dependensi:
     ```
     composer install --no-dev
     ```
   - Salin dan konfigurasi file .env untuk production
   - Generate application key:
     ```
     php artisan key:generate
     ```
   - Jalankan migrasi database:
     ```
     php artisan migrate
     ```
   - Optimalkan Laravel untuk production:
     ```
     php artisan config:cache
     php artisan route:cache
     php artisan view:cache
     ```


### 5. Manajemen Proyek dengan GitHub Projects

1. Buat GitHub Project board:
   - Di repository GitHub, klik tab "Projects"
   - Klik "New project"
   - Pilih template "Basic kanban"
   - Beri nama proyek dan klik "Create project"

2. Konfigurasi kolom:
   - Atur kolom: "To Do", "In Progress", "Review", "Done"

3. Buat Issues untuk setiap tugas:
   - Di tab "Issues", klik "New issue"
   - Beri judul dan deskripsi tugas
   - Assign ke anggota tim yang bertanggung jawab
   - Tambahkan label yang sesuai (e.g., "frontend", "backend", "bug")
   - Klik "Submit new issue"

4. Hubungkan Pull Requests dengan Issues:
   - Saat membuat pull request, tambahkan "Closes #X" di deskripsi, di mana X adalah nomor issue
   - Ini akan otomatis menutup issue saat pull request di-merge

5. Update Project Board secara rutin:
   - Pindahkan kartu antar kolom sesuai dengan progress
   - Gunakan fitur automasi untuk memindahkan kartu secara otomatis berdasarkan status pull request


## Tugas Praktikum

1. Anggota 1 (Project Manager):
   - Buat struktur dasar proyek Laravel
     - Atur routing di `routes/web.php`
     - Buat controller dasar di `app/Http/Controllers`
   - Atur GitHub repository dan branch
     - Pastikan branch main dan development sudah ada
     - Atur branch protection rules di GitHub
   - Buat GitHub Project board

2. Anggota 2 (Frontend Developer):
   - Buat halaman utama (home page)
	- Buat view di `resources/views`
     	- Implementasikan layout dasar dengan header, footer, dan area konten utama
   - Implementasi template Laravel yang responsive
	- Gunakan framework CSS seperti Bootstrap atau Tailwind
        - Buat partial views untuk komponen yang dapat digunakan kembali

3. Anggota 3 (Backend Developer):
   - Buat migrasi dan model untuk fitur Utama
     - Minimal 3 model (misalnya User, Post, Comment)
     - Buat relasi antar model


Setiap anggota harus mengikuti workflow yang telah ditentukan dan berkolaborasi menggunakan GitHub.

## Evaluasi
Evaluasi akan dilakukan berdasarkan:
1. Kualitas kode dan implementasi fitur:
   - Kepatuhan terhadap standar penulisan kode Laravel
   - Implementasi fitur yang berfungsi dan bebas bug
2. Penggunaan Git dan GitHub yang efektif:
   - Commit yang teratur dan deskriptif
   - Branch yang terorganisir
   - Pull request yang jelas dan informatif
3. Kolaborasi tim dan komunikasi:
   - Partisipasi aktif dalam code review
   - Respons yang tepat waktu terhadap komentar dan permintaan perubahan
4. Penyelesaian tugas sesuai peran masing-masing:
   - Kualitas dan kelengkapan deliverable untuk setiap peran
   - Kontribusi yang seimbang dari setiap anggota tim

Setiap kriteria akan dinilai pada skala 1-5, dengan 5 sebagai nilai tertinggi. Nilai akhir akan dihitung berdasarkan rata-rata dari keempat kriteria tersebut.

