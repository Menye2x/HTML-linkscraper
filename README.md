# Link Scraper & Organizer

**Link Scraper & Organizer** adalah aplikasi web berbasis lokal (berjalan sepenuhnya di sisi klien/browser) yang dirancang untuk mengekstrak, membersihkan, dan mengelola tautan (URL) dari file atau direktori HTML. Aplikasi ini dibuat dalam satu file tunggal ("HTML link scrapper.html") untuk kemudahan portabilitas dan penggunaan *offline*.

## 💡 Konsep Utama

- **Local-First & Privacy-Focused:** Semua pemrosesan data (parsing HTML, ekstraksi URL, dan penyimpanan) dilakukan secara lokal di dalam browser menggunakan JavaScript dan `localStorage`. Tidak ada data yang diunggah ke server eksternal.
- **Smart Parsing:** Menggunakan `DOMParser` bawaan browser untuk membaca dan mengekstrak tautan secara akurat dari berbagai elemen HTML (bukan hanya tag `<a>`, tetapi juga `<img>`, `<script>`, `<link>`, `<iframe>`, hingga atribut `data-*`).
- **Data Persistence:** Status ruang kerja (workspace), kategori, dan tautan yang disimpan akan tetap ada meskipun browser ditutup berkat fitur autosave lokal.

## ✨ Fitur-Fitur Utama

### 1. Ekstraksi HTML Komprehensif
- Mendukung impor file individual (`.html`, `.htm`) maupun impor seluruh direktori/folder.
- Mendukung metode *Drag-and-Drop* untuk memuat file dengan cepat.
- Mengekstrak berbagai tipe media: Tautan/Anchor, Gambar, Skrip, Stylesheet, Embed (iframe/object), Media (video/audio), dan Form.

### 2. Pengelompokan Cerdas (*Smart Auto-Categorize*)
Aplikasi dapat mendeteksi dan mengelompokkan tautan secara otomatis berdasarkan struktur dokumen aslinya:
- **Heading Sections:** Mengelompokkan tautan berdasarkan tag H1-H6 terdekat.
- **HTML Classes:** Mengelompokkan berdasarkan *class* CSS yang sering digunakan (mengabaikan class *noise* atau *utility*).
- **Data Attributes:** Mengelompokkan berdasarkan atribut `data-*`.
- **Hierarki Induk (Parents):** Berdasarkan path elemen induk (DOM tree).
- **Domain:** Mengelompokkan tautan eksternal berdasarkan nama domain.

### 3. Normalisasi URL (*URL Normalization*)
Alat pembersih URL bawaan yang dapat:
- Menambahkan prefix `https://` pada URL yang hanya menggunakan `www.`.
- Mendekode URL (mengubah `%20` menjadi spasi, `%2F` menjadi `/`, dll).
- Menghapus parameter pelacakan (*tracking parameters*) seperti `utm_*`, `fbclid`, `gclid`, dll.
- Mengekstrak URL target asli dari tautan *redirect* (misal: tautan redirect Google, Facebook, atau YouTube).

### 4. Manajemen & Organisasi Workspace
- **Sistem Kategori:** Buat, ubah nama, dan hapus kategori kustom.
- **Drag-and-Drop Reordering:** Pindahkan tautan antar kategori atau ubah urutan tautan hanya dengan menarik item.
- **Bulk Actions:** Pilih banyak tautan sekaligus untuk dipindahkan atau dihapus.
- **Pencarian Real-time:** Cari tautan berdasarkan label, URL, elemen asal, atau nama file.

### 5. Opsi Ekspor Data
- **TXT per Kategori:** Ekspor tautan setiap kategori menjadi file `.txt` terpisah (dipisahkan dengan titik koma `;`).
- **Detailed Report:** Laporan teks lengkap yang menyertakan konteks label, file sumber, dan kategori.
- **PDF / Print:** Cetak laporan langsung ke dalam format PDF dengan tata letak yang bersih.

### 6. Antarmuka Pengguna (UI/UX)
- Tampilan responsif yang mendukung perangkat desktop maupun *mobile*.
- Dukungan *Dark Mode* dan *Light Mode*.
- Indikator status jaringan (Online/Offline).

## 🚀 Cara Penggunaan

1. Buka file `HTML link scrapper.html` langsung di browser web modern Anda (Chrome, Firefox, Edge, Safari, dll). Tidak perlu web server.
2. Klik tombol **Import HTML** atau seret-dan-lepas (*drag-and-drop*) file HTML ke dalam jendela browser.
3. Aplikasi akan langsung mengekstrak semua tautan.
4. Gunakan fitur **Smart Group** untuk mengkategorikan ribuan tautan secara otomatis, atau gunakan fitur **Normalize** untuk membersihkan tautan pelacakan.
5. Klik **Export** untuk menyimpan hasil ekstraksi Anda.