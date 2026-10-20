# Panduan Reviewer (@username-3)

> **Tugas kamu**
> - Memeriksa (review) semua Pull Request (PR) dari Coder 1, Coder 2, dan Dokumentator sebelum masuk ke `main`.
> - Menguji kode di komputermu sendiri, menulis komentar per baris dengan label, lalu memilih **Request changes**, **Comment**, atau **Approve**.
> - Meng-**merge** PR yang sudah beres di repo tim (`Borayaa/JendEdu`) dan memperbarui `main` lokal. Branch di fork dihapus oleh author-nya sendiri.
> - Di akhir proyek, membuat PR `docs/review-log` berisi folder `review\` dari **fork**-mu (PR ini di-approve oleh Dokumentator).

> ⚠️ **Jangan pernah `git push` ke `main`.** Hanya branch `feature/...`, `chore/...`, atau `docs/...` yang di-push (ke fork-mu, `origin`). `main` hanya berubah lewat PR yang di-merge.

**Sebelum mulai:** selesaikan [01-persiapan-semua-anggota.md](01-persiapan-semua-anggota.md) (Git terpasang, sudah **fork** `Borayaa/JendEdu`, sudah clone `JendEdu-template` dan fork-mu ke `C:\Proyek`, dan sudah menjalankan `git remote add upstream`).

Kamu punya **dua peran sekaligus**:

1. Seperti semua anggota, kamu punya **fork** sendiri (`origin`) dan remote **upstream** (repo tim `Borayaa/JendEdu`). Dipakai untuk PR `docs/review-log` milikmu dan untuk mengambil PR orang lain ke komputermu.
2. Kamu adalah **collaborator** di `Borayaa/JendEdu` (hak akses Write), supaya bisa **Approve dan Merge** PR. Owner (Borayaa) mengirim undangan; **terima undangannya**: buka email dari GitHub atau https://github.com/Borayaa/JendEdu/invitations lalu klik **Accept invitation**.

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
8. [Resolve, Approve, Merge](#8-resolve-approve-merge)
9. [Update `main` lokal](#9-update-main-lokal)
10. [Rekomendasi branch protection (untuk owner)](#10-rekomendasi-branch-protection-untuk-owner)
11. [PR `docs/review-log` milikmu sendiri](#11-pr-docsreview-log-milikmu-sendiri)
12. [Checklist review](#12-checklist-review)
13. [Bonus: GitHub CLI](#13-bonus-github-cli)
14. [Kalau error](#14-kalau-error)

---

## 1. Mencari PR yang harus kamu review

Semua PR ditujukan ke repo tim (**upstream**), tetapi berasal dari **fork** masing-masing anggota. Di halaman PR akan tertulis, misalnya:

```
username-1 wants to merge 1 commit into Borayaa:main from username-1:feature/homepage
```

Artinya: PR masuk ke `main` milik `Borayaa/JendEdu`, kodenya ada di branch `feature/homepage` di fork `username-1/JendEdu`.

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

### Tabel urutan PR dan PR yang punya kesalahan

| Urutan merge | Branch | Author | PR di review.md | Ada kesalahan yang harus dikomentari? |
|--------------|--------|--------|-----------------|----------------------------------------|
| 1 | `chore/setup-template` | Coder 1 | #1 | Tidak, approve langsung |
| 2 | `feature/navbar-footer` | Coder 2 | #4 | **Ya** (`css\style.css`) |
| 3 | `feature/pricing` | Coder 1 | #3 | **Ya** (`pricing.html`) |
| 3 | `feature/contact` | Coder 2 | #5 | **Ya** (`contact.html`) |
| 3 | `feature/news` | Coder 2 | #7 | **Ya** (`berita-beasiswa-jendedu-2027.html`) |
| 3 | `feature/homepage`, `feature/about`, `feature/courses`, `feature/gallery` (Coder 1), `feature/posts` (Coder 2) | Coder 1 / Coder 2 | #2, #6, dst. | Tidak, periksa dengan checklist lalu approve |
| 4 | `docs/readme` | Dokumentator | #8 | Tidak, periksa dengan checklist lalu approve |
| 5 | `docs/review-log` | Kamu | - | Di-approve oleh Dokumentator |

Nomor di kolom "PR di review.md" hanya contoh dari `review\review.md`. Nomor sebenarnya di GitHub mengikuti urutan pembuatan PR dan bisa berbeda. Pakai **nama branch** sebagai pegangan; yang berkesalahan adalah `feature/pricing`, `feature/navbar-footer`, `feature/contact`, dan `feature/news`.

### Daftar komentar siap pakai: review\review.md

Untuk PR `feature/pricing`, `feature/navbar-footer`, `feature/contact`, dan `feature/news` (#3, #4, #5, #7 di review.md), buka daftar komentarmu di (Command Prompt, dari folder `C:\Proyek\JendEdu`):

```
notepad ..\JendEdu-template\review\review.md
```

atau di GitHub: https://github.com/Borayaa/JendEdu-template/blob/main/review/review.md

Nomor baris di review.md sama dengan file di dalam PR (karena PR berisi draft dari root template). Posting tiap poin sebagai komentar per baris, lalu kirim review dengan **Request changes**.

Setelah author push perbaikan, ambil ulang branch PR seperti dijelaskan di bagian 4, lalu bandingkan dengan versi benar memakai `fc` di Command Prompt:

```
fc ..\JendEdu-template\review\codes\pricing.html pricing.html
```

Untuk `feature/navbar-footer` (CSS):

```
fc ..\JendEdu-template\review\codes\css\style.css css\style.css
```

Kalau muncul `FC: no differences encountered`, lanjut **Approve**, lalu **Merge**. PR lain cukup diperiksa dengan checklist lalu langsung di-approve.

Pada PR `docs/review-log` di akhir, folder `review\` (termasuk `codes` berisi file perbaikan) disalin sebagai dokumentasi.

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

### Langkah 1: ambil PR dari GitHub (Git Bash)

Karena kodenya ada di fork orang lain, kamu mengambilnya lewat nomor PR (bukan nama branch). Nomor PR tertulis di judul halaman PR di GitHub, misalnya `#3` (nomor di sini hanya contoh; pakai nomor asli PR-nya).

