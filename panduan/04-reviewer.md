# Panduan Reviewer (@username-3)

> **Tugas kamu**
> - Memeriksa (review) semua Pull Request (PR) dari Coder 1, Coder 2, dan Dokumentator sebelum masuk ke `main`.
> - Menguji kode di komputermu sendiri, menulis komentar per baris dengan label, lalu memilih **Request changes**, **Comment**, atau **Approve**.
> - Meng-**merge** PR yang sudah beres, menghapus branch-nya, dan memperbarui `main` lokal.
> - Di akhir proyek, membuat PR `docs/review-log` berisi folder `review\` (PR ini di-approve oleh Dokumentator).

**Sebelum mulai:** selesaikan [01-persiapan-semua-anggota.md](01-persiapan-semua-anggota.md) (Git terpasang, sudah clone `JendEdu-template` dan `JendEdu` ke `C:\Proyek`, sudah menerima undangan collaborator).

Aplikasi yang dipakai:

| Aplikasi | Untuk apa |
|----------|-----------|
| **Browser (github.com)** | Membuka PR, membaca "Files changed", komentar, Approve, Merge |
| **Git Bash** | Semua perintah `git` (fetch, switch, pull) |
| **Command Prompt (cmd)** | Membuka situs (`start index.html`) dan menyalin folder `review\` |

---

## Daftar isi

1. [Mencari PR yang harus kamu review](#1-mencari-pr-yang-harus-kamu-review)
2. [Urutan review yang disarankan](#2-urutan-review-yang-disarankan)
3. [Membaca tab "Files changed"](#3-membaca-tab-files-changed)
4. [Mengetes branch di komputermu](#4-mengetes-branch-di-komputermu)
5. [Menulis komentar per baris](#5-menulis-komentar-per-baris)
6. [Request changes, Comment, atau Approve?](#6-request-changes-comment-atau-approve)
7. [Memeriksa ulang setelah author memperbaiki](#7-memeriksa-ulang-setelah-author-memperbaiki)
8. [Resolve, Approve, Merge, hapus branch](#8-resolve-approve-merge-hapus-branch)
9. [Update `main` lokal](#9-update-main-lokal)
10. [Rekomendasi branch protection (untuk owner)](#10-rekomendasi-branch-protection-untuk-owner)
11. [PR `docs/review-log` milikmu sendiri](#11-pr-docsreview-log-milikmu-sendiri)
12. [Checklist review](#12-checklist-review)
13. [Bonus: GitHub CLI](#13-bonus-github-cli)
14. [Kalau error](#14-kalau-error)

---

## 1. Mencari PR yang harus kamu review

Author akan memilih kamu di kolom **Reviewers** saat membuat PR. Cara menemukannya:

1. Buka browser, masuk ke https://github.com/Borayaa/JendEdu
2. Klik tab **Pull requests**.
3. Daftar semua PR yang terbuka (status **Open**) muncul di sini. Klik judul PR untuk membukanya.

Cara cepat memfilter hanya PR yang menunggu kamu:

1. Di kotak pencarian di atas daftar PR, hapus isinya lalu ketik:

```
is:pr is:open review-requested:@me
```

2. Tekan Enter. Hanya PR yang meminta review darimu yang tampil.

Cara lain: klik ikon lonceng (notifikasi) di kanan atas GitHub, atau buka https://github.com/pulls/review-requested

> Kalau tidak ada PR yang muncul, mungkin author lupa memilih Reviewer. Buka PR-nya, lihat kolom **Reviewers** di kanan, klik ikon roda gigi, lalu pilih dirimu sendiri.

---

## 2. Urutan review yang disarankan

PR **harus** di-merge berurutan karena sebagian bergantung pada yang lain. Review dan merge dengan urutan ini:

```
1. chore/setup-template   (Coder 1)  <-- PERTAMA, semua menunggu ini
        |
        v
2. feature/navbar-footer  (Coder 2)  <-- CSS + logo
        |
        v
