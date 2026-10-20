# 01. Persiapan untuk Semua Anggota (Windows)

Kerjakan panduan ini **sekali saja**, oleh **semua anggota** (Coder 1, Coder 2, Reviewer, Dokumentator), sebelum membuka panduan peranmu.

Kembali ke: [00-mulai-di-sini.md](00-mulai-di-sini.md)

## Daftar isi

1. Buat akun GitHub
2. Fork repo tim di browser
3. Pemilik repo: tambahkan Reviewer, catatan pemilik, dan proteksi `main` (khusus Borayaa)
4. Install Git for Windows
5. Cara membuka Command Prompt dan Git Bash
6. Atur nama dan email Git
7. Buat folder kerja `C:\Proyek`
8. Clone template dan fork, lalu tambah `upstream`
9. (Opsional) Install VS Code
10. Perbedaan cmd dan Git Bash
11. Troubleshooting

---

## Istilah penting: upstream dan fork

- **Upstream** = repo tim `https://github.com/Borayaa/JendEdu`. Semua Pull Request ditujukan ke sini.
- **Fork** = salinan repo tim di akunmu sendiri: `https://github.com/<username-kamu>/JendEdu` (contoh `https://github.com/username-1/JendEdu`). Di komputermu fork ini bernama **`origin`**.
- Kamu **tidak** push ke `Borayaa/JendEdu` secara langsung. Kamu push ke fork-mu, lalu membuka Pull Request ke upstream.
- Repo template tidak di-fork. Cukup di-clone langsung dan hanya dibaca.

> **⚠️ Jangan pernah `git push` ke `main`.** Hanya branch kerja yang di-push (ke fork-mu). `main` hanya berubah lewat Pull Request yang di-merge.

## 1. Buat akun GitHub

1. Buka https://github.com di browser.
2. Klik **Sign up** dan ikuti langkahnya (email, password, username).
3. Verifikasi email-mu.
4. Catat **username** GitHub-mu. Kirim ke pemilik repo (Borayaa) dan ke teman satu tim. Khusus Reviewer: username ini dibutuhkan untuk undangan kolaborator (langkah 3).

Kalau sudah punya akun, lewati langkah ini.

## 2. Fork repo tim di browser

Dikerjakan oleh **semua anggota** (Coder 1, Coder 2, Reviewer, Dokumentator). Pemilik repo (Borayaa) tidak bisa fork repo sendiri; lihat catatan di langkah 3.

1. Login ke GitHub, lalu buka https://github.com/Borayaa/JendEdu.
2. Klik tombol **Fork** di kanan atas.
3. Di halaman **Create a new fork**: **Owner** = akunmu, **Repository name** = `JendEdu`. Biarkan **Copy the main branch only** tercentang.
4. Klik **Create fork**.

Hasilnya, kamu diarahkan ke fork-mu: `https://github.com/<username-kamu>/JendEdu` (contoh `https://github.com/username-1/JendEdu`), dengan tulisan kecil "forked from Borayaa/JendEdu" di bawah nama repo.

## 3. Pemilik repo: tambahkan Reviewer, catatan pemilik, dan proteksi `main` (khusus Borayaa)

Bagian ini hanya untuk **pemilik** repo (Borayaa). Anggota lain boleh lewati ke langkah 4.

### Tambahkan hanya Reviewer sebagai kolaborator

Coder 1, Coder 2, dan Dokumentator **tidak perlu** jadi kolaborator karena mereka bekerja lewat fork. Hanya **Reviewer** yang ditambahkan, agar bisa **Approve dan Merge** PR.

1. Buka https://github.com/Borayaa/JendEdu di browser.
2. Klik tab **Settings** (paling kanan di baris tab atas repo).
3. Di menu kiri, klik **Collaborators**. GitHub mungkin meminta password; masukkan.
4. Klik tombol hijau **Add people**.
5. Ketik username Reviewer (contoh `username-3`), pilih dari daftar, klik **Add ... to this repository**. Role-nya **Write**.
6. Reviewer menerima undangan: lewat email GitHub berjudul "Borayaa invited you to collaborate on Borayaa/JendEdu" lalu **View invitation** dan **Accept invitation**, atau buka https://github.com/Borayaa/JendEdu/invitations (sambil login).

### Catatan untuk pemilik (Borayaa)

