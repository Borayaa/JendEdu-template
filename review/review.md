# Log Review Pull Request - JendEdu

- **Reviewer:** @username-3
- **Periode:** Oktober 2026
- **Repositori:** JendEdu (situs statis Bootstrap 3, Bahasa Indonesia)

## Ringkasan Status

| PR | Judul | Branch | Author | Status |
|----|-------|--------|--------|--------|
| #1 | Setup template dasar & struktur folder | `chore/setup-template` | @username-1 | ✅ Approved & merged |
| #2 | Halaman Beranda (index.html) | `feature/homepage` | @username-1 | ✅ Approved & merged |
| #3 | Tambah halaman Harga | `feature/pricing-page` | @username-1 | 🔴 Changes requested |
| #4 | Navbar dan footer bersama | `feature/navbar-footer` | @username-2 | 🔴 Changes requested |
| #5 | Halaman Kontak | `feature/contact-page` | @username-2 | 🔴 Changes requested |
| #6 | Tiga halaman artikel + CSS artikel | `feature/artikel-pages` | @username-2 | ✅ Approved & merged |
| #7 | Tiga halaman berita | `feature/berita-pages` | @username-2 | 🔴 Changes requested |
| #8 | README.md | `docs/readme` | @username-4 | ✅ Approved & merged |

Label komentar: 🔴 Wajib diperbaiki - 🟡 Saran - 🟢 Nit (hal kecil, opsional).

---

## PR #3 - Tambah halaman Harga

- **Branch:** `feature/pricing-page` -> `main`
- **Author:** @username-1
- **Snapshot kode:** [codes/PR-03_pricing.html](codes/PR-03_pricing.html)

**Deskripsi:** Menambahkan `pricing.html` berisi paket SD, SMP, dan SMA beserta tombol pendaftaran dan catatan diskon tahunan.

### Komentar review

**`PR-03_pricing.html` baris 28-37**

```html
<section id="inner-headline">
...
</div>

<section id="content">
```

🔴 **Wajib diperbaiki.** Tag `<section id="inner-headline">` tidak pernah ditutup dengan `</section>`, sehingga `#content` tersarang di dalamnya dan gaya header judul ikut mengenai konten. Ini juga bug yang sama dengan template aslinya, jadi mohon dirapikan sekalian.

```suggestion
</div>
</section>

<section id="content">
```

**`PR-03_pricing.html` baris 46, 65, 84**

```html
<h6>Rp 99000 / bln</h6>
<h6>Rp129.000 / bulan</h6>
<h6>Rp 159.000 /bulan</h6>
```

🔴 **Wajib diperbaiki.** Format harga tidak konsisten di ketiga paket (spasi setelah "Rp", titik ribuan, "bln" vs "bulan"). Samakan dengan format `Rp99.000 / bulan` seperti di meta description dan halaman Beranda.

```suggestion
<h6>Rp99.000 / bulan</h6>
```

(Terapkan pola yang sama untuk Rp129.000 dan Rp159.000.)

**`PR-03_pricing.html` baris 55, 74, 93**

```html
<a href="#" class="btn btn-medium btn-theme"><i class="icon-bolt"></i> Daftar Sekarang</a>
```

🔴 **Wajib diperbaiki.** Tombol "Daftar Sekarang" memakai `href="#"` sehingga tidak ke mana-mana. Arahkan ke halaman Kontak.

```suggestion
<a href="contact.html" class="btn btn-medium btn-theme"><i class="icon-bolt"></i> Daftar Sekarang</a>
```

**`PR-03_pricing.html` baris 74**

```html
<i class="icon-bolt"></i> Get Now</a>
```

🔴 **Wajib diperbaiki.** Teks masih bahasa Inggris. Seluruh situs memakai Bahasa Indonesia, jadi ganti menjadi "Daftar Sekarang".

**`PR-03_pricing.html` baris 12**

```html
<img src="img/logo.png"/>
```

🟡 **Saran.** Gambar logo belum punya atribut `alt`. Tambahkan untuk aksesibilitas dan SEO.

```suggestion
<img src="img/logo.png" alt="JendEdu"/>
```

**`PR-03_pricing.html` baris 100**

```html
<p class="text-center" style="margin-top:30px; color:red; font-size:18px;">
```

🟡 **Saran.** Hindari inline style. Pindahkan ke kelas di `css/style.css`, dan warna merah terlalu mencolok dibanding tema situs. Cukup `class="text-center"` dengan margin dari CSS.

