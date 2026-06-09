# Roadmap Belajar

Berikut adalah daftar materi (learning path) yang akan kita pelajari hari demi hari, dibagi menjadi 4 sesi utama sebelum melangkah ke pembahasan proyek.

## Sesi 1: Fondasi Adaptivitas & Size Classes
Fokus: Memahami bagaimana iOS mengenali ukuran layar dan bagaimana SwiftUI mengubah susunan layout secara dinamis.

- Size Classes & Environment
  - Mempelajari konsep Horizontal & Vertical Size Classes (.compact vs .regular).
  - Menggunakan `@Environment(\.horizontalSizeClass)` untuk mendeteksi apakah aplikasi sedang berjalan di iPhone atau iPad.

- Adaptive Layout Containers (iOS 16+)
  - Mempelajari `ViewThatFits`: container yang otomatis memilih view terbaik yang muat di layar.
  - Mempelajari `AnyLayout`: mengubah layout secara dinamis (misal: otomatis berubah dari `HStack` ke `VStack` saat layar menyempit) tanpa merusak state.
  - Mempelajari `LazyVGrid` dan `LazyHGrid` dengan konfigurasi kolom yang fleksibel (`GridItem(.adaptive(minimum: ...))`).

- GeometryReader & Container Queries
  - Menggunakan `GeometryReader` untuk mengambil ukuran spesifik dari sebuah komponen (bukan hanya ukuran layar).
  - Mempelajari cara membatasi penggunaan `GeometryReader` agar tidak memicu over-rendering atau penurunan performa.

## Sesi 2: Structural Layout Hierarchy & Apple HIG Precision
Fokus: Mengatur jarak, keselarasan, tipografi, dan penempatan komponen sesuai standar estetika Apple.

- Tipografi Sistem & Dynamic Type
  - Memahami hierarki teks menggunakan Text Styles bawaan Apple (`.largeTitle`, `.title`, `.body`, `.caption`).
  - Mempelajari Dynamic Type agar ukuran font membesar/mengecil otomatis sesuai pengaturan aksesibilitas pengguna tanpa merusak tampilan UI.

- Spacing, Padding, & Sistem Grid Apple
  - Menerapkan sistem grid kelipatan 8 (`8pt`, `16pt`, `24pt`, `32pt`) yang menjadi standar industri dan Apple HIG untuk padding serta margin.
  - Menggunakan `.frame(maxWidth: ...)` untuk membatasi lebar konten di iPad agar teks tidak terlalu melar dan tetap nyaman dibaca.

- Penempatan Komponen (Apple HIG Component Placement)
  - Memahami aturan Safe Area Insets agar komponen tidak tertutup oleh Dynamic Island, notch, atau home indicator.
  - Memahami kapan tombol aksi utama (Primary Call-to-Action / CTA) diletakkan di bawah sebagai tombol besar dan kapan diletakkan di toolbar (`ToolbarItem(placement: .navigationBarTrailing)`).

## Sesi 3: Navigasi Multikolom & Adaptasi Scene
Fokus: Mengatur alur navigasi aplikasi agar berubah bentuk secara elegan saat dibuka di iPad.

- `NavigationSplitView` (iPad Layout)
  - Mempelajari `NavigationSplitView` (2-kolom atau 3-kolom) yang merupakan standar navigasi modern untuk iPad.
  - Mengatur agar aplikasi otomatis melebur menjadi `NavigationStack` tunggal saat dibuka di iPhone.

- Modal Presentations & Sheets Adaptif
  - Mempelajari perilaku `.sheet` pada iPhone yang otomatis menjadi popover atau kartu di tengah layar pada iPad.
  - Mengontrol ukuran modal menggunakan `.presentationDetents([.medium, .large])`.

- Previewing Adaptivity & Multi-Device Matrix
  - Memaksimalkan Xcode Previews untuk menampilkan beberapa perangkat sekaligus (misal: iPhone SE, iPhone 15 Pro Max, iPad Pro 13-inch).
  - Mempelajari cara melakukan simulasi iPad Split View / Slide Over pada simulator.

## Sesi 4: Aksesibilitas & Validasi Akhir
Fokus: Memastikan aplikasi tidak hanya responsif terhadap ukuran layar, tetapi juga inklusif untuk semua pengguna.

- Accessibility Large Sizes & Layout Breakdown
  - Menguji UI ketika pengguna mengaktifkan ukuran teks ekstrem (Accessibility Sizes).
  - Membuat fallback layout khusus agar komponen tidak saling bertumpuk saat teks membesar.