GitHub tidak mengizinkan kamu mem-fork repomu sendiri. Kalau Borayaa juga ikut mengerjakan sebagai anggota tim:
- Clone langsung `https://github.com/Borayaa/JendEdu.git` (tanpa fork).
- **Lewati** `git remote add upstream ...`.
- Di semua alur kerja, pakai `origin` sebagai pengganti `upstream` (contoh `git pull origin main`).
- Branch-mu di-push ke repo yang sama dan PR-nya dibuat dari branch di repo yang sama.
- Borayaa juga **tidak pernah** push ke `main`; kerja di branch lalu merge lewat PR.

### Proteksi branch `main` (sangat disarankan)

1. Masih di **Settings**, klik **Branches** di menu kiri.
2. Klik **Add rule** (atau **Add branch ruleset**).
3. Branch name pattern: `main`.
4. Centang **Require a pull request before merging**, lalu **Require approvals** dengan nilai `1`.
5. Klik **Create** / **Save changes**.

Dengan aturan ini, siapa pun (termasuk pemilik) tidak bisa push langsung ke `main`.

## 4. Install Git for Windows

1. Buka https://git-scm.com/download/win di browser. Unduhan akan mulai otomatis. Kalau tidak, klik **Click here to download**, pilih **64-bit Git for Windows Setup**.
2. Buka file `.exe` yang terunduh (dobel-klik). Kalau muncul "Do you want to allow this app...", klik **Yes**.
3. Klik **Next** pada layar-layar awal. Kebanyakan pilihan **biarkan default**. Hanya perhatikan layar berikut:

| Layar installer | Pilihan yang benar |
|-----------------|--------------------|
| Select Components | Biarkan default. Pastikan **Git Bash Here** tercentang (agar bisa klik kanan folder). |
| Choosing the default editor | Boleh biarkan default (Vim). Kalau mau lebih mudah, pilih **Visual Studio Code** atau **Notepad** kalau ada di daftar. |
| Adjusting the name of the initial branch | Pilih **Override the default branch name for new repositories** dan isi `main`. |
| Adjusting your PATH environment | Pilih **Git from the command line and also from 3rd-party software** (yang tengah, biasanya sudah terpilih). Ini penting agar `git` bisa dipakai di Command Prompt juga. |
| Choosing HTTPS transport backend | Biarkan default (OpenSSL). |
| Line ending conversions | Biarkan default (Checkout Windows-style, commit Unix-style). |
| Terminal emulator | Biarkan default (MinTTY). |
| Credential Manager | Biarkan default (**Git Credential Manager**). Ini yang memunculkan jendela login GitHub saat push pertama. |

4. Klik **Install**, tunggu selesai, lalu klik **Finish**.

### Cek instalasi

Buka **Command Prompt** (lihat langkah 5), lalu ketik:

```
git --version
```

Hasil yang diharapkan (angka versi bisa berbeda):

```
git version 2.46.0.windows.1
```

Lalu buka **Git Bash** dan ketik perintah yang sama:

```
git --version
```

Kalau keduanya menampilkan versi, instalasi berhasil.

## 5. Cara membuka Command Prompt dan Git Bash

### Command Prompt (cmd)

1. Tekan tombol **Windows + R** bersamaan.
2. Ketik `cmd`, lalu tekan **Enter**.
3. Jendela hitam terbuka dengan teks seperti `C:\Users\NamaKamu>`.

### Git Bash

Cara 1 (dari Start menu):
1. Klik tombol **Start** di Windows.
2. Ketik `Git Bash`.
3. Klik **Git Bash** pada hasil pencarian.

Cara 2 (dari folder, paling praktis):
1. Buka **File Explorer** dan masuk ke folder tujuan, misalnya `C:\Proyek\JendEdu`.
2. Klik kanan di area kosong dalam folder.
3. Pilih **Show more options** (Windows 11) lalu **Open Git Bash here**. Di Windows 10 langsung terlihat **Git Bash Here**.

Dengan cara 2, Git Bash otomatis berada di folder tersebut.

## 6. Atur nama dan email Git

Git perlu tahu siapa kamu agar commit-mu ada namanya. Lakukan **sekali saja** di **Git Bash**.

1. Buka **Git Bash**.
2. Ketik perintah berikut (ganti dengan nama aslimu, pakai tanda kutip):

```
git config --global user.name "Nama Kamu"
```