1. Buka **Git Bash** (klik kanan folder `C:\Proyek\JendEdu` > **Open Git Bash here**, atau lewat menu Start).
2. Kalau belum di folder yang benar:

```
cd /c/Proyek/JendEdu
```

3. Ambil PR ke komputermu sebagai branch lokal bernama `pr-<nomor-PR>`. Contoh untuk PR nomor 3:

```
git fetch upstream pull/3/head:pr-3
```

Hasil yang diharapkan (contoh):

```
From https://github.com/Borayaa/JendEdu
 * [new ref]         refs/pull/3/head -> pr-3
```

4. Pindah ke branch tersebut:

```
git switch pr-3
```

Hasil yang diharapkan:

```
Switched to branch 'pr-3'
```

> Ganti `3` dengan nomor PR yang kamu review. Cara ini bekerja untuk PR dari fork mana pun, tanpa perlu menambah remote baru.

### Kalau author sudah push perbaikan

Branch `pr-3` di komputermu adalah salinan lama, tidak ikut ter-update. Untuk mengambil versi terbaru, hapus lalu ambil ulang:

```
git switch main
```

```
git branch -D pr-3
```

```
git fetch upstream pull/3/head:pr-3
```

```
git switch pr-3
```

(Pakai `-D` huruf besar karena branch ini tidak pernah di-merge dari komputermu.)

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

Opsional: hapus branch tes yang sudah tidak dipakai (ganti `3` dengan nomor PR-nya):

```
git branch -D pr-3
```

### Pengecualian: PR `chore/setup-template`

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