**Catatan tambahan:** 🟢 Paket UTBK Intensif ada di brief tetapi belum ada di PR ini. Mohon konfirmasi apakah akan ditambahkan di PR ini atau PR terpisah.

**Keputusan: Request changes**

Checklist yang harus diperbaiki sebelum approval:

- [ ] Tutup `</section>` untuk `#inner-headline`
- [ ] Samakan format semua harga (`Rp99.000 / bulan`)
- [ ] Ganti semua `href="#"` pada tombol "Daftar Sekarang" menjadi `contact.html`
- [ ] Ganti "Get Now" menjadi "Daftar Sekarang"
- [ ] Tambah `alt` pada logo
- [ ] Pindahkan inline style ke CSS
- [ ] Konfirmasi paket UTBK Intensif

---

## PR #4 - Navbar dan footer bersama

- **Branch:** `feature/navbar-footer` -> `main`
- **Author:** @username-2
- **Snapshot kode:** [codes/PR-04_navbar-footer.html](codes/PR-04_navbar-footer.html)

**Deskripsi:** Membuat navbar dan footer yang dipakai semua halaman, termasuk daftar artikel terbaru dan tautan media sosial.

### Komentar review

**`PR-04_navbar-footer.html` baris 18 dan 21**

```html
<li class="active"><a href="index.html">Beranda</a></li>
...
<li class="active"><a href="portfolio.html">Galeri</a></li>
```

🔴 **Wajib diperbaiki.** Dua item menu sama-sama `active`. Hanya halaman yang sedang dibuka yang boleh `active`. Di snapshot ini sepertinya baris Galeri tersalin dari halaman lain.

```suggestion
<li><a href="portfolio.html">Galeri</a></li>
```

**`PR-04_navbar-footer.html` baris 8**

```html
<link href="http://fonts.googleapis.com/css?family=Open+Sans:400,600,700" rel="stylesheet">
```

🔴 **Wajib diperbaiki.** Impor font memakai `http://`, memicu peringatan mixed content di situs HTTPS dan font bisa diblokir.

```suggestion
<link href="https://fonts.googleapis.com/css?family=Open+Sans:400,600,700" rel="stylesheet">
```

**`PR-04_navbar-footer.html` baris 51**

```html
<a href="artikel-belajar-online-efektif-smp.htm">
```

🔴 **Wajib diperbaiki.** Ekstensi salah (`.htm`), padahal berkasnya `artikel-belajar-online-efektif-smp.html`. Tautan ini akan 404.

```suggestion
<a href="artikel-belajar-online-efektif-smp.html">
```

**`PR-04_navbar-footer.html` baris 59**

```html
<a href="https://www.instagram.com/jendedu" target="_blank">
```

🟡 **Saran.** `target="_blank"` tanpa `rel` membuka celah `window.opener`. Tambahkan `rel="noopener"`.

```suggestion
<a href="https://www.instagram.com/jendedu" target="_blank" rel="noopener">
```

**`PR-04_navbar-footer.html` baris 14 dan 35**

```html
<img src="img/logo.png">
<h5 class="widgetheading">Our Contact</h5>
```

🟡 **Saran.** Logo belum punya `alt="JendEdu"`. Judul widget "Our Contact" masih bahasa Inggris, ganti menjadi "Hubungi Kami". 🟢 Nomor WhatsApp 0812-3456-7890 juga belum ada di footer, sesuaikan dengan halaman Kontak.

**Keputusan: Request changes**

Checklist yang harus diperbaiki sebelum approval:

- [ ] Hanya satu `class="active"` per halaman
- [ ] Ubah impor font ke `https://`
- [ ] Perbaiki tautan `.htm` menjadi `.html`
- [ ] Tambah `rel="noopener"` pada tautan `_blank`
- [ ] Tambah `alt` pada logo
- [ ] Ganti "Our Contact" menjadi "Hubungi Kami"

---

## PR #5 - Halaman Kontak

- **Branch:** `feature/contact-page` -> `main`
- **Author:** @username-2
- **Snapshot kode:** [codes/PR-05_contact.html](codes/PR-05_contact.html)

**Deskripsi:** Menambahkan `contact.html` dengan peta lokasi, formulir pesan, dan informasi kontak perusahaan.

### Komentar review

**`PR-05_contact.html` baris 11**

```html
<script src="http://maps.google.com/maps/api/js?sensor=false"></script>
```