- Touch Targets & VoiceOver Basics
  - Memastikan semua area tombol yang bisa ditekan memenuhi batas minimum Apple HIG, yaitu minimal `44x44` poin (atau `48x48` poin untuk standar terbaru) agar mudah ditekan oleh jari.
  - Menambahkan `.accessibilityLabel()` dan `.accessibilityHint()` pada tombol ikon yang tidak memiliki teks.

- Checklist Uji Coba Produksi (Responsive Checklist)
  - Membuat dokumentasi uji coba personal: menguji aplikasi dalam mode Portrait, Landscape, serta Multitasking Mode di iPad untuk memastikan tidak ada UI yang hancur.

# Tujuan Utama Aplikasi

FocalGrid adalah aplikasi interactive photography workshop yang bertujuan melatih insting dan kepekaan mata fotografer pemula dalam menguasai komposisi visual (`Rule of Thirds`, `Golden Ratio`, `Diagonal Lines`, `Leading Lines`).

Aplikasi ini berkolaborasi langsung dengan fotografer profesional yang mendonasikan karya mereka sebagai bahan simulasi. Selain itu, aplikasi ini menyediakan wadah bagi pengguna untuk mempraktikkan teori dalam album koleksi mandiri tanpa mengganggu fokus pembelajaran utama.

# Daftar Fitur Utama

## 1. Menu "Learn Forge" (Core Learning Flow)

- Daftar Komposisi Berbasis Thumbnail Rasio: Halaman awal menyajikan pilihan jenis komposisi menggunakan kartu informasi. Setiap kartu dilengkapi dengan thumbnail bentuk geometris/rasio dari komposisi tersebut.
- Detail Teori & Catatan Fotografer: Halaman penjelasan mendalam mengenai fungsi estetika komposisi, tips dari para ahli, dan tombol utama untuk masuk ke ruang simulasi.
- Imersif Simulator (Menggunakan Foto Fotografer Pro): Halaman simulasi menggunakan foto asli dari fotografer ternama. Foto ditampilkan dalam kondisi mentah (posisinya digeser atau diperbesar secara acak). Pengguna ditantang menyelaraskan foto di bawah garis pandu overlay agar komposisinya menjadi sempurna.

## 2. Menu "Collector Vault" (User Sandbox & Portfolio)

- Album Koleksi Terpisah: Menu khusus pada tab berbeda agar tidak mendistraksi alur belajar pengguna.
- Dump Foto Latihan Mandiri: Wadah bagi pengguna untuk mengunggah foto latihan mereka sendiri ke dalam kategori komposisi yang sesuai.
- Kategorisasi Multi-Dimensi: Pengguna dapat melihat foto berdasarkan dua kategori utama: nama fotografer profesional atau tipe komposisi.

# Teknologi Layout & HIG yang Dipelajari

Melalui proyek ini, Anda akan menutup skill gap dengan mempelajari taktik layout modern SwiftUI berikut:

- Navigasi Adaptif Campuran: menerapkan `TabView` sebagai dasar aplikasi. Di tab "Learn Forge", `NavigationSplitView` 2-kolom otomatis menampilkan menu di kiri dan detail di kanan pada iPad, serta melebur menjadi `NavigationStack` tunggal pada iPhone.
- Dinamika Komponen (`AnyLayout` & `ViewThatFits`): pada layar simulasi, menggunakan `AnyLayout` untuk memindahkan panel kontrol dari bawah foto di iPhone ke samping foto di iPad. `ViewThatFits` mengubah barisan tombol aspek rasio menjadi menu drop-down ketika ruang horizontal terlalu sempit.
- Kepresisian Spasial & Sistem Grid Apple: menerapkan sistem spacing kelipatan 8 (`8pt`, `16pt`, `24pt`) dan membatasi lebar teks teori maksimal `600pt` di iPad agar teks tetap nyaman dibaca.
- Skala Gambar & Koordinat Relatif (Persentase): menempatkan objek secara responsif menggunakan koordinat berbasis persentase terhadap ukuran layar perangkat.
- Aksesibilitas Ekstrem: memastikan area sentuh minimal `48x48` poin agar ramah jari, serta menggunakan `LazyVGrid` fleksibel di menu "Collector Vault" agar teks tidak terpotong saat Dynamic Type diaktifkan.

# Alur Pengguna secara Berurutan

1. Peluncuran Aplikasi (Root Scene): pengguna membuka aplikasi dan disambut antarmuka bersih berbasis `TabView`. Secara default, pengguna berada di tab "Learn Forge".
2. Memilih Materi Pembelajaran: pengguna melihat daftar menu komposisi fotografi estetik, lengkap dengan thumbnail bentuk rasio, lalu mengetuk kartu pilihan.
3. Membaca Detail Teori: di iPhone, layar detail dipush ke dalam tumpukan navigasi; di iPad, layar tampil di panel kanan. Pengguna membaca penjelasan teori dan mengetuk "Mulai Simulasi".
4. Masuk ke Ruang Simulasi (Immersive Transition): aplikasi menampilkan full-screen cover yang menyembunyikan Tab Bar dan Nav Bar, sehingga fokus pengguna tertuju pada kanvas foto mentah fotografer profesional.
5. Melakukan Interaksi Simulasi:
   - memilih aspek rasio jendela bidik di panel kontrol;
   - menggeser foto dengan satu jari (pan) dan memperbesar foto dengan dua jari (pinch);
   - menggeser slider kemiringan (tilt) untuk memutar foto.
6. Pemicu Sukses (Magnetic Snap & Haptic): ketika objek utama foto tepat berada di titik pusat spiral emas dalam batas toleransi sistem, foto mengunci otomatis, muncul haptic feedback, dan tombol "Submit Verdict" menyala.
7. Evaluasi & Apresiasi: layar simulasi menutup, pengguna melihat perbandingan hasil kerja dengan versi asli fotografer dan membaca catatan kurator.
8. Eksperimen Mandiri di Menu Koleksi: pengguna berpindah ke tab "Collector Vault", memilih album berdasarkan kategori komposisi, lalu mengunggah foto hasil jepretan pribadi untuk portofolio latihan.

---

# PRODUCT REQUIREMENT DOCUMENT (PRD)

## Dokumen Kontrol

- **Nama Produk:** FocalGrid
- **Target Platform:** iOS & iPadOS (Universal App)
- **Bahasa Pengembangan:** Swift / SwiftUI
- **Versi PRD:** 1.1 (Full Layout Matrix Integration)
- **Tanggal:** 9 Juni 2026
- **Status:** Siap untuk Fase Pengembangan (Development-Ready)

## 1. Ringkasan Eksekutif & Tujuan Produk

FocalGrid adalah aplikasi interactive photography workshop adaptif yang dirancang untuk membantu fotografer pemula mengasah insting dan kepekaan visual terhadap empat teknik komposisi utama: `Rule of Thirds`, `Golden Ratio`, `Diagonal Lines`, dan `Leading Lines`.

Aplikasi ini menjembatani kesenjangan antara teori abstrak dan praktik nyata dengan dua pilar utama:

1. **Fase Belajar & Simulasi Imersif:** pengguna berinteraksi langsung memanipulasi karya terkurasi yang didonasikan oleh fotografer profesional.
2. **Fase Praktik & Pengarsipan (Sandbox):** pengguna mengunggah dan mengategorikan hasil jepretan mandiri ke dalam album terorganisir tanpa mengganggu fokus belajar inti.

Dari sudut pandang teknis, FocalGrid menjadi media pembuktian arsitektur antarmuka modern yang memenuhi standar `Apple Human Interface Guidelines (HIG)`, responsivitas multi-perangkat, dan prinsip aksesibilitas.

## 2. Cakupan Fitur & Kebutuhan Fungsional

### 2.1 Tab Menu 1: "Learn Forge" (Core Learning Flow)

- **FR-LF-01: Dasbor Pembelajaran (Bento Style)**
  - Menampilkan daftar empat komposisi dasar menggunakan kartu informasi bergaya Bento Grid asimetris.
  - Setiap kartu wajib memiliki thumbnail visual statis yang mencerminkan bentuk geometris rasio komposisi terkait.

- **FR-LF-02: Modul Teori & Catatan Kurator**
  - Menampilkan teks edukasi fungsional, kegunaan estetika komposisi, dan tips dari fotografer.
  - Menyediakan tombol utama "Mulai Simulasi" yang mencolok di bawah layar iPhone atau area navigasi iPad.

