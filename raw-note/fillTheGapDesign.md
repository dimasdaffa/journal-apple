# Roadmap Belajar

## Challenge Statement
Fill my knowledge/skill gap in visual hierarchy when designing an app.

## Sesi 1: Komposisi Spasial & Kontainer Layout Dinamis
Fokus: Menggunakan berat visual, white space, skala, dan tata letak kontainer dinamis untuk membangun hierarki antarmuka yang logis.

- Struktur Bento Box Asimetris dengan `LazyVGrid`
  - Mendesain struktur dashboard utama dan galeri album menggunakan `LazyVGrid` dan `GridItem`.
  - Mempelajari cara mengatur berat visual (*visual weight*) agar elemen penting (seperti *Featured Hero Card*) mendapatkan perhatian utama dibanding elemen sekunder.

- Penyelarasan Layout Kontekstual dengan `AnyLayout`
  - Mempelajari cara memindahkan panel kontroler dari posisi bawah (iPhone) ke posisi samping (iPad) secara otomatis menggunakan `AnyLayout`.
  - Memastikan *state* interaksi gambar tidak terputus saat struktur layout berubah.

- Proteksi Komponen dari UI Clipping dengan `ViewThatFits`
  - Menerapkan `ViewThatFits` untuk memberikan opsi *fallback* otomatis dari barisan tombol horizontal (`HStack`) menjadi menu *drop-down* yang ringkas jika ruang layar horizontal menyempit.

## Sesi 2: Aturan Spacing & Kepresisian Tipografi HIG
Fokus: Mengatur keterbacaan teks, jarak antar-elemen, dan batas aman visual menggunakan standar baku Apple.

- Hierarki Tipografi Sistem & Aksesibilitas Teks
  - Menerapkan kontras tipografi menggunakan Text Styles bawaan Apple (`.largeTitle`, `.title2`, `.body`).
  - Menguji ketahanan layout agar tidak hancur saat pengguna mengaktifkan ukuran teks ekstrem (*Dynamic Type / Accessibility Large Sizes*).

- Jarak Spasial Sistem Grid Kelipatan 8
  - Mengunci seluruh dimensi *padding*, *margin*, dan *gaps* antarkomponen menggunakan kelipatan 8pt (`8pt`, `16pt`, `24pt`, `32pt`) sesuai panduan HIG.
  - Menggunakan `.frame(maxWidth: 600)` untuk mengisolasi lebar teks teori di iPad agar mata pengguna tidak lelah membaca kalimat yang terlalu panjang.

- Batas Aman & Target Sentuh Fisik (Touch Targets)
  - Memahami aturan *Safe Area Insets* agar komponen tidak terpotong oleh notch atau pulau dinamis (*Dynamic Island*).
  - Memastikan seluruh elemen yang dapat ditekan memiliki area target sentuh minimal `48x48` poin demi kenyamanan fisik jari pengguna.

## Sesi 3: Navigasi Multikolom & Integrasi Kamera Live
Fokus: Memisahkan konteks penggunaan perangkat (iPad sebagai Meja Belajar, iPhone sebagai Senjata Lapangan) melalui navigasi tingkat lanjut dan akses perangkat keras.

- Arsitektur Navigasi Modern `NavigationSplitView`
  - Membangun navigasi 2-kolom pada iPad yang otomatis melebur (*collapse*) menjadi `NavigationStack` tunggal yang linier saat dibuka di iPhone.

- Integrasi Viewfinder Kamera Real-Time (AVFoundation)
  - Menjebloskan fungsi native kamera belakang langsung ke dalam antarmuka aplikasi dengan performa tinggi (60 FPS).
  - Memproyeksikan lapisan pemandu geometri elektrik (*Live Grid Overlay*) secara presisi di atas *Live Viewfinder*.

- Deteksi Kedataran Fisik dengan Giroskop (CoreMotion)
  - Membaca sensor giroskop internal perangkat untuk menghadirkan garis leveler cakrawala virtual (*virtual horizon*) secara *real-time*.