🔴 **Wajib diperbaiki.** Ini versi lama Google Maps JavaScript API: parameter `sensor=false` sudah tidak dipakai, tidak ada API key, dan memakai `http://`. Peta kemungkinan besar gagal tampil. Untuk situs statis, cukup pakai embed iframe yang tidak butuh key.

```suggestion
<iframe src="https://maps.google.com/maps?q=Tebet,%20Jakarta%20Selatan&z=14&output=embed" width="100%" height="300" style="border:0;" allowfullscreen loading="lazy" title="Lokasi JendEdu"></iframe>
```

Dengan begitu skrip `initMap()` (baris 12-19) dan `<div id="map">` (baris 26) bisa dihapus.

**`PR-05_contact.html` baris 37 dan 41**

```html
<input type="text" class="form-control" id="name" name="name">
<input type="email" class="form-control" id="name" name="email">
```

🔴 **Wajib diperbaiki.** `id="name"` dipakai dua kali. Akibatnya `label for="email"` tidak terhubung ke input yang benar dan validasi JS bisa salah sasaran.

```suggestion
<input type="email" class="form-control" id="email" name="email">
```

**`PR-05_contact.html` baris 33 dan 47**

```html
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Kirim pesan kepada kami.</p>
<input type="submit" value="Submit" class="btn btn-default">
```

🔴 **Wajib diperbaiki.** Masih ada teks Lorem ipsum dan tombol berlabel "Submit". Ganti dengan teks Indonesia, misalnya "Ada pertanyaan seputar kursus, paket belajar, atau pendaftaran? Tim kami siap membantu Anda." dan tombol "Kirim Pesan".

```suggestion
<input type="submit" value="Kirim Pesan" class="btn btn-default">
```

**`PR-05_contact.html` baris 32**

```html
<br><br>
```

🟡 **Saran.** Jarak dengan `<br><br>` rapuh di layar kecil. Gunakan class spacing dari CSS (mis. `margin-top` pada form) atau satu `<br>` saja seperti halaman lain.

**`PR-05_contact.html` baris 26**

```html
<div id="map" style="width:100%; height:300px;"></div>
```

🟢 **Nit.** Inline style, sebaiknya dipindah ke CSS jika elemen ini tetap dipakai.

**`PR-05_contact.html` baris 52-57** (blok alamat)

🟡 **Saran.** Tambahkan WhatsApp dan jam layanan (Senin-Sabtu, 08.00-20.00 WIB) agar sama dengan footer, dan bungkus email dengan `<a href="mailto:halo@jendedu.id">`.

**Keputusan: Request changes**

Checklist yang harus diperbaiki sebelum approval:

- [ ] Ganti Google Maps JS API lama dengan iframe embed `https://`
- [ ] Hilangkan `id` ganda (`id="email"` untuk input email)
- [ ] Hapus Lorem ipsum, ganti tombol menjadi "Kirim Pesan"
- [ ] Ganti `<br><br>` dengan spacing yang lebih rapi
- [ ] Lengkapi info kontak (WhatsApp, jam layanan, tautan `mailto:`)

---

## PR #7 - Tiga halaman berita

- **Branch:** `feature/berita-pages` -> `main`
- **Author:** @username-2
- **Snapshot kode:** [codes/PR-07_berita-beasiswa.html](codes/PR-07_berita-beasiswa.html)

**Deskripsi:** Menambahkan tiga halaman berita; snapshot ini memakai `berita-beasiswa-jendedu-2027.html` sebagai contoh.

### Komentar review

**`PR-07_berita-beasiswa.html` baris 13**

```html
<h1>Program Beasiswa JendEdu 2026/2027 Resmi Dibuka</h2>
```

🔴 **Wajib diperbaiki.** Tag pembuka `<h1>` ditutup dengan `</h2>`. Ini merusak struktur DOM dan gagal validasi HTML.

```suggestion
<h1>Program Beasiswa JendEdu 2026/2027 Resmi Dibuka</h1>
```

**`PR-07_berita-beasiswa.html` baris 18**

```html
<img src="img/blog/berita-3.jpg" style="width:100%; margin:20px 0;">
```

🔴 **Wajib diperbaiki.** Gambar tidak punya `alt`, dan memakai inline style. Pakai class yang sudah ada (`img-responsive post-image`) dari CSS artikel.

