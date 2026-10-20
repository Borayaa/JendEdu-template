# Panduan Coder 2 (@username-2)

> **Tugas kamu**
> - Branch `feature/navbar-footer`: styling (CSS) bersama untuk navbar dan footer + logo. Ini PR **kedua**, dikerjakan setelah PR setup-template Coder 1 di-merge.
> - Halaman lain: `feature/contact`, `feature/posts` (3 artikel), `feature/news` (3 berita).
> - Kamu adalah **pemilik** blok navbar dan footer beserta CSS-nya. Kalau Reviewer minta perbaikan navbar/footer di halaman mana pun, **kamu** yang memperbaikinya.
> - Setiap branch = satu Pull Request (PR) yang di-review oleh Reviewer (@username-3).

**Sebelum mulai: selesaikan [01-persiapan-semua-anggota.md](01-persiapan-semua-anggota.md).** Pastikan Git terpasang, `user.name`/`user.email` terisi, kamu sudah mem-fork Borayaa/JendEdu menjadi https://github.com/username-2/JendEdu (`origin`), remote `upstream` (https://github.com/Borayaa/JendEdu.git) sudah ditambahkan (cek `git remote -v`), dan `C:\Proyek\JendEdu-template` serta `C:\Proyek\JendEdu` (clone dari fork kamu) sudah ada. Kamu **tidak** push langsung ke Borayaa/JendEdu.

> **⚠️ Jangan pernah `git push` ke `main`.** Hanya branch kerja (`feature/...`, `chore/...`) yang di-push, dan hanya ke `origin` (fork kamu). `main` hanya berubah lewat PR yang di-merge. Fork kamu di GitHub boleh tertinggal (`X commits behind`); itu tidak masalah, karena branch baru selalu dibuat dari `main` lokal yang sudah di-pull dari upstream. Jangan klik/jalankan apa pun yang mem-push ke main.

> **📌 Draft vs versi perbaikan**
>
> - File di **root** `C:\Proyek\JendEdu-template` adalah **draft**. Untuk PR yang ditugaskan ke kamu di bawah ini, draft itu **sengaja mengandung kesalahan** supaya Reviewer punya sesuatu untuk di-review.
> - PR kamu yang berisi draft dengan kesalahan: **`feature/navbar-footer` ("PR #4" di review.md)** dengan `css\style.css`, **`feature/contact` ("PR #5")** dengan `contact.html`, dan **`feature/news` ("PR #7")** dengan `berita-beasiswa-jendedu-2027.html` (dua berita lainnya, `berita-kelas-live-utbk-2027.html` dan `berita-kemitraan-sekolah.html`, tidak bermasalah).
> - Nomor PR (#4, #5, #7) mengikuti contoh di `review\review.md`; nomor sebenarnya di GitHub bisa berbeda. Kenali PR lewat **nama branch**.
> - Versi **yang sudah diperbaiki** ada di `C:\Proyek\JendEdu-template\review\codes\`.
> - **Urutan yang benar:** (1) salin **draft** dari root dan buat PR; (2) **tunggu** Reviewer memberi **Request changes**; (3) baru setelah itu salin file perbaikan dari `review\codes\`, commit, dan push.
> - **Jangan** menyalin dari `review\codes\` sebelum Reviewer berkomentar, dan **jangan pernah** menyalin folder `review\` ke proyek (itu bagian PR dokumentasi di akhir).
> - PR kamu yang lain (`feature/posts`) **tidak** punya kesalahan yang disengaja, jadi Reviewer langsung **Approve** (tetap dicek).

---

## Gambaran urutan kerja

| No | Branch | Kapan boleh mulai | Isi |
|----|--------|-------------------|-----|
| 1 | `feature/navbar-footer` | Setelah PR `chore/setup-template` (Coder 1) di-merge | folder `css`, `img\logo.png` |
| 2 | `feature/contact` | Setelah PR setup-template **dan** navbar-footer di-merge | `contact.html` |
| 3 | `feature/posts` | Sama | `artikel-*.html` + gambar artikel |
| 4 | `feature/news` | Sama | `berita-*.html` + gambar berita |

Branch 2-4 sebaiknya dikerjakan satu per satu.

## Aturan emas: dua aplikasi, dua fungsi

- **Git Bash** = semua perintah `git ...`.
- **Command Prompt (cmd)** = pindah folder, menyalin file, membuka website.
- **Browser (github.com)** = membuat PR dari fork kamu ke Borayaa/JendEdu.

Cara membuka:
- cmd: `Win + R`, ketik `cmd`, Enter.
- Git Bash: menu Start, ketik "Git Bash". Atau klik kanan di folder `C:\Proyek\JendEdu` lalu **Open Git Bash here**.

Di Git Bash, `C:\Proyek\JendEdu` ditulis `/c/Proyek/JendEdu`.

---

# BRANCH 1: `feature/navbar-footer`

Penjelasan: blok navbar (menu atas) dan footer (bagian bawah) isinya **sama** di setiap halaman. Styling-nya ada di folder `css` (terutama `css\style.css`). Kamu memasukkan CSS dan logo ini lebih dulu supaya halaman-halaman lain tampil benar.

### Langkah 1.1 - Siapkan branch (Git Bash)

Pastikan dulu PR Coder 1 (`chore/setup-template`) sudah di-merge. Lalu:

```bash
cd /c/Proyek/JendEdu
```

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git switch -c feature/navbar-footer
```

### Langkah 1.2 - Salin file (cmd)

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
xcopy ..\JendEdu-template\css css\ /E /I /Y
```

```cmd
copy ..\JendEdu-template\img\logo.png img\
```

Catatan: `css\style.css` di root adalah **draft** (sengaja mengandung kesalahan untuk PR #4). Salin apa adanya; jangan ambil dari `review\codes\` dulu.

Kalau `img\` belum ada (PR Coder 1 belum ter-pull), jalankan `git pull upstream main` di Git Bash dulu. Cek:

```cmd
dir css
```

```cmd
dir img\logo.png
```

### Langkah 1.3 - Commit dan push (Git Bash)

```bash
git status
```

```bash
git add css img/logo.png
```

```bash
git commit -m "Tambah CSS navbar-footer dan logo"
```

```bash
git push -u origin feature/navbar-footer
```

Branch terkirim ke **fork kamu**.

Pertama kali push akan muncul jendela login GitHub (Git Credential Manager); login lalu **Authorize**.

### Langkah 1.4 - Buat PR (Browser)

Buka fork kamu di browser: https://github.com/username-2/JendEdu. Klik tombol kuning **Compare & pull request** (muncul di bar "feature/navbar-footer had recent pushes"). Kalau tombol tidak muncul: tab **Pull requests** -> **New pull request** -> **compare across forks**.

Cek **empat dropdown** (ini penting):

- base repository: `Borayaa/JendEdu`
- base: `main`
- head repository: `username-2/JendEdu`
- compare: `feature/navbar-footer`

Isi judul dan deskripsi (di bawah), centang **Allow edits by maintainers**, lalu klik **Create pull request**. Setelah PR terbuat (halamannya di Borayaa/JendEdu), di panel kanan klik **Reviewers** dan pilih **@username-3**. Kalau tidak bisa memilih, tulis komentar `@username-3 mohon di-review` di PR.

Judul:

```
Tambah CSS navbar-footer dan logo
```

Deskripsi:

```
## Ringkasan
Menambahkan styling bersama (navbar, footer, dan gaya umum) beserta logo JendEdu.

## Perubahan
- Menambahkan folder `css` (bootstrap, style.css, font-awesome, flexslider, fancybox, animate, custom-fonts)
- Menambahkan `img/logo.png`

## Catatan
- Blok navbar dan footer sama di semua halaman; styling-nya dikelola di PR ini.
- PR ini harus di-merge sebelum halaman-halaman lain di-review.

## Cara mengecek
Belum ada halaman di PR ini. Cukup cek folder `css` dan `img/logo.png` ada. Tampilan lengkap terlihat setelah halaman pertama di-merge.
```

Setelah deskripsi terisi: centang **Allow edits by maintainers** -> **Create pull request** -> minta review **@username-3** (panel kanan **Reviewers**, atau mention `@username-3` di komentar). Kabari tim bahwa PR ini siap, karena PR halaman Coder 1 menunggu ini.

### Langkah 1.5 - Setelah Reviewer meminta perbaikan (Request changes), PR #4

Reviewer akan memeriksa folder `css` (terutama `css\style.css`) dan memberi status **Request changes** (PR #4) dengan komentar di baris tertentu. Itu normal dan memang direncanakan. Hanya `css\style.css` yang diganti; folder `css` lain dan `img\logo.png` tidak berubah. Lakukan urutan ini:

1. **Baca komentar** di GitHub: buka PR kamu di Borayaa/JendEdu, tab **Files changed** (atau **Conversation**). Komentar yang sama juga tertulis di `C:\Proyek\JendEdu-template\review\review.md` bagian **PR #4**, lengkap dengan nomor baris.

2. **Pastikan masih di branch `feature/navbar-footer`** (Git Bash):

```bash
cd /c/Proyek/JendEdu
```

```bash
git switch feature/navbar-footer
```

3. **Salin file versi perbaikan** (cmd):

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
copy /Y ..\JendEdu-template\review\codes\css\style.css css\
```

Output yang diharapkan: `1 file(s) copied.` (`/Y` berarti timpa file lama tanpa bertanya).

4. **Cek di browser** (cmd):

Buka salah satu halaman yang sudah ada di `main` (misalnya `start index.html` kalau sudah ter-pull), atau cukup pastikan `css\style.css` sudah berubah di `git status`. Navbar dan footer harus rapi.

```cmd
dir css\style.css
```

5. **Cek, add, commit, push** (Git Bash):

```bash
git status
```

```bash
git add css/style.css
```

```bash
git commit -m "Perbaiki sesuai review PR #4"
```

```bash
git push
```

Perintah ini mengirim ke branch yang sama di **fork kamu** (`origin`), tanpa `-u` dan tanpa PR baru; PR #4 otomatis ter-update. Jangan push ke `main`.

6. **Balas setiap komentar** di GitHub dengan: `Sudah diperbaiki`. Jangan klik "Resolve conversation" sendiri kalau tidak diminta.

7. **Tunggu** Reviewer meng-**Approve** dan me-merge PR, lalu lanjut ke Langkah 1.6.

> **Alternatif (opsional):** kamu boleh memperbaiki **manual** per komentar, bukan menyalin file. Hasil akhirnya **harus sama persis** dengan file di `review\codes\`. Cek di cmd:
>
> ```cmd
> fc ..\JendEdu-template\review\codes\css\style.css css\style.css
> ```
>
> Hasil yang benar: `FC: no differences encountered`.

### Langkah 1.6 - Setelah di-merge (Git Bash)

Setelah Reviewer me-merge PR, perbarui `main` lokal dari upstream (tanpa push ke main):

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git branch -d feature/navbar-footer
```

```bash
git push origin --delete feature/navbar-footer
```

Baris terakhir menghapus branch di fork kamu (opsional, tapi rapi). Hanya branch kerja yang pernah di-push; `main` tidak.

---

# BRANCH 2: `feature/contact`

### Langkah 2.1 - Siapkan branch (Git Bash)

```bash
cd /c/Proyek/JendEdu
```

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git switch -c feature/contact
```

### Langkah 2.2 - Salin file (cmd)

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
copy ..\JendEdu-template\contact.html .
```

```cmd
start contact.html
```

Ini **draft** (sengaja mengandung kesalahan untuk PR #5); jangan ambil dari `review\codes\` dulu.

Cek: peta Google Maps tampil (butuh internet), formulir kontak muncul, menu berfungsi.

### Langkah 2.3 - Commit dan push (Git Bash)

```bash
git status
```

```bash
git add contact.html
```

```bash
git commit -m "Tambah halaman Kontak (contact.html)"
```

```bash
git push -u origin feature/contact
```

Branch terkirim ke **fork kamu**.

### Langkah 2.4 - Buat PR (Browser)

Judul:

```
Tambah halaman Kontak (contact.html)
```

Deskripsi:

```
## Ringkasan
Menambahkan halaman kontak JendEdu dengan peta lokasi dan formulir.

## Isi halaman
- Google Maps embed
- Formulir kontak
- Alamat, email, dan nomor telepon
- Navbar dan footer

## Cara mengecek
1. `git fetch origin` lalu `git switch feature/contact`
2. Buka `contact.html` di browser (perlu internet untuk peta)
3. Cek peta tampil, formulir lengkap, dan tampilan responsif

## Catatan
Bergantung pada PR setup-template dan navbar-footer yang sudah di-merge.
```

Setelah deskripsi terisi: centang **Allow edits by maintainers** -> **Create pull request** -> minta review **@username-3** (panel kanan **Reviewers**, atau mention `@username-3` di komentar).

### Langkah 2.5 - Setelah Reviewer meminta perbaikan (Request changes), PR #5

Reviewer akan memeriksa `contact.html` dan memberi status **Request changes** (PR #5) dengan komentar di baris tertentu. Itu normal dan memang direncanakan. Lakukan urutan ini:

1. **Baca komentar** di GitHub: buka PR kamu di Borayaa/JendEdu, tab **Files changed** (atau **Conversation**). Komentar yang sama juga tertulis di `C:\Proyek\JendEdu-template\review\review.md` bagian **PR #5**, lengkap dengan nomor baris.

2. **Pastikan masih di branch `feature/contact`** (Git Bash):

```bash
cd /c/Proyek/JendEdu
```

```bash
git switch feature/contact
```

3. **Salin file versi perbaikan** (cmd):

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
copy /Y ..\JendEdu-template\review\codes\contact.html .
```

Output yang diharapkan: `1 file(s) copied.` (`/Y` berarti timpa file lama tanpa bertanya).

4. **Cek di browser** (cmd):

```cmd
start contact.html
```

5. **Cek, add, commit, push** (Git Bash):

```bash
git status
```

```bash
git add contact.html
```

```bash
git commit -m "Perbaiki sesuai review PR #5"
```

```bash
git push
```

Perintah ini mengirim ke branch yang sama di **fork kamu** (`origin`), tanpa `-u` dan tanpa PR baru; PR #5 otomatis ter-update. Jangan push ke `main`.

6. **Balas setiap komentar** di GitHub dengan: `Sudah diperbaiki`. Jangan klik "Resolve conversation" sendiri kalau tidak diminta.

7. **Tunggu** Reviewer meng-**Approve** dan me-merge PR, lalu lanjut ke Langkah 2.6.

> **Alternatif (opsional):** kamu boleh memperbaiki **manual** per komentar, bukan menyalin file. Hasil akhirnya **harus sama persis** dengan file di `review\codes\`. Cek di cmd:
>
> ```cmd
> fc ..\JendEdu-template\review\codes\contact.html contact.html
> ```
>
> Hasil yang benar: `FC: no differences encountered`.

### Langkah 2.6 - Setelah di-merge (Git Bash)

Setelah Reviewer me-merge PR, perbarui `main` lokal dari upstream (tanpa push ke main):

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git branch -d feature/contact
```

```bash
git push origin --delete feature/contact
```

Baris terakhir menghapus branch di fork kamu (opsional, tapi rapi). Hanya branch kerja yang pernah di-push; `main` tidak.

---

# BRANCH 3: `feature/posts`

Tiga artikel edukatif: `artikel-belajar-online-efektif-smp.html`, `artikel-strategi-persiapan-ujian-sma.html`, `artikel-tips-belajar-matematika-sd.html`, plus gambarnya `artikel-1.jpg`, `artikel-2.jpg`, `artikel-3.jpg`.

### Langkah 3.1 - Siapkan branch (Git Bash)

```bash
cd /c/Proyek/JendEdu
```

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git switch -c feature/posts
```

### Langkah 3.2 - Salin file (cmd)

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
copy ..\JendEdu-template\artikel-*.html .
```

Buat folder `img\blog` kalau belum ada (kalau muncul "A subdirectory or file img\blog already exists", itu aman, abaikan):

```cmd
mkdir img\blog
```

```cmd
copy ..\JendEdu-template\img\blog\artikel-*.jpg img\blog\
```

Cek tiga artikel di browser, satu per satu:

```cmd
start artikel-belajar-online-efektif-smp.html
```

```cmd
start artikel-strategi-persiapan-ujian-sma.html
```

```cmd
start artikel-tips-belajar-matematika-sd.html
```

Cek: gambar artikel tampil, sidebar "artikel terkait" muncul, tautan footer berfungsi.

### Langkah 3.3 - Commit dan push (Git Bash)

```bash
git status
```

Harus terlihat 3 file `artikel-*.html` dan 3 gambar `img/blog/artikel-*.jpg`.

```bash
git add artikel-belajar-online-efektif-smp.html artikel-strategi-persiapan-ujian-sma.html artikel-tips-belajar-matematika-sd.html img/blog/artikel-1.jpg img/blog/artikel-2.jpg img/blog/artikel-3.jpg
```

```bash
git commit -m "Tambah 3 halaman artikel edukatif"
```

```bash
git push -u origin feature/posts
```

Branch terkirim ke **fork kamu**.

### Langkah 3.4 - Buat PR (Browser)

Judul:

```
Tambah 3 halaman artikel edukatif
```

Deskripsi:

```
## Ringkasan
Menambahkan tiga artikel edukatif untuk blog JendEdu.

## Isi
- artikel-belajar-online-efektif-smp.html
- artikel-strategi-persiapan-ujian-sma.html
- artikel-tips-belajar-matematika-sd.html
- Gambar artikel di `img/blog/` (artikel-1.jpg sampai artikel-3.jpg)

## Cara mengecek
1. `git fetch origin` lalu `git switch feature/posts`
2. Buka ketiga file artikel di browser
3. Cek gambar tampil (ada teks alt), sidebar artikel terkait berfungsi, tautan footer benar, dan tampilan responsif

## Catatan
Bergantung pada PR setup-template dan navbar-footer yang sudah di-merge. Gambar berita dikerjakan di PR `feature/news`.
```

Setelah deskripsi terisi: centang **Allow edits by maintainers** -> **Create pull request** -> minta review **@username-3** (panel kanan **Reviewers**, atau mention `@username-3` di komentar).

### Langkah 3.5 - Setelah di-merge (Git Bash)

Setelah Reviewer me-merge PR, perbarui `main` lokal dari upstream (tanpa push ke main):

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git branch -d feature/posts
```

```bash
git push origin --delete feature/posts
```

Baris terakhir menghapus branch di fork kamu (opsional, tapi rapi). Hanya branch kerja yang pernah di-push; `main` tidak.

---

# BRANCH 4: `feature/news`

Tiga berita: `berita-beasiswa-jendedu-2027.html`, `berita-kelas-live-utbk-2027.html`, `berita-kemitraan-sekolah.html`, plus gambar `berita-1.jpg`, `berita-2.jpg`, `berita-3.jpg`.

### Langkah 4.1 - Siapkan branch (Git Bash)

```bash
cd /c/Proyek/JendEdu
```

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git switch -c feature/news
```

### Langkah 4.2 - Salin file (cmd)

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
copy ..\JendEdu-template\berita-*.html .
```

```cmd
mkdir img\blog
```

(Kalau muncul "already exists", abaikan.)

```cmd
copy ..\JendEdu-template\img\blog\berita-*.jpg img\blog\
```

Catatan: `berita-beasiswa-jendedu-2027.html` di root adalah **draft** (sengaja mengandung kesalahan untuk PR #7); dua berita lain sudah benar. Jangan ambil dari `review\codes\` dulu.

Cek di browser:

```cmd
start berita-beasiswa-jendedu-2027.html
```

```cmd
start berita-kelas-live-utbk-2027.html
```

```cmd
start berita-kemitraan-sekolah.html
```

### Langkah 4.3 - Commit dan push (Git Bash)

```bash
git status
```

```bash
git add berita-beasiswa-jendedu-2027.html berita-kelas-live-utbk-2027.html berita-kemitraan-sekolah.html img/blog/berita-1.jpg img/blog/berita-2.jpg img/blog/berita-3.jpg
```

```bash
git commit -m "Tambah 3 halaman berita"
```

```bash
git push -u origin feature/news
```

Branch terkirim ke **fork kamu**.

### Langkah 4.4 - Buat PR (Browser)

Judul:

```
Tambah 3 halaman berita
```

Deskripsi:

```
## Ringkasan
Menambahkan tiga halaman berita terkini tentang JendEdu.

## Isi
- berita-beasiswa-jendedu-2027.html
- berita-kelas-live-utbk-2027.html
- berita-kemitraan-sekolah.html
- Gambar berita di `img/blog/` (berita-1.jpg sampai berita-3.jpg)

## Cara mengecek
1. `git fetch origin` lalu `git switch feature/news`
2. Buka ketiga file berita di browser
3. Cek gambar tampil, teks Bahasa Indonesia, tautan footer benar, dan tampilan responsif

## Catatan
Bergantung pada PR setup-template dan navbar-footer yang sudah di-merge.
```

Setelah deskripsi terisi: centang **Allow edits by maintainers** -> **Create pull request** -> minta review **@username-3** (panel kanan **Reviewers**, atau mention `@username-3` di komentar).

### Langkah 4.5 - Setelah Reviewer meminta perbaikan (Request changes), PR #7

Reviewer akan memeriksa `berita-beasiswa-jendedu-2027.html` dan memberi status **Request changes** (PR #7) dengan komentar di baris tertentu. Itu normal dan memang direncanakan. Hanya berita beasiswa yang bermasalah; `berita-kelas-live-utbk-2027.html` dan `berita-kemitraan-sekolah.html` sudah benar, jadi jangan diubah. Lakukan urutan ini:

1. **Baca komentar** di GitHub: buka PR kamu di Borayaa/JendEdu, tab **Files changed** (atau **Conversation**). Komentar yang sama juga tertulis di `C:\Proyek\JendEdu-template\review\review.md` bagian **PR #7**, lengkap dengan nomor baris.

2. **Pastikan masih di branch `feature/news`** (Git Bash):

```bash
cd /c/Proyek/JendEdu
```

```bash
git switch feature/news
```

3. **Salin file versi perbaikan** (cmd):

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
copy /Y ..\JendEdu-template\review\codes\berita-beasiswa-jendedu-2027.html .
```

Output yang diharapkan: `1 file(s) copied.` (`/Y` berarti timpa file lama tanpa bertanya).

4. **Cek di browser** (cmd):

```cmd
start berita-beasiswa-jendedu-2027.html
```

5. **Cek, add, commit, push** (Git Bash):

```bash
git status
```

```bash
git add berita-beasiswa-jendedu-2027.html
```

```bash
git commit -m "Perbaiki sesuai review PR #7"
```

```bash
git push
```

Perintah ini mengirim ke branch yang sama di **fork kamu** (`origin`), tanpa `-u` dan tanpa PR baru; PR #7 otomatis ter-update. Jangan push ke `main`.

6. **Balas setiap komentar** di GitHub dengan: `Sudah diperbaiki`. Jangan klik "Resolve conversation" sendiri kalau tidak diminta.

7. **Tunggu** Reviewer meng-**Approve** dan me-merge PR, lalu lanjut ke Langkah 4.6.

> **Alternatif (opsional):** kamu boleh memperbaiki **manual** per komentar, bukan menyalin file. Hasil akhirnya **harus sama persis** dengan file di `review\codes\`. Cek di cmd:
>
> ```cmd
> fc ..\JendEdu-template\review\codes\berita-beasiswa-jendedu-2027.html berita-beasiswa-jendedu-2027.html
> ```
>
> Hasil yang benar: `FC: no differences encountered`.

### Langkah 4.6 - Setelah di-merge (Git Bash)

Setelah Reviewer me-merge PR, perbarui `main` lokal dari upstream (tanpa push ke main):

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git branch -d feature/news
```

```bash
git push origin --delete feature/news
```

Baris terakhir menghapus branch di fork kamu (opsional, tapi rapi). Hanya branch kerja yang pernah di-push; `main` tidak.

---

# Menanggapi komentar Reviewer

Label komentar:
- 🔴 **Wajib**: harus diperbaiki sebelum di-approve.
- 🟡 **Saran**: sebaiknya diperbaiki.
- 🟢 **Nit**: hal kecil, opsional.

Tiga PR kamu mengandung draft yang sengaja salah, jadi Reviewer pasti meminta perbaikan:

| PR | Branch | File | Salin perbaikan (cmd) | `git add` (Git Bash) |
|----|--------|------|-----------------------|----------------------|
| #4 | `feature/navbar-footer` | `css\style.css` | `copy /Y ..\JendEdu-template\review\codes\css\style.css css\` | `git add css/style.css` |
| #5 | `feature/contact` | `contact.html` | `copy /Y ..\JendEdu-template\review\codes\contact.html .` | `git add contact.html` |
| #7 | `feature/news` | `berita-beasiswa-jendedu-2027.html` | `copy /Y ..\JendEdu-template\review\codes\berita-beasiswa-jendedu-2027.html .` | `git add berita-beasiswa-jendedu-2027.html` |

Alur lengkapnya ada di **Langkah 1.5** (navbar-footer), **2.5** (contact), dan **4.5** (news). Ringkasnya, untuk tiap PR: baca komentar (GitHub dan `review\review.md`), `git switch <branch>`, jalankan perintah `copy /Y` di atas, cek di browser, `git status`, `git add <file>`, `git commit -m "Perbaiki sesuai review PR #N"`, `git push`, balas tiap komentar "Sudah diperbaiki", lalu tunggu Approve dan merge.

Contoh komentar di PR #5:

> 🔴 **Wajib**: (komentar Reviewer pada baris tertentu di `contact.html`).

Boleh juga memperbaiki manual per komentar, asal hasilnya sama dengan file di `review\codes\`. Cek, misalnya:

```cmd
fc ..\JendEdu-template\review\codes\contact.html contact.html
```

Hasil yang benar: `FC: no differences encountered`.

`feature/posts` **tidak** punya kesalahan yang disengaja; Reviewer langsung Approve. Kalau Reviewer tetap meninggalkan komentar kecil di PR itu, perbaiki dengan mengedit file lalu `git add`, `git commit -m "Perbaiki sesuai review"`, `git push`, dan balas "Sudah diperbaiki".

### Kalau komentar tentang navbar atau footer

Kamu pemilik blok ini. Misalnya Reviewer bilang menu "Harga" tidak ada di navbar halaman `contact.html`, atau gaya footer berantakan di HP:
- Perbaiki blok HTML navbar/footer di file yang dikomentari, dan pastikan blok yang sama di halaman lain (termasuk halaman Coder 1) tidak berbeda.
- Kalau masalahnya di tampilan, ubah `css\style.css`, lalu `git add css/style.css` dan commit di branch yang tepat.
- Kalau halaman yang bermasalah milik Coder 1 (misal `pricing.html`), koordinasikan dengan Coder 1 atau minta izin agar kamu yang memperbaikinya di PR terpisah, supaya tidak terjadi konflik.

### Kalau push ditolak atau konflik

- `! [rejected] ... (fetch first)`: `git pull origin <nama-branch>` lalu `git push`.
- `fatal: 'upstream' does not appear to be a git repository`: jalankan `git remote add upstream https://github.com/Borayaa/JendEdu.git`, lalu ulangi perintah sebelumnya.
- `CONFLICT (content)`: buka file yang disebut, cari tanda `<<<<<<<`, `=======`, `>>>>>>>`, pilih isi yang benar, hapus tandanya, `git add <file>`, lalu `git commit`. Bingung? Tanya tim.

---

# Kalau error...

| Masalah | Solusi |
|---------|--------|
| `'copy' is not recognized` / `xcopy` tidak dikenal | Kamu di Git Bash. Jalankan di **cmd**. |
| `git: command not found` di cmd | Pakai **Git Bash** untuk git. |
| `The system cannot find the path specified` | Belum `cd C:\Proyek\JendEdu`, atau folder template belum di-clone. |
| `The system cannot find the file specified` pada `copy ... artikel-*.html` | Kamu tidak berada di `C:\Proyek\JendEdu`, atau template belum ter-clone. Cek dengan `dir ..\JendEdu-template`. |
| `A subdirectory or file img\blog already exists` | Aman, abaikan. |
| `Permission denied` / `403` saat push | Kamu mem-push ke `upstream` (Borayaa/JendEdu) secara tidak sengaja. Selalu pakai `origin` (fork kamu): `git push -u origin <nama-branch>`. Cek juga login GitHub benar. |
| `fatal: 'upstream' does not appear to be a git repository` | Jalankan `git remote add upstream https://github.com/Borayaa/JendEdu.git`, lalu `git remote -v` untuk cek. |
| PR menampilkan "There isn't anything to compare" | Dropdown base/head salah. Pastikan base repository `Borayaa/JendEdu` base `main`, head repository fork kamu, compare nama branch kamu. |
| Fork tertulis "X commits behind" | Aman, abaikan. Fork boleh tertinggal; branch baru dibuat dari `main` lokal setelah `git pull upstream main`. Jangan push ke main. |
| `fatal: A branch named ... already exists` | Pakai `git switch <nama-branch>` tanpa `-c`. |
| Halaman tanpa gaya (polos) | `css` belum ada di `main`. Pastikan PR navbar-footer sudah di-merge lalu `git pull upstream main`. |
| Gambar artikel/berita tidak muncul | Cek `dir img\blog` dan nama file; pastikan sudah di-`git add`. |

---

# Checklist akhir Coder 2

- [ ] `feature/navbar-footer` (PR #4): draft `css\style.css` disalin dulu, perbaikan dari `review\codes\css\style.css` disalin **setelah** Request changes, lalu di-merge (folder `css` dan `img\logo.png` ada)
- [ ] `feature/contact` (PR #5): draft dulu, perbaikan dari `review\codes\contact.html` setelah Request changes, lalu di-merge
- [ ] `feature/posts` di-merge (3 artikel + gambar; tanpa kesalahan yang disengaja)
- [ ] `feature/news` (PR #7): draft dulu, perbaikan dari `review\codes\berita-beasiswa-jendedu-2027.html` setelah Request changes, lalu di-merge (3 berita + gambar)
- [ ] Tidak pernah menyalin folder `review\` ke proyek
- [ ] Navbar dan footer identik di semua halaman
- [ ] Semua komentar Reviewer sudah dibalas "Sudah diperbaiki"
- [ ] `git switch main` dan `git pull upstream main` dijalankan; semua halaman terbuka normal
- [ ] Folder `panduan\` **tidak** ikut disalin ke JendEdu

---

Kembali ke [00-mulai-di-sini.md](00-mulai-di-sini.md)