## Sesi 4: Komunikasi Warna, Kontras, & Validasi Akhir
Fokus: Menggunakan warna sebagai media komunikasi semantik dan mengunci kualitas produk sebelum rilis.

- Skema Warna Semantik & Kontras Studio
  - Menerapkan tema *dark mode charcoal* mendalam dengan semburan aksen *warm amber* sebagai penanda hierarki tertinggi ketika kondisi komposisi berhasil terpenuhi (*Magnetic Snap*).

- Integrasi Umpan Balik Taktil (Haptic Feedback)
  - Menyelaraskan getaran motor internal iPhone (`UIImpactFeedbackGenerator`) tepat pada milidetik terjadinya penguncian objek gambar.

- Checklist Uji Coba Lintas Perangkat (Responsive Checklist)
  - Melakukan dokumentasi pengujian dalam mode Portrait, Landscape, serta Multitasking Mode (Split View) di iPad untuk memastikan tidak terjadi kebocoran atau kegagalan tata letak visual.

# Tujuan Utama Aplikasi

FocalGrid adalah aplikasi *interactive photography workshop* adaptif yang dirancang untuk membantu fotografer pemula mengasah insting dan kepekaan visual terhadap empat teknik komposisi utama: `Rule of Thirds`, `Golden Ratio`, `Diagonal Lines`, dan `Leading Lines`.

Aplikasi ini **mengedepankan fungsi native perangkat keras Apple** yang tidak bisa digantikan oleh website responsif biasa, melalui pemisahan konteks penggunaan:

- **iPadOS (The Studio Desk Mode):** Digunakan di dalam ruangan sebagai pusat analisis visual. Memanfaatkan layar besar untuk membaca teori dengan nyaman, melihat portofolio master lewat bento grid, dan melatih insting lewat Simulator Gambar Statis.
- **iOS (The Field Trip Mode):** Digunakan secara lari/bergerak di luar ruangan sebagai alat bidik nyata. Memanfaatkan keunggulan *hardware* berupa **Live Camera Overlay**, **CoreMotion Gyroscope (Virtual Horizon)**, dan **Micro-Haptics** untuk berburu foto asli di dunia nyata.

# Daftar Fitur Utama

## 1. Menu "Learn Forge" (Core Learning Flow)

- Dasbor Pembelajaran Bento Box: sistem menyajikan daftar pilihan jenis komposisi menggunakan kartu bento asimetris. Setiap kartu dilengkapi gambar thumbnail geometri statis yang presisi.
- Modul Teori & Catatan Kurator: menampilkan penjelasan fungsi estetika komposisi dan tips dari fotografer, serta menyediakan tombol utama "Mulai Simulasi" yang mencolok secara hierarki visual.
- Kanvas Simulasi Imersif (Multi-Photo Picker): memuat foto kurasi profesional dalam keadaan teracak. Menyediakan `Quick Photo Picker` (matriks 6 pilihan foto alternatif per materi) dan kontrol aspek rasio pemotretan serta slider kemiringan.
- Mekanik Pendeteksi Akurasi (Magnetic Snap): sistem membaca koordinat titik fokus objek berbasis persentase. Ketika pengguna mencapai toleransi ≤ 5%, sistem memicu `Magnetic Snap` otomatis dan mengaktifkan tombol "Submit Verdict".
- Halaman Evaluasi & Apresiasi: menampilkan perbandingan *Before vs After* hasil penataan pengguna disandingkan dengan versi asli milik sang maestro.

## 2. Menu "Collector Vault" (User Sandbox & Portfolio)

- Album Koleksi Terpisah: menampilkan daftar foto hasil jepretan atau latihan mandiri pengguna yang dikelompokkan menggunakan bento box asimetris yang estetik.
- Dump Foto Latihan Mandiri: menyediakan fitur impor foto dari galeri lokal atau jepretan langsung dari modul kamera internal aplikasi.
- Kategorisasi Multi-Dimensi: menyediakan filter pengelompokan berdasarkan jenis komposisi atau berdasarkan nama fotografer profesional sebagai papan inspirasi.

