Link GitHub Pages: https://USERNAME_GITHUB_KAMU.github.io/kedai_kopi/

# Kedai Kopi Senja — Website Statis (Minggu 2 & Minggu 3)

---

## Jawaban Pertanyaan Coding 2 (Minggu 3: CSS, Layout, dan Responsive Design)

### a. Sebutkan satu bagian yang kamu susun dengan Flexbox dan satu bagian dengan Grid. Mengapa pilihan itu cocok untuk kedua bagian tersebut?

1. **Bagian yang disusun dengan Flexbox:** Bagian **Header dan Navigasi** (`.header-inner` dan `.nav-list`).  
   **Alasan:** Flexbox sangat cocok untuk tata letak **satu dimensi** (satu arah, baik satu baris maupun satu kolom). Pada header, kita hanya perlu mengatur susunan nama kedai dan deretan menu navigasi dalam satu sumbu: tersusun vertikal ke bawah (`flex-direction: column`) saat di layar ponsel, lalu berubah menjadi satu baris horizontal (`flex-direction: row`) dengan nama kedai di kiri dan menu navigasi di kanan (`justify-content: space-between`) saat layar melebar.

2. **Bagian yang disusun dengan Grid:** Bagian **Daftar Card Menu** (`.menu-grid`) di halaman `menu.html`.  
   **Alasan:** CSS Grid dirancang untuk tata letak **dua dimensi** (mengatur baris dan kolom sekaligus). Dengan Grid, kita bisa dengan mudah membagi ukuran kolom yang sama rata menggunakan `grid-template-columns` secara responsif (*mobile-first*): 1 kolom (`1fr`) di ponsel, 2 kolom (`repeat(2, 1fr)`) mulai lebar `600px`, dan 3 kolom (`repeat(3, 1fr)`) mulai lebar `960px`, sambil menjaga tinggi setiap *card* pada baris yang sama tetap rapi dan sejajar.

---

### b. Ceritakan satu aturan CSS yang awalnya tidak berlaku. Apa yang kamu lihat di panel Styles, dan bagaimana kamu memperbaikinya?

Saat pertama kali menata tautan navigasi di dalam header, saya mencoba mengubah warna teks link menjadi krem (`#FBF9F5`) dengan menuliskan aturan warna pada elemen `<li>` atau `.nav-list` saja, serta sempat menulis aturan umum `a { color: #3E2723; }` di bagian bawah file CSS. Akibatnya, warna teks link di navigasi tidak berubah seperti yang diinginkan.

**Apa yang terlihat di panel Styles (Developer Tools):**  
Ketika saya klik kanan pada teks link navigasi lalu memilih **Inspect**, di tab **Elements -> panel Styles** terlihat bahwa properti `color` yang saya pasang pada `.nav-list` tidak menang pada elemen `<a>` karena elemen `<a>` memiliki aturan warna sendiri (baik bawaan *user agent stylesheet* browser maupun selector `a` yang ditulis setelahnya), sehingga aturan warna yang kalah tampak **dicoret (*strikethrough*)** di panel Styles.

**Cara memperbaikinya:**  
Saya memperbaikinya dengan membuat *descendant selector* yang lebih spesifik langsung ke elemen tautannya, yaitu `.nav-list a { color: #FBF9F5; }`. Karena `.nav-list a` memiliki *specificity* lebih tinggi (gabungan 1 class dan 1 elemen) dan menargetkan elemen `<a>` secara langsung, aturan tersebut menang di panel Styles dan warna link navigasi berhasil berubah.

---

## Jawaban Pertanyaan Coding 1 (Minggu 2: HTML Statis)

### a. Apa yang muncul di address bar setelah form dikirim, dan mengapa data form tampil di sana? Hubungkan dengan materi method HTTP di Minggu 1.

Setelah form pada `pesan.html` diisi lengkap lalu tombol **Kirim** ditekan, URL di *address bar* berubah dengan tambahan tanda tanya (`?`) yang diikuti oleh pasangan `name=value` dari setiap input form yang dipisahkan dengan tanda `&` (*query string*). Contohnya:

```text
pesan.html?nama=Budi&whatsapp=08123456789&menu=kopi_susu_gula_aren&jumlah=2&cara_ambil=ambil_di_tempat&catatan=es+sedikit
```

Hal ini terjadi karena elemen `<form>` menggunakan atribut `method="get"`. Berdasarkan materi **method HTTP di Minggu 1**, metode **HTTP GET** mengirimkan data parameter langsung melalui URL (*query string*), bukan di dalam *body* pesan HTTP, sehingga seluruh isian form tampak di *address bar*.

### b. Pilih satu bagian halamanmu yang memakai element semantic. Mengapa kamu memilih element itu dan bukan `<div>`?

Salah satu bagian yang memakai elemen semantik adalah bagian navigasi di dalam `<header>`, yaitu menggunakan elemen **`<nav>`** (serta `<header>`, `<main>`, `<section>`, `<article>`, dan `<footer>`).

Memilih `<nav>` dibanding `<div>` memberikan makna struktur yang jelas bagi browser, mempermudah alat bantu pembaca layar (*screen reader*) untuk mengenali menu navigasi utama (*accessibility*), dan membuat kode HTML jauh lebih mudah dibaca serta dipelihara dibandingkan deretan `<div>` tanpa makna.