- **FR-LF-03: Kanvas Simulasi Imersif (Multi-Photo Picker)**
  - Memuat foto kurasi profesional dalam keadaan posisi acak.
  - Menyediakan `Quick Photo Picker` dengan minimal tiga pilihan foto pro per kategori.
  - Menampilkan overlay pandu geometris di atas foto.
  - Menyediakan kontrol `Aspect Ratio Selector` dan `Tilt Slider`.

- **FR-LF-04: Mekanik Pendeteksi Akurasi (Magnetic Snap)**
  - Membaca koordinat titik fokus objek foto berbasis persentase relatif terhadap dimensi gambar.
  - Ketika pengguna mencapai toleransi ≤ 5%, sistem memicu `Magnetic Snap` dan mengaktifkan tombol "Submit Verdict".

- **FR-LF-05: Halaman Evaluasi & Apresiasi**
  - Menampilkan perbandingan `Before vs After` hasil pengguna dan versi asli fotografer.
  - Menyajikan cerita latar belakang pengambilan foto sebagai penutup pembelajaran.

### 2.2 Tab Menu 2: "Collector Vault" (User Sandbox & Portfolio)

- **FR-CV-01: Manajemen Pengunggahan Foto**
  - Menyediakan fitur impor foto atau jepret langsung dari kamera, lalu menyimpan ke penyimpanan lokal aplikasi.

- **FR-CV-02: Kategorisasi Multi-Dimensi**
  - Menyediakan filter dan pengelompokan foto berdasarkan kategori komposisi.
  - Menyediakan pengelompokan berdasarkan nama fotografer profesional sebagai inspirasi.

## 3. Spesifikasi Teknis Antarmuka & Tata Letak Adaptif

Aplikasi wajib menangani perubahan geometri layar secara dinamis tanpa merusak konten foto atau keterbacaan teks.

### 3.1 Peta Matriks Navigasi & Ukuran Layar

- **Root Container:** menggunakan `TabView` untuk memisahkan menu "Learn Forge" dan "Collector Vault".
- **Perilaku iPhone (Compact Width Class):**
  - Navigasi utama menggunakan `NavigationStack` linier.
  - Dasbor menggunakan Bento Grid 2 kolom asimetris.
  - Layar simulasi menempatkan panel kontrol secara vertikal di sepertiga bawah layar.
- **Perilaku iPad (Regular Width Class):**
  - Navigasi utama berubah menjadi `NavigationSplitView` 2 kolom.
  - Sidebar kiri lebar tetap `320pt`, kolom kanan sebagai area detail.
  - Galeri "Collector Vault" berubah dari 2 kolom menjadi 4-5 kolom secara otomatis.

### 3.2 Pemetaan Fitur Layout Modern SwiftUI

#### A. Implementasi `AnyLayout`

- **Lokasi:** `Views/Simulation/SimulationView.swift`
- Membaca `@Environment(\.horizontalSizeClass)`.
- Menggunakan `AnyLayout` untuk membungkus kanvas foto dan panel kontrol.
- Pada `.regular`, menggunakan `HStackLayout`.
- Pada `.compact`, menggunakan `VStackLayout`.

#### B. Implementasi `ViewThatFits`

- **Lokasi:** `Views/Simulation/Components/AspectRatioSelector.swift`
- `ViewThatFits` menilai ruang horizontal untuk menampilkan tombol aspek rasio atau fallback ke menu drop-down.

#### C. Implementasi `LazyVGrid`

- **Lokasi:** `Views/Collector/Components/AlbumBentoGridView.swift`
- Menggunakan `GridItem(.flexible(), spacing: 16)` untuk struktur Bento Box.
- Kartu hero utama dapat ditempatkan di luar grid atau menggunakan sel lebar penuh.
- Jarak komponen di dalam grid dikunci pada `16pt`.

### 3.3 Struktur Folder Arsitektur Tampilan

```text
FocalGrid/
└── Views/
    ├── MainTabView.swift
    ├── LearnForge/
    │   ├── LearnForgeDashboardView.swift
    │   └── CompositionDetailView.swift
    ├── Simulation/
    │   ├── SimulationView.swift
    │   └── Components/
    │       ├── PhotoCanvasView.swift
    │       ├── AspectRatioSelector.swift
    │       └── MultiPhotoPicker.swift
    └── Collector/
        ├── CollectorVaultView.swift
        └── Components/
            └── AlbumBentoGridView.swift
```

### 3.4 Kepresisian Spasial & Aturan Spacing Apple HIG

- Sistem kisi spasial menggunakan aturan grid kelipatan 8.
- Grid item spacing pada galeri: `8pt`.
