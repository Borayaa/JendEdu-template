# JendEdu

## 1. Nama dan Deskripsi Project

**Nama:** JendEdu

**Deskripsi:** Website profil bisnis kursus online untuk mata pelajaran SD, SMP, dan SMA. Dibangun dari template "Above Educational Bootstrap Responsive Template" (WebThemez), dengan seluruh konten dalam Bahasa Indonesia. Website ini menyajikan katalog kursus, informasi paket harga, galeri kegiatan, berita dan artikel edukatif, serta formulir kontak yang terintegrasi dengan Google Maps.

---

## 2. Anggota Kelompok

| Nama | Username GitHub | Peran |
|------|-----------------|-------|
| [Nama Anggota 1] | @username-1 | Coder 1 |
| [Nama Anggota 2] | @username-2 | Coder 2 |
| [Nama Anggota 3] | @username-3 | Reviewer |
| [Nama Anggota 4] | @username-4 | Dokumentator |

*Catatan: Silakan ganti placeholder di atas dengan nama dan username GitHub asli anggota kelompok.*

---

## 3. Tujuan / Latar Belakang

Banyak siswa membutuhkan pembelajaran yang terjangkau dan fleksibel di luar sekolah formal. JendEdu memerlukan website profesional untuk mempresentasikan program kursus, paket harga, dan konten edukatif kepada calon peserta. Proyek ini juga merupakan kesempatan untuk mempraktikkan kolaborasi tim menggunakan Git/GitHub (branching, pull request, dan code review).

---

## 4. Fitur / Section yang Tersedia

- **Navbar**: Navigasi responsif di semua halaman
- **Slider Beranda**: Menampilkan konten utama dengan FlexSlider
- **Keunggulan**: Daftar keunggulan JendEdu
- **Testimoni**: Ulasan dari peserta kursus
- **Daftar Kursus**: Katalog kursus untuk berbagai jenjang
- **Tentang Kami + Tim**: Profil perusahaan dan tim pengajar
- **Kursus per Jenjang**: SD, SMP, SMA (di halaman courses.html)
- **Galeri dengan Filter**: Portfolio kegiatan (filter SD/SMP/SMA)
- **Paket Harga**:
  - Paket SD: Rp99.000 per bulan
  - Paket SMP: Rp129.000 per bulan
  - Paket SMA: Rp159.000 per bulan
  - Paket UTBK Intensif: Rp249.000 per bulan
- **Kontak**: Google Maps embed + formulir kontak
- **3 Halaman Berita**: Artikel berita terkini tentang JendEdu
- **3 Halaman Artikel**: Artikel edukatif dengan sidebar terkait
- **Footer**: Tautan ke berita dan artikel terbaru

---

## 5. Teknologi yang Digunakan

- **HTML5**: Struktur halaman
- **CSS3**: Styling dan responsive design
- **Bootstrap 3.3.1**: Framework responsive
- **jQuery**: Manipulasi DOM dan interaktivitas
- **FlexSlider**: Slider responsif
- **Fancybox**: Lightbox untuk galeri
- **Quicksand**: Filter galeri
- **Font Awesome 4**: Icon library
- **Google Fonts**: Open Sans, Noto Serif
- **Google Maps Embed**: Integrasi peta lokasi
- **Git & GitHub**: Kontrol versi dan kolaborasi (branch, pull request, code review)
- **Gambar**: Dari Unsplash (Unsplash License)

---

## 6. Cara Menjalankan Secara Lokal

### Opsi 1: Clone Repository

```bash
git clone https://github.com/Borayaa/JendEdu.git
cd JendEdu
```

### Opsi 2: Buka Langsung di Browser

Buka file `index.html` langsung di browser web Anda.

### Opsi 3: Server Lokal dengan Python

Jalankan perintah berikut di folder proyek:

```bash
python3 -m http.server 8000
```

Kemudian buka browser dan akses: `http://localhost:8000`

### Opsi 4: VS Code Live Server

Jika menggunakan VS Code, install ekstension "Live Server" dan klik "Go Live" pada file `index.html`.

---

## 7. Pembagian Tugas & Kontribusi