1. Author memperbaiki, melakukan commit dan push ke branch yang sama **di fork-nya**, lalu membalas komentarmu dengan "Sudah diperbaiki". PR otomatis ter-update, tidak perlu PR baru.
2. Kamu akan dapat notifikasi. Buka PR-nya.
3. Di tab **Files changed**, klik menu **Changes from** (dropdown dekat atas) lalu pilih **Changes since your last review** supaya hanya melihat yang baru.
4. Ambil ulang kode terbaru ke komputermu (Git Bash). Ganti `3` dengan nomor PR-nya:

```
cd /c/Proyek/JendEdu
```

```
git switch main
```

```
git branch -D pr-3
```

```
git fetch upstream pull/3/head:pr-3
```

```
git switch pr-3
```

5. Jalankan lagi di cmd (`start index.html` dll.) dan cek ulang semua poin 🔴 dari review sebelumnya.
6. Kalau masih ada yang kurang, balas di komentar yang sama, atau tulis komentar baru, lalu submit **Request changes** lagi.
7. Kalau sudah beres, lanjut ke bagian 8.

> Kalau yang diminta adalah perbaikan navbar/footer, itu tugas **Coder 2** walaupun ditemukan di halaman milik Coder 1. Tulis di komentar dan mention `@username-2`.

---

## 8. Resolve, Approve, Merge

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

Merge dilakukan di halaman PR pada repo **Borayaa/JendEdu** (kamu bisa karena sudah menjadi collaborator).

1. Kembali ke tab **Conversation**, gulir ke bawah sampai kotak hijau "This branch has no conflicts".
2. Klik tombol hijau **Merge pull request**.

   Tombol ini punya panah kecil di sebelahnya dengan tiga pilihan. Untuk proyek ini **pakai yang default: "Create a merge commit"**. Ini paling sederhana dan riwayat commit setiap anggota tetap terlihat (bagus untuk penilaian kontribusi). Dua pilihan lain (**Squash and merge** dan **Rebase and merge**) tidak perlu dipakai.

3. Klik **Confirm merge**.
4. Muncul tulisan ungu "Pull request successfully merged and closed".

### Langkah 4: branch dihapus oleh author

Branch PR ada di **fork milik author**, bukan di repo tim, jadi kamu tidak perlu (dan biasanya tidak bisa) menghapusnya. Author yang menghapus branch itu di fork-nya sendiri sesudah merge (ada di panduan mereka). Kalau tombol **Delete branch** tidak muncul, itu normal.