3. Ketik perintah berikut dengan **email yang sama dengan akun GitHub-mu**:

```
git config --global user.email "emailkamu@contoh.com"
```

4. Cek hasilnya:

```
git config --global --list
```

Hasil yang diharapkan mengandung:

```
user.name=Nama Kamu
user.email=emailkamu@contoh.com
```

Kalau salah ketik, ulangi perintah yang sama dengan nilai yang benar.

## 7. Buat folder kerja `C:\Proyek`

Di **Command Prompt**:

```
mkdir C:\Proyek
```

Kalau muncul "A subdirectory or file C:\Proyek already exists", artinya folder sudah ada. Tidak masalah, lanjut.

Pindah ke folder itu:

```
cd /d C:\Proyek
```

(`/d` dipakai agar bisa pindah drive jika kamu sedang di drive lain.)

## 8. Clone template dan fork, lalu tambah `upstream`

Pastikan kamu sudah mem-fork repo (langkah 2). Di **Git Bash**:

1. Pindah ke folder kerja:

```
cd /c/Proyek
```

2. Clone repo template (sumber file, hanya dibaca):

```
git clone https://github.com/Borayaa/JendEdu-template.git
```

3. Clone **fork-mu** (ganti `<username-kamu>` dengan username GitHub-mu, contoh `username-1`):

```
git clone https://github.com/<username-kamu>/JendEdu.git
```

4. Masuk ke folder JendEdu:

```
cd JendEdu
```

5. Tambahkan repo tim sebagai `upstream`:

```
git remote add upstream https://github.com/Borayaa/JendEdu.git
```

6. Cek daftar remote:

```
git remote -v
```

Hasil yang diharapkan (contoh untuk `username-1`):

```
origin    https://github.com/username-1/JendEdu.git (fetch)
origin    https://github.com/username-1/JendEdu.git (push)
upstream  https://github.com/Borayaa/JendEdu.git (fetch)
upstream  https://github.com/Borayaa/JendEdu.git (push)
```

`origin` harus mengarah ke **fork-mu**, `upstream` ke **Borayaa/JendEdu**. (Pemilik repo: lihat catatan di langkah 3.)

7. Kembali ke `C:\Proyek` dan cek isinya:

```
cd ..
```

```
ls
```

Harus terlihat dua folder:

```
JendEdu  JendEdu-template
```

Sekarang struktur di komputermu:

```
C:\Proyek\
    JendEdu-template\     (sumber file, jangan diubah)
    JendEdu\              (clone dari fork-mu, tempat kamu bekerja)
```

Kedua folder harus **bersebelahan** seperti ini, karena perintah `copy` di panduan memakai `..\JendEdu-template`.

PENTING: Jangan pernah mengedit atau `push` dari folder `JendEdu-template`.

Catatan: beberapa file di root `JendEdu-template` (`pricing.html`, `contact.html`, `berita-beasiswa-jendedu-2027.html`, `css\style.css`) sengaja berupa draft dengan kesalahan untuk latihan code review. Penjelasan lengkap ada di bagian "Draft vs versi perbaikan" di [00-mulai-di-sini.md](00-mulai-di-sini.md).

Fork-mu di GitHub boleh tertinggal (`X commits behind`). Itu tidak masalah, karena branch baru selalu dibuat dari `main` lokal yang sudah di-pull dari upstream. Jangan klik atau jalankan apa pun yang push ke `main`.

## 9. (Opsional) Install Visual Studio Code

VS Code adalah editor teks yang nyaman untuk membuka dan mengedit file HTML.

1. Buka https://code.visualstudio.com dan klik **Download for Windows**.
2. Jalankan installer. Centang **Add to PATH** dan **Add "Open with Code" action** (opsi klik kanan) kalau ada.
3. Setelah terpasang, buka folder proyek dari Git Bash:

```
cd /c/Proyek/JendEdu
code .
```

Tanpa VS Code, kamu tetap bisa mengedit file memakai Notepad.

## 10. Perbedaan cmd dan Git Bash

Keduanya jendela hitam, tapi cara menulis alamat folder berbeda:

