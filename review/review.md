# Log Review Pull Request - JendEdu

- **Reviewer:** @username-3
- **Periode:** Oktober 2026
- **Repositori:** JendEdu (situs statis Bootstrap 3, Bahasa Indonesia)

Nomor PR di dokumen ini adalah contoh; nomor sebenarnya di GitHub bisa berbeda — cocokkan dengan nama branch.

> **Catatan:** File di root template untuk PR #3, #4, #5, #7 adalah draft yang sengaja berisi kesalahan; versi yang sudah diperbaiki ada di `review/codes/`. Nomor baris di bawah mengacu pada file draft di root template (sama dengan file yang ada di PR).

## Ringkasan Status

| PR | Judul | Branch | Author | Status |
|----|-------|--------|--------|--------|
| #1 | Setup template dasar & struktur folder | `chore/setup-template` | @username-1 | ✅ Approved & merged |
| #2 | Halaman Beranda (index.html) | `feature/homepage` | @username-1 | ✅ Approved & merged |
| #3 | Tambah halaman Harga | `feature/pricing` | @username-1 | 🔴 Changes requested |
| #4 | Navbar dan footer bersama (CSS) | `feature/navbar-footer` | @username-2 | 🔴 Changes requested |
| #5 | Halaman Kontak | `feature/contact` | @username-2 | 🔴 Changes requested |
| #6 | Tiga halaman artikel + CSS artikel | `feature/posts` | @username-2 | ✅ Approved & merged |
| #7 | Tiga halaman berita | `feature/news` | @username-2 | 🔴 Changes requested |
| #8 | README.md | `docs/readme` | @username-4 | ✅ Approved & merged |

Label komentar: 🔴 Wajib diperbaiki - 🟡 Saran - 🟢 Nit (hal kecil, opsional).

---

## PR #3 - Tambah halaman Harga

- **Branch:** `feature/pricing` -> `main`
- **Author:** @username-1
- **File di PR:** `pricing.html`

**Deskripsi:** Menambahkan `pricing.html` berisi paket SD, SMP, SMA, dan UTBK Intensif beserta tombol pendaftaran dan catatan diskon tahunan.

### Komentar review

**`pricing.html` baris 50-58**

```html
	<section id="inner-headline">
	...
	</div>
	<section id="content">
```

🔴 **Wajib diperbaiki.** Tag `<section id="inner-headline">` (baris 50) tidak pernah ditutup dengan `</section>`, sehingga `#content` tersarang di dalamnya dan gaya header judul ikut mengenai konten.

```suggestion
	</div>
	</section>
	<section id="content">
```

**`pricing.html` baris 68, 90, 112**

```html
<h6>Rp 99000 / bln</h6>
<h6>Rp129.000 / bln</h6>
<h6>Rp 159.000 /bulan</h6>
```

🔴 **Wajib diperbaiki.** Format harga tidak konsisten di ketiga paket (spasi setelah "Rp", titik ribuan, "bln" vs "bulan"). Samakan dengan format `Rp99.000 / bulan` seperti di meta description dan paket UTBK (baris 134).

```suggestion
<h6>Rp99.000 / bulan</h6>
```

(Terapkan pola yang sama untuk Rp129.000 dan Rp159.000.)

**`pricing.html` baris 80, 102, 124**

```html
<a href="#" class="btn btn-medium btn-theme"><i class="icon-bolt"></i> Daftar Sekarang</a>
```

🔴 **Wajib diperbaiki.** Tombol memakai `href="#"` sehingga tidak ke mana-mana. Arahkan ke halaman Kontak, seperti tombol paket UTBK Intensif (baris 146).

```suggestion
<a href="contact.html" class="btn btn-medium btn-theme"><i class="icon-bolt"></i> Daftar Sekarang</a>
```

**`pricing.html` baris 102**

```html
<a href="#" class="btn btn-medium btn-theme"><i class="icon-bolt"></i> Get Now</a>
```

🔴 **Wajib diperbaiki.** Teks masih bahasa Inggris. Seluruh situs memakai Bahasa Indonesia, jadi ganti menjadi "Daftar Sekarang" (sekaligus perbaiki `href="#"` di atas).

**`pricing.html` baris 33**

```html
<a class="navbar-brand" href="index.html"><img src="img/logo.png"/></a>
```

🟡 **Saran.** Gambar logo belum punya atribut `alt`. Tambahkan untuk aksesibilitas dan SEO.

```suggestion
<a class="navbar-brand" href="index.html"><img src="img/logo.png" alt="JendEdu"/></a>
```

**`pricing.html` baris 153**

```html
<p class="text-center" style="margin-top:30px; color:red; font-size:18px;">
```