3. Halaman Coder 1                 4. Halaman Coder 2 (paralel dengan #3)
   feature/homepage                    feature/contact
   feature/about                       feature/posts
   feature/courses                     feature/news
   feature/gallery
   feature/pricing
        |                                   |
        +-----------------+-----------------+
                          v
5. docs/readme            (Dokumentator)
                          |
                          v
6. docs/review-log        (kamu, di-approve Dokumentator)
```

Aturan praktis:

1. **`chore/setup-template`** dulu. Kalau ini belum di-merge, jangan merge PR lain.
2. **`feature/navbar-footer`** kedua, karena semua halaman memakai CSS dan logo dari sini.
3. Setelah #1 dan #2 ter-merge, PR halaman dari Coder 1 dan Coder 2 boleh kamu review kapan saja (urutan antar halaman bebas).
4. **`docs/readme`** sebaiknya terakhir di antara PR kode, supaya screenshot di presentasi diambil dari situs yang sudah jadi.
5. **`docs/review-log`** milikmu paling akhir.

---

## 3. Membaca tab "Files changed"

1. Buka PR-nya, lalu klik tab **Files changed** (di sebelah **Conversation** dan **Commits**).
2. Di kiri ada daftar berkas yang berubah. Klik nama berkas untuk melompat ke sana.
3. Cara membaca warna:
   - Baris **hijau** dengan tanda `+` = baris baru yang ditambahkan.
   - Baris **merah** dengan tanda `-` = baris yang dihapus.
   - Baris putih = tidak berubah (konteks).
4. Untuk berkas yang sangat panjang (misalnya `index.html`), klik ikon tiga titik atau panah kecil untuk membuka bagian yang tersembunyi.
5. Gambar (`.jpg`, `.png`) tidak tampil sebagai teks. Cukup pastikan berkasnya ada dan namanya sesuai yang dipakai di HTML.
6. Gunakan kotak centang **Viewed** di kanan atas tiap berkas untuk menandai berkas yang sudah selesai kamu baca.

Perhatikan juga di tab **Conversation** apakah ada tulisan hijau "This branch has no conflicts with the base branch". Kalau ada "conflicts", minta author menyelesaikannya dulu.

---

## 4. Mengetes branch di komputermu

Membaca kode saja tidak cukup. Jalankan situsnya.

### Langkah 1: ambil branch dari GitHub (Git Bash)

1. Buka **Git Bash** (klik kanan folder `C:\Proyek\JendEdu` > **Open Git Bash here**, atau lewat menu Start).
2. Kalau belum di folder yang benar:

```
cd /c/Proyek/JendEdu
```

3. Ambil info branch terbaru dari GitHub:

```
git fetch origin
```

4. Pindah ke branch yang sedang direview. Contoh untuk `feature/navbar-footer`:

```
git switch feature/navbar-footer
```

Hasil yang diharapkan:

```
branch 'feature/navbar-footer' set up to track 'origin/feature/navbar-footer'.
Switched to a new branch 'feature/navbar-footer'
```

5. Pastikan isinya yang terbaru (penting kalau author baru push perbaikan):

```
git pull origin feature/navbar-footer
```

> Ganti `feature/navbar-footer` dengan nama branch PR yang kamu review. Nama branch tertulis di bagian atas halaman PR.

### Langkah 2: buka situs (Command Prompt)

1. Buka **Command Prompt**: tekan **Win+R**, ketik `cmd`, Enter.
2. Masuk ke folder proyek:

```
cd C:\Proyek\JendEdu
```

3. Buka halaman yang direview. Contoh beranda:

```
start index.html
```

Halaman lain:

```
start about.html
```

```
start courses.html
```

```
start portfolio.html
```

```
start pricing.html
```

```
start contact.html
```

Untuk artikel dan berita, ketik nama berkasnya sesuai yang ada di folder (lihat dengan `dir artikel-*.html` dan `dir berita-*.html`):

```
dir artikel-*.html
```

```
start artikel-nama-berkas.html
```

### Langkah 3: tes responsif di browser

1. Di halaman yang terbuka, tekan **F12** (atau **Ctrl+Shift+I**) untuk membuka DevTools.
2. Tekan **Ctrl+Shift+M** untuk mode perangkat (device toolbar).
3. Pilih ukuran ponsel (misalnya iPhone SE), tablet, lalu desktop. Pastikan menu berubah jadi tombol dan tidak ada tampilan yang terpotong.

### Langkah 4: kembali ke `main` setelah selesai

```
git switch main
```

### Pengecualian: PR #1 (`chore/setup-template`)

PR ini hanya berisi aset (js, fonts, img), belum ada halaman baru. Cukup cek dengan `dir js`, `dir fonts`, `dir img` di cmd bahwa folder-nya terisi, dan di tab Files changed pastikan **tidak ada** `logo.png` dan folder `img\blog` (itu masuk PR lain).

---

## 5. Menulis komentar per baris

### Cara menulis komentar

1. Di tab **Files changed**, arahkan kursor ke nomor baris yang bermasalah. Muncul tombol **+** biru.
2. Klik **+** lalu tulis komentarmu di kotak yang muncul.
3. Untuk komentar yang mencakup beberapa baris: klik dan seret dari **+** baris pertama sampai baris terakhir.
4. Klik **Start a review** (bukan "Add single comment"). Dengan "Start a review", semua komentarmu dikumpulkan dulu dan baru dikirim bersamaan saat kamu submit. Author tidak kebanjiran notifikasi.
5. Komentar berikutnya akan menampilkan tombol **Add review comment**. Klik itu untuk menambah komentar.

### Label komentar

Awali setiap komentar dengan label supaya author tahu mana yang wajib:

| Label | Arti | Perlu diperbaiki sebelum approve? |
|-------|------|-----------------------------------|
| 🔴 **Wajib** | Bug, tautan rusak, teks Inggris, lorem ipsum, tag tidak tertutup | Ya |
| 🟡 **Saran** | Perbaikan yang bagus tapi tidak merusak, misalnya aksesibilitas | Sebaiknya |
| 🟢 **Nit** | Hal kecil/selera, opsional | Tidak |

### Memakai "Insert a suggestion"

Kalau perbaikannya jelas, tulis sebagai saran kode supaya author cukup klik satu tombol:

1. Di kotak komentar, klik ikon **Insert a suggestion** (ikon `±` di toolbar, di sebelah ikon tebal/miring).
2. GitHub otomatis menyisipkan blok seperti ini berisi baris asli:

````
```suggestion
isi baris asli
```
````

3. Ubah isi di dalam blok menjadi versi yang benar. Tulis penjelasan di atasnya.
4. Author akan melihat tombol **Commit suggestion** di komentarmu. Satu klik dan perbaikan masuk.

### Tiga contoh komentar siap pakai

**Contoh 1: 🔴 Wajib (tautan rusak)**, diletakkan pada baris `<a href="kontak.html">Kontak</a>`:

````
🔴 **Wajib.** Tautan rusak: nama berkasnya `contact.html`, bukan `kontak.html`. Klik ini akan menghasilkan halaman 404.

```suggestion
<a href="contact.html">Kontak</a>
```
````

**Contoh 2: 🟡 Saran (aksesibilitas)**, diletakkan pada baris `<img src="img/logo.png">`:

````
🟡 **Saran.** Gambar logo belum punya atribut `alt`. Tambahkan supaya terbaca oleh screen reader dan lebih baik untuk SEO.

```suggestion
<img src="img/logo.png" alt="JendEdu">
```
````

**Contoh 3: 🟢 Nit (hal kecil)**, diletakkan pada baris `<h5 class="widgetheading">Our Contact</h5>` atau spasi berlebih:

````
🟢 **Nit.** Opsional: judul widget ini masih bahasa Inggris. Kalau mau konsisten dengan halaman lain, ganti menjadi "Hubungi Kami". Tidak menghalangi approve.
````

> Tips menulis komentar: sebut masalahnya, alasannya, lalu solusinya. Gunakan bahasa yang sopan dan fokus ke kode, bukan ke orangnya. Contoh baik: "Harga di sini Rp 99000, di Beranda Rp99.000 / bulan. Mohon disamakan."

---

## 6. Request changes, Comment, atau Approve?

Setelah selesai membaca dan mengumpulkan komentar:

1. Klik tombol hijau **Review changes** di kanan atas tab Files changed.
2. Tulis ringkasan di kotak teks, misalnya:

````
Terima kasih, sudah rapi. Ada 3 hal 🔴 yang perlu diperbaiki:

- [ ] Tautan kontak.html -> contact.html
- [ ] Hapus teks Lorem ipsum di bagian persyaratan
- [ ] Samakan format harga menjadi Rp99.000 / bulan

Poin 🟡 dan 🟢 opsional. Kabari kalau sudah diperbaiki ya.
````

3. Pilih salah satu dari tiga pilihan, lalu klik **Submit review**.

| Pilihan | Kapan dipakai | Efek |
|---------|---------------|------|
| **Comment** | Hanya memberi masukan/pertanyaan umum, belum memutuskan | Tidak menyetujui, tidak memblokir |
| **Approve** | Semua poin 🔴 sudah beres, kode siap masuk `main` | PR boleh di-merge |
| **Request changes** | Ada minimal satu poin 🔴 | Menandai PR "belum boleh merge" sampai kamu approve |

Aturan sederhana: **ada 🔴 = Request changes. Tidak ada 🔴 = Approve.** Pakai Comment kalau kamu cuma bertanya dan menunggu jawaban.

---

## 7. Memeriksa ulang setelah author memperbaiki

1. Author memperbaiki, melakukan commit dan push ke branch yang sama, lalu membalas komentarmu dengan "Sudah diperbaiki". PR otomatis ter-update, tidak perlu PR baru.
2. Kamu akan dapat notifikasi. Buka PR-nya.
3. Di tab **Files changed**, klik menu **Changes from** (dropdown dekat atas) lalu pilih **Changes since your last review** supaya hanya melihat yang baru.
4. Tarik kode terbaru ke komputermu (Git Bash):

```
cd /c/Proyek/JendEdu
```

```
git switch feature/navbar-footer
```

```
git pull origin feature/navbar-footer
```

5. Jalankan lagi di cmd (`start index.html` dll.) dan cek ulang semua poin 🔴 dari review sebelumnya.
6. Kalau masih ada yang kurang, balas di komentar yang sama, atau tulis komentar baru, lalu submit **Request changes** lagi.
7. Kalau sudah beres, lanjut ke bagian 8.

> Kalau yang diminta adalah perbaikan navbar/footer, itu tugas **Coder 2** walaupun ditemukan di halaman milik Coder 1. Tulis di komentar dan mention `@username-2`.

---

## 8. Resolve, Approve, Merge, hapus branch

### Langkah 1: resolve conversation

Untuk setiap komentar yang sudah diperbaiki dengan benar:

1. Buka tab **Conversation** atau **Files changed**.
2. Pada thread komentarnya, klik **Resolve conversation**.
3. Thread yang belum beres biarkan terbuka, dan jangan approve dulu.

### Langkah 2: approve

1. Klik **Review changes** (tombol hijau kanan atas).
2. Tulis pesan singkat, contoh: `Semua poin sudah diperbaiki, mantap! LGTM.` (LGTM = "Looks Good To Me").
3. Pilih **Approve**.
4. Klik **Submit review**.

### Langkah 3: merge

1. Kembali ke tab **Conversation**, gulir ke bawah sampai kotak hijau "This branch has no conflicts".
2. Klik tombol hijau **Merge pull request**.

   Tombol ini punya panah kecil di sebelahnya dengan tiga pilihan. Untuk proyek ini **pakai yang default: "Create a merge commit"**. Ini paling sederhana dan riwayat commit setiap anggota tetap terlihat (bagus untuk penilaian kontribusi). Dua pilihan lain (**Squash and merge** dan **Rebase and merge**) tidak perlu dipakai.

3. Klik **Confirm merge**.
4. Muncul tulisan ungu "Pull request successfully merged and closed".

### Langkah 4: hapus branch

1. Setelah merge, klik tombol **Delete branch** yang muncul di kotak ungu tadi.
2. Aman dilakukan: kodenya sudah ada di `main`, hanya "label" branch-nya yang dihapus.

Ulangi untuk PR berikutnya sesuai [urutan di bagian 2](#2-urutan-review-yang-disarankan).

> Setelah PR #1 atau #2 ter-merge, kabari author PR lain lewat grup bahwa mereka bisa mulai mengerjakan atau membuat PR (dan jika perlu menjalankan `git switch main` + `git pull origin main`).

---

## 9. Update `main` lokal

Setiap habis merge, perbarui `main` di komputermu supaya tidak ketinggalan. Di **Git Bash**:

```
cd /c/Proyek/JendEdu
```

```
git switch main
```

```
git pull origin main
```

Hasil yang diharapkan (contoh):

```
Updating 3f2a1b0..9c8d7e6
Fast-forward
 css/style.css | 120 +++++++++++++
 1 file changed, 120 insertions(+)
```

Opsional: hapus branch lokal yang sudah ter-merge supaya daftar tidak penuh:

```
git branch -d feature/navbar-footer
```

---

## 10. Rekomendasi branch protection (untuk owner)

Minta owner repo (**Borayaa**) mengaktifkan perlindungan `main` supaya tidak ada yang bisa push langsung atau merge tanpa review:

1. Buka https://github.com/Borayaa/JendEdu
2. **Settings** > **Branches** (menu kiri).
3. Klik **Add rule** (atau **Add branch protection rule**).
4. **Branch name pattern:** ketik `main`
5. Centang **Require a pull request before merging**.
6. Centang **Require approvals** dan isi jumlahnya **1**.
7. Klik **Create** / **Save changes**.

Dengan ini, PR tidak bisa di-merge tanpa satu Approve, dan `main` tetap bersih.

> Kalau repo privat di paket gratis, fitur ini bisa tidak tersedia. Dalam kasus itu, kesepakatan tim saja: **tidak ada yang push langsung ke `main`**.

---

## 11. PR `docs/review-log` milikmu sendiri

Di akhir, kamu mengumpulkan catatan review (folder `review\`) ke repo. Karena tidak boleh meng-approve PR sendiri, PR ini di-review dan di-approve oleh **Dokumentator** (@username-4).

**Syarat:** semua PR lain sudah ter-merge (atau minimal sudah selesai direview), dan `main` lokal sudah terbaru (bagian 9).

### Langkah 1: buat branch (Git Bash)

```
cd /c/Proyek/JendEdu
```

```
git switch main
```

```
git pull origin main
```

```
git switch -c docs/review-log
```

### Langkah 2: salin folder review (Command Prompt)

```
cd C:\Proyek\JendEdu
```

```
xcopy ..\JendEdu-template\review review\ /E /I /Y
```

Hasil yang diharapkan: daftar berkas yang disalin dan baris `N File(s) copied`.

Lalu edit `review\review.md` di VS Code atau Notepad:

1. Ganti status PR dan tanggal sesuai kenyataan.
2. Pastikan `@username-3` sudah menjadi username GitHub aslimu, dan username author lain juga diganti dengan yang asli.
3. Sesuaikan isi dengan review yang benar-benar kamu lakukan (nomor PR, komentar, keputusan).

> Jangan menyalin folder `panduan\` ke JendEdu.

### Langkah 3: commit dan push (Git Bash)

```
git status
```

```
git add review
```

```
git commit -m "Tambah log review pull request"
```

```
git push -u origin docs/review-log
```

> Push pertama kali bisa membuka jendela login GitHub di browser (Git Credential Manager). Login dan klik authorize.

### Langkah 4: buka PR (Browser)

1. Buka https://github.com/Borayaa/JendEdu
2. Klik tombol kuning **Compare & pull request**.
3. Pastikan **base: `main`** dan **compare: `docs/review-log`**.
4. Isi judul: `Tambah log review pull request`. Isi deskripsi singkat tentang isi `review\`.
5. Di kolom **Reviewers** pilih **Dokumentator (@username-4)**.
6. Klik **Create pull request**.

### Langkah 5: tunggu review, lalu merge

1. Dokumentator meninjau dan memberi komentar/Approve.
2. Kalau ada komentar, perbaiki berkasnya, lalu di Git Bash:

```
git add review
```

```
git commit -m "Perbaiki sesuai review"
```

```
git push
```

3. Balas komentar dengan "Sudah diperbaiki", dan tunggu **Approve** dari Dokumentator.
4. Setelah di-approve, klik **Merge pull request** > **Confirm merge** > **Delete branch**.
5. Terakhir `git switch main` dan `git pull origin main` (bagian 9).

---

## 12. Checklist review

Salin daftar ini ke kotak komentar review kalau perlu. Centang satu per satu untuk **setiap** PR.

### Isi dan bahasa

- [ ] Seluruh teks dalam **Bahasa Indonesia** (tidak ada "Get Now", "Submit", "Back to Home", "Our Contact")
- [ ] Tidak ada **Lorem ipsum** atau teks placeholder lain
- [ ] Harga konsisten di semua halaman: **Rp99.000 / Rp129.000 / Rp159.000 / Rp249.000 per bulan** (format `Rp99.000 / bulan`)
- [ ] Tidak ada typo yang mencolok

### Tautan dan gambar

- [ ] Semua **tautan berfungsi** (tidak ada `href="#"`, nama berkas benar, ekstensi `.html` bukan `.htm`)
- [ ] Semua gambar **tampil** (path benar, berkas ada di `img\` atau `img\blog\`)
- [ ] Semua `<img>` punya **`alt`** yang bermakna
- [ ] Tautan `target="_blank"` disertai `rel="noopener"`
- [ ] Sumber eksternal memakai `https://`, bukan `http://`

### Struktur dan kode

- [ ] Hanya **satu** item navbar yang `active`, sesuai halaman yang dibuka
- [ ] Navbar dan footer **sama** di semua halaman
- [ ] Tag HTML tertutup dan cocok (contoh salah: `<h1>...</h2>`, `<section>` tidak ditutup)
- [ ] Tidak ada `id` ganda
- [ ] Tidak ada inline style dan `<br><br>` untuk spacing, gunakan CSS

### Tampilan

- [ ] Tampilan **responsif**: cek ponsel, tablet, desktop (**Ctrl+Shift+M** di DevTools)
- [ ] Tidak ada tampilan terpotong atau menumpuk

### Hal khusus per PR

- [ ] PR #1: folder `js`, `fonts`, `img` ada; `logo.png` dan `img\blog` **tidak** ikut
- [ ] PR #2: folder `css` lengkap dan `img\logo.png` ada
- [ ] PR halaman: hanya berkas halaman itu yang berubah (tidak ada berkas nyasar, tidak ada folder `panduan\`)
- [ ] PR docs: placeholder `[Nama Anggota 1..4]` dan `@username-1..4` sudah diganti nama/username asli

---

## 13. Bonus: GitHub CLI

Ini **opsional**. Kalau kamu sudah memasang GitHub CLI (`gh`), beberapa langkah bisa lebih singkat. Jalankan di Git Bash, di folder `/c/Proyek/JendEdu`:

```
gh pr list
```

```
gh pr checkout 3
```

```
gh pr review 3 --approve
```

Angka `3` adalah nomor PR. Untuk pemula, cara lewat browser di atas sudah cukup.

---

## 14. Kalau error

**Kalau `git switch <branch>` bilang "invalid reference"...**
Kamu belum `git fetch origin`. Jalankan dulu, lalu coba lagi. Periksa juga ejaan nama branch (huruf besar/kecil, `feature/` vs `feat/`).

**Kalau `git switch` bilang "Your local changes would be overwritten"...**
Ada berkas yang kamu ubah di branch sebelumnya. Reviewer sebaiknya tidak mengedit berkas. Buang perubahan yang tidak perlu dengan `git restore .` (hati-hati: perubahan hilang), lalu coba lagi.

**Kalau `start index.html` bilang "The system cannot find the file"...**
Kamu belum ada di folder yang benar, atau branch ini memang belum berisi `index.html`. Cek dengan `cd` dan `dir`.

**Kalau halaman terbuka tapi tanpa gaya/gambar...**
Itu hampir pasti temuan 🔴: path CSS/gambar salah, atau PR #2 (CSS) belum ter-merge. Pastikan `main` lokal terbaru dan branch yang dites sudah berisi folder `css\`.

**Kalau tombol "Merge pull request" abu-abu...**
Biasanya ada konflik, atau branch protection menunggu approval. Baca pesan di atas tombol. Untuk konflik, minta author menjalankan `git pull origin main` di branch-nya, menyelesaikan konflik, lalu push lagi.

**Kalau tidak bisa meng-approve PR milikmu sendiri...**
Memang begitu aturan GitHub. Minta anggota lain (Dokumentator untuk `docs/review-log`).

**Kalau perintah `robocopy` memberi kode 1...**
Itu berarti berhasil ("files copied"), bukan error.

---

Kembali ke: [00-mulai-di-sini.md](00-mulai-di-sini.md) | Persiapan: [01-persiapan-semua-anggota.md](01-persiapan-semua-anggota.md) | Dokumentator: [05-dokumentator.md](05-dokumentator.md)
