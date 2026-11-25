Link GitHub: https://github.com/thirdflwy/kedai_kopi.git

# Kedai Kopi (Minggu 3: CSS, Layout, dan Responsive Design)

### a. Sebutkan satu bagian yang kamu susun dengan Flexbox dan satu bagian dengan Grid. Mengapa pilihan itu cocok untuk kedua bagian tersebut?

**Bagian yang menggunakan Flexbox:** Bagian **Header dan Navigasi** (`.header-inner` dan `.nav-list`). Flexbox cocok digunakan pada bagian ini karena susunannya hanya perlu diatur dalam satu arah. Pada layar ponsel, nama kedai dan menu navigasi disusun secara vertikal menggunakan (`flex-direction: column`). Ketika layar lebih lebar, susunannya berubah menjadi horizontal menggunakan (`flex-direction: row`) dengan nama kedai di sebelah kiri dan menu navigasi di sebelah kanan. Properti (`justify-content: space-between`) digunakan agar keduanya memiliki jarak yang sesuai. Penggunaan Flexbox memudahkan pengaturan posisi elemen tanpa perlu mengatur setiap elemen secara terpisah.

Sementara itu, daftar card menu(`.menu-grid`) di halaman `menu.html`.  menggunakan CSS Grid. Grid dipilih karena bagian ini membutuhkan pengaturan elemen dalam bentuk baris dan kolom sekaligus. Melalui properti `grid-template-columns` jumlah kolom dapat diubah menyesuaikan ukuran layar. Pada ponsel, card ditampilkan dalam satu kolom (`1fr`), kemudian menjadi dua kolom (`repeat(2, 1fr)`) saat lebar layar `600px`, dan tiga kolom (`repeat(3, 1fr)`) pada lebar `960px`. Pengaturan tersebut membuat tampilan menu lebih terstruktur dan ukuran card pada setiap baris tetap sejajar, sehingga layout terlihat lebih rapi ketika dibuka pada ukuran layar yang berbeda.

---

### b. Ceritakan satu aturan CSS yang awalnya tidak berlaku. Apa yang kamu lihat di panel Styles, dan bagaimana kamu memperbaikinya?

Saat mengatur warna teks pada tautan navigasi di header, saya sempat mengalami masalah ketika warna link tidak berubah menjadi krem (`#FBF9F5`) sesuai keinginan. Awalnya, saya mencoba memberikan properti color pada elemen `<li>` atau `.nav-list`, tetapi warna teks pada link tetap tidak berubah. Saya juga sempat menambahkan aturan umum `a { color: #3E2723; }` di bagian bawah file CSS, yang menyebabkan warna link masih mengikuti aturan tersebut.

Untuk mengetahui penyebabnya, saya membuka Developer Tools dengan klik kanan pada teks navigasi, lalu memilih Inspect. Pada tab Elements, tepatnya di panel Styles, terlihat bahwa aturan `color` yang saya terapkan pada `.nav-list` tidak digunakan oleh elemen `<a>` karena elemen tersebut memiliki aturan warna tersendiri. Selain itu, terdapat aturan `color` dari selector `a` yang posisinya lebih bawah pada CSS. Aturan yang tidak digunakan terlihat dicoret (strikethrough) pada panel Styles, sehingga saya dapat mengetahui bahwa deklarasi tersebut kalah dalam penerapan CSS.

Masalah tersebut kemudian saya perbaiki dengan menggunakan descendant selector `.nav-list a { color: #FBF9F5; }` agar warna diterapkan langsung pada elemen tautan di dalam navigasi. Selector ini memiliki tingkat spesifisitas lebih tinggi dibandingkan selector `a` biasa karena menggabungkan class dan elemen. Setelah aturan tersebut diterapkan, warna teks link navigasi berubah menjadi krem sesuai yang diharapkan.