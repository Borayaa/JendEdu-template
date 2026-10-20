# 01. Persiapan untuk Semua Anggota (Windows)

Kerjakan panduan ini **sekali saja**, oleh **semua anggota** (Coder 1, Coder 2, Reviewer, Dokumentator), sebelum membuka panduan peranmu.

Kembali ke: [00-mulai-di-sini.md](00-mulai-di-sini.md)

## Daftar isi

1. Buat akun GitHub
2. Pemilik repo menambahkan anggota (khusus Borayaa)
3. Terima undangan kolaborator
4. Install Git for Windows
5. Cara membuka Command Prompt dan Git Bash
6. Atur nama dan email Git
7. Buat folder kerja `C:\Proyek`
8. Clone kedua repo
9. (Opsional) Install VS Code
10. Perbedaan cmd dan Git Bash
11. Troubleshooting

---

## 1. Buat akun GitHub

1. Buka https://github.com di browser.
2. Klik **Sign up** dan ikuti langkahnya (email, password, username).
3. Verifikasi email-mu.
4. Catat **username** GitHub-mu, lalu kirim ke pemilik repo (Borayaa) untuk ditambahkan sebagai kolaborator.

Kalau sudah punya akun, lewati langkah ini.

## 2. Pemilik repo menambahkan anggota (khusus Borayaa)

Bagian ini hanya untuk **pemilik** repo (Borayaa). Anggota lain boleh lewati ke langkah 3.

1. Buka https://github.com/Borayaa/JendEdu di browser.
2. Klik tab **Settings** (paling kanan di baris tab atas repo).
3. Di menu kiri, klik **Collaborators**. GitHub mungkin meminta password; masukkan.
4. Klik tombol hijau **Add people**.
5. Ketik username anggota (contoh `username-1`), pilih dari daftar, klik **Add ... to this repository**. Role-nya **Write**.
6. Ulangi untuk ketiga anggota lain, yaitu `username-2`, `username-3`, dan `username-4`. Tulis satu per satu dan ganti dengan username asli.

Saran tambahan (aman diaktifkan agar `main` terlindungi):
1. Masih di **Settings**, klik **Branches** di menu kiri.
2. Klik **Add rule** (atau **Add branch ruleset**).
3. Branch name pattern: `main`.
4. Centang **Require a pull request before merging**, lalu **Require approvals** dengan nilai `1`.
5. Klik **Create** / **Save changes**.

## 3. Terima undangan kolaborator

Sebelum bisa `push`, kamu **harus menerima undangan** dulu.

1. Buka email yang kamu pakai untuk GitHub. Cari email dari GitHub berjudul seperti "Borayaa invited you to collaborate on Borayaa/JendEdu".
2. Klik tombol **View invitation**, lalu klik **Accept invitation**.
3. Alternatif kalau email tidak ketemu: buka https://github.com/Borayaa/JendEdu/invitations (sambil login), atau klik ikon lonceng notifikasi di GitHub.

Kalau undangan tidak muncul, minta Borayaa mengecek kembali username-mu di **Settings > Collaborators**.

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

## 8. Clone kedua repo

Di **Git Bash**:

1. Pindah ke folder kerja:

```
cd /c/Proyek
```

2. Clone repo template (sumber file, hanya dibaca):

```
git clone https://github.com/Borayaa/JendEdu-template.git
```

3. Clone repo tempat tim bekerja:

```
git clone https://github.com/Borayaa/JendEdu.git
```

Hasil yang diharapkan (contoh):

```
Cloning into 'JendEdu'...
remote: Enumerating objects: ...
Receiving objects: 100% (...), done.
```

4. Cek isinya:

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
    JendEdu\              (tempat kamu bekerja)
```

Kedua folder harus **bersebelahan** seperti ini, karena perintah `copy` di panduan memakai `..\JendEdu-template`.

PENTING: Jangan pernah mengedit atau `push` dari folder `JendEdu-template`.

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
- Kamu belum menerima undangan kolaborator (langkah 3), atau belum ditambahkan oleh Borayaa. Cek https://github.com/Borayaa/JendEdu/invitations.

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
