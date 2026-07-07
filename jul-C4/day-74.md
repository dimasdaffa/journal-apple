## # Day 74: Technology Exploration (Day 1 of Challenge 4)
**Date:** Tuesday, June 30, 2026
**Phase:** Challenge 4 (Technology Exploration - Day 1)

---

### # Activities

* **Challenge 4 Onboarding & Kickoff:** Memulai hari pertama Challenge 4 bertemakan **Technology Exploration**, sebuah fase intensif untuk mengeksplorasi framework atau teknologi baru di ekosistem Apple guna memperluas kapabilitas pengembangan aplikasi kami.
* **Researching Authentication Services Framework:** Melakukan riset mendalam mengenai framework native Apple, **Authentication Services**, untuk memahami bagaimana integrasi autentikasi yang aman dan seamless dilakukan di iOS/macOS. Riset berfokus pada:
  * **Sign in with Apple:** Mempelajari alur autentikasi pengguna secara aman, privat, dan cepat menggunakan Apple ID.
  * **Passkeys & Password Autofill:** Mengeksplorasi dukungan pengisian kata sandi otomatis dan transisi menuju keamanan tanpa sandi (*passwordless*) menggunakan Passkeys (`ASAuthorizationPlatformPublicKeyCredentialProvider`).
  * **ASWebAuthenticationSession:** Memahami cara mengintegrasikan alur autentikasi berbasis web pihak ketiga (seperti OAuth) dengan aman di dalam aplikasi tanpa harus keluar dari konteks aplikasi.
* **Mapping Research to Miro Board:** Menyusun hasil temuan riset secara terstruktur ke dalam board Miro ([Miro Board - Authentication Services](https://miro.com/app/board/uXjVHAACojY=/?share_link_id=304562518553)) untuk kolaborasi dan presentasi tim.

---

### # Key Learning: The Authentication Services Ecosystem

* **Security & User Privacy First:** Salah satu keunggulan terbesar *Sign in with Apple* adalah opsi *Hide My Email* yang menyembunyikan email asli pengguna dengan email relai Apple. Hal ini meminimalkan risiko kebocoran data pengguna dan meningkatkan kenyamanan privasi.
* **Seamless Web-to-App Flows:** Menggunakan `ASWebAuthenticationSession` memberikan antarmuka terpadu yang aman untuk otentikasi berbasis browser web. Framework ini otomatis menangani token dan *callback* kembali ke aplikasi secara aman menggunakan skema URL kustom (*Custom URL Scheme*).
* **The Rise of Passkeys:** Mempelajari bagaimana Apple mempromosikan Passkeys sebagai pengganti kata sandi tradisional dengan memanfaatkan otentikasi biometrik Face ID atau Touch ID, memberikan keamanan kriptografis yang sangat tinggi serta bebas dari ancaman phising.

---

### # Reflection

Hari pertama Challenge 4 bertema "Technology Exploration" ini membuka wawasan baru bagi saya tentang bagaimana Apple menangani keamanan dan kenyamanan pengguna dalam proses masuk log (*login*). Diberikan tugas untuk meriset **Authentication Services Framework** memaksa saya melihat ke balik layar bagaimana sebuah aplikasi iOS dapat melakukan verifikasi identitas secara sangat aman namun tetap memberikan pengalaman pengguna yang sangat mulus (*frictionless*). 

Menuangkan hasil riset ini ke dalam Miro board membantu saya menyederhanakan konsep teknis yang kompleks menjadi alur visual yang mudah dipahami. Fase eksplorasi ini sangat penting karena fitur autentikasi adalah pintu gerbang utama dari hampir setiap aplikasi modern. Saya merasa lebih siap untuk merancang sistem keamanan yang sesuai dengan panduan Apple pada proyek-proyek mendatang.

---
