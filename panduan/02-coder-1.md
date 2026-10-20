# Panduan Coder 1 (@username-1)

> **Tugas kamu**
> - Branch `chore/setup-template`: memasukkan aset template (js, fonts, img) ke repo **JendEdu** lewat fork kamu. Ini PR **PERTAMA**; semua orang menunggu PR ini di-merge.
> - Lima halaman: `feature/homepage`, `feature/about`, `feature/courses`, `feature/gallery`, `feature/pricing`.
> - Setiap branch = satu Pull Request (PR) yang di-review oleh Reviewer (@username-3).

**Sebelum mulai: selesaikan [01-persiapan-semua-anggota.md](01-persiapan-semua-anggota.md).** Pastikan:
- Git sudah terpasang dan `git config --global user.name` / `user.email` sudah diisi.
- Kamu sudah mem-fork https://github.com/Borayaa/JendEdu menjadi https://github.com/username-1/JendEdu (**fork** kamu = `origin`).
- Remote `upstream` (https://github.com/Borayaa/JendEdu.git) sudah ditambahkan; cek dengan `git remote -v`.
- Folder `C:\Proyek\JendEdu-template` dan `C:\Proyek\JendEdu` (clone dari fork kamu) sudah ada.
- Kamu **tidak** push langsung ke Borayaa/JendEdu; semua kerja lewat fork lalu PR.

> **⚠️ Jangan pernah `git push` ke `main`.** Hanya branch kerja (`feature/...`, `chore/...`) yang di-push, dan hanya ke `origin` (fork kamu). `main` hanya berubah lewat PR yang di-merge. Fork kamu di GitHub boleh tertinggal (`X commits behind`); itu tidak masalah, karena branch baru selalu dibuat dari `main` lokal yang sudah di-pull dari upstream. Jangan klik/jalankan apa pun yang mem-push ke main.

> **📌 Draft vs versi perbaikan**
>
> - File di **root** `C:\Proyek\JendEdu-template` adalah **draft**. Untuk PR yang ditugaskan ke kamu di bawah ini, draft itu **sengaja mengandung kesalahan** supaya Reviewer punya sesuatu untuk di-review.
> - PR kamu yang berisi draft dengan kesalahan: **`feature/pricing` (disebut "PR #3" di review.md)** dengan file `pricing.html`. Nomor PR (#3, #4, dst.) di panduan ini mengikuti contoh di `review\review.md`. Nomor sebenarnya di GitHub bisa berbeda, tergantung urutan PR dibuka. Selalu kenali PR lewat **nama branch**-nya.
> - Versi **yang sudah diperbaiki** ada di folder `C:\Proyek\JendEdu-template\review\codes\`.
> - **Urutan yang benar:** (1) salin **draft** dari root dan buat PR; (2) **tunggu** Reviewer memberi **Request changes**; (3) baru setelah itu salin file perbaikan dari `review\codes\`, commit, dan push.
> - **Jangan** menyalin dari `review\codes\` sebelum Reviewer berkomentar, dan **jangan pernah** menyalin folder `review\` ke proyek (itu bagian PR dokumentasi di akhir).
> - PR kamu yang lain (`chore/setup-template`, `homepage`, `about`, `courses`, `gallery`) **tidak** punya kesalahan yang disengaja, jadi Reviewer langsung **Approve** (tetap dicek).

---

## Gambaran urutan kerja

| No | Branch | Kapan boleh mulai | Isi |
|----|--------|-------------------|-----|
| 1 | `chore/setup-template` | Langsung (kamu yang pertama) | js, fonts, img, readme.txt |
| 2 | `feature/homepage` | Setelah PR `chore/setup-template` **dan** PR `feature/navbar-footer` (Coder 2) sudah di-merge | `index.html` |
| 3 | `feature/about` | Sama seperti di atas | `about.html` |
| 4 | `feature/courses` | Sama seperti di atas | `courses.html` |
| 5 | `feature/gallery` | Sama seperti di atas | `portfolio.html` |
| 6 | `feature/pricing` | Sama seperti di atas | `pricing.html` |

Kamu boleh mengerjakan branch 2-6 satu per satu (tunggu satu PR selesai di-merge, lalu lanjut), atau membuat beberapa PR sekaligus. Cara paling aman untuk pemula: **satu per satu**.

## Aturan emas: dua aplikasi, dua fungsi

- **Git Bash** = semua perintah `git ...`.
- **Command Prompt (cmd)** = pindah folder, menyalin file (`copy`, `xcopy`, `robocopy`), membuka website (`start`).
- **Browser (github.com)** = membuat PR dari fork kamu ke Borayaa/JendEdu.

Cara membuka:
- cmd: tekan `Win + R`, ketik `cmd`, Enter.
- Git Bash: menu Start, ketik "Git Bash", Enter. Atau buka folder `C:\Proyek\JendEdu` di File Explorer, klik kanan di area kosong, pilih **Open Git Bash here** (Windows 11: Show more options dulu).

Di Git Bash, `C:\Proyek\JendEdu` ditulis `/c/Proyek/JendEdu`.

---

# BRANCH 1: `chore/setup-template`

Tujuan: menyalin aset (js, fonts, gambar) dari template. Kamu **tidak** menyalin logo.png (itu bagian Coder 2) dan folder `img\blog` (bagian Coder 2).

### Langkah 1.1 - Siapkan branch (Git Bash)

Buka **Git Bash**, lalu:

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
git switch -c chore/setup-template
```

Output terakhir yang diharapkan: `Switched to a new branch 'chore/setup-template'`.

### Langkah 1.2 - Salin aset (cmd)

Buka **Command Prompt** (jangan tutup Git Bash, biarkan terbuka), lalu:

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
xcopy ..\JendEdu-template\js js\ /E /I /Y
```

```cmd
xcopy ..\JendEdu-template\fonts fonts\ /E /I /Y
```

```cmd
robocopy ..\JendEdu-template\img img /E /XF logo.png /XD blog
```

```cmd
copy ..\JendEdu-template\readme.txt .
```

Catatan penting:
- `robocopy` menampilkan tabel ringkasan. Kode keluar **1** artinya "file berhasil disalin" - itu **bukan error**. Kalau ada tulisan merah/`ERROR`, baru ada masalah.
- Setelah selesai, cek isinya:

```cmd
dir
```

Kamu harus melihat folder `js`, `fonts`, `img`, dan file `readme.txt`.

### Langkah 1.3 - Cek, add, commit, push (Git Bash)

```bash
git status
```

Kamu akan melihat daftar folder dan file baru (merah, belum di-add).

```bash
git add js fonts img readme.txt
```

```bash
git status
```

Sekarang semuanya hijau. Lalu commit:

```bash
git commit -m "Setup aset template (js, fonts, img)"
```

```bash
git push -u origin chore/setup-template
```

Perintah ini mengirim branch ke **fork kamu** (`origin`). Pertama kali push, akan muncul jendela browser untuk login GitHub (Git Credential Manager). Login lalu klik **Authorize**.

### Langkah 1.4 - Buat Pull Request (Browser)

Buka fork kamu di browser: https://github.com/username-1/JendEdu. Klik tombol kuning **Compare & pull request** (muncul di bar "chore/setup-template had recent pushes"). Kalau tombol tidak muncul: tab **Pull requests** -> **New pull request** -> **compare across forks**.

Cek **empat dropdown** (ini penting):

- base repository: `Borayaa/JendEdu`
- base: `main`
- head repository: `username-1/JendEdu`
- compare: `chore/setup-template`

Lalu isi judul dan deskripsi seperti di bawah.

Judul:

```
Setup aset template (js, fonts, img)
```

Deskripsi:

```
## Ringkasan
Menambahkan aset dasar dari template JendEdu supaya halaman-halaman berikutnya bisa berjalan.

## Perubahan
- Menambahkan folder `js` (jQuery, Bootstrap, FlexSlider, Fancybox, dll.)
- Menambahkan folder `fonts` (Font Awesome dan ikon kustom)
- Menambahkan folder `img` (gambar template, kecuali `logo.png` dan `img/blog`)
- Menambahkan `readme.txt` bawaan template

## Catatan
- Logo dan folder `css` dikerjakan Coder 2 di PR terpisah.
- PR ini harus di-merge lebih dulu sebelum PR lain.

## Cara mengecek
Tidak ada halaman yang ditampilkan di PR ini. Cukup cek bahwa folder `js`, `fonts`, `img` ada.
```

Setelah deskripsi terisi: centang **Allow edits by maintainers** -> **Create pull request** -> minta review **@username-3** (panel kanan **Reviewers**, atau mention `@username-3` di komentar).

Beritahu tim (grup chat) bahwa PR `chore/setup-template` sudah siap di-review.

### Langkah 1.5 - Setelah di-merge (Git Bash)

Setelah Reviewer me-merge PR, perbarui `main` lokal dari upstream (tanpa push ke main):

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git branch -d chore/setup-template
```

```bash
git push origin --delete chore/setup-template
```

Baris terakhir menghapus branch di fork kamu (opsional, tapi rapi). Hanya branch kerja yang pernah di-push; `main` tidak.

Cek dengan `ls` bahwa folder `js`, `fonts`, `img` ada di `main`.

---

# BRANCH 2: `feature/homepage`

**Syarat**: PR `chore/setup-template` dan PR `feature/navbar-footer` (Coder 2) sudah di-merge. Cek di https://github.com/Borayaa/JendEdu/pulls?q=is%3Apr+is%3Aclosed.

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
git switch -c feature/homepage
```

### Langkah 2.2 - Salin file (cmd)

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
copy ..\JendEdu-template\index.html .
```

Output yang diharapkan: `1 file(s) copied.`

Cek di browser:

```cmd
start index.html
```

Pastikan slider tampil, gambar muncul, navbar dan footer rapi.

### Langkah 2.3 - Commit dan push (Git Bash)

```bash
git status
```

Harus ada `index.html` (daftar file baru / `Untracked files`, karena repo `JendEdu` awalnya kosong).

```bash
git add index.html
```

```bash
git commit -m "Tambah halaman beranda (index.html)"
```

```bash
git push -u origin feature/homepage
```

Branch terkirim ke **fork kamu**.

### Langkah 2.4 - Buat PR (Browser)

Buka fork kamu di browser: https://github.com/username-1/JendEdu. Klik tombol kuning **Compare & pull request** (muncul di bar "feature/homepage had recent pushes"). Kalau tombol tidak muncul: tab **Pull requests** -> **New pull request** -> **compare across forks**.

Cek **empat dropdown** (ini penting):

- base repository: `Borayaa/JendEdu`
- base: `main`
- head repository: `username-1/JendEdu`
- compare: `feature/homepage`

Isi judul dan deskripsi (di bawah), centang **Allow edits by maintainers**, lalu klik **Create pull request**. Setelah PR terbuat (halamannya di Borayaa/JendEdu), di panel kanan klik **Reviewers** dan pilih **@username-3**. Kalau tidak bisa memilih, tulis komentar `@username-3 mohon di-review` di PR.

Judul:

```
Tambah halaman beranda (index.html)
```

Deskripsi:

```
## Ringkasan
Menambahkan halaman beranda JendEdu (`index.html`).

## Isi halaman
- Slider utama (FlexSlider)
- Keunggulan JendEdu
- Testimoni peserta
- Daftar kursus singkat
- Navbar dan footer

## Cara mengecek
1. Pindah ke branch ini: `git fetch origin` lalu `git switch feature/homepage`
2. Buka `index.html` di browser
3. Cek slider berjalan, gambar tampil, tautan menu berfungsi, dan tampilan rapi di ukuran HP (Ctrl+Shift+M di DevTools)

```

Setelah deskripsi terisi: centang **Allow edits by maintainers** -> **Create pull request** -> minta review **@username-3** (panel kanan **Reviewers**, atau mention `@username-3` di komentar).

### Langkah 2.5 - Setelah di-merge (Git Bash)

Setelah Reviewer me-merge PR, perbarui `main` lokal dari upstream (tanpa push ke main):

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git branch -d feature/homepage
```

```bash
git push origin --delete feature/homepage
```

Baris terakhir menghapus branch di fork kamu (opsional, tapi rapi). Hanya branch kerja yang pernah di-push; `main` tidak.

---

# BRANCH 3: `feature/about`

### Langkah 3.1 - Siapkan branch (Git Bash)

Sebelum mulai, pastikan PR sebelumnya sudah di-merge (atau kamu sengaja bekerja paralel). Lalu:

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
git switch -c feature/about
```

### Langkah 3.2 - Salin file (cmd)

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
copy ..\JendEdu-template\about.html .
```

```cmd
start about.html
```

Cek: foto tim (team1-4.jpg) muncul, teks Bahasa Indonesia, menu berfungsi.

### Langkah 3.3 - Commit dan push (Git Bash)

```bash
git status
```

```bash
git add about.html
```

```bash
git commit -m "Tambah halaman Tentang Kami (about.html)"
```

```bash
git push -u origin feature/about
```

Branch terkirim ke **fork kamu**.

### Langkah 3.4 - Buat PR (Browser)

Buka fork kamu di browser: https://github.com/username-1/JendEdu. Klik tombol kuning **Compare & pull request** (muncul di bar "feature/about had recent pushes"). Kalau tombol tidak muncul: tab **Pull requests** -> **New pull request** -> **compare across forks**.

Cek **empat dropdown** (ini penting):

- base repository: `Borayaa/JendEdu`
- base: `main`
- head repository: `username-1/JendEdu`
- compare: `feature/about`

Isi judul dan deskripsi (di bawah), centang **Allow edits by maintainers**, lalu klik **Create pull request**. Setelah PR terbuat (halamannya di Borayaa/JendEdu), di panel kanan klik **Reviewers** dan pilih **@username-3**. Kalau tidak bisa memilih, tulis komentar `@username-3 mohon di-review` di PR.

Judul:

```
Tambah halaman Tentang Kami (about.html)
```

Deskripsi:

```
## Ringkasan
Menambahkan halaman Tentang Kami berisi profil JendEdu dan tim pengajar.

## Isi halaman
- Profil dan visi JendEdu
- Tim pengajar beserta foto
- Navbar dan footer

## Cara mengecek
1. `git fetch origin` lalu `git switch feature/about`
2. Buka `about.html` di browser
3. Cek foto tim tampil, tautan menu berfungsi, dan tampilan responsif

## Catatan
Bergantung pada PR setup-template dan navbar-footer yang sudah di-merge.
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
git branch -d feature/about
```

```bash
git push origin --delete feature/about
```

Baris terakhir menghapus branch di fork kamu (opsional, tapi rapi). Hanya branch kerja yang pernah di-push; `main` tidak.

---

# BRANCH 4: `feature/courses`

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
git switch -c feature/courses
```

### Langkah 4.2 - Salin file (cmd)

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
copy ..\JendEdu-template\courses.html .
```

```cmd
start courses.html
```

Cek: tiga jenjang (SD, SMP, SMA) tampil, gambar service1-3 muncul.

### Langkah 4.3 - Commit dan push (Git Bash)

```bash
git status
```

```bash
git add courses.html
```

```bash
git commit -m "Tambah halaman Kursus (courses.html)"
```

```bash
git push -u origin feature/courses
```

Branch terkirim ke **fork kamu**.

### Langkah 4.4 - Buat PR (Browser)

Buka fork kamu di browser: https://github.com/username-1/JendEdu. Klik tombol kuning **Compare & pull request** (muncul di bar "feature/courses had recent pushes"). Kalau tombol tidak muncul: tab **Pull requests** -> **New pull request** -> **compare across forks**.

Cek **empat dropdown** (ini penting):

- base repository: `Borayaa/JendEdu`
- base: `main`
- head repository: `username-1/JendEdu`
- compare: `feature/courses`

Isi judul dan deskripsi (di bawah), centang **Allow edits by maintainers**, lalu klik **Create pull request**. Setelah PR terbuat (halamannya di Borayaa/JendEdu), di panel kanan klik **Reviewers** dan pilih **@username-3**. Kalau tidak bisa memilih, tulis komentar `@username-3 mohon di-review` di PR.

Judul:

```
Tambah halaman Kursus (courses.html)
```

Deskripsi:

```
## Ringkasan
Menambahkan halaman katalog kursus per jenjang.

## Isi halaman
- Kursus SD, SMP, dan SMA
- Gambar dan deskripsi tiap jenjang
- Navbar dan footer

## Cara mengecek
1. `git fetch origin` lalu `git switch feature/courses`
2. Buka `courses.html` di browser
3. Cek semua jenjang tampil, gambar muncul, tautan berfungsi, dan responsif

## Catatan
Bergantung pada PR setup-template dan navbar-footer yang sudah di-merge.
```

Setelah deskripsi terisi: centang **Allow edits by maintainers** -> **Create pull request** -> minta review **@username-3** (panel kanan **Reviewers**, atau mention `@username-3` di komentar).

### Langkah 4.5 - Setelah di-merge (Git Bash)

Setelah Reviewer me-merge PR, perbarui `main` lokal dari upstream (tanpa push ke main):

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git branch -d feature/courses
```

```bash
git push origin --delete feature/courses
```

Baris terakhir menghapus branch di fork kamu (opsional, tapi rapi). Hanya branch kerja yang pernah di-push; `main` tidak.

---

# BRANCH 5: `feature/gallery`

Nama branch `gallery`, tetapi file-nya `portfolio.html`.

### Langkah 5.1 - Siapkan branch (Git Bash)

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
git switch -c feature/gallery
```

### Langkah 5.2 - Salin file (cmd)

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
copy ..\JendEdu-template\portfolio.html .
```

```cmd
start portfolio.html
```

Cek: gambar galeri tampil, filter SD/SMP/SMA berfungsi, klik gambar membuka lightbox (Fancybox).

### Langkah 5.3 - Commit dan push (Git Bash)

```bash
git status
```

```bash
git add portfolio.html
```

```bash
git commit -m "Tambah halaman Galeri kegiatan (portfolio.html)"
```

```bash
git push -u origin feature/gallery
```

Branch terkirim ke **fork kamu**.

### Langkah 5.4 - Buat PR (Browser)

Buka fork kamu di browser: https://github.com/username-1/JendEdu. Klik tombol kuning **Compare & pull request** (muncul di bar "feature/gallery had recent pushes"). Kalau tombol tidak muncul: tab **Pull requests** -> **New pull request** -> **compare across forks**.

Cek **empat dropdown** (ini penting):

- base repository: `Borayaa/JendEdu`
- base: `main`
- head repository: `username-1/JendEdu`
- compare: `feature/gallery`

Isi judul dan deskripsi (di bawah), centang **Allow edits by maintainers**, lalu klik **Create pull request**. Setelah PR terbuat (halamannya di Borayaa/JendEdu), di panel kanan klik **Reviewers** dan pilih **@username-3**. Kalau tidak bisa memilih, tulis komentar `@username-3 mohon di-review` di PR.

Judul:

```
Tambah halaman Galeri kegiatan (portfolio.html)
```

Deskripsi:

```
## Ringkasan
Menambahkan halaman galeri kegiatan JendEdu dengan filter jenjang.

## Isi halaman
- Galeri gambar dengan filter SD / SMP / SMA (Quicksand)
- Lightbox saat gambar diklik (Fancybox)
- Navbar dan footer

## Cara mengecek
1. `git fetch origin` lalu `git switch feature/gallery`
2. Buka `portfolio.html` di browser
3. Klik tiap filter, klik gambar untuk lightbox, cek tampilan responsif

## Catatan
Nama file tetap `portfolio.html` (sesuai template), nama branch `gallery`.
```

Setelah deskripsi terisi: centang **Allow edits by maintainers** -> **Create pull request** -> minta review **@username-3** (panel kanan **Reviewers**, atau mention `@username-3` di komentar).

### Langkah 5.5 - Setelah di-merge (Git Bash)

Setelah Reviewer me-merge PR, perbarui `main` lokal dari upstream (tanpa push ke main):

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git branch -d feature/gallery
```

```bash
git push origin --delete feature/gallery
```

Baris terakhir menghapus branch di fork kamu (opsional, tapi rapi). Hanya branch kerja yang pernah di-push; `main` tidak.

---

# BRANCH 6: `feature/pricing`

### Langkah 6.1 - Siapkan branch (Git Bash)

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
git switch -c feature/pricing
```

### Langkah 6.2 - Salin file (cmd)

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
copy ..\JendEdu-template\pricing.html .
```

```cmd
start pricing.html
```

Ini adalah **draft** (sengaja mengandung kesalahan untuk PR #3). Salin apa adanya; **jangan** mengambil dari `review\codes\` dulu. Harga yang benar nanti: **Rp99.000** (SD), **Rp129.000** (SMP), **Rp159.000** (SMA), **Rp249.000** (UTBK Intensif), semuanya "per bulan".

### Langkah 6.3 - Commit dan push (Git Bash)

```bash
git status
```

```bash
git add pricing.html
```

```bash
git commit -m "Tambah halaman Paket Harga (pricing.html)"
```

```bash
git push -u origin feature/pricing
```

Branch terkirim ke **fork kamu**.

### Langkah 6.4 - Buat PR (Browser)

Buka fork kamu di browser: https://github.com/username-1/JendEdu. Klik tombol kuning **Compare & pull request** (muncul di bar "feature/pricing had recent pushes"). Kalau tombol tidak muncul: tab **Pull requests** -> **New pull request** -> **compare across forks**.

Cek **empat dropdown** (ini penting):

- base repository: `Borayaa/JendEdu`
- base: `main`
- head repository: `username-1/JendEdu`
- compare: `feature/pricing`

Isi judul dan deskripsi (di bawah), centang **Allow edits by maintainers**, lalu klik **Create pull request**. Setelah PR terbuat (halamannya di Borayaa/JendEdu), di panel kanan klik **Reviewers** dan pilih **@username-3**. Kalau tidak bisa memilih, tulis komentar `@username-3 mohon di-review` di PR.

Judul:

```
Tambah halaman Paket Harga (pricing.html)
```

Deskripsi:

```
## Ringkasan
Menambahkan halaman paket harga kursus JendEdu.

## Isi halaman
- Paket SD: Rp99.000 per bulan
- Paket SMP: Rp129.000 per bulan
- Paket SMA: Rp159.000 per bulan
- Paket UTBK Intensif: Rp249.000 per bulan
- Navbar dan footer

## Cara mengecek
1. `git fetch origin` lalu `git switch feature/pricing`
2. Buka `pricing.html` di browser
3. Cek keempat harga sesuai daftar di atas dan tampilan responsif

## Catatan
Bergantung pada PR setup-template dan navbar-footer yang sudah di-merge.
```

Setelah deskripsi terisi: centang **Allow edits by maintainers** -> **Create pull request** -> minta review **@username-3** (panel kanan **Reviewers**, atau mention `@username-3` di komentar).

### Langkah 6.5 - Setelah Reviewer meminta perbaikan (Request changes)

Reviewer akan memeriksa `pricing.html` dan memberi status **Request changes** ("PR #3" di review.md; nomor di GitHub-mu bisa berbeda) dengan komentar di baris tertentu. Itu normal dan memang direncanakan. Lakukan urutan ini:

1. **Baca komentar** di GitHub: buka PR kamu di Borayaa/JendEdu, tab **Files changed** (atau **Conversation**). Komentar yang sama juga tertulis di `C:\Proyek\JendEdu-template\review\review.md` bagian **PR #3**, lengkap dengan nomor baris. Pahami dulu apa yang salah.

2. **Pastikan masih di branch `feature/pricing`** (Git Bash):

```bash
cd /c/Proyek/JendEdu
```

```bash
git switch feature/pricing
```

3. **Salin file versi perbaikan** (cmd):

```cmd
cd /d C:\Proyek\JendEdu
```

```cmd
copy /Y ..\JendEdu-template\review\codes\pricing.html .
```

Output yang diharapkan: `1 file(s) copied.` (`/Y` berarti timpa file lama tanpa bertanya).

4. **Cek di browser** (cmd):

```cmd
start pricing.html
```

Pastikan keempat harga sudah `Rp99.000`, `Rp129.000`, `Rp159.000`, `Rp249.000` per bulan dan tampilan rapi.

5. **Cek, add, commit, push** (Git Bash):

```bash
git status
```

Harus ada `modified: pricing.html` (file ini sudah ada di branch dari commit pertama).

```bash
git add pricing.html
```

```bash
git commit -m "Perbaiki halaman Harga sesuai review PR #3"
```

```bash
git push
```

Perintah ini mengirim ke branch yang sama di **fork kamu** (`origin`), tanpa `-u` dan tanpa PR baru; PR #3 di Borayaa/JendEdu ter-update otomatis. Jangan push ke `main`.

6. **Balas setiap komentar** di GitHub dengan: `Sudah diperbaiki`. Jangan klik "Resolve conversation" sendiri kalau tidak diminta.

7. **Tunggu** Reviewer meng-**Approve** dan me-merge PR. Setelah itu lanjut ke Langkah 6.6.

> **Alternatif (opsional):** kamu boleh memperbaiki **manual** satu per satu sesuai komentar (buka `pricing.html`, ubah barisnya, simpan), bukan menyalin file. Tetapi hasil akhirnya **harus sama persis** dengan `review\codes\pricing.html`. Cek di cmd:
>
> ```cmd
> fc ..\JendEdu-template\review\codes\pricing.html pricing.html
> ```
>
> Hasil yang benar: `FC: no differences encountered`. Kalau ada perbedaan, FC menampilkan baris yang berbeda; perbaiki sampai sama.

### Langkah 6.6 - Setelah di-merge (Git Bash)

Setelah Reviewer me-merge PR, perbarui `main` lokal dari upstream (tanpa push ke main):

```bash
git switch main
```

```bash
git pull upstream main
```

```bash
git branch -d feature/pricing
```

```bash
git push origin --delete feature/pricing
```

Baris terakhir menghapus branch di fork kamu (opsional, tapi rapi). Hanya branch kerja yang pernah di-push; `main` tidak.

---

# Menanggapi komentar Reviewer

Reviewer akan menulis komentar di tab **Files changed**. Labelnya:
- 🔴 **Wajib**: harus diperbaiki sebelum bisa di-approve.
- 🟡 **Saran**: sebaiknya diperbaiki, boleh didiskusikan.
- 🟢 **Nit**: hal kecil, opsional.

Kamu akan mendapat email / notifikasi GitHub. Buka PR-nya, tab **Conversation** atau **Files changed**.

### Contoh nyata: PR #3 `pricing.html`

`pricing.html` yang kamu salin dari root adalah draft yang sengaja salah, jadi Reviewer pasti meminta perbaikan. Contoh komentar di baris harga paket (kutipan dari `review\review.md`):

> 🔴 **Wajib diperbaiki.** Format harga tidak konsisten di ketiga paket (spasi setelah "Rp", titik ribuan, "bln" vs "bulan"). Samakan dengan format `Rp99.000 / bulan`.

Cara menanggapinya adalah alur lengkap di **Langkah 6.5** (bagian "Setelah Reviewer meminta perbaikan"):

1. Baca semua komentar di GitHub (dan di `review\review.md` bagian PR #3).
2. Git Bash: `git switch feature/pricing`.
3. cmd: `copy /Y ..\JendEdu-template\review\codes\pricing.html .` lalu `start pricing.html`.
4. Git Bash: `git status`, `git add pricing.html`, `git commit -m "Perbaiki halaman Harga sesuai review PR #3"`, `git push`.
5. Balas tiap komentar: "Sudah diperbaiki".
6. Tunggu Approve dan merge, lalu Langkah 6.6.

Boleh juga memperbaiki manual per komentar (alternatif di Langkah 6.5), asal hasilnya sama dengan `review\codes\pricing.html` (cek dengan `fc ..\JendEdu-template\review\codes\pricing.html pricing.html`).

> Kalau reviewer memakai fitur **Insert a suggestion**, kamu bisa klik **Commit suggestion** di GitHub. Setelah itu jalankan `git pull origin feature/pricing` di Git Bash supaya laptopmu ikut terbaru.

Untuk PR lain (homepage, about, courses, gallery, setup-template) biasanya tidak ada permintaan perbaikan; Reviewer langsung Approve.

> Tips: kalau komentar menyangkut **navbar atau footer** (menu salah, tautan rusak di footer), itu urusan **Coder 2**. Beri tahu Coder 2 atau balas "Ini bagian Coder 2, sudah saya teruskan".

### Kalau ada konflik atau push ditolak

- `! [rejected] ... (fetch first)`: jalankan `git pull origin feature/pricing` lalu `git push` lagi.
- `fatal: 'upstream' does not appear to be a git repository`: jalankan `git remote add upstream https://github.com/Borayaa/JendEdu.git`, lalu ulangi perintah sebelumnya.
- `CONFLICT (content)`: buka file yang disebut, cari tanda `<<<<<<<`, `=======`, `>>>>>>>`, pilih isi yang benar, hapus tanda-tandanya, lalu `git add <file>` dan `git commit`. Kalau bingung, minta bantuan tim.

---

# Kalau error...

| Masalah | Solusi |
|---------|--------|
| `'xcopy' is not recognized` | Kamu di Git Bash. Perintah `copy`/`xcopy`/`robocopy` dijalankan di **cmd**. |
| `git: command not found` di cmd | Pakai **Git Bash** untuk perintah git, atau pasang ulang Git (lihat panduan persiapan). |
| `The system cannot find the path specified` | Kamu belum `cd C:\Proyek\JendEdu` di cmd, atau folder template belum di-clone. |
| `File not found - ...` saat copy | Pastikan file ada di `C:\Proyek\JendEdu-template` dan template sudah di-clone. |
| `error: pathspec ... did not match` saat `git add` | Nama file salah ketik, atau file tidak disalin ke `C:\Proyek\JendEdu`. Jalankan `dir` di cmd. |
| `Permission denied` / `403` saat push | Kamu mem-push ke `upstream` (Borayaa/JendEdu) secara tidak sengaja. Selalu pakai `origin` (fork kamu): `git push -u origin <nama-branch>`. Cek juga login GitHub benar. |
| `fatal: 'upstream' does not appear to be a git repository` | Jalankan `git remote add upstream https://github.com/Borayaa/JendEdu.git`, lalu `git remote -v` untuk cek. |
| PR menampilkan "There isn't anything to compare" | Dropdown base/head salah. Pastikan base repository `Borayaa/JendEdu` base `main`, head repository fork kamu, compare nama branch kamu. |
| Fork tertulis "X commits behind" | Aman, abaikan. Fork boleh tertinggal; branch baru dibuat dari `main` lokal setelah `git pull upstream main`. Jangan push ke main. |
| `fatal: A branch named ... already exists` | Branch sudah ada. Pakai `git switch <nama-branch>`, bukan `-c`. |
| `Your local changes would be overwritten` saat `git switch` | Ada perubahan belum di-commit. Commit dulu, atau tanya tim sebelum memakai `git stash`. |
| `error: The branch ... is not fully merged` saat `git branch -d` | PR di-merge dengan cara lain (bukan merge commit). Kalau PR-nya memang sudah ter-merge di GitHub, aman memakai `git branch -D <nama-branch>`. |
| Halaman tampil tanpa gaya / tanpa gambar | PR setup-template atau navbar-footer belum di-merge ke `main`. Jalankan `git pull upstream main`. |

---

# Checklist akhir Coder 1

- [ ] `chore/setup-template` sudah di-merge (js, fonts, img ada)
- [ ] `feature/homepage` di-merge
- [ ] `feature/about` di-merge
- [ ] `feature/courses` di-merge
- [ ] `feature/gallery` di-merge
- [ ] `feature/pricing` ("PR #3" di review.md): draft dari root disalin lebih dulu, perbaikan dari `review\codes\pricing.html` disalin **setelah** Reviewer Request changes, lalu di-merge
- [ ] Tidak pernah menyalin folder `review\` ke proyek
- [ ] Semua komentar Reviewer sudah dibalas "Sudah diperbaiki"
- [ ] Harga konsisten: Rp99.000 / Rp129.000 / Rp159.000 / Rp249.000 per bulan
- [ ] `git switch main` dan `git pull upstream main` sudah dijalankan; semua halaman terbuka normal dengan `start index.html`
- [ ] Folder `panduan\` **tidak** ikut disalin ke JendEdu

---

Kembali ke [00-mulai-di-sini.md](00-mulai-di-sini.md)
