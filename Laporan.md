# LAPORAN TUGAS PEMROGRAMAN WEBSITE LANDING PAGE

## Anggota
| Nama | NRP | 
| :--- | :---: |
| Angela Vania Sugiyono | 5025241226 |
| Maleka Ghaniya | 5025241189 | 

## Deskripsi Latihan
Pada pembelajaran ini kami belajar membuat landing page wisata yang ada di Surabaya. Kami memilih SWK Deles Surabaya sebagai objek wisata yang menjadi inspirasi dalam pembuatan tugas ini. Kami memilih SWK Deles Surabaya sebagai inspirasi dalam pembuatan landing page karena tempat ini merupakan pusat wisata kuliner yang ramai dan memiliki potensi besar untuk dipromosikan secara digital. Landing page ini kami rancang sebagai sarana promosi dan media informasi praktis bagi masyarakat, dengan harapan dapat menarik perhatian lebih banyak pengunjung serta menjadi proyek yang dapat dikembangkan dan direalisasikan di dunia nyata.
Dalam proses pembuatan, kami menggunakan HTML, CSS, dan JavaScript. Struktur utama halaman dibangun menggunakan HTML, yang mencakup elemen header untuk judul dan navigasi, section untuk menampilkan informasi tentang SWK Deles, galeri foto, serta footer berisi kontak dan hak cipta.

Kemudian, CSS digunakan untuk mengatur tampilan visual, seperti warna, tata letak, tipografi, serta membuat tampilan menjadi lebih menarik dan konsisten. Kami juga menerapkan responsive design agar tampilan website dapat menyesuaikan berbagai ukuran layar perangkat.

Selanjutnya, JavaScript digunakan untuk menambah interaktivitas pada halaman, seperti efek animasi, transisi halus saat berpindah menu, serta fitur navigasi yang lebih dinamis.

Berikut merupakan penjelasan kode :

#### Kode HTML
1. Hero Section (Wajah Utama Halaman)
```
HTML

<section class="hero">
    <div class="hero-background-image"></div>
    <div class="hero-content">
        <h1>Sensasi Kuliner Legendaris Surabaya</h1>
        <p class="subtitle">Nikmati kelezatan autentik yang telah menjadi favorit...</p>
        <a href="#reservasi" class="cta-button">Pesan Sekarang</a>
    </div>
</section>
```
Penjelasan: Kode ini menjadi bagian terdepan yang menarik perhatian dan berisi Call-to-Action (CTA).

2. Benefit Card (Bagian Keunggulan)
```
HTML

<div class="features-grid">
    <div class="benefit-card">
        <div class="benefit-icon">🍲</div>
        <h3>Resep Autentik</h3>
        <p>Dimasak dengan resep turun temurun yang telah terbukti kelezatannya...</p>
    </div>
    </div>
```
Penjelasan: Struktur HTML untuk kartu keunggulan yang akan di-styling oleh CSS menjadi elemen terpisah dan rapi.

3. Menu Carousel (Daftar Menu Interaktif)

```
HTML

<div class="menu-carousel">
    <button class="carousel-btn prev-btn" onclick="scrollCarousel('prev')">‹</button>
    <div class="menu-scroll-container" id="menuScroll">
        <div class="menu-card">
            <button class="order-btn">+ Pesan</button>
        </div>
        </div>
    <button class="carousel-btn next-btn" onclick="scrollCarousel('next')">›</button>
</div>
```
Penjelasan: Potongan kode yang menyediakan container yang akan di-scroll secara horizontal, dikendalikan oleh tombol dan JavaScript.

#### Kode JavaScript
1. Carousel Scroll Function
```
JavaScript
function scrollCarousel(direction) {
    const container = document.getElementById('menuScroll');
    const scrollAmount = 320; // Disesuaikan dengan lebar kartu menu + gap
    
    if (direction === 'next') {
        container.scrollLeft += scrollAmount;
    } else {
        container.scrollLeft -= scrollAmount;
    }
}
```
Penjelasan: Fungsi ini memungkinkan pengguna menggeser daftar menu secara terprogram menggunakan tombol navigasi. Nilai scrollAmount yang tetap (320) memastikan pergeseran seukuran satu kartu menu, memberikan pengalaman carousel yang mulus.

2. Event Handlers

A. Order Button Handler:
```
JavaScript

if (e.target.classList.contains('order-btn')) {
    const menuName = e.target.closest('.menu-card').querySelector('h4').textContent;
    alert(`Pesanan "${menuName}" ditambahkan! Hubungi kami...`);
}
```
Penjelasan: Menggunakan Event Delegation `document.addEventListener('click', function(e) {...})` untuk menangani semua tombol '+ Pesan'. Ini efisien karena tidak perlu menambahkan event listener ke setiap kartu menu. Setelah tombol diklik, akan muncul notifikasi nama menu yang dipesan.

B. Form Submission Handler:
```
JavaScript

reservationForm.addEventListener('submit', function(e) {
    e.preventDefault(); // Mencegah reload halaman
    alert('Terima kasih! Reservasi Anda telah kami terima...');
    this.reset(); // Mengosongkan form
});
```
Penjelasan: Mencegah perilaku bawaan submit form `e.preventDefault()`, menampilkan notifikasi keberhasilan, dan mereset form, memberikan umpan balik instan kepada pengguna tanpa meninggalkan halaman.

C. Smooth Scroll:
```
JavaScript

document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    // ...
    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
});
```
Penjelasan: Memberikan efek gulir yang halus (smooth scroll) ketika mengklik tautan internal `<a href="#section">`. Ini meningkatkan user experience dan membuat navigasi terasa lebih modern.

