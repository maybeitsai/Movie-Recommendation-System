# Laporan Proyek Machine Learning - Harry Mardika

## Project Overview

### Latar Belakang
Dalam era digital yang terus berkembang, hiburan melalui film telah menjadi bagian penting yang mengisi kehidupan sehari-hari. Namun, dengan berlimpahnya pilihan film yang tersedia di berbagai platform, pengguna seringkali merasa kebingungan untuk memilih film yang cocok dengan preferensi dan selera yang unik. Maka dari itu, tujuan dari proyek ini adalah untuk memberikan solusi yang memadai dengan mengembangkan sebuah sistem rekomendasi film yang tidak hanya inovatif, tetapi juga efektif. Sistem ini akan memberikan rekomendasi yang akurat dan personal kepada setiap pengguna berdasarkan preferensi film, sejarah penontonannya, dan faktor-faktor lainnya yang relevan. Dengan demikian, diharapkan pengguna dapat menemukan film-film yang sesuai dengan lebih mudah dan lebih relevan.

### Pentingnya Proyek
- Meningkatkan Pengalaman Pengguna: Sistem rekomendasi dapat meningkatkan pengalaman pengguna dengan menyediakan rekomendasi yang sesuai dengan preferensi penonton.
- Meningkatkan Retensi Pengguna: Dengan menyediakan rekomendasi yang tepat waktu dan relevan, platform streaming atau penjualan film dapat meningkatkan retensi pengguna.
- Pengoptimalan Konten: Produsen dan distributor film dapat menggunakan sistem rekomendasi untuk memahami tren dan preferensi pengguna, serta membantu dalam mengoptimalkan portofolio konten.

## Business Understanding
Dalam dunia yang penuh dengan pilihan film yang tak terbatas, pengguna sering kali merasa kewalahan dalam mencari konten yang sesuai dengan preferensi pengguna. Oleh karena itu, dengan adanya kebutuhan mendesak untuk menciptakan solusi yang efisien dan efektif untuk membantu pengguna memilih film yang relevan. Melalui pemahaman terhadap kebutuhan pasar dan kemampuan teknologi, proyek ini bertujuan untuk menghadirkan pengalaman sinematik yang paling memuaskan bagi pengguna, serta mendukung pertumbuhan bisnis dan industri film secara keseluruhan.

### Problem Statements
- Ketidakefisienan dalam Pencarian Film: Pengguna sering kali menghabiskan waktu yang berharga untuk mencari film yang sesuai dengan preferensi mereka, menyebabkan frustrasi dan penurunan kepuasan.
- Keterbatasan dalam Rekomendasi yang Akurat: Algoritma rekomendasi yang kurang canggih cenderung memberikan rekomendasi yang kurang relevan, mengakibatkan pengguna kehilangan minat dan potensi untuk menemukan film-film baru yang menarik.

### Goals
- Menghasilkan Rekomendasi Film yang relevan: Tujuan utama proyek ini adalah mengembangkan sistem rekomendasi yang dapat menganalisis preferensi pengguna dengan mendalam dan memberikan rekomendasi film yang sesuai dengan preferensi pengguna dengan tingkat kesalahan yang rendah.

- Meningkatkan Kepuasan Pengguna: Proyek ini juga bertujuan untuk meningkatkan kepuasan pengguna dengan menyediakan pengalaman pencarian film yang lebih efisien dan memuaskan, sehingga mengurangi kebingungan dan meningkatkan retensi pengguna.

### Solution statements
- Content-Based Filtering dengan Cosine Similarity: Pendekatan ini bertujuan untuk membangun model yang dapat memberikan rekomendasi film berdasarkan kesamaan konten film yang disukai oleh pengguna. Dengan menganalisis atribut genre film, rekomendasi yang lebih relevan dapat diberikan.

- Collaborative Filtering dengan Algoritma KMeans Clustering dan Deep Learning: Proyek ini juga membuat sistem rekomendasi dengan teknik Clustering dan Deep Learning. Kedua teknik ini berfungsi untuk mengidentifikasi pola-pola dalam perilaku penonton dan membuat cluster yang sesuai. Dengan demikian, pemberian rekomendasi film yang berdasarkan penilaian pengguna terhadap film-film yang tersedia dapat dilakukan, serta menerapkan algoritma yang baik untuk menghasilkan model yang memiliki kesalahan yang rendah.