🟡 **Saran.** Warna merah dan ukuran font lewat inline style terlalu mencolok dibanding tema situs dan sulit dirawat. Hapus `color` dan `font-size`; margin atas boleh dipertahankan sementara.

```suggestion
<p class="text-center" style="margin-top:30px;">
```

**Keputusan: Request changes**

Checklist yang harus diperbaiki sebelum approval:

- [ ] Tutup `</section>` untuk `#inner-headline` (baris 50-58)
- [ ] Samakan format semua harga (`Rp99.000 / bulan`) (baris 68, 90, 112)
- [ ] Ganti semua `href="#"` pada tombol "Daftar Sekarang" menjadi `contact.html` (baris 80, 102, 124)
- [ ] Ganti "Get Now" menjadi "Daftar Sekarang" (baris 102)
- [ ] Tambah `alt` pada logo (baris 33)
- [ ] Hapus `color:red; font-size:18px;` dari inline style (baris 153)

Versi setelah diperbaiki: [`review/codes/pricing.html`](codes/pricing.html)

---

## PR #4 - Navbar dan footer bersama (CSS)

- **Branch:** `feature/navbar-footer` -> `main`
- **Author:** @username-2
- **File di PR:** `css/style.css` (serta `img/logo.png`)

**Deskripsi:** Membawa `css/style.css` berisi gaya navbar, footer, dan artikel/berita yang dipakai semua halaman. Markup navbar dan footer sendiri ada di dalam tiap halaman HTML.

### Komentar review

**`css/style.css` baris 8**

```css
@import url('http://fonts.googleapis.com/css?family=Noto+Serif:400,400italic,700|Open+Sans:400,600,700');
```

🔴 **Wajib diperbaiki.** Impor font memakai `http://`, memicu peringatan mixed content di situs HTTPS dan font bisa diblokir.

```suggestion
@import url('https://fonts.googleapis.com/css?family=Noto+Serif:400,400italic,700|Open+Sans:400,600,700');
```

**`css/style.css` baris 89-92**

```css
.navbar-brand {
    font-size: 18px;
    margin-top: 5px;
}
```

🔴 **Wajib diperbaiki.** Aturan `.navbar-brand` sudah ada di baris 76-85; blok kedua ini menimpa `font-size` dan `margin-top` secara diam-diam sehingga logo/brand bergeser dan sulit dilacak. Hapus blok duplikat ini; ubah nilai di aturan pertama bila memang perlu.

**`css/style.css` baris 100**

```css
header .navbar-default{
    min-width: 960px;
    background-color: #FFFFFF;
}
```

🔴 **Wajib diperbaiki.** Lebar minimum tetap 960px memaksa navbar melebihi layar ponsel dan tablet sehingga muncul scroll horizontal. Navbar Bootstrap sudah responsif; hapus baris ini.

**`css/style.css` baris 1013**

```css
footer ul.link-list li a{
	color: #0E7A66;
}
```

🟡 **Saran.** Hijau tua di atas latar footer `#14A085` kontrasnya sangat rendah (sulit dibaca, tidak lolos WCAG). Gunakan putih seperti `footer a` (baris 1328).

```suggestion
	color: #FFFFFF;
```

**`css/style.css` baris 1788**

```css
	line-heigth: 1.8em;
```

🔴 **Wajib diperbaiki.** Typo nama properti (`line-heigth`), sehingga diabaikan browser dan jarak baris isi artikel/berita tidak sesuai desain.

```suggestion
	line-height: 1.8em;
```

**`css/style.css` baris 1792-1793**

```css
	margin-top: 30px !important;
	font-size: 20px !important;
```

🟡 **Saran.** `!important` tidak diperlukan di `.post-body h3` dan menyulitkan penimpaan gaya di kemudian hari. Hapus.

```suggestion
	margin-top: 30px;
	font-size: 20px;
```

**Keputusan: Request changes**

Checklist yang harus diperbaiki sebelum approval:

- [ ] Ubah impor font ke `https://` (baris 8)
- [ ] Hapus aturan `.navbar-brand` ganda (baris 89-92)
- [ ] Hapus `min-width: 960px` pada navbar (baris 100)
- [ ] Kembalikan warna tautan footer ke putih agar kontras cukup (baris 1013)
- [ ] Perbaiki typo `line-heigth` menjadi `line-height` (baris 1788)
- [ ] Hapus `!important` yang tidak perlu (baris 1792-1793)

Versi setelah diperbaiki: [`review/codes/css/style.css`](codes/css/style.css)

---

## PR #5 - Halaman Kontak

- **Branch:** `feature/contact` -> `main`
- **Author:** @username-2
- **File di PR:** `contact.html`

