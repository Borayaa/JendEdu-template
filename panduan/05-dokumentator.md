# 05. Panduan Dokumentator (@username-4)

> **Tugas kamu**
> - Membuat PR `docs/readme`: menyalin `README.md` dan folder `presentasi\` ke repo JendEdu, mengganti semua placeholder nama dan username dengan data asli, dan melengkapi screenshot di presentasi.
> - Menjadi **pe-review dan approver** untuk PR `docs/review-log` milik Reviewer (tidak ada yang meng-approve PR-nya sendiri).
>
> **Sebelum mulai:** selesaikan [01-persiapan-semua-anggota.md](01-persiapan-semua-anggota.md) (Git terpasang, nama/email diatur, fork dibuat, template dan fork sudah di-clone ke `C:\Proyek`, remote `upstream` sudah ditambahkan).

> **⚠️ Jangan pernah `git push` ke `main`.** Hanya branch `docs/readme` yang di-push, ke fork-mu (`origin`). `main` hanya berubah lewat Pull Request yang di-merge.

Kembali ke: [00-mulai-di-sini.md](00-mulai-di-sini.md)

## Kapan giliranmu?

- Kamu bisa mulai `docs/readme` kapan saja setelah PR `chore/setup-template` ter-merge, tapi **screenshot** baru bisa diambil setelah halaman-halaman situs ter-merge ke `main`.
- Saran: siapkan README dulu, lalu isi screenshot di akhir. Bisa juga dibuat satu PR setelah situs selesai.
- Mintalah **Reviewer (@username-3)** me-review PR `docs/readme`-mu.

---

## Bagian A. PR `docs/readme`

### Langkah 1. Siapkan branch (Git Bash)

1. Buka **Git Bash** di folder `JendEdu` (klik kanan folder `C:\Proyek\JendEdu` lalu **Open Git Bash here**), atau ketik:

```
cd /c/Proyek/JendEdu
```

2. Pindah ke `main`:

```
git switch main
```

3. Ambil update terbaru dari repo tim (upstream):

```
git pull upstream main
```

Fork-mu di GitHub boleh tertinggal (`X commits behind`). Itu tidak masalah, karena branch baru selalu dibuat dari `main` lokal yang sudah di-pull dari upstream. Jangan menjalankan apa pun yang push ke `main`.

4. Buat branch baru:

```
git switch -c docs/readme
```

Hasil yang diharapkan:

```
Switched to a new branch 'docs/readme'
```

### Langkah 2. Salin README dan presentasi (Command Prompt)

1. Buka **Command Prompt** (Win+R, ketik `cmd`, Enter).
2. Pindah ke folder JendEdu:

```
cd /d C:\Proyek\JendEdu
```

3. Salin `README.md`:

```
copy ..\JendEdu-template\README.md .
```

4. Salin folder presentasi:

```
xcopy ..\JendEdu-template\presentasi presentasi\ /E /I /Y
```

Hasil yang diharapkan: tulisan seperti `2 File(s) copied`.

PENTING: Jangan menyalin folder `panduan\` ke JendEdu.

### Langkah 3. Ganti placeholder di README.md

Di README ada placeholder yang harus diganti dengan data asli:

| Placeholder | Ganti dengan |
|-------------|--------------|
| `[Nama Anggota 1]` | Nama asli Coder 1 |
| `[Nama Anggota 2]` | Nama asli Coder 2 |
| `[Nama Anggota 3]` | Nama asli Reviewer |
| `[Nama Anggota 4]` | Nama asli Dokumentator (kamu) |
| `@username-1` | Username GitHub Coder 1 |
| `@username-2` | Username GitHub Coder 2 |
| `@username-3` | Username GitHub Reviewer |
| `@username-4` | Username GitHub Dokumentator (kamu) |

Cara paling mudah memakai VS Code (atau Notepad):

1. Buka file `C:\Proyek\JendEdu\README.md`. Di VS Code: di Git Bash ketik `code README.md`. Di Notepad: klik kanan file lalu **Open with** lalu **Notepad**.
2. Di VS Code tekan **Ctrl + H** (Find and Replace). Di Notepad tekan **Ctrl + H** (Replace).
3. Ganti satu per satu: ketik `@username-1` pada kolom Find, username asli pada kolom Replace, lalu klik **Replace All**. Lakukan sama untuk `@username-2`, `@username-3`, `@username-4`.
4. Lakukan hal yang sama untuk `[Nama Anggota 1]` sampai `[Nama Anggota 4]` (sertakan tanda kurung siku saat mencari).
5. Cari juga kata `username-1` (tanpa `@`), karena ada di contoh perintah clone pada bagian "Cara Menjalankan Secara Lokal". Ganti URL itu menjadi:

```
https://github.com/Borayaa/JendEdu.git
```

6. Hapus baris catatan "*Catatan: Silakan ganti placeholder di atas...*" jika sudah tidak diperlukan.
7. Simpan dengan **Ctrl + S**.
8. Cek: tekan Ctrl + F, cari `username-` dan `[Nama`. Hasilnya harus 0 (tidak ditemukan).

### Langkah 4. Ganti placeholder di presentasi (PowerPoint)

1. Buka File Explorer ke `C:\Proyek\JendEdu\presentasi`.
2. Dobel-klik `JendEdu-Presentasi.pptx` (dan nanti juga `JendEdu-Presentasi-dengan-Naskah.pptx`) untuk membuka di PowerPoint.
3. Tekan **Ctrl + H** (Replace). Ganti `[Nama Anggota 1]` sampai `[Nama Anggota 4]` dan `@username-1` sampai `@username-4` sama seperti di README. Klik **Replace All**.
4. Simpan dengan **Ctrl + S**. Tutup PowerPoint.

Lakukan hal yang sama untuk kedua file PPTX.

### Langkah 5. Isi screenshot di presentasi (setelah situs ter-merge)

Langkah ini dikerjakan **setelah** halaman situs sudah ter-merge ke `main`.

1. Di **Git Bash**, pastikan `main` ter-update lalu kembali ke branch kamu. Karena `docs/readme` dibuat dari `main` lama, lakukan:

```
git switch main
```

```
git pull upstream main
```

```
git switch docs/readme
```

```
git merge main
```

Perintah `git merge main` menggabungkan file situs terbaru ke branch-mu agar bisa dibuka lokal. Kalau muncul editor pesan merge, simpan dan tutup (di Vim: tekan `Esc`, ketik `:wq`, Enter).

2. Di **Command Prompt**, buka situs:

```
cd /d C:\Proyek\JendEdu
```

```
start index.html
```

Browser akan membuka beranda. Buka halaman lain dengan `start about.html`, `start courses.html`, `start portfolio.html`, `start pricing.html`, dan `start contact.html`.

3. Ambil screenshot: tekan **Win + Shift + S**, seret area yang mau diambil, lalu gambar tersalin ke clipboard.
4. Di PowerPoint, klik slide yang punya placeholder screenshot, hapus gambar placeholder, lalu tekan **Ctrl + V** untuk menempel. Atur ukuran agar pas.
5. Ulangi untuk setiap slide yang butuh screenshot.
6. Simpan (**Ctrl + S**) untuk kedua file PPTX.

### Langkah 6. Commit dan push (Git Bash)

1. Cek apa saja yang berubah:

```
git status
```

Harus terlihat `README.md` dan folder `presentasi/`.

2. Tambahkan file:

```
git add README.md presentasi
```

3. Commit:

```
git commit -m "Tambah README dan presentasi proyek"
```

4. Push (terkirim ke **fork-mu**, bukan ke repo tim):

```
git push -u origin docs/readme
```

Saat push pertama, jendela login GitHub bisa muncul (Git Credential Manager). Login dan klik **Authorize**.

### Langkah 7. Buka Pull Request lintas fork (Browser)

1. Buka fork-mu: `https://github.com/<username-kamu>/JendEdu` (ganti dengan username-mu).
2. Klik tombol kuning **Compare & pull request** pada bar "docs/readme had recent pushes". Kalau bar tidak muncul: tab **Pull requests**, **New pull request**, lalu **compare across forks**.
3. **Cek empat dropdown** di bagian atas:
   - base repository: `Borayaa/JendEdu`
   - base: `main`
   - head repository: `<username-kamu>/JendEdu`
   - compare: `docs/readme`

   Kalau tertulis "There isn't anything to compare", berarti ada dropdown yang salah.
4. Judul, contoh: `Tambah README dan presentasi proyek`.
5. Deskripsi, contoh:

```
Menambahkan README.md dan folder presentasi (2 file PPTX).
Placeholder nama dan username sudah diganti dengan data asli.
Screenshot di presentasi sudah diisi.
```

6. Centang **Allow edits by maintainers**.
7. Klik **Create pull request**. Kamu diarahkan ke halaman PR di `Borayaa/JendEdu`.
8. Di panel kanan halaman PR itu, klik **Reviewers** dan pilih Reviewer (**@username-3**). Kalau tidak bisa memilih (non-kolaborator kadang tidak bisa meminta reviewer), tulis komentar `@username-3 mohon di-review ya` di PR.

### Langkah 8. Setelah itu

Kalau Reviewer memberi komentar, lihat bagian **Menanggapi komentar review** di bawah. Kalau sudah approve dan merge, lanjut ke langkah akhir (sinkron `main`).

---

> **Catatan draft dan perbaikan:** Dokumentator tidak punya file draft. "Perbaikan" setelah review untukmu adalah mengganti placeholder (nama, username, dll). Screenshot untuk PPTX harus diambil **SETELAH semua PR, termasuk perbaikannya, ter-merge**, dari `C:\Proyek\JendEdu` (bukan dari root `JendEdu-template`, karena root berisi file draft dengan kesalahan).

## Bagian B. Me-review PR `docs/review-log` milik Reviewer

Di akhir proyek, Reviewer membuat PR `docs/review-log` (folder `review\`). Karena tidak ada yang boleh meng-approve PR sendiri, **kamu yang me-review dan meng-approve** PR itu.

1. Buka https://github.com/Borayaa/JendEdu/pulls dan klik PR `docs/review-log` (tertulis "<username> wants to merge 1 commit into Borayaa:main from <username>:docs/review-log").
2. Klik tab **Files changed**.
3. Periksa bahwa:
   - Ada `review/review.md` dan folder `review/codes/`.
   - `review/codes` berisi `pricing.html`, `contact.html`, `berita-beasiswa-jendedu-2027.html`, dan `css/style.css`.
   - Isinya rapi, memakai Bahasa Indonesia, dan tidak ada tulisan placeholder yang aneh.
   - Tidak ada file yang bukan milik folder `review` (misalnya folder `panduan`).
4. Kalau ada yang perlu diperbaiki: arahkan kursor ke baris, klik tanda **+** biru, tulis komentar, klik **Start a review**. Setelah selesai klik **Review changes** (kanan atas), pilih **Request changes**, tulis ringkasan, lalu **Submit review**.
5. Kalau sudah baik: klik **Review changes**, pilih **Approve**, lalu **Submit review**. Siapa pun yang punya akun GitHub boleh memberi Approve, jadi kamu tidak perlu jadi kolaborator.
6. Setelah kamu approve, PR di-merge oleh pemilik repo (Borayaa) atau Reviewer (pembuat PR, yang punya akses Write): **Merge pull request**, lalu **Confirm merge**. Kamu sendiri tidak perlu merge. Branch di fork Reviewer dihapus oleh Reviewer sendiri.

---

## Menanggapi komentar review

Kalau Reviewer meminta perbaikan pada PR `docs/readme`:

1. Baca komentar di tab **Conversation** atau **Files changed**. Label komentar: 🔴 Wajib (harus diperbaiki), 🟡 Saran (sebaiknya diperbaiki), 🟢 Nit (hal kecil).
2. Perbaiki file di komputermu (edit README di VS Code/Notepad, atau edit PPTX di PowerPoint). Pastikan kamu masih di branch yang sama. Cek di Git Bash:

```
git status
```

3. Simpan perbaikan ke Git (Git Bash):

```
git add README.md presentasi
```

```
git commit -m "Perbaiki sesuai review"
```

```
git push
```

(Tidak perlu `-u` karena branch sudah pernah di-push. Push ini masuk ke fork-mu, dan PR di `Borayaa/JendEdu` akan **otomatis terupdate**.)

4. Kembali ke GitHub, balas setiap komentar dengan `Sudah diperbaiki`.
5. Tunggu Reviewer menekan **Approve** dan melakukan merge.

Kalau error:
- `git push` ditolak ("rejected"): jalankan `git pull origin docs/readme`, lalu `git push` lagi.
- `403` ke Borayaa/JendEdu: kamu push ke `upstream` secara tidak sengaja. Pakai `origin` (fork-mu).
- Lupa mengganti satu placeholder: perbaiki, commit lagi, push lagi.

---

## Setelah PR ter-merge: sinkronkan `main`

Di Git Bash:

```
git switch main
```

```
git pull upstream main
```

Hapus branch lokal yang sudah selesai:

```
git branch -d docs/readme
```

(Opsional) hapus juga branch di fork-mu:

```
git push origin --delete docs/readme
```

Selesai! Ingat, tidak ada `git push` ke `main`. Kalau fork-mu di GitHub tertulis "X commits behind", biarkan saja.

## Bonus: cek tampilan README di GitHub

Setelah merge, buka https://github.com/Borayaa/JendEdu. README tampil otomatis di bawah daftar file. Pastikan tabel anggota menampilkan nama dan username asli, bukan `[Nama Anggota 1]` atau `@username-1`.

## Checklist akhir Dokumentator

- [ ] Sudah menyelesaikan [01-persiapan-semua-anggota.md](01-persiapan-semua-anggota.md) (fork, clone, `git remote -v` menunjukkan `origin` dan `upstream`).
- [ ] Branch `docs/readme` dibuat dari `main` yang terbaru (`git pull upstream main`).
- [ ] `README.md` dan folder `presentasi\` tersalin (`panduan\` TIDAK ikut tersalin).
- [ ] Semua `[Nama Anggota 1..4]` dan `@username-1..4` di README.md sudah diganti.
- [ ] URL clone di README sudah memakai `https://github.com/Borayaa/JendEdu.git`.
- [ ] Placeholder nama/username di kedua PPTX juga sudah diganti.
- [ ] Screenshot di PPTX sudah diisi dengan tampilan situs asli.
- [ ] `git add`, `git commit`, `git push -u origin docs/readme` sudah dijalankan.
- [ ] PR dibuat lintas fork (base `Borayaa/JendEdu` `main` dari head `<username-kamu>/JendEdu` `docs/readme`), **Allow edits by maintainers** dicentang, dan Reviewer @username-3 dipilih.
- [ ] Semua komentar review sudah dibalas "Sudah diperbaiki" dan PR di-approve lalu di-merge.
- [ ] PR `docs/review-log` milik Reviewer sudah kamu review dan approve.
- [ ] Sudah `git switch main` dan `git pull upstream main` (tanpa push ke `main`).

Kembali ke: [00-mulai-di-sini.md](00-mulai-di-sini.md)
