# Laporan Proyek Machine Learning - Harry Mardika

## Project Overview

### Latar Belakang
Dalam era digital yang terus berkembang, hiburan melalui film telah menjadi bagian penting yang mengisi kehidupan sehari-hari kita. Namun, dengan berlimpahnya pilihan film yang tersedia di berbagai platform, pengguna seringkali merasa kebingungan untuk memilih film yang cocok dengan preferensi dan selera mereka yang unik. Maka dari itu, tujuan dari proyek ini adalah untuk memberikan solusi yang memadai dengan mengembangkan sebuah sistem rekomendasi film yang tidak hanya inovatif, tetapi juga efektif. Sistem ini akan memberikan rekomendasi yang akurat dan personal kepada setiap pengguna berdasarkan preferensi film, sejarah penontonannya, dan faktor-faktor lainnya yang relevan. Dengan demikian, diharapkan pengguna dapat menemukan film-film yang sesuai dengan selera mereka dengan lebih mudah dan lebih cepat.

### Pentingnya Proyek
- Meningkatkan Pengalaman Pengguna: Sistem rekomendasi dapat meningkatkan pengalaman pengguna dengan menyediakan rekomendasi yang sesuai dengan preferensi penonton.
- Meningkatkan Retensi Pengguna: Dengan menyediakan rekomendasi yang tepat waktu dan relevan, platform streaming atau penjualan film dapat meningkatkan retensi pengguna.
- Pengoptimalan Konten: Produsen dan distributor film dapat menggunakan sistem rekomendasi untuk memahami tren dan preferensi pengguna, membantu mereka dalam mengoptimalkan portofolio konten mereka.

## Business Understanding
Dalam dunia yang penuh dengan pilihan film yang tak terbatas, pengguna sering kali merasa kewalahan dalam mencari konten yang sesuai dengan preferensi mereka. Oleh karena itu, kami memahami bahwa ada kebutuhan mendesak untuk menciptakan solusi yang efisien dan efektif untuk membantu pengguna menavigasi lautan film yang luas ini. Melalui pemahaman yang dalam terhadap kebutuhan pasar dan kemampuan teknologi, proyek kami bertujuan untuk menghadirkan pengalaman sinematik yang paling memuaskan bagi pengguna, sambil mendukung pertumbuhan bisnis dan industri film secara keseluruhan.

### Problem Statements
- Kepuasan Pengguna Terhadap Pencarian Film: Pengguna sering merasa frustrasi dan kehilangan arah saat mencari film baru untuk ditonton. Mereka membutuhkan solusi yang dapat memberikan rekomendasi film yang sesuai dengan preferensi mereka dengan cepat dan akurat.
- Meningkatkan Retensi dan Loyalitas Pengguna: Tingkat retensi dan loyalitas pengguna merupakan faktor kunci dalam keberhasilan platform streaming. Kami perlu meningkatkan pengalaman pengguna sehingga mereka merasa terhubung secara emosional dengan platform kami dan tetap setia dalam jangka panjang.

### Goals
- Menghasilkan Rekomendasi Film yang Personal dan Akurat: Tujuan utama proyek ini adalah mengembangkan sistem rekomendasi yang dapat menganalisis preferensi pengguna dengan mendalam dan memberikan rekomendasi film yang sesuai dengan preferensi pengguna dengan tingkat kesalahan yang rendah.

- Meningkatkan Tingkat Retensi dan Loyalitas Pengguna: Proyek ini juga bertujuan untuk meningkatkan tingkat retensi dan loyalitas pengguna dengan menyediakan rekomendasi film yang relevan.

### Solution statements
- Content-Based Filtering dengan Cosine Similarity: Kami akan menggunakan pendekatan ini untuk membangun model yang dapat memberikan rekomendasi film berdasarkan kesamaan konten film yang disukai oleh pengguna. Dengan menganalisis atribut genre film, kami dapat menciptakan profil pengguna yang lebih akurat dan memberikan rekomendasi yang lebih relevan.

- Collaborative Filtering dengan Algoritma KMeans Clustering dan Deep Learning: Kami akan menggabungkan kedua teknik ini untuk mengidentifikasi pola-pola yang tersembunyi dalam perilaku penonton dan membuat cluster yang sesuai. Dengan demikian, kami dapat memberikan rekomendasi film yang berdasarkan pada preferensi yang serupa antar pengguna, serta menerapkan algoritma deep learning untuk menghasilkan model yang akurasi sehingga dapat membandingkan antara penggunaan algoritma KMeans dan Deep Learning.

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