**Deskripsi:** Menambahkan `contact.html` dengan peta lokasi, formulir pesan, dan informasi kontak perusahaan.

### Komentar review

**`contact.html` baris 14-22 dan 73**

```html
<script src="http://maps.google.com/maps/api/js?sensor=false"></script>
...
<div id="map" style="width:100%; height:300px;"></div>
```

🔴 **Wajib diperbaiki.** Ini versi lama Google Maps JavaScript API: parameter `sensor=false` sudah tidak dipakai, tidak ada API key, dan memakai `http://`. Peta kemungkinan besar gagal tampil. Untuk situs statis, cukup pakai embed iframe yang tidak butuh key; skrip `initMap()` (baris 14-22) lalu bisa dihapus.

```suggestion
<iframe src="https://maps.google.com/maps?q=Tebet,%20Jakarta%20Selatan&z=14&output=embed" width="100%" height="300" style="border:0;" allowfullscreen loading="lazy" title="Lokasi JendEdu"></iframe>
```

**`contact.html` baris 96**

```html
<input type="email" class="form-control" id="name" name="email" placeholder="">
```

🔴 **Wajib diperbaiki.** `id="name"` dipakai dua kali (juga di baris 91). Akibatnya `label for="email"` tidak terhubung ke input yang benar dan validasi JS bisa salah sasaran.

```suggestion
<input type="email" class="form-control" id="email" name="email" placeholder="">
```

**`contact.html` baris 116 dan 109**

```html
<h5>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Kirim pesan kepada kami.</h5>
<input type="submit" value="Submit" class="btn btn-default">
```

🔴 **Wajib diperbaiki.** Masih ada teks Lorem ipsum dan tombol berlabel "Submit". Ganti dengan teks Indonesia dan tombol "Kirim Pesan".

```suggestion
<h5>Ada pertanyaan seputar kursus, paket belajar, atau pendaftaran? Tim kami siap membantu Anda.</h5>
```

```suggestion
<input type="submit" value="Kirim Pesan" class="btn btn-default">
```

**`contact.html` baris 80**

```html
<br><br>
```

🟡 **Saran.** Jarak dengan `<br><br>` rapuh di layar kecil. Gunakan satu `<br>` saja seperti halaman lain.

```suggestion
<br>
```

**`contact.html` baris 123** (blok alamat, setelah baris Telepon)

```html
Telepon: (021) 8765-4321<br>
Email: halo@jendedu.id<br>
```

🟡 **Saran.** Tambahkan WhatsApp dan jam layanan (Senin-Sabtu, 08.00-20.00 WIB) agar sama dengan footer, dan bungkus email dengan tautan `mailto:`.

```suggestion
WhatsApp: 0812-3456-7890<br>
Email: <a href="mailto:halo@jendedu.id">halo@jendedu.id</a><br>
Jam layanan: Senin–Sabtu, 08.00–20.00 WIB<br>
```

**Keputusan: Request changes**

Checklist yang harus diperbaiki sebelum approval:

- [ ] Ganti Google Maps JS API lama dengan iframe embed `https://` (baris 14-22, 73)
- [ ] Hilangkan `id` ganda: `id="email"` untuk input email (baris 96)
- [ ] Hapus Lorem ipsum, ganti tombol menjadi "Kirim Pesan" (baris 116, 109)
- [ ] Ganti `<br><br>` dengan satu `<br>` (baris 80)
- [ ] Lengkapi info kontak: WhatsApp, jam layanan, tautan `mailto:` (baris 123)

Versi setelah diperbaiki: [`review/codes/contact.html`](codes/contact.html)

---

## PR #7 - Tiga halaman berita

- **Branch:** `feature/news` -> `main`
- **Author:** @username-2
- **File di PR:** `berita-beasiswa-jendedu-2027.html` (dan dua halaman berita lainnya)

**Deskripsi:** Menambahkan tiga halaman berita; komentar di bawah memakai `berita-beasiswa-jendedu-2027.html` sebagai contoh.

### Komentar review

**`berita-beasiswa-jendedu-2027.html` baris 63**

```html
<h1>Program Beasiswa JendEdu 2026/2027 Resmi Dibuka</h2>
```

🔴 **Wajib diperbaiki.** Tag pembuka `<h1>` ditutup dengan `</h2>`. Ini merusak struktur DOM dan gagal validasi HTML.

```suggestion
<h1>Program Beasiswa JendEdu 2026/2027 Resmi Dibuka</h1>
```

**`berita-beasiswa-jendedu-2027.html` baris 69**

```html
<img src="img/blog/berita-3.jpg" style="width:100%; margin:20px 0;">
```