### Tabel Pembagian Tugas

| Anggota | Peran | Tugas | Branch / Kontribusi |
|---------|-------|-------|-------------------|
| Coder 1 (@username-1) | Coder 1 | Beranda (index.html), Tentang Kami (about.html), Kursus (courses.html), Galeri (portfolio.html), Harga (pricing.html) | feature/homepage, feature/about, feature/courses, feature/gallery, feature/pricing |
| Coder 2 (@username-2) | Coder 2 | Navbar & footer (semua halaman), Kontak (contact.html), 3 Artikel (artikel-*.html), 3 Berita (berita-*.html), CSS artikel | feature/navbar-footer, feature/contact, feature/posts, feature/news |
| Reviewer (@username-3) | Reviewer | Memeriksa setiap Pull Request, memberi komentar, meminta perbaikan, lalu approve & merge setelah diperbaiki. Catatan review ada di folder `review/` | review/review.md, review/codes/ |
| Dokumentator (@username-4) | Dokumentator | README.md dan presentasi project | presentasi/JendEdu-Presentasi.pptx, presentasi/JendEdu-Presentasi-dengan-Naskah.pptx |

### Alur Kerja (Workflow)

Setiap anggota bekerja lewat **fork** pribadi dari [Borayaa/JendEdu](https://github.com/Borayaa/JendEdu). **Tidak ada yang push langsung ke `main`** — `main` hanya berubah lewat Pull Request yang sudah di-approve.

1. **Fork**: Fork `Borayaa/JendEdu` ke akun GitHub sendiri, clone fork tersebut, lalu tambahkan remote `upstream` ke `Borayaa/JendEdu`
2. **Sinkron**: `git switch main` lalu `git pull upstream main`
3. **Buat Branch**: Buat branch baru dari `main` dengan nama sesuai fitur (contoh: `feature/homepage`, `feature/contact`)
4. **Kerjakan Fitur**: Kerjakan halaman/fitur di branch tersebut, lalu cek di browser
5. **Commit**: Commit perubahan dengan pesan yang deskriptif
6. **Push**: Push branch `feature/...` ke fork sendiri (`git push -u origin feature/...`)
7. **Buka Pull Request**: Dari fork ke `Borayaa/JendEdu` branch `main`, minta review ke Reviewer (@username-3)
8. **Review**: Reviewer memeriksa kode, memberi komentar, dan meminta perbaikan jika diperlukan
9. **Perbaikan**: Penulis memperbaiki lalu push lagi ke branch yang sama di fork (PR ter-update otomatis)
10. **Approve & Merge**: Setelah semua komentar terpenuhi, Reviewer approve dan merge PR ke `main`

```
folder lokal ──push branch──▶ fork kamu (origin) ──Pull Request──▶ Borayaa/JendEdu main (upstream)
```

---

## Struktur Folder

```
JendEdu/
├── index.html                                    # Halaman beranda utama
├── about.html                                    # Halaman tentang kami
├── courses.html                                  # Halaman katalog kursus
├── portfolio.html                                # Galeri kegiatan (dengan filter)
├── pricing.html                                  # Halaman harga
├── contact.html                                  # Halaman kontak
├── berita-kelas-live-utbk-2027.html            # Berita 1
├── berita-kemitraan-sekolah.html               # Berita 2
├── berita-beasiswa-jendedu-2027.html           # Berita 3
├── artikel-tips-belajar-matematika-sd.html      # Artikel 1
├── artikel-belajar-online-efektif-smp.html      # Artikel 2
├── artikel-strategi-persiapan-ujian-sma.html    # Artikel 3
├── css/
│   └── style.css                                # Stylesheet utama + style article kustom
├── js/                                          # File JavaScript (jQuery, FlexSlider, dll)
├── fonts/                                       # Font Awesome dan font lainnya
├── img/
│   ├── logo.png                                 # Logo JendEdu
│   ├── slides/                                  # Gambar slider (1440x520)
│   ├── works/                                   # Galeri kegiatan (830x550)
│   ├── blog/                                    # Gambar berita & artikel (830x450)
│   ├── service1-3.jpg                          # Ikon fitur
│   ├── team1-4.jpg                             # Foto tim pengajar (400x400)
│   └── about.jpg                               # Gambar halaman tentang
├── README.md                                    # File dokumentasi ini

```

## 8. Daftar Halaman

| Halaman | File | Deskripsi |
|---------|------|-----------|
| Beranda | `index.html` | Slider, keunggulan, testimoni, kursus unggulan |
| Tentang Kami | `about.html` | Profil perusahaan, keunggulan, tim pengajar |
| Kursus | `courses.html` | Katalog kursus per jenjang (SD, SMP, SMA) |
| Galeri | `portfolio.html` | Galeri kegiatan dengan filter SD/SMP/SMA |
| Harga | `pricing.html` | Paket harga kursus |
| Kontak | `contact.html` | Formulir kontak + Google Maps |
| Berita 1 | `berita-kelas-live-utbk-2027.html` | JendEdu Luncurkan Kelas Live Persiapan UTBK-SNBT 2027 |
| Berita 2 | `berita-kemitraan-sekolah.html` | JendEdu Jalin Kemitraan dengan 50 Sekolah Mitra |
| Berita 3 | `berita-beasiswa-jendedu-2027.html` | Program Beasiswa JendEdu 2026/2027 Resmi Dibuka |
| Artikel 1 | `artikel-tips-belajar-matematika-sd.html` | Tips Belajar Matematika SD |
| Artikel 2 | `artikel-belajar-online-efektif-smp.html` | Belajar Online Efektif untuk SMP |
| Artikel 3 | `artikel-strategi-persiapan-ujian-sma.html` | Strategi Persiapan Ujian SMA |

Berita dan artikel dapat diakses dari footer di setiap halaman (bagian "Artikel Terbaru" dan "Berita Terkini") serta dari sidebar di setiap artikel.

## 9. Kustomisasi

### Mengubah Harga

Edit file `pricing.html` dan cari bagian yang berisi nilai harga. Ubah nilai Rp sesuai kebutuhan.

### Mengubah Informasi Kontak

Informasi kontak tersebar di beberapa tempat:
1. **Footer**: Edit bagian footer di setiap file HTML
   - Alamat: Jl. Pendidikan Raya No. 21 Tebet Jakarta Selatan
   - Email: halo@jendedu.id
   - Telepon: (sesuaikan dengan nomor Anda)

2. **Halaman Kontak** (`contact.html`): Edit bagian kontak dan update Google Maps embed

### Menambah Artikel Baru

1. Buat copy dari salah satu file artikel yang ada (contoh: `artikel-tips-belajar-matematika-sd.html`)
2. Ubah judul, konten, dan metadata sesuai kebutuhan
3. Simpan dengan nama baru (format: `artikel-[topik].html`)
4. Tambahkan link ke artikel baru di:
   - Footer setiap halaman (bagian "Artikel Terbaru")
   - Sidebar di artikel-artikel lainnya

### Mengganti Gambar

Saat mengganti gambar, perhatikan dimensi yang sudah ada:
- **Slider**: 1440 × 520 px
- **Galeri/Kursus**: 830 × 550 px
- **Tim Pengajar**: 400 × 400 px
- **Blog/Artikel**: 830 × 450 px
- **Logo**: Sesuaikan dengan ukuran asli

Semua gambar dalam proyek ini bersumber dari Unsplash (Unsplash License) dan bebas digunakan.

## 10. Kredit & Lisensi

Template ini menggunakan "Above Educational Bootstrap Responsive Template" oleh WebThemez di bawah lisensi Creative Commons Attribution 3.0.

**Atribusi:**
- Kredit template: "Template oleh WebThemez" (tautan di footer dapat tetap ada atau diganti sesuai kebijakan)
- Teknologi: Bootstrap 3.3.1, jQuery, FlexSlider, Fancybox, Quicksand, Font Awesome 4
- Gambar: Unsplash (Unsplash License - bebas penggunaan komersial)

Sumber template asli: https://github.com/dawidolko/Website-Templates/tree/master/above-educational-bootstrap-responsive-template

Konten Bahasa Indonesia dibuat khusus untuk JendEdu.