## 3. Modul Utama Hardware: "Live Field Camera"

- Viewfinder Kamera Real-Time (AVFoundation): aplikasi mampu mengaktifkan kamera belakang secara native dan memproyeksikan garis pandu geometri (*Live Grid Overlay*) secara dinamis di atas aliran video 60 FPS.
- Cakrawala Virtual Giroskop (CoreMotion): sistem wajib membaca data giroskop untuk menampilkan indikator level kedataran (*virtual horizon/leveler*) di tengah layar kamera.
- Real-World Lock & Haptic: ketika tangan pengguna berhasil meluruskan perangkat fisik pada posisi sudut sempurna, sistem wajib menembakkan getaran taktil (*Haptic Feedback*) instan ke tangan pengguna.

# Teknologi Layout & HIG yang Dipelajari

Melalui proyek ini, Anda akan menutup skill gap dengan mempelajari teknik desain visual modern SwiftUI berikut:

- Hierarki Berat Visual & White Space: menggunakan `LazyVGrid` dengan grid item asimetris untuk menonjolkan kartu utama (*hero card*) di atas kartu sekunder, menciptakan alur visual yang intuitif.
- Adaptasi Layout Dinamis: menerapkan `AnyLayout` untuk memindahkan posisi panel inspector dari bawah ke samping, dan `ViewThatFits` untuk fallback otomatis tombol ke menu saat ruang sempit.
- Sistem Spacing Konsisten: menerapkan grid kelipatan 8pt di seluruh komponen dan membatasi lebar teks maksimal 600pt di iPad untuk kenyamanan membaca.
- Integrasi Hardware Native: memanfaatkan `AVFoundation` untuk live camera, `CoreMotion` untuk giroskop, dan `UIImpactFeedbackGenerator` untuk haptic feedback yang presisi.
- Navigasi Multi-Context: menggunakan `NavigationSplitView` untuk iPad yang otomatis collapse menjadi `NavigationStack` pada iPhone sesuai konteks penggunaan.

# Alur Pengguna & Transisi State

| **State Awal** | **Aksi Pengguna** | **Transisi / Efek UI** | **State Akhir** |
|---|---|---|---|
| Aplikasi Diluncurkan | Sistem mendeteksi jenis perangkat aktif. | Aplikasi memuat *Root View* bersih dan mengaktifkan tab "Learn Forge". | Dasbor Utama aktif (iPhone: Bento 2 Kolom / iPad: `NavigationSplitView`). |
| Dasbor Belajar | Mengetuk salah satu kartu Bento Komposisi. | Layar melakukan animasi transisi bergeser (*Push* di iPhone, *Detail loading* di panel kanan iPad). | Halaman Detail Teori aktif. Teks diisolasi maks 600pt di iPad. |
| Detail Teori | Mengetuk tombol aksi utama "Mulai Simulasi". | Memicu presentasi halaman *Full-Screen Cover*. Menyembunyikan Tab Bar dan Nav Bar secara total. | `Immersive Simulator Screen` aktif. Foto dalam kondisi teracak. |
| Ruang Simulator | Mengetuk ikon "Kamera Live" di pojok kanan atas *Toolbar*. | Layar membuka jendela kamera belakang. Sistem meminta izin privasi kamera jika pertama kali. | `Live Field Camera Screen` aktif. |
| Live Kamera Aktif (iPhone) | Mengubah genggaman orientasi iPhone dari Portrait ke Landscape. | `AnyLayout` mendeteksi rotasi fisik. Tombol *shutter* otomatis bergeser mulus ke sisi kanan jempol pengguna. | Kamera menyesuaikan orientasi landscape penuh secara mulus. |
| Membidik Objek Nyata | Menyelaraskan objek dunia nyata dengan pemandu grid di layar. | Sensor giroskop membaca kedataran. Sistem mendeteksi keseimbangan sudut lurus rata air, lalu memicu ketukan motor getar. | Garis grid menyala warna *amber*, tombol jepret menyala penuh. |
| Kondisi Terkunci | Menekan tombol jepret (*shutter*). | Kamera menangkap gambar, memicu flash layar halus, dan secara otomatis menyimpan file foto ke penyimpanan lokal. | Foto sukses terlempar ke tab `Collector Vault` di dalam folder kategori komposisi terkait. |