Ulangi untuk PR berikutnya sesuai [urutan di bagian 2](#2-urutan-review-yang-disarankan).

> Setelah PR `chore/setup-template` atau `feature/navbar-footer` ter-merge, kabari author PR lain lewat grup bahwa mereka bisa mulai mengerjakan atau membuat PR (dan menjalankan `git switch main` lalu `git pull upstream main`).

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
git pull upstream main
```

> Fork-mu di GitHub boleh tertinggal (`X commits behind`). Itu tidak masalah, karena branch baru selalu dibuat dari `main` lokal yang sudah di-pull dari upstream. Jangan klik atau jalankan apa pun yang melakukan push ke `main`.

Hasil `git pull upstream main` yang diharapkan (contoh):

```
Updating 3f2a1b0..9c8d7e6
Fast-forward
 css/style.css | 120 +++++++++++++
 1 file changed, 120 insertions(+)
```

Opsional: hapus branch tes `pr-<nomor>` yang sudah ter-merge supaya daftar tidak penuh (ganti `3` dengan nomor PR-nya):

```
git branch -D pr-3
```

---

## 10. Rekomendasi branch protection (untuk owner)

Minta owner repo (**Borayaa**) mengaktifkan perlindungan `main` di repo tim supaya tidak ada yang bisa push langsung atau merge tanpa review:

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

Di akhir, kamu mengumpulkan catatan review (folder `review\`) ke repo. PR ini dibuat dari **fork-mu**, sama seperti anggota lain. Karena tidak boleh meng-approve PR sendiri, PR ini di-review dan di-approve oleh **Dokumentator** (@username-4).

**Syarat:** semua PR lain sudah ter-merge (atau minimal sudah selesai direview), dan `main` lokal sudah terbaru (bagian 9).

### Langkah 1: buat branch (Git Bash)

```
cd /c/Proyek/JendEdu
```

```
git switch main
```

```
git pull upstream main
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

### Langkah 3: commit dan push ke fork-mu (Git Bash)

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

Perintah ini mengirim branch ke **fork-mu** (`origin`), bukan ke repo tim.

> Push pertama kali bisa membuka jendela login GitHub di browser (Git Credential Manager). Login dan klik authorize.

### Langkah 4: buka PR (Browser)

1. Buka fork-mu: `https://github.com/username-3/JendEdu` (ganti `username-3` dengan username aslimu).
2. Klik tombol kuning **Compare & pull request** (atau tab **Pull requests** > **New pull request** > **compare across forks**).
3. **Periksa empat dropdown**, harus persis seperti ini:
   `base repository: Borayaa/JendEdu` · `base: main` ← `head repository: username-3/JendEdu` · `compare: docs/review-log`
4. Isi judul: `Tambah log review pull request`. Isi deskripsi singkat tentang isi `review\`.
5. Centang **Allow edits by maintainers**.
6. Klik **Create pull request**.
7. Di halaman PR (di `Borayaa/JendEdu`), kolom **Reviewers** di kanan, pilih **Dokumentator (@username-4)**.

### Langkah 5: tunggu review, lalu merge

1. Dokumentator meninjau dan memberi komentar/Approve (Files changed > Review changes > Approve).
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

PR di `Borayaa/JendEdu` ter-update otomatis.

3. Balas komentar dengan "Sudah diperbaiki", dan tunggu **Approve** dari Dokumentator.
4. **Setelah Approve dari Dokumentator**, PR ini di-merge oleh kamu (Reviewer) atau owner Borayaa: klik **Merge pull request** > **Confirm merge**.
5. Sinkronkan lokal (Git Bash):

```
git switch main
```

```
git pull upstream main
```

6. Hapus branch di fork-mu (karena ini PR milikmu, kamu sendiri yang menghapusnya):

```
git branch -d docs/review-log
```

```
git push origin --delete docs/review-log
```

(Dua perintah terakhir opsional.)

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

### Tujuan PR

- [ ] Tidak ada yang **push langsung ke `main`**: `main` hanya berubah lewat PR yang di-merge (cek riwayat commit `main`; kalau ada commit tanpa PR, beri tahu owner)
- [ ] PR menuju **base `Borayaa/JendEdu` : `main`** (lihat tulisan "wants to merge ... into `Borayaa:main`"), **bukan** ke fork seseorang atau branch lain

### Hal khusus per PR

- [ ] PR `chore/setup-template`: folder `js`, `fonts`, `img` ada; `logo.png` dan `img\blog` **tidak** ikut
- [ ] PR `feature/navbar-footer`: folder `css` lengkap dan `img\logo.png` ada
- [ ] PR halaman: hanya berkas halaman itu yang berubah (tidak ada berkas nyasar, tidak ada folder `panduan\`)
- [ ] PR docs: placeholder `[Nama Anggota 1..4]` dan `@username-1..4` sudah diganti nama/username asli

---

## 13. Bonus: GitHub CLI

Ini **opsional**. Kalau kamu sudah memasang GitHub CLI (`gh`), beberapa langkah bisa lebih singkat. Jalankan di Git Bash, di folder `/c/Proyek/JendEdu`:

```
gh pr list -R Borayaa/JendEdu
```

```
gh pr checkout 3 -R Borayaa/JendEdu
```

```
gh pr review 3 --approve -R Borayaa/JendEdu
```

Angka `3` adalah nomor PR. Perintah `gh pr checkout` mengambil PR dari fork author sekaligus berpindah ke branch-nya (pengganti `git fetch upstream pull/3/head:pr-3` dan `git switch pr-3`). Untuk pemula, cara lewat browser di atas sudah cukup.

---

## 14. Kalau error

**Kalau `git fetch upstream pull/3/head:pr-3` bilang "fatal: 'upstream' does not appear to be a git repository"...**
Remote `upstream` belum ditambahkan. Jalankan:

```
git remote add upstream https://github.com/Borayaa/JendEdu.git
```

Lalu cek dengan `git remote -v` (harus ada `origin` dan `upstream`), dan ulangi perintah fetch.

**Kalau `git fetch` bilang "fatal: a branch named 'pr-3' already exists" atau "refusing to fetch into current branch"...**
Branch `pr-3` sudah ada dari tes sebelumnya. Jalankan `git switch main`, lalu `git branch -D pr-3`, lalu fetch lagi.

**Kalau `git switch pr-3` bilang "invalid reference"...**
Kamu belum menjalankan `git fetch upstream pull/3/head:pr-3`, atau nomor PR-nya salah. Periksa nomor di judul PR.

**Kalau `git switch` bilang "Your local changes would be overwritten"...**
Ada berkas yang kamu ubah di branch sebelumnya. Reviewer sebaiknya tidak mengedit berkas. Buang perubahan yang tidak perlu dengan `git restore .` (hati-hati: perubahan hilang), lalu coba lagi.

**Kalau `start index.html` bilang "The system cannot find the file"...**
Kamu belum ada di folder yang benar, atau branch ini memang belum berisi `index.html`. Cek dengan `cd` dan `dir`.

**Kalau halaman terbuka tapi tanpa gaya/gambar...**
Itu hampir pasti temuan 🔴: path CSS/gambar salah, atau PR `feature/navbar-footer` (CSS) belum ter-merge. Pastikan `main` lokal terbaru dan branch yang dites sudah berisi folder `css\`.

**Kalau tombol "Merge pull request" abu-abu...**
Biasanya ada konflik, atau branch protection menunggu approval. Baca pesan di atas tombol. Untuk konflik, minta author menjalankan `git switch main`, `git pull upstream main`, lalu `git switch` ke branch-nya dan `git merge main`, menyelesaikan konflik, lalu `git push` lagi ke fork-nya.

**Kalau halaman PR menulis "There isn't anything to compare" (di PR milikmu) atau PR menuju tujuan yang salah...**
Dropdown base/head salah. Periksa: `base repository: Borayaa/JendEdu` · `base: main` ← `head repository: username-3/JendEdu` · `compare: docs/review-log`. Kalau PR author lain salah tujuan, minta mereka membuat ulang PR dengan dropdown yang benar.

**Kalau `git push` ditolak dengan "403" ke Borayaa/JendEdu...**
Kamu mengirim ke upstream secara tidak sengaja. Selalu `git push` ke `origin` (fork-mu), contoh `git push -u origin docs/review-log`.

**Kalau fork-mu tertulis "X commits behind Borayaa:main"...**
Itu tidak masalah dan tidak perlu diperbaiki: branch baru selalu dibuat dari `main` lokal yang sudah di-pull (`git switch main` lalu `git pull upstream main`). Jangan push ke `main`.

**Kalau tombol Merge atau Approve tidak muncul...**
Undangan collaborator belum kamu terima. Buka https://github.com/Borayaa/JendEdu/invitations lalu klik **Accept invitation**.

**Kalau tidak bisa meng-approve PR milikmu sendiri...**
Memang begitu aturan GitHub. Minta anggota lain (Dokumentator untuk `docs/review-log`).

**Kalau perintah `robocopy` memberi kode 1...**
Itu berarti berhasil ("files copied"), bukan error.

---

Kembali ke: [00-mulai-di-sini.md](00-mulai-di-sini.md) | Persiapan: [01-persiapan-semua-anggota.md](01-persiapan-semua-anggota.md) | Dokumentator: [05-dokumentator.md](05-dokumentator.md)