🔴 **Wajib diperbaiki.** Gambar tidak punya `alt`, dan memakai inline style. Pakai class yang sudah ada (`img-responsive post-image`) dari CSS artikel.

```suggestion
<img class="img-responsive post-image" src="img/blog/berita-3.jpg" alt="Siswa tersenyum saat belajar di meja, penerima beasiswa JendEdu">
```

**`berita-beasiswa-jendedu-2027.html` baris 96**

```html
<a href="kontak.html">Kontak</a>
```

🔴 **Wajib diperbaiki.** Tautan rusak: nama berkasnya `contact.html`, bukan `kontak.html`.

```suggestion
<a href="contact.html">Kontak</a>
```

**`berita-beasiswa-jendedu-2027.html` baris 85**

```html
<li>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</li>
```

🔴 **Wajib diperbaiki.** Placeholder Lorem ipsum di daftar persyaratan. Isi dengan persyaratan sebenarnya (rapor, surat keterangan, esai, persetujuan orang tua, perangkat dan internet).

```suggestion
<li>Melampirkan fotokopi rapor semester terakhir.</li>
<li>Melampirkan surat keterangan tidak mampu atau surat rekomendasi dari sekolah.</li>
<li>Menulis esai singkat sekitar 300 kata tentang cita-cita dan alasan membutuhkan beasiswa.</li>
<li>Mendapat persetujuan orang tua atau wali.</li>
<li>Memiliki perangkat (ponsel, tablet, atau laptop) dan sambungan internet yang memadai.</li>
```

**`berita-beasiswa-jendedu-2027.html` baris 72**

```html
<br><br>
```

🟡 **Saran.** Hapus `<br><br>` sebagai pengatur jarak. `.post-body` sudah mengatur margin antar elemen.

**`berita-beasiswa-jendedu-2027.html` baris 100**

```html
<a href="index.html" class="btn btn-theme">Back to Home</a>
```

🟡 **Saran.** Teks masih Inggris. Ganti menjadi "Kembali ke Beranda" dan bungkus dengan `<div class="post-back">`.

```suggestion
<div class="post-back">
	<a href="index.html" class="btn btn-theme"><i class="fa fa-angle-left"></i> Kembali ke Beranda</a>
</div>
```

**`berita-beasiswa-jendedu-2027.html` baris 114**

```html
<a href="https://wa.me/6281234567890" target="_blank" class="btn btn-theme">Chat WhatsApp</a>
```

🟡 **Saran.** `target="_blank"` tanpa `rel="noopener"` membuka celah `window.opener`. Selain itu, sidebar "Mulai Belajar" pada dua halaman berita lain mengarah ke `pricing.html`, mohon samakan.

```suggestion
<a href="pricing.html" class="btn btn-theme">Lihat Paket Harga</a>
```

**`berita-beasiswa-jendedu-2027.html` baris 105-110**

```html
<ul class="link-list">
	<li>...berita-kelas-live-utbk-2027.html...</li>
	<li>...berita-kemitraan-sekolah.html...</li>
</ul>
```

🟢 **Nit.** Daftar "Berita Terkini" hanya berisi 2 item; tambahkan berita yang sedang dibuka agar konsisten dengan dua halaman berita lain (dan dengan footer), serta tambahkan widget "Artikel Terbaru" sebelum widget "Mulai Belajar" (baris 111).

```suggestion
	<li><a href="berita-beasiswa-jendedu-2027.html">Program Beasiswa JendEdu 2026/2027 Resmi Dibuka</a></li>
```

**Keputusan: Request changes**

Checklist yang harus diperbaiki sebelum approval:

- [ ] Perbaiki `<h1>...</h2>` menjadi `<h1>...</h1>` (baris 63)
- [ ] Tambah `alt` dan ganti inline style dengan class CSS pada gambar (baris 69)
- [ ] Perbaiki tautan `kontak.html` menjadi `contact.html` (baris 96)
- [ ] Hapus Lorem ipsum, isi persyaratan sebenarnya (baris 85)
- [ ] Hapus `<br><br>`, ganti "Back to Home" menjadi "Kembali ke Beranda" (baris 72, 100)
- [ ] Ganti tombol WhatsApp `_blank` tanpa `rel` dengan tautan ke `pricing.html` (baris 114)
- [ ] Lengkapi sidebar: berita yang sedang dibuka dan widget "Artikel Terbaru" (baris 105-111)
- [ ] Terapkan perbaikan yang sama pada dua halaman berita lainnya bila ada

Versi setelah diperbaiki: [`review/codes/berita-beasiswa-jendedu-2027.html`](codes/berita-beasiswa-jendedu-2027.html)

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