```suggestion
<img class="img-responsive post-image" src="img/blog/berita-3.jpg" alt="Siswa tersenyum saat belajar di meja, penerima beasiswa JendEdu">
```

**`PR-07_berita-beasiswa.html` baris 28**

```html
<a href="kontak.html">Kontak</a>
```

🔴 **Wajib diperbaiki.** Tautan rusak: nama berkasnya `contact.html`, bukan `kontak.html`.

```suggestion
<a href="contact.html">Kontak</a>
```

**`PR-07_berita-beasiswa.html` baris 25**

```html
<li>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</li>
```

🔴 **Wajib diperbaiki.** Placeholder Lorem ipsum di daftar persyaratan. Isi dengan persyaratan sebenarnya (rapor, surat keterangan, esai, persetujuan orang tua, dll.).

**`PR-07_berita-beasiswa.html` baris 21**

```html
<br><br>
```

🟡 **Saran.** Hapus `<br><br>` sebagai pengatur jarak. `.post-body` sudah mengatur margin antar elemen.

**`PR-07_berita-beasiswa.html` baris 30**

```html
<a href="index.html" class="btn btn-theme">Back to Home</a>
```

🟡 **Saran.** Teks masih Inggris. Ganti menjadi "Kembali ke Beranda" dan bungkus dengan `<div class="post-back">`.

**`PR-07_berita-beasiswa.html` baris 43**

```html
<a href="https://wa.me/6281234567890" target="_blank" class="btn btn-theme">Chat WhatsApp</a>
```

🟡 **Saran.** Tambahkan `rel="noopener"`. 🟢 Sidebar "Mulai Belajar" pada halaman lain mengarah ke `pricing.html`, mohon samakan.

**`PR-07_berita-beasiswa.html` baris 35-39**

🟢 **Nit.** Daftar "Berita Terkini" hanya berisi 2 item; tambahkan berita yang sedang dibuka agar konsisten dengan dua halaman berita lain, dan tambahkan widget "Artikel Terbaru".

**Keputusan: Request changes**

Checklist yang harus diperbaiki sebelum approval:

- [ ] Perbaiki `<h1>...</h2>` menjadi `<h1>...</h1>`
- [ ] Tambah `alt` dan ganti inline style dengan class CSS pada gambar
- [ ] Perbaiki tautan `kontak.html` menjadi `contact.html`
- [ ] Hapus Lorem ipsum, isi persyaratan sebenarnya
- [ ] Hapus `<br><br>`, ganti "Back to Home" menjadi "Kembali ke Beranda"
- [ ] Tambah `rel="noopener"` pada tautan `_blank`
- [ ] Terapkan perbaikan yang sama pada dua halaman berita lainnya

---

## Alur Review

1. **Author membuka PR** dari branch fitur (`feature/...`) ke `main`, dengan deskripsi singkat dan daftar berkas yang diubah.
2. **Reviewer memberi komentar** per baris kode, lengkap dengan label (🔴 / 🟡 / 🟢) dan suggestion bila memungkinkan, lalu memilih **Request changes**.
3. **Author memperbaiki** dengan menambah commit baru ke branch yang sama (tanpa membuat PR baru) dan membalas komentar yang sudah ditangani.
4. **Reviewer memeriksa ulang** perubahan, menandai thread yang selesai, dan menambah komentar jika masih ada yang kurang.
5. Setelah semua poin 🔴 beres, reviewer memilih **Approve**.
6. PR di-**merge ke `main`** (oleh author atau reviewer), lalu branch fitur dihapus.

## Checklist Review Umum

- [ ] Seluruh teks dalam Bahasa Indonesia (tidak ada "Get Now", "Submit", "Back to Home")
- [ ] Semua tautan berfungsi (tidak ada `href="#"`, nama berkas benar, ekstensi `.html`)
- [ ] Semua `<img>` punya `alt` yang bermakna
- [ ] Harga konsisten di seluruh halaman (`Rp99.000 / bulan`)
- [ ] Tampilan responsif di lebar ponsel, tablet, dan desktop
- [ ] Tidak ada Lorem ipsum atau teks placeholder
- [ ] Hanya satu item navbar `active`, sesuai halaman
- [ ] Tidak ada inline style dan `<br><br>` untuk spacing; gunakan CSS
- [ ] Sumber eksternal memakai `https://`, dan `target="_blank"` disertai `rel="noopener"`
- [ ] HTML valid (tag ditutup dan cocok, tidak ada `id` ganda) dan sudah dicek di validator W3C