#### Kode CSS
1. Styling Hero Section dan Overlay

```
CSS

.hero {
    color: white;
    padding: 100px 20px 80px;
    text-align: center;
    position: relative;
    overflow: hidden;
    min-height: 70vh;
    display: flex; /* Kunci untuk pemosisian vertikal */
    align-items: center; /* Memosisikan konten di tengah vertikal */
    justify-content: center;
}

.hero::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    /* Gradasi warna ungu kebiruan */
    background: linear-gradient(135deg, rgba(102, 126, 234, 0.8), rgba(118, 75, 162, 0.8));
    z-index: 1; /* Di bawah konten, di atas gambar latar */
}
/* Konten Hero diatur z-index lebih tinggi */
.hero-content {
    position: relative;
    z-index: 2; 
}
```
Penjelasan: Kode ini mengatur tata letak Hero dan menambahkan lapisan gradien untuk meningkatkan keterbacaan.

2. Styling Benefit Card
```
CSS

.benefit-card {
    background: white;
    padding: 40px 30px;
    border-radius: 15px;
    text-align: center;
    /* Memberikan efek bayangan lembut */
    box-shadow: 0 5px 20px rgba(0,0,0,0.08); 
    transition: transform 0.3s ease; /* Transisi untuk efek hover (jika ada) */
}
```
Penjelasan: Kode yang menciptakan efek "kartu" terangkat dengan bayangan lembut.


3. Styling Menu Carousel
```
CSS

.menu-scroll-container {
    display: flex; /* Kunci agar kartu berjejer horizontal */
    overflow-x: scroll; /* Mengaktifkan gulir horizontal */
    scroll-behavior: smooth; /* Gulir halus saat tombol diklik (JS) */
    -webkit-overflow-scrolling: touch; /* Optimasi untuk iOS */
    gap: 20px; /* Jarak antar kartu menu */
    padding-bottom: 10px;
}
/* Memastikan kartu tidak melompat ke baris baru */
.menu-card {
    min-width: 300px;
    flex-shrink: 0;
    /* ... styling card lainnya ... */
}
```
Penjelasan: Kode ini mengatur container menu agar dapat digulir secara horizontal dan memastikan kartu menu berjejer.

4. Media Query untuk Responsivitas
```
CSS

@media (max-width: 768px) {
    h1 {
        font-size: 2.2em; /* Mengurangi ukuran font H1 */
    }
    .benefits-grid {
        /* Mengubah tata letak 4 kolom menjadi 1 kolom */
        grid-template-columns: 1fr; 
    }
    .menu-carousel {
        /* Menyembunyikan tombol navigasi pada perangkat kecil jika ingin mengandalkan sentuhan */
        /* display: none; */ 
    }
}
```
Penjelasan: Kode ini penting untuk penyesuaian tampilan di perangkat seluler.


### Dokumentasi page header
![alt](https://github.com/Maleka0809/tugas_kelompok_landing_page_PWEB/blob/43cc3beec04bcc5b053eed84306b16088d0b0f06/dokumentasi/header_klmpk.png)

### Dokumentasi page benefit section
![alt](https://github.com/Maleka0809/tugas_kelompok_landing_page_PWEB/blob/43cc3beec04bcc5b053eed84306b16088d0b0f06/dokumentasi/benefisec_klmpk.png)

### Dokumentasi page rating
![alt](https://github.com/Maleka0809/tugas_kelompok_landing_page_PWEB/blob/43cc3beec04bcc5b053eed84306b16088d0b0f06/dokumentasi/rate_klmpk.png)

### Dokumentasi page promosi
![alt](https://github.com/Maleka0809/tugas_kelompok_landing_page_PWEB/blob/43cc3beec04bcc5b053eed84306b16088d0b0f06/dokumentasi/promo_klmpk.png)

### Dokumentasi page about
![alt](https://github.com/Maleka0809/tugas_kelompok_landing_page_PWEB/blob/43cc3beec04bcc5b053eed84306b16088d0b0f06/dokumentasi/tentang_klmpk.png)

### Dokumentasi page produk atau menu
![alt](https://github.com/Maleka0809/tugas_kelompok_landing_page_PWEB/blob/43cc3beec04bcc5b053eed84306b16088d0b0f06/dokumentasi/produk_klmpk.png)

### Dokumentasi page layanan
![alt](https://github.com/Maleka0809/tugas_kelompok_landing_page_PWEB/blob/43cc3beec04bcc5b053eed84306b16088d0b0f06/dokumentasi/layanan_klmpk.png)


### Dokumentasi page reservasi
![alt](https://github.com/Maleka0809/tugas_kelompok_landing_page_PWEB/blob/43cc3beec04bcc5b053eed84306b16088d0b0f06/dokumentasi/login_klmpk.png)

### Dokumentasi page FAQ
![alt](https://github.com/Maleka0809/tugas_kelompok_landing_page_PWEB/blob/43cc3beec04bcc5b053eed84306b16088d0b0f06/dokumentasi/FAQ_klmpk.png)

### Dokumentasi page footer
![alt](https://github.com/Maleka0809/tugas_kelompok_landing_page_PWEB/blob/43cc3beec04bcc5b053eed84306b16088d0b0f06/dokumentasi/footer_klmpk.png)

### Link Folder
Bisa dilihat pada [folder](https://github.com/Maleka0809/tugas_kelompok_landing_page_PWEB)

### Link Website
Bisa dilihat pada [Website](https://shzirley.github.io/landingpage-pweb-a/deles.html)