---

# PRODUCT REQUIREMENT DOCUMENT (PRD)

## Dokumen Kontrol

- **Nama Produk:** FocalGrid
- **Target Platform:** iOS & iPadOS (Universal App)
- **Bahasa Pengembangan:** Swift / SwiftUI
- **Versi PRD:** 1.2 (Live Hardware & Visual Hierarchy Integration)
- **Tanggal:** 10 Juni 2026
- **Status:** Siap untuk Fase Pengembangan (Development-Ready)

## 1. Ringkasan Eksekutif & Tujuan Produk

FocalGrid adalah aplikasi *interactive photography workshop* adaptif yang dirancang untuk membantu fotografer pemula mengasah insting dan kepekaan visual terhadap empat teknik komposisi utama: `Rule of Thirds`, `Golden Ratio`, `Diagonal Lines`, dan `Leading Lines`.

Aplikasi ini mengedepankan fungsi native perangkat keras Apple yang tidak bisa digantikan oleh website responsif biasa.

## 2. Cakupan Fitur & Kebutuhan Fungsional

### 2.1 Tab Menu 1: "Learn Forge" (Core Learning Flow)

- **FR-LF-01: Dasbor Pembelajaran Bento Box**
  - Menyajikan daftar pilihan jenis komposisi menggunakan kartu bento asimetris.
  - Setiap kartu dilengkapi gambar thumbnail geometri statis yang presisi.

- **FR-LF-02: Modul Teori & Catatan Kurator**
  - Menampilkan penjelasan fungsi estetika komposisi dan tips dari fotografer.
  - Menyediakan tombol utama "Mulai Simulasi" yang mencolok secara hierarki visual.

- **FR-LF-03: Kanvas Simulasi Imersif (Multi-Photo Picker)**
  - Memuat foto kurasi profesional dalam keadaan teracak (*scrambled position & zoom*).
  - Menyediakan `Quick Photo Picker` (matriks 6 pilihan foto alternatif per materi).
  - Menyediakan kontrol aspek rasio pemotretan dan slider kemiringan.

- **FR-LF-04: Mekanik Pendeteksi Akurasi (Magnetic Snap)**
  - Membaca koordinat titik fokus objek berbasis persentase relatif.
  - Ketika toleransi ≤ 5%, sistem memicu `Magnetic Snap` otomatis.

- **FR-LF-05: Halaman Evaluasi & Apresiasi**
  - Menampilkan perbandingan *Before vs After* hasil pengguna dengan versi asli.

### 2.2 Tab Menu 2: "Collector Vault" (User Sandbox & Portfolio)

- **FR-CV-01: Manajemen Album Koleksi**
  - Menampilkan daftar foto hasil jepretan atau latihan mandiri pengguna.

- **FR-CV-02: Manajemen Penggudangan Foto**
  - Fitur impor foto dari galeri lokal atau jepretan langsung dari kamera internal.

- **FR-CV-03: Kategorisasi Multi-Dimensi**
  - Filter pengelompokan berdasarkan jenis komposisi atau nama fotografer profesional.

### 2.3 Modul Hardware: "Live Field Camera"

- **FR-LF-06: Viewfinder Kamera Real-Time (AVFoundation)**
  - Mengaktifkan kamera belakang secara native dengan performa 60 FPS.
  - Memproyeksikan garis pandu geometri (*Live Grid Overlay*) secara dinamis.

- **FR-LF-07: Cakrawala Virtual Giroskop (CoreMotion)**
  - Membaca sensor giroskop untuk menampilkan indikator level kedataran.
  - Virtual horizon (*leveler*) di tengah layar kamera.

- **FR-LF-08: Real-World Lock & Haptic**
  - Menembakkan getaran taktil (*Haptic Feedback*) saat sudut sempurna terdeteksi.

## 3. Spesifikasi Teknis Antarmuka & Tata Letak Adaptif

### 3.1 Peta Matriks Navigasi & Ukuran Layar

- **Root Container:** menggunakan `TabView` untuk memisahkan menu "Learn Forge" dan "Collector Vault".

- **Perilaku iPhone (Compact Width Class):**
  - Navigasi utama melebur menjadi `NavigationStack` linier.
  - Dasbor dan Collector Vault menggunakan Bento Grid 2 kolom asimetris.
  - Layar *Live Camera* mengambil 100% penuh layar imersif.

- **Perilaku iPad (Regular Width Class):**
  - Navigasi utama bertransformasi menjadi `NavigationSplitView` 2-kolom.
  - Sidebar kiri berukuran tetap `320pt`, kolom kanan sebagai kanvas detail.
  - Layar *Live Camera* dirender di dalam bingkai jendela terkontrol (View Window) rasio 4:3.

### 3.2 Pemetaan Fitur Layout Modern SwiftUI

#### A. Implementasi `AnyLayout`

- **Lokasi:** `Views/Simulation/SimulationView.swift`
- Membaca kondisi layar lewat `@Environment(\.horizontalSizeClass)`.
- Pada `.regular` (iPad), bertindak sebagai `HStackLayout`.
- Pada `.compact` (iPhone), berubah menjadi `VStackLayout`.

#### B. Implementasi `ViewThatFits`

- **Lokasi:** `Views/Simulation/Components/AspectRatioSelector.swift`
- *Opsi Utama:* Barisan tombol rasio berjejer ke samping.
- *Opsi Fallback:* Tombol **Menu Drop-Down** jika ruang terbatas.

#### C. Implementasi `LazyVGrid`

- **Lokasi:** `Views/Collector/Components/AlbumBentoGridView.swift`
- Menggunakan array konfigurasi `GridItem(.flexible(), spacing: 16)`.
- Kartu koleksi utama mengambil porsi lebar penuh.

#### D. Implementasi Integrasi Hardware

- **Lokasi:** `Views/Simulation/Components/LiveCameraView.swift`
- **iPhone:** *Live Viewfinder* full screen dengan tombol jepret transparan.
- **iPad:** Jendela kontrol rasio 4:3 di panel kanan, instruksi di panel kiri.

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
    │       ├── LiveCameraView.swift
    │       ├── AspectRatioSelector.swift
    │       └── MultiPhotoPicker.swift
    └── Collector/
        ├── CollectorVaultView.swift
        └── Components/
            └── AlbumBentoGridView.swift
```

### 3.4 Kepresisian Spasial & Aturan Spacing Apple HIG

- **Sistem Kisi Spasial:** Seluruh komponen dikunci mati menggunakan aturan grid kelipatan 8.
- **Grid Item Spacing:** `8pt`.
- **Internal Component Padding:** `16pt`.
- **Screen Safe Area Margins:** iPhone `24pt`, iPad `32pt`.
- **Batas Aman Keterbacaan Teks:** Lebar area teks teori iPad maksimal `600pt`.

## 4. Kebutuhan Aksesibilitas & Inklusivitas

- **Target Sentuh Fisik Aman:** Semua elemen interaktif minimal `48 x 48` poin.
- **Dukungan Dynamic Type Skala Ekstrem:** Tata letak elastis dengan text wrap otomatis.
- **Umpan Balik Taktil Semantik:** Getaran sukses (`UIImpactFeedbackGenerator`) pada *Magnetic Snap*.