| Hal | Command Prompt (cmd) | Git Bash |
|-----|----------------------|----------|
| Contoh alamat folder | `C:\Proyek\JendEdu` | `/c/Proyek/JendEdu` |
| Pemisah folder | `\` (backslash) | `/` (slash) |
| Pindah folder | `cd /d C:\Proyek\JendEdu` | `cd /c/Proyek/JendEdu` |
| Lihat isi folder | `dir` | `ls` |
| Pakai untuk | membuat folder, `copy`/`xcopy`/`robocopy`, `start` | semua perintah `git` |

Aturan sederhana untuk panduan ini:
- Perintah yang diawali `git` dijalankan di **Git Bash**.
- Perintah `copy`, `xcopy`, `robocopy`, `mkdir`, `start` dijalankan di **Command Prompt**.
- Kalau tidak yakin lagi ada di folder mana, ketik `pwd` di Git Bash atau `cd` (tanpa apa-apa) di cmd.

Tip: kamu bisa membiarkan dua jendela terbuka sekaligus, satu cmd dan satu Git Bash, keduanya di folder `JendEdu`.

Tip menempel (paste): di Git Bash gunakan **Shift + Insert** atau klik kanan lalu Paste. Di cmd, klik kanan atau **Ctrl + V**.

## 11. Troubleshooting

**`git` is not recognized as an internal or external command (di cmd)**
- Tutup semua jendela cmd lalu buka lagi (PATH baru terbaca setelah dibuka ulang).
- Kalau masih gagal, jalankan ulang installer Git dan pada layar "Adjusting your PATH environment" pilih **Git from the command line and also from 3rd-party software**.

**`git: command not found` di Git Bash**
- Berarti Git belum terpasang benar. Pasang ulang (langkah 4).

**`fatal: not a git repository`**
- Kamu berada di folder yang salah. Pindah dulu: `cd /c/Proyek/JendEdu` (Git Bash).

**Saat clone muncul `fatal: destination path 'JendEdu' already exists`**
- Folder sudah pernah di-clone. Tidak perlu clone lagi. Cek dengan `ls`.

**`remote: Permission to Borayaa/JendEdu.git denied` / `403` saat push**
- Kamu tidak sengaja push ke `upstream` (repo tim). Push selalu ke `origin` (fork-mu), contoh `git push -u origin feature/<nama-fitur>`. Cek dengan `git remote -v`.

**`fatal: 'upstream' does not appear to be a git repository`**
- Remote `upstream` belum ditambahkan. Di Git Bash, di folder `/c/Proyek/JendEdu`, jalankan:

```
git remote add upstream https://github.com/Borayaa/JendEdu.git
```

**Di GitHub muncul "There isn't anything to compare"**
- Dropdown base/head di halaman Pull Request salah. Pastikan: `base repository: Borayaa/JendEdu`, `base: main`, `head repository: <username-kamu>/JendEdu`, `compare: feature/<nama-fitur>`.

**Fork-mu tertulis "X commits behind"**
- Tidak masalah dan tidak perlu disamakan. Cukup jalankan `git switch main` lalu `git pull upstream main` sebelum membuat branch baru. Jangan push ke `main`.

**Jendela login GitHub muncul saat push pertama**
- Itu normal (Git Credential Manager). Klik **Sign in with your browser**, login ke GitHub, lalu klik **Authorize**. Selanjutnya tidak ditanya lagi.

**`Author identity unknown` / `Please tell me who you are` saat commit**
- Kamu belum mengatur nama dan email. Kerjakan langkah 6.

**Muncul editor aneh (Vim) setelah `git commit`**
- Kamu lupa menulis pesan dengan `-m`. Untuk keluar dari Vim: tekan `Esc`, ketik `:q!`, lalu Enter. Ulangi commit dengan format `git commit -m "pesan"`.

**Karakter `\` atau spasi bikin error di Git Bash**
- Di Git Bash pakai `/` (contoh `/c/Proyek/JendEdu`). Kalau ada spasi di nama folder, apit alamat dengan tanda kutip.

**Lupa sedang di branch mana**
- Di Git Bash, ketik `git status`. Baris pertama menunjukkan nama branch.

---

Setelah semua selesai, lanjut ke panduan perananmu:

- Coder 1: [02-coder-1.md](02-coder-1.md)
- Coder 2: [03-coder-2.md](03-coder-2.md)
- Reviewer: [04-reviewer.md](04-reviewer.md)
- Dokumentator: [05-dokumentator.md](05-dokumentator.md)

Kembali ke: [00-mulai-di-sini.md](00-mulai-di-sini.md)
