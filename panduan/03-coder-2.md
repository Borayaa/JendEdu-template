# Panduan Coder 2 (@username-2)

> **Tugas kamu**
> - Branch `feature/navbar-footer`: styling (CSS) bersama untuk navbar dan footer + logo. Ini PR **kedua**, dikerjakan setelah PR setup-template Coder 1 di-merge.
> - Halaman lain: `feature/contact`, `feature/posts` (3 artikel), `feature/news` (3 berita).
> - Kamu adalah **pemilik** blok navbar dan footer beserta CSS-nya. Kalau Reviewer minta perbaikan navbar/footer di halaman mana pun, **kamu** yang memperbaikinya.
> - Setiap branch = satu Pull Request (PR) yang di-review oleh Reviewer (@username-3).

**Sebelum mulai: selesaikan [01-persiapan-semua-anggota.md](01-persiapan-semua-anggota.md).** Pastikan Git terpasang, `user.name`/`user.email` terisi, undangan collaborator sudah diterima, dan `C:\Proyek\JendEdu-template` serta `C:\Proyek\JendEdu` sudah di-clone.

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
- **Browser (github.com)** = membuat PR.

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
git pull origin main
```

```bash
git switch -c feature/navbar-footer
```

### Langkah 1.2 - Salin file (cmd)

```cmd
cd C:\Proyek\JendEdu
```

```cmd
xcopy ..\JendEdu-template\css css\ /E /I /Y
```

```cmd
copy ..\JendEdu-template\img\logo.png img\
```

Kalau `img\` belum ada (PR Coder 1 belum ter-pull), jalankan `git pull origin main` di Git Bash dulu. Cek:

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

Pertama kali push akan muncul jendela login GitHub (Git Credential Manager); login lalu **Authorize**.

### Langkah 1.4 - Buat PR (Browser)

Buka https://github.com/Borayaa/JendEdu, klik **Compare & pull request**, base `main` <- compare `feature/navbar-footer`.

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

Reviewers: **@username-3** -> **Create pull request**. Kabari tim bahwa PR ini siap, karena PR halaman Coder 1 menunggu ini.

### Langkah 1.5 - Setelah di-merge (Git Bash)

```bash
git switch main
```

```bash
git pull origin main
```

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
git pull origin main
```

```bash
git switch -c feature/contact
```

### Langkah 2.2 - Salin file (cmd)

```cmd
cd C:\Proyek\JendEdu
```

```cmd
copy ..\JendEdu-template\contact.html .
```

```cmd
start contact.html
```

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

Reviewers: **@username-3** -> **Create pull request**.

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
git pull origin main
```

```bash
git switch -c feature/posts
```

### Langkah 3.2 - Salin file (cmd)

```cmd
cd C:\Proyek\JendEdu
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

Reviewers: **@username-3** -> **Create pull request**.

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
git pull origin main
```

```bash
git switch -c feature/news
```

### Langkah 4.2 - Salin file (cmd)

```cmd
cd C:\Proyek\JendEdu
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

Reviewers: **@username-3** -> **Create pull request**.

---

# Menanggapi komentar Reviewer

Label komentar:
- 🔴 **Wajib**: harus diperbaiki sebelum di-approve.
- 🟡 **Saran**: sebaiknya diperbaiki.
- 🟢 **Nit**: hal kecil, opsional.

### Contoh nyata: tautan footer salah di artikel

Reviewer menulis di `artikel-tips-belajar-matematika-sd.html`:

> 🔴 **Wajib**: Tautan footer "Berita terbaru" mengarah ke `berita-1.html`, padahal file-nya tidak ada. Seharusnya `berita-beasiswa-jendedu-2027.html`.

Langkah memperbaiki (kamu masih di branch `feature/posts`):

1. Pindah ke branch (Git Bash):

```bash
cd /c/Proyek/JendEdu
```

```bash
git switch feature/posts
```

2. Buka `C:\Proyek\JendEdu\artikel-tips-belajar-matematika-sd.html` di VS Code atau Notepad. `Ctrl + F`, cari `berita-1.html`. Ubah:

```html
<a href="berita-1.html">Beasiswa JendEdu 2027</a>
```

menjadi:

```html
<a href="berita-beasiswa-jendedu-2027.html">Beasiswa JendEdu 2027</a>
```

Karena blok footer sama di semua halaman, cari juga kesalahan yang sama di artikel lain (`artikel-belajar-online-efektif-smp.html`, `artikel-strategi-persiapan-ujian-sma.html`). Simpan dengan `Ctrl + S`.

3. Cek di browser (cmd), klik tautan footer-nya:

```cmd
start artikel-tips-belajar-matematika-sd.html
```

4. Commit dan push (Git Bash):

```bash
git status
```

```bash
git add artikel-tips-belajar-matematika-sd.html
```

```bash
git commit -m "Perbaiki sesuai review: tautan footer di artikel"
```

```bash
git push
```

Tanpa `-u` dan tanpa PR baru; PR yang sama ter-update otomatis. (Kalau kamu juga mengubah file artikel lain, tambahkan namanya di `git add`.)

5. Balas komentar di GitHub: "Sudah diperbaiki, tautan footer sekarang ke `berita-beasiswa-jendedu-2027.html`."
6. Tunggu Reviewer meng-**Approve** dan me-merge.

### Kalau komentar tentang navbar atau footer

Kamu pemilik blok ini. Misalnya Reviewer bilang menu "Harga" tidak ada di navbar halaman `contact.html`, atau gaya footer berantakan di HP:
- Perbaiki blok HTML navbar/footer di file yang dikomentari, dan pastikan blok yang sama di halaman lain (termasuk halaman Coder 1) tidak berbeda.
- Kalau masalahnya di tampilan, ubah `css\style.css`, lalu `git add css/style.css` dan commit di branch yang tepat.
- Kalau halaman yang bermasalah milik Coder 1 (misal `pricing.html`), koordinasikan dengan Coder 1 atau minta izin agar kamu yang memperbaikinya di PR terpisah, supaya tidak terjadi konflik.

### Kalau push ditolak atau konflik

- `! [rejected] ... (fetch first)`: `git pull origin <nama-branch>` lalu `git push`.
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
| `Permission denied` / `403` saat push | Undangan collaborator belum diterima atau salah akun GitHub. |
| `fatal: A branch named ... already exists` | Pakai `git switch <nama-branch>` tanpa `-c`. |
| Halaman tanpa gaya (polos) | `css` belum ada di `main`. Pastikan PR navbar-footer sudah di-merge lalu `git pull origin main`. |
| Gambar artikel/berita tidak muncul | Cek `dir img\blog` dan nama file; pastikan sudah di-`git add`. |

---

# Checklist akhir Coder 2

- [ ] `feature/navbar-footer` di-merge (folder `css` dan `img\logo.png` ada)
- [ ] `feature/contact` di-merge
- [ ] `feature/posts` di-merge (3 artikel + gambar)
- [ ] `feature/news` di-merge (3 berita + gambar)
- [ ] Navbar dan footer identik di semua halaman
- [ ] Semua komentar Reviewer sudah dibalas "Sudah diperbaiki"
- [ ] `git switch main` dan `git pull origin main` dijalankan; semua halaman terbuka normal
- [ ] Folder `panduan\` **tidak** ikut disalin ke JendEdu

---

Kembali ke [00-mulai-di-sini.md](00-mulai-di-sini.md)
