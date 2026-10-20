# Panduan Coder 1 (@username-1)

> **Tugas kamu**
> - Branch `chore/setup-template`: memasukkan aset template (js, fonts, img) ke repo **JendEdu**. Ini PR **PERTAMA**; semua orang menunggu PR ini di-merge.
> - Lima halaman: `feature/homepage`, `feature/about`, `feature/courses`, `feature/gallery`, `feature/pricing`.
> - Setiap branch = satu Pull Request (PR) yang di-review oleh Reviewer (@username-3).

**Sebelum mulai: selesaikan [01-persiapan-semua-anggota.md](01-persiapan-semua-anggota.md).** Pastikan:
- Git sudah terpasang dan `git config --global user.name` / `user.email` sudah diisi.
- Kamu sudah menerima undangan collaborator dari Borayaa.
- Folder `C:\Proyek\JendEdu-template` dan `C:\Proyek\JendEdu` sudah ada (hasil `git clone`).

---

## Gambaran urutan kerja

| No | Branch | Kapan boleh mulai | Isi |
|----|--------|-------------------|-----|
| 1 | `chore/setup-template` | Langsung (kamu yang pertama) | js, fonts, img, readme.txt |
| 2 | `feature/homepage` | Setelah PR #1 **dan** PR navbar-footer (Coder 2) sudah di-merge | `index.html` |
| 3 | `feature/about` | Sama seperti di atas | `about.html` |
| 4 | `feature/courses` | Sama seperti di atas | `courses.html` |
| 5 | `feature/gallery` | Sama seperti di atas | `portfolio.html` |
| 6 | `feature/pricing` | Sama seperti di atas | `pricing.html` |

Kamu boleh mengerjakan branch 2-6 satu per satu (tunggu satu PR selesai di-merge, lalu lanjut), atau membuat beberapa PR sekaligus. Cara paling aman untuk pemula: **satu per satu**.

## Aturan emas: dua aplikasi, dua fungsi

- **Git Bash** = semua perintah `git ...`.
- **Command Prompt (cmd)** = pindah folder, menyalin file (`copy`, `xcopy`, `robocopy`), membuka website (`start`).
- **Browser (github.com)** = membuat PR.

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
git pull origin main
```

```bash
git switch -c chore/setup-template
```

Output terakhir yang diharapkan: `Switched to a new branch 'chore/setup-template'`.

### Langkah 1.2 - Salin aset (cmd)

Buka **Command Prompt** (jangan tutup Git Bash, biarkan terbuka), lalu:

```cmd
cd C:\Proyek\JendEdu
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

Pertama kali push, akan muncul jendela browser untuk login GitHub (Git Credential Manager). Login lalu klik **Authorize**.

### Langkah 1.4 - Buat Pull Request (Browser)

1. Buka https://github.com/Borayaa/JendEdu
2. Klik tombol kuning **Compare & pull request**.
3. Pastikan `base: main` <- `compare: chore/setup-template`.
4. Isi **judul**:

```
Setup aset template (js, fonts, img)
```

5. Isi **deskripsi**:

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

6. Di panel kanan, klik **Reviewers**, pilih **@username-3** (Reviewer).
7. Klik **Create pull request**.

Beritahu tim (grup chat) bahwa PR #1 sudah siap di-review.

### Langkah 1.5 - Setelah di-merge (Git Bash)

Reviewer akan me-merge PR. Setelah itu:

```bash
git switch main
```

```bash
git pull origin main
```

Cek dengan `ls` bahwa folder `js`, `fonts`, `img` ada di `main`. Kamu boleh hapus branch lokal yang sudah selesai:

```bash
git branch -d chore/setup-template
```

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
git pull origin main
```

```bash
git switch -c feature/homepage
```

### Langkah 2.2 - Salin file (cmd)

```cmd
cd C:\Proyek\JendEdu
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

Harus ada `modified: index.html`.

```bash
git add index.html
```

```bash
git commit -m "Tambah halaman beranda (index.html)"
```

```bash
git push -u origin feature/homepage
```

### Langkah 2.4 - Buat PR (Browser)

Buka https://github.com/Borayaa/JendEdu, klik **Compare & pull request**, base `main` <- compare `feature/homepage`.

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

Reviewers: **@username-3** -> **Create pull request**.

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
git pull origin main
```

```bash
git switch -c feature/about
```

### Langkah 3.2 - Salin file (cmd)

```cmd
cd C:\Proyek\JendEdu
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

### Langkah 3.4 - Buat PR (Browser)

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

Reviewers: **@username-3** -> **Create pull request**.

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
git pull origin main
```

```bash
git switch -c feature/courses
```

### Langkah 4.2 - Salin file (cmd)

```cmd
cd C:\Proyek\JendEdu
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

### Langkah 4.4 - Buat PR (Browser)

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

Reviewers: **@username-3** -> **Create pull request**.

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
git pull origin main
```

```bash
git switch -c feature/gallery
```

### Langkah 5.2 - Salin file (cmd)

```cmd
cd C:\Proyek\JendEdu
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

### Langkah 5.4 - Buat PR (Browser)

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

Reviewers: **@username-3** -> **Create pull request**.

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
git pull origin main
```

```bash
git switch -c feature/pricing
```

### Langkah 6.2 - Salin file (cmd)

```cmd
cd C:\Proyek\JendEdu
```

```cmd
copy ..\JendEdu-template\pricing.html .
```

```cmd
start pricing.html
```

Cek harga harus konsisten: **Rp99.000** (SD), **Rp129.000** (SMP), **Rp159.000** (SMA), **Rp249.000** (UTBK Intensif), semuanya "per bulan".

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

### Langkah 6.4 - Buat PR (Browser)

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

Reviewers: **@username-3** -> **Create pull request**.

---

# Menanggapi komentar Reviewer

Reviewer akan menulis komentar di tab **Files changed**. Labelnya:
- 🔴 **Wajib**: harus diperbaiki sebelum bisa di-approve.
- 🟡 **Saran**: sebaiknya diperbaiki, boleh didiskusikan.
- 🟢 **Nit**: hal kecil, opsional.

Kamu akan mendapat email / notifikasi GitHub. Buka PR-nya, tab **Conversation** atau **Files changed**.

### Contoh nyata: format harga di `pricing.html`

Reviewer menulis di baris harga paket SMP:

> 🔴 **Wajib**: Harga ditulis `Rp 129,000/bln`. Seharusnya `Rp129.000 per bulan` supaya konsisten dengan README dan halaman lain.

Langkah memperbaiki (kamu masih di branch `feature/pricing`):

1. **Pastikan berada di branch yang benar** (Git Bash):

```bash
cd /c/Proyek/JendEdu
```

```bash
git switch feature/pricing
```

2. **Buka file** `C:\Proyek\JendEdu\pricing.html` di VS Code atau Notepad. Tekan `Ctrl + F`, cari `129`. Ubah:

```html
<span class="price">Rp 129,000/bln</span>
```

menjadi:

```html
<span class="price">Rp129.000 per bulan</span>
```

(Teks aslinya bisa sedikit berbeda; yang penting formatnya `Rp129.000 per bulan`.) Cari juga harga lain di file yang sama (`99`, `159`, `249`) supaya semuanya konsisten. Simpan dengan `Ctrl + S`.

> Kalau reviewer memakai fitur **Insert a suggestion**, kamu bisa langsung klik **Commit suggestion** di GitHub. Tetapi setelah itu jalankan `git pull` di Git Bash supaya laptopmu ikut terbaru.

3. **Cek di browser** (cmd):

```cmd
start pricing.html
```

4. **Commit dan push** (Git Bash):

```bash
git status
```

```bash
git add pricing.html
```

```bash
git commit -m "Perbaiki sesuai review: format harga di pricing.html"
```

```bash
git push
```

Tidak perlu `-u` lagi dan tidak perlu membuat PR baru; PR yang sama otomatis ter-update.

5. **Balas komentar** di GitHub: "Sudah diperbaiki, harga sekarang `Rp129.000 per bulan` di semua paket." Jangan klik "Resolve conversation" sendiri kalau tidak diminta; biasanya Reviewer yang me-resolve.
6. Tunggu Reviewer meng-**Approve** dan me-merge.

> Tips: kalau komentar menyangkut **navbar atau footer** (menu salah, tautan rusak di footer), itu urusan **Coder 2**. Beri tahu Coder 2 atau balas "Ini bagian Coder 2, sudah saya teruskan".

### Kalau ada konflik atau push ditolak

- `! [rejected] ... (fetch first)`: jalankan `git pull origin feature/pricing` lalu `git push` lagi.
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
| `Permission denied` / `403` saat push | Undangan collaborator belum diterima, atau login GitHub salah. Cek email / https://github.com/Borayaa/JendEdu/invitations. |
| `fatal: A branch named ... already exists` | Branch sudah ada. Pakai `git switch <nama-branch>`, bukan `-c`. |
| `Your local changes would be overwritten` saat `git switch` | Ada perubahan belum di-commit. Commit dulu, atau tanya tim sebelum memakai `git stash`. |
| Halaman tampil tanpa gaya / tanpa gambar | PR setup-template atau navbar-footer belum di-merge ke `main`. Jalankan `git pull origin main`. |

---

# Checklist akhir Coder 1

- [ ] `chore/setup-template` sudah di-merge (js, fonts, img ada)
- [ ] `feature/homepage` di-merge
- [ ] `feature/about` di-merge
- [ ] `feature/courses` di-merge
- [ ] `feature/gallery` di-merge
- [ ] `feature/pricing` di-merge
- [ ] Semua komentar Reviewer sudah dibalas "Sudah diperbaiki"
- [ ] Harga konsisten: Rp99.000 / Rp129.000 / Rp159.000 / Rp249.000 per bulan
- [ ] `git switch main` dan `git pull origin main` sudah dijalankan; semua halaman terbuka normal dengan `start index.html`
- [ ] Folder `panduan\` **tidak** ikut disalin ke JendEdu

---

Kembali ke [00-mulai-di-sini.md](00-mulai-di-sini.md)