## Data Understanding
Terdapat dua dataset yang digunakan pada proyek ini yaitu movies.csv dan ratings.csv yang bersumber dari kaggle [Movies and Ratings](https://www.kaggle.com/datasets/nicoletacilibiu/movies-and-ratings-for-recommendation-system?select=ratings.csv).
### movies.csv
Dataset movies.csv merupakan kumpulan data tentang film-film beserta genre-genre yang dimilikinya. Dataset ini membantu dalam pemahaman tentang katalog film yang tersedia, serta genre-genre yang populer atau yang umumnya dipilih. Dataset ini terdiri dari 9742 baris dan 3 kolom. Kolom-kolom tersebut adalah sebagai berikut:

- movieId: Merupakan ID unik untuk setiap film dalam dataset. Ini dapat digunakan sebagai kunci untuk menghubungkan data dengan dataset lainnya.
- title: Menyajikan judul film.
- genres: Merupakan genre-genre yang terkait dengan film tersebut.

### ratings.csv
Dataset ratings.csv berisi informasi tentang penilaian yang diberikan oleh pengguna terhadap film-film tertentu. Dataset ini memberikan wawasan tentang preferensi pengguna terhadap film-film tertentu. Dataset ini terdiri dari 100836 baris dan 4 kolom. Kolom-kolom tersebut adalah sebagai berikut:
- userId: Merupakan ID unik untuk setiap pengguna yang memberikan penilaian.
- movieId: Merupakan ID unik untuk setiap film yang dinilai.
- rating: Menunjukkan penilaian yang diberikan oleh pengguna terhadap film tersebut.
- timestamp: Merupakan timestamp ketika penilaian diberikan.

### Exploratory Data Analysis (EDA)
- Menampilkan dataset movies
  
  Langkah pertama adalah memuat dataset movies.csv yang berisi informasi tentang film-film beserta genre film tersebut. Dataset kemudian ditampilkan untuk memeriksa struktur dan konten awalnya.
  
  |      | movieId |                   title                   |                      genres                     |
  |:----:|:-------:|:-----------------------------------------:|:-----------------------------------------------:|
  |   0  |    1    |                          Toy Story (1995) | Adventure\|Animation\|Children\|Comedy\|Fantasy |
  |   1  |    2    |                            Jumanji (1995) |                    Adventure\|Children\|Fantasy |
  |   2  |    3    |                   Grumpier Old Men (1995) |                                 Comedy\|Romance |
  |   3  |    4    |                  Waiting to Exhale (1995) |                          Comedy\|Drama\|Romance |
  |   4  |    5    |        Father of the Bride Part II (1995) |                                          Comedy |
  |  ... |   ...   |                                       ... |                                             ... |
  | 9737 |  193581 | Black Butler: Book of the Atlantic (2017) |              Action\|Animation\|Comedy\|Fantasy |
  | 9738 |  193583 |              No Game No Life: Zero (2017) |                      Animation\|Comedy\|Fantasy |
  | 9739 |  193585 |                              Flint (2017) |                                           Drama |
  | 9740 |  193587 |       Bungo Stray Dogs: Dead Apple (2018) |                               Action\|Animation |
  | 9741 |  193609 |       Andrew Dice Clay: Dice Rules (1991) |                                          Comedy |

- Menghitung jumlah film pada dataset movies
  
  Setelah dataset movies ditampilkan, langkah selanjutnya adalah menghitung jumlah film yang terdapat dalam dataset tersebut. Hal ini membantu dalam memahami ukuran dataset film yang dimiliki. Jumlah film pada dataset movies adalah 9742.
 
- Melakukan visualisasi jumlah film per genre
  
  Visualisasi digunakan untuk menampilkan jumlah film yang termasuk dalam setiap genre. Hal ini memberikan gambaran visual tentang sebaran genre film dan popularitas relatif dari masing-masing genre.
![jumlah film per genre](https://github.com/maybeitsai/Movie-Recommendation-System/assets/130530985/ceaeef38-91f4-4383-9c00-6a9f1e407ec2)

  
- Menampilkan dataset ratings
  
  Dataset ratings.csv yang berisi informasi tentang penilaian user terhadap film-film dimuat. Dataset ini ditampilkan untuk memeriksa struktur dan konten awalnya.
  |        | userId | movieId | rating |  timestamp |
  |:------:|:------:|:-------:|:------:|:----------:|
  |      0 |      1 |       1 |    4.0 |  964982703 |
  |      1 |      1 |       3 |    4.0 |  964981247 |
  |      2 |      1 |       6 |    4.0 |  964982224 |
  |      3 |      1 |      47 |    5.0 |  964983815 |
  |      4 |      1 |      50 |    5.0 |  964982931 |
  |    ... |    ... |     ... |    ... |        ... |
  | 100831 |    610 |  166534 |    4.0 | 1493848402 |
  | 100832 |    610 |  168248 |    5.0 | 1493850091 |
  | 100833 |    610 |  168250 |    5.0 | 1494273047 |
  | 100834 |    610 |  168252 |    5.0 | 1493846352 |
  | 100835 |    610 |  170875 |    3.0 | 1493846415 |

- Menghitung jumlah user dan film pada dataset ratings
  
  Setelah dataset ratings ditampilkan, langkah berikutnya adalah menghitung jumlah pengguna unik (user) dan jumlah film unik yang ada dalam dataset tersebut. Informasi ini penting untuk memahami cakupan data yang dimiliki. Jumlah pengguna unik adalah 610 dan jumlah film unik adalah 9724.
  
- Menampilkan ringkasan statistik dataset ratings
  
  Statistik deskriptif seperti rata-rata, median, dan kuartil dihitung untuk dataset ratings. Ini membantu dalam memahami distribusi rating yang diberikan oleh pengguna.
  
  |        | userId | movieId | rating |  timestamp |
  |:------:|:------:|:-------:|:------:|:----------:|
  |      0 |      1 |       1 |    4.0 |  964982703 |
  |      1 |      1 |       3 |    4.0 |  964981247 |
  |      2 |      1 |       6 |    4.0 |  964982224 |
  |      3 |      1 |      47 |    5.0 |  964983815 |
  |      4 |      1 |      50 |    5.0 |  964982931 |
  |    ... |    ... |     ... |    ... |        ... |
  | 100831 |    610 |  166534 |    4.0 | 1493848402 |
  | 100832 |    610 |  168248 |    5.0 | 1493850091 |
  | 100833 |    610 |  168250 |    5.0 | 1494273047 |
  | 100834 |    610 |  168252 |    5.0 | 1493846352 |
  | 100835 |    610 |  170875 |    3.0 | 1493846415 |

- Melakukan visualisasi rating film
  
  Visualisasi digunakan untuk memahami distribusi rating yang diberikan oleh pengguna untuk film-film dalam dataset. Grafik seperti histogram memberikan gambaran visual tentang sebaran rating.
  ![distribusi rating film](https://github.com/maybeitsai/Movie-Recommendation-System/assets/130530985/6fe6d8a6-15b9-4ff3-9304-c2c9cfd3239c)

- Menganalisa jumlah rating film per tahun
  
  Analisis dilakukan untuk melihat jumlah rating film yang diberikan oleh pengguna per tahun. Hal ini membantu dalam memahami tren penilaian pengguna dari waktu ke waktu dan mencari pola-pola menarik.
  ![jumlah rating per tahun](https://github.com/maybeitsai/Movie-Recommendation-System/assets/130530985/4b2feb61-060b-484f-8d5f-83da93ab1bee)

## Data Preparation

### Content-Based Filtering
- Menyalin dataset movies

  Langkah pertama adalah menyalin dataset movies. Hal ini bertujuan untuk mempertahankan dataset asli dan mencegah perubahan yang tidak disengaja.
  
- Membuat kolom baru berdasarkan genre

  Kolom baru dibuat berdasarkan genre yang terdapat dalam dataset. Hal ini penting karena content-based filtering menggunakan informasi tentang konten (misalnya, genre film) untuk membuat rekomendasi.
  
- Menghapus baris yang tidak memiliki genre

  Baris-baris yang tidak memiliki informasi genre dihapus. Ini dilakukan agar dataset bersih dan hanya mengandung data yang relevan.
  
- Menampilkan data yang sudah diolah

  Setelah data diproses, hasilnya ditampilkan untuk memastikan transformasi telah dilakukan dengan benar.
  
- Menghapus kolom yang tidak diperlukan

  Kolom-kolom yang tidak diperlukan untuk proses content-based filtering dihapus. Hal ini bertujuan untuk membantu mengurangi dimensi data dan mempercepat proses komputasi.
  
- Menampilkan kolom pada data

  Setelah kolom-kolom yang tidak diperlukan dihapus, kolom-kolom yang tersisa ditampilkan untuk memastikan data telah siap untuk digunakan dalam model.

### Collaborative Filtering

#### Cluster Based Algorithm
- Melakukan import library yang dibutuhkan

  Langkah pertama adalah mengimpor library atau modul yang dibutuhkan untuk menerapkan algoritma collaborative filtering berbasis cluster.
  
- Menggabungkan dataset ratings dan movies

  Dataset ratings dan movies digabungkan untuk membuat user-item matrix yang akan digunakan dalam proses rekomendasi.
  
- Membuat pivot table untuk user-item

  Pivot table dibuat dengan menggunakan dataset gabungan untuk menyusun user-item matrix, yang merupakan dasar dari algoritma collaborative filtering.
  
- Mengisi nilai null dengan 0
  
  Nilai null (atau NaN) dalam user-item matrix diisi dengan 0. Hal ini dilakukan agar matrix bisa diproses dengan benar oleh algoritma.
  
- Menampilkan matrix rating

  Matrix rating yang telah dibuat ditampilkan untuk memastikan bahwa data telah dipersiapkan dengan benar.

#### Deep Learning
- Melakukan import library yang dibutuhkan

  Sama seperti sebelumnya, langkah pertama adalah mengimpor library atau modul yang dibutuhkan untuk menerapkan algoritma collaborative filtering berbasis deep learning.
  
- Menggabungkan dataset ratings dan movies
- 
  Dataset ratings dan movies digabungkan untuk menciptakan dataset yang akan digunakan dalam proses pembelajaran.
  
- Menampilkan dataset

  Dataset yang telah digabungkan ditampilkan untuk memastikan bahwa penggabungan data telah dilakukan dengan benar.
  
- Melakukan proses encoding pada userId dan movieId

  UserId dan movieId dienkripsi agar bisa digunakan dalam model deep learning.
  
- Melakukan mapping pada data

  Data di-mapping untuk memperoleh jumlah user dan film serta nilai maksimum dan minimum rating.
  
- Mencari jumlah user dan movie serta nilai maksimum dan minimum rating

  Langkah ini membantu dalam menentukan dimensi input dan output dari model deep learning.
  
- Melakukan teknik one-hot encoding

  Teknik one-hot encoding diterapkan untuk mewakili data dalam bentuk vektor biner.
  
- Menentukan variabel x dan y

  Variabel x dan y ditentukan untuk melatih model deep learning.
  
- Membagi dataset untuk training dan testing

  Dataset dibagi menjadi subset training dan testing untuk melatih dan mengevaluasi model dengan perbandingan 90% untuk data training dan 10% untuk data testing.

## Modeling

### Content-Based Filtering
Penjelasan Model:
- Model ini menggunakan cosine similarity untuk menghitung seberapa mirip antara film-film berdasarkan fitur genre.
- Cosine similarity digunakan untuk menghasilkan matriks similarity antar film.
- Fungsi get_recommendations digunakan untuk mendapatkan rekomendasi film berdasarkan similarity score.

Berikut adalah top 10 rekomendasi film berdasarkan model ini:
![image](https://github.com/maybeitsai/Movie-Recommendation-System/assets/130530985/cc052e34-baed-4887-b198-c019e6182d6a)

Kelebihan:

- Sederhana dan mudah diimplementasikan.
- Efektif dalam merekomendasikan film berdasarkan kesamaan genre.

Kekurangan:

- Mengabaikan informasi selain genre dalam film, seperti rating atau ulasan pengguna.
- Tidak memperhitungkan preferensi individu pengguna.

### Collaborative Filtering

#### Cluster Based Algorithm
Penjelasan Model:
- Model ini menggunakan algoritma KMeans untuk melakukan clustering terhadap pengguna berdasarkan preferensi mereka terhadap film.
- Pada model ini dilakukan hyperparameter tuning menggunakan GridSearchCV untuk mencari parameter terbaik.
- Fungsi recommend_movies_kmeans digunakan untuk merekomendasikan film berdasarkan kluster pengguna.

Berikut adalah top 10 rekomendasi film berdasarkan model ini untuk pengguna acak:
|   | movieId |                       title                       |             genres             |
|:-:|:-------:|:-------------------------------------------------:|:------------------------------:|
| 0 |   318   |                  Shawshank Redemption, The (1994) |                   Crime\|Drama |
| 1 |   2571  |                                Matrix, The (1999) |       Action\|Sci-Fi\|Thriller |
| 2 |   356   |                               Forrest Gump (1994) |    Comedy\|Drama\|Romance\|War |
| 3 |   260   |         Star Wars: Episode IV - A New Hope (1977) |      Action\|Adventure\|Sci-Fi |
| 4 |   296   |                               Pulp Fiction (1994) | Comedy\|Crime\|Drama\|Thriller |
| 5 |   2959  |                                 Fight Club (1999) | Action\|Crime\|Drama\|Thriller |
| 6 |   593   |                  Silence of the Lambs, The (1991) |        Crime\|Horror\|Thriller |
| 7 |   2858  |                            American Beauty (1999) |                 Drama\|Romance |
| 8 |   858   |                             Godfather, The (1972) |                   Crime\|Drama |
| 9 |   1198  | Raiders of the Lost Ark (Indiana Jones and the... |              Action\|Adventure |

Kelebihan:

- Memperhitungkan preferensi pengguna berdasarkan pola penilaian mereka.
- Mampu menyesuaikan rekomendasi berdasarkan kluster pengguna.

Kekurangan:

- Bergantung pada kualitas clustering, bisa jadi kurang akurat jika cluster tidak merepresentasikan preferensi dengan baik.
- Tidak memperhitungkan informasi film selain kluster pengguna.

#### Deep Learning
Penjelasan Model:

- Model ini menggunakan jaringan saraf tiruan untuk memprediksi rating film yang belum ditonton oleh pengguna.
- Pada model ini dilakukan hyperparameter tuning menggunakan RandomSearch untuk mencari parameter terbaik.
- Fungsi recommend_movies_dl digunakan untuk merekomendasikan film berdasarkan prediksi rating.

Berikut adalah top 10 rekomendasi film berdasarkan model ini untuk pengguna acak:
|   | movieId |                       title                       |             genres             |
|:-:|:-------:|:-------------------------------------------------:|:------------------------------:|
| 0 |   318   |                  Shawshank Redemption, The (1994) |                   Crime\|Drama |
| 1 |   2571  |                                Matrix, The (1999) |       Action\|Sci-Fi\|Thriller |
| 2 |   356   |                               Forrest Gump (1994) |    Comedy\|Drama\|Romance\|War |
| 3 |   260   |         Star Wars: Episode IV - A New Hope (1977) |      Action\|Adventure\|Sci-Fi |
| 4 |   296   |                               Pulp Fiction (1994) | Comedy\|Crime\|Drama\|Thriller |
| 5 |   2959  |                                 Fight Club (1999) | Action\|Crime\|Drama\|Thriller |
| 6 |   593   |                  Silence of the Lambs, The (1991) |        Crime\|Horror\|Thriller |
| 7 |   2858  |                            American Beauty (1999) |                 Drama\|Romance |
| 8 |   858   |                             Godfather, The (1972) |                   Crime\|Drama |
| 9 |   1198  | Raiders of the Lost Ark (Indiana Jones and the... |              Action\|Adventure |

Kelebihan:

- Mampu memperhitungkan pola yang kompleks dan non-linear dalam preferensi pengguna.
- Dapat memanfaatkan informasi lebih lanjut seperti metadata film.
- Mampu memperbaiki rekomendasi seiring waktu dengan training ulang.

Kekurangan:

- Membutuhkan komputasi yang lebih intensif untuk training model.
- Bergantung pada kualitas dan kuantitas data yang digunakan untuk training model.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
