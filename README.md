Karena Anda tidak menggunakan Data Test (Excel/CSV), maka README.md harus disesuaikan untuk mencerminkan bahwa proyek ini adalah script-based automation yang mengandalkan Dynamic Locators.

Berikut adalah draf README.md yang sudah saya optimasi untuk kasus Anda:

Automation Bookstore Testing (Katalon Studio)
Repositori ini berisi proyek automasi pengujian fungsional untuk website Automation Bookstore. Pengujian difokuskan pada validasi fitur filter pencarian dinamis.

📋 Cakupan Pengujian
Search by Author: Memvalidasi bahwa aplikasi dapat memfilter dan menampilkan buku berdasarkan nama pengarang secara akurat.

Search by Title: Memvalidasi bahwa aplikasi dapat memfilter hasil berdasarkan judul buku yang diinputkan.

🛠️ Strategi Automasi & Tantangan Teknis
Sebagai QA Engineer, saya menerapkan beberapa pendekatan teknis untuk memastikan tes ini reliabel:

Parameterized Dynamic XPaths: Alih-alih membuat puluhan Test Object statis, saya menggunakan satu objek dinamis dengan parameter ${bookTitle} dan ${authorName}. Hal ini membuat repositori objek tetap bersih dan mudah dipelihara.

Judul: //h2[contains(normalize-space(), '${bookTitle}')]
Pengarang: //p[contains(normalize-space(), '${authorName}')]

Handling Asynchronous UI: Aplikasi ini menggunakan jQuery Mobile yang melakukan filter secara asinkron. Skrip menggunakan waitForElementVisible untuk menangani perubahan status elemen dari tersembunyi menjadi tampil tanpa menggunakan hardcoded sleep yang tidak efisien.

Element Normalization: Menggunakan fungsi normalize-space() pada XPath untuk menghindari kegagalan deteksi akibat spasi kosong (whitespace) yang sering muncul pada elemen HTML.

🚀 Cara Menjalankan
1. Buka Katalon Studio.
2. Pilih Open Project dan arahkan ke folder hasil clone repositori ini.
3. Buka Test Cases/bookstore_test.
4. Klik dua kali pada salah satu file:
   - searchByAuthor: Untuk menguji fitur pencarian berdasarkan nama pengarang.
   - searchByTitle: Untuk menguji fitur pencarian berdasarkan judul buku.
6. Klik tombol Run (ikon Play) di toolbar atas, lalu pilih browser (contoh: Chrome).

📂 Struktur Proyek
Object Repository/bookstore: Berisi locator dinamis untuk judul dan pengarang.
Test Cases/bookstore_test: Berisi logika sekuensial untuk skenario pengujian pencarian.
