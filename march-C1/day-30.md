## # Day 30: Studio Time (Day 17 of Challenge 1 - Back to Basics)
**Date:** Wednesday, April 22, 2026

### # Activities
* **Architectural Debugging:** Mengidentifikasi hambatan teknis dalam mengimplementasikan *ViewModel* pada *UI static* dan memahami mengapa pendekatan lama (*standard NavigationLink*) tidak lagi memadai untuk skala aplikasi kita.
* **Problem Analysis:** Menganalisis *memory leak* dan *stacking issue* di mana halaman tidak ter-*deallocate* dengan benar, serta memahami batasan *State management* pada struktur yang ada saat ini.
* **Research Phase:** Mulai melakukan eksplorasi teknis mengenai *Programmatic Navigation* (menggunakan `NavigationStack` dan `NavigationPath`) sebagai persiapan untuk implementasi di hari berikutnya.

### # Key Findings: The "Struggle"
* **Beyond Basics:** Saya menyadari bahwa aplikasi kita tidak lagi sesederhana *Challenge 0*. Kebutuhan untuk mengelola *data flow* antara jurnal, fase *lockdown*, dan hasil validasi memerlukan arsitektur yang lebih profesional (MVVM).
* **Navigation Logic:** Menemukan bahwa `NavigationLink` standar terlalu restriktif untuk alur aplikasi yang bersifat *non-linear* dan membutuhkan kontrol navigasi yang dinamis.
* **Architecture Matters:** Saya belajar bahwa kode yang "jalan" tidak selalu berarti kode yang "sehat". *Struggle* hari ini menyadarkan saya pentingnya *memory management* agar aplikasi tetap ringan dan responsif.

### # Key Learning
* **Resilience in Coding:** *Struggle* hari ini menguji **Courage** saya. Bukannya menyerah, saya justru termotivasi untuk mencari tahu bagaimana aplikasi profesional mengelola navigasi mereka.
* **The "Ah-ha" Moment:** Memahami bahwa *View* harusnya bersifat "bodoh" (hanya menampilkan data) dan *ViewModel* adalah "otak"-nya. Memisahkan keduanya adalah kunci untuk mengatasi kekacauan kode yang saya alami.
* **Patience:** Mengakui bahwa tidak semua hal bisa diselesaikan dalam satu hari. Memilih untuk berhenti sejenak dan menjadwalkan riset *Programmatic Navigation* untuk esok hari adalah keputusan yang bijak.

### # Reflection
Hari ini mungkin terasa berat karena kode tidak berjalan seperti yang diharapkan. Namun, saya melihat ini sebagai progres yang positif. Kegagalan hari ini justru membukakan mata saya pada konsep arsitektur yang selama ini hanya saya dengar sekilas. Saya merasa lebih tenang setelah memetakan masalahnya, dan saya siap untuk "menaklukkan" navigasi aplikasi ini di hari Kamis.

---