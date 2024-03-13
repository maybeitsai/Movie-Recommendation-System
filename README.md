# Laporan Proyek Machine Learning - Harry Mardika

## Project Overview

### Latar Belakang
Dalam era digital yang terus berkembang, hiburan melalui film telah menjadi bagian penting yang mengisi kehidupan sehari-hari. Namun, dengan berlimpahnya pilihan film yang tersedia di berbagai platform, pengguna seringkali merasa kebingungan untuk memilih film yang cocok dengan preferensi dan selera yang unik. Maka dari itu, tujuan dari proyek ini adalah untuk memberikan solusi yang memadai dengan mengembangkan sebuah sistem rekomendasi film yang tidak hanya inovatif, tetapi juga efektif. Sistem ini akan memberikan rekomendasi yang akurat dan personal kepada setiap pengguna berdasarkan preferensi film, sejarah penontonannya, dan faktor-faktor lainnya yang relevan. Dengan demikian, diharapkan pengguna dapat menemukan film-film yang sesuai dengan lebih mudah dan lebih relevan.

### Pentingnya Proyek
- Meningkatkan Pengalaman Pengguna: Sistem rekomendasi dapat meningkatkan pengalaman pengguna dengan menyediakan rekomendasi yang sesuai dengan preferensi penonton.
- Meningkatkan Retensi Pengguna: Dengan menyediakan rekomendasi yang tepat waktu dan relevan, platform _streaming_ atau penjualan film dapat meningkatkan retensi pengguna.
- Pengoptimalan Konten: Produsen dan distributor film dapat menggunakan sistem rekomendasi untuk memahami tren dan preferensi pengguna, serta membantu dalam mengoptimalkan portofolio konten.

## Business Understanding
Dalam dunia yang penuh dengan pilihan film yang tak terbatas, pengguna sering kali merasa kewalahan dalam mencari konten yang sesuai dengan preferensi pengguna. Oleh karena itu, dengan adanya kebutuhan mendesak untuk menciptakan solusi yang efisien dan efektif untuk membantu pengguna memilih film yang relevan. Melalui pemahaman terhadap kebutuhan pasar dan kemampuan teknologi, proyek ini bertujuan untuk menghadirkan pengalaman sinematik yang paling memuaskan bagi pengguna, serta mendukung pertumbuhan bisnis dan industri film secara keseluruhan.

### Problem Statements
- Ketidakefisienan dalam Pencarian Film: Pengguna sering kali menghabiskan waktu yang berharga untuk mencari film yang sesuai dengan preferensi pengguna, menyebabkan kebingungan dan penurunan kepuasan.
- Keterbatasan dalam Rekomendasi yang Akurat: Algoritma rekomendasi yang kurang canggih cenderung memberikan rekomendasi yang kurang relevan, mengakibatkan pengguna kehilangan minat dan potensi untuk menemukan film-film baru yang menarik.

### Goals
- Menghasilkan Rekomendasi Film yang relevan: Tujuan utama proyek ini adalah mengembangkan sistem rekomendasi yang dapat menganalisis preferensi pengguna dengan mendalam dan memberikan rekomendasi film yang sesuai dengan preferensi pengguna dengan tingkat kesalahan yang rendah.

- Meningkatkan Kepuasan Pengguna: Proyek ini juga bertujuan untuk meningkatkan kepuasan pengguna dengan menyediakan pengalaman pencarian film yang lebih efisien dan memuaskan, sehingga mengurangi kebingungan dan meningkatkan retensi pengguna.

### Solution statements
- _Content-Based Filtering_ dengan _Cosine Similarity_: Pendekatan ini bertujuan untuk membangun model yang dapat memberikan rekomendasi film berdasarkan kesamaan konten film yang disukai oleh pengguna. Dengan menganalisis atribut genre film, rekomendasi yang lebih relevan dapat diberikan.

- _Collaborative Filtering_ dengan Algoritma _KMeans Clustering_ dan _Deep Learning_: Proyek ini juga membuat sistem rekomendasi dengan teknik _Clustering_ dan _Deep Learning_. Kedua teknik ini berfungsi untuk mengidentifikasi pola-pola dalam perilaku penonton dan membuat _cluster_ yang sesuai. Dengan demikian, pemberian rekomendasi film yang berdasarkan penilaian pengguna terhadap film-film yang tersedia dapat dilakukan, serta menerapkan algoritma yang baik untuk menghasilkan model yang memiliki kesalahan yang rendah.

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
- timestamp: Merupakan waktu ketika penilaian diberikan.

### Exploratory Data Analysis (EDA)
- Menampilkan dataset "movies"
  
  Langkah pertama adalah memuat dataset ini yang berisi informasi tentang film-film beserta genre film tersebut. Dataset kemudian ditampilkan untuk memeriksa struktur dan konten awalnya.
  
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
  
  Tabel 1. Dataset "movies"

- Menghitung jumlah film pada dataset "movies"
  
  Setelah dataset ditampilkan, langkah selanjutnya adalah menghitung jumlah film yang terdapat dalam dataset tersebut. Hal ini membantu dalam memahami ukuran dataset film yang dimiliki. Jumlah film pada dataset "movies" adalah 9742.
 
- Melakukan visualisasi jumlah film per genre
  
  Visualisasi digunakan untuk menampilkan jumlah film yang termasuk dalam setiap genre. Hal ini memberikan gambaran visual tentang sebaran genre film dan popularitas relatif dari masing-masing genre. Berdasarkan gambar 1, dapat dilihat bahwa genre film terbanyak yaitu drama lalu diikuti dengan genre comedy.
![jumlah film per genre](https://github.com/maybeitsai/Movie-Recommendation-System/assets/130530985/ceaeef38-91f4-4383-9c00-6a9f1e407ec2)

  Gambar 1. Distribusi film per genre

  
- Menampilkan dataset "ratings"
  
  Dataset ini yang berisi informasi tentang penilaian user terhadap film-film dimuat. Dataset ini ditampilkan untuk memeriksa struktur dan konten awalnya.
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
  
  Tabel 2. Dataset "ratings"

- Menghitung jumlah user dan film pada dataset ratings
  
  Setelah dataset "ratings" ditampilkan, langkah berikutnya adalah menghitung jumlah pengguna unik (user) dan jumlah film unik yang ada dalam dataset tersebut. Informasi ini penting untuk memahami cakupan data yang dimiliki. Jumlah pengguna unik adalah 610 dan jumlah film unik adalah 9724.
  
- Menampilkan ringkasan statistik dataset ratings
  
  Statistik deskriptif seperti rata-rata, median, dan kuartil dihitung untuk dataset "ratings". Ini membantu dalam memahami distribusi rating yang diberikan oleh pengguna.
  
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
  
  Tabel 3. Ringkasan statistik

- Melakukan visualisasi rating film
  
  Visualisasi digunakan untuk memahami distribusi rating yang diberikan oleh pengguna untuk film-film dalam dataset. Grafik seperti histogram memberikan gambaran visual tentang sebaran rating. Berdasarkan gambar 2, dapat dilihat kebanyakan pengguna memberikan rating dengan nilai 4 dari 5.
  ![distribusi rating film](https://github.com/maybeitsai/Movie-Recommendation-System/assets/130530985/6fe6d8a6-15b9-4ff3-9304-c2c9cfd3239c)
  
  Gambar 2. Persebaran rating film

- Menganalisa jumlah rating film per tahun
  
  Analisis dilakukan untuk melihat jumlah rating film yang diberikan oleh pengguna per tahun. Hal ini membantu dalam memahami tren penilaian pengguna dari waktu ke waktu dan mencari pola-pola menarik. Berdasarkan gambar 3, dapat dilihat jumlah rating tertinggi terdapat pada tahun 2000.
  ![jumlah rating per tahun](https://github.com/maybeitsai/Movie-Recommendation-System/assets/130530985/4b2feb61-060b-484f-8d5f-83da93ab1bee)

  Gambar 3. Distribusi rating film per tahun

## Data Preparation

### Content-Based Filtering
- Menyalin dataset "movies"

  Langkah pertama adalah menyalin dataset "movies". Hal ini bertujuan untuk mempertahankan dataset asli dan mencegah perubahan yang tidak disengaja.
  
- Membuat kolom baru berdasarkan genre

  Kolom baru dibuat berdasarkan genre yang terdapat dalam dataset. Hal ini penting karena _content-based filtering_ menggunakan informasi tentang konten (misalnya, genre film) untuk membuat rekomendasi.
  
- Menghapus baris yang tidak memiliki genre

  Baris-baris yang tidak memiliki informasi genre dihapus. Ini dilakukan agar dataset bersih dan hanya mengandung data yang relevan.
  
- Menampilkan data yang sudah diolah

  Setelah data diproses, hasilnya ditampilkan untuk memastikan transformasi telah dilakukan dengan benar.
  
- Menghapus kolom yang tidak diperlukan

  Kolom-kolom yang tidak diperlukan untuk proses _content-based filtering_ dihapus. Hal ini bertujuan untuk membantu mengurangi dimensi data dan mempercepat proses komputasi.
  
- Menampilkan kolom pada data

  Setelah kolom-kolom yang tidak diperlukan dihapus, kolom-kolom yang tersisa ditampilkan untuk memastikan data telah siap untuk digunakan dalam model.

### Collaborative Filtering

#### Cluster Based Algorithm
- Mengimpor librari yang dibutuhkan

  Langkah pertama adalah mengimpor librari atau modul yang dibutuhkan untuk menerapkan algoritma collaborative filtering berbasis cluster.
  
- Menggabungkan dataset "ratings" dan "movies"

  Dataset "ratings" dan "movies" digabungkan untuk membuat _user-item matrix_ yang akan digunakan dalam proses rekomendasi.
  
- Membuat pivot tabel untuk _user-item_

  Pivot tabel dibuat dengan menggunakan dataset gabungan untuk menyusun _user-item matrix_, yang merupakan dasar dari algoritma _collaborative filtering_.
  
- Mengisi nilai _null_ dengan 0
  
  Nilai _null_ (atau _NaN_) dalam _user-item matrix_ diisi dengan 0. Hal ini dilakukan agar matrix bisa diproses dengan benar oleh algoritma.
  
- Menampilkan matrix rating

  Matrix rating yang telah dibuat ditampilkan untuk memastikan bahwa data telah dipersiapkan dengan benar.

#### Deep Learning
- Mengimpor librari yang dibutuhkan

  Sama seperti sebelumnya, langkah pertama adalah mengimpor librari atau modul yang dibutuhkan untuk menerapkan algoritma _collaborative filtering_ berbasis _Deep Learning_.
  
- Menggabungkan dataset "ratings" dan "movies"
- 
  Dataset "ratings" dan "movies" digabungkan untuk menciptakan dataset yang akan digunakan dalam proses pembelajaran.
  
- Menampilkan dataset

  Dataset yang telah digabungkan ditampilkan untuk memastikan bahwa penggabungan data telah dilakukan dengan benar.
  
- Melakukan proses _encoding_ pada userId dan movieId

  UserId dan movieId dienkripsi agar bisa digunakan dalam model _Deep Learning_.
  
- Melakukan _mapping_ pada data

  Melakukan _mapping_ pada data untuk memperoleh jumlah user dan film serta nilai maksimum dan minimum rating.
  
- Mencari jumlah pengguna dan film serta nilai maksimum dan minimum rating

  Langkah ini membantu dalam menentukan dimensi input dan output dari model _Deep Learning_.
  
- Melakukan teknik _one-hot encoding_

  Teknik _one-hot encoding_ diterapkan untuk mewakili data dalam bentuk vektor biner.
  
- Menentukan variabel x dan y

  Variabel x dan y ditentukan untuk melatih model _Deep Learning_.
  
- Membagi dataset untuk _training_ dan _testing_

  Dataset dibagi menjadi subset _training_ dan _testing_ untuk melatih dan mengevaluasi model dengan perbandingan 90% untuk data _training_ dan 10% untuk data _testing_.

## Modeling

### Content-Based Filtering
Penjelasan Model:
- Model ini menggunakan _cosine similarity_ untuk menghitung seberapa mirip antara film-film berdasarkan fitur genre.
- _Cosine similarity_ digunakan untuk menghasilkan matriks _similarity_ antar film.
- Fungsi "get_recommendations" digunakan untuk mendapatkan rekomendasi film berdasarkan _similarity score_.

Berikut adalah top 10 rekomendasi film berdasarkan model ini:

|   |                       title                       |           genres          | movieId | Similarity Score |
|:-:|:-------------------------------------------------:|:-------------------------:|:-------:|:----------------:|
| 0 |         Star Wars: Episode IV - A New Hope (1977) | Action\|Adventure\|Sci-Fi |   260   |        1.0       |
| 1 |                                   Stargate (1994) | Action\|Adventure\|Sci-Fi |   316   |        1.0       |
| 2 |                             Demolition Man (1993) | Action\|Adventure\|Sci-Fi |   442   |        1.0       |
| 3 | Star Wars: Episode V - The Empire Strikes Back... | Action\|Adventure\|Sci-Fi |   1196  |        1.0       |
| 4 | Star Wars: Episode VI - Return of the Jedi (1983) | Action\|Adventure\|Sci-Fi |   1210  |        1.0       |
| 5 |        Star Trek III: The Search for Spock (1984) | Action\|Adventure\|Sci-Fi |   1375  |        1.0       |
| 6 |                              Lost in Space (1998) | Action\|Adventure\|Sci-Fi |   1831  |        1.0       |
| 7 |                             Rocketeer, The (1991) | Action\|Adventure\|Sci-Fi |   2094  |        1.0       |
| 8 |                                       Tron (1982) | Action\|Adventure\|Sci-Fi |   2105  |        1.0       |
| 9 |                         Six-String Samurai (1998) | Action\|Adventure\|Sci-Fi |   2275  |        1.0       |

Tabel 4. Rekomendasi berdasarkan konten

Kelebihan:

- Sederhana dan mudah diimplementasikan.
- Efektif dalam merekomendasikan film berdasarkan kesamaan genre.

Kekurangan:

- Mengabaikan informasi selain genre dalam film, seperti rating atau ulasan pengguna.
- Tidak memperhitungkan preferensi individu pengguna.

### Collaborative Filtering

#### Cluster Based Algorithm
Penjelasan Model:
- Model ini menggunakan algoritma _KMeans_ untuk melakukan _clustering_ terhadap pengguna berdasarkan preferensi pengguna terhadap film.
- Pada model ini dilakukan _hyperparameter tuning_ menggunakan _GridSearchCV_ untuk mencari parameter terbaik.
- Fungsi "recommend_movies_kmeans" digunakan untuk merekomendasikan film berdasarkan kluster pengguna.

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

Tabel 5. Rekomendasi film dengan menggunakan teknik _clustering_

Kelebihan:

- Memperhitungkan preferensi pengguna berdasarkan pola penilaian pengguna.
- Mampu menyesuaikan rekomendasi berdasarkan kluster pengguna.

Kekurangan:

- Bergantung pada kualitas _clustering_, bisa jadi kurang akurat jika kluster tidak merepresentasikan preferensi dengan baik.
- Tidak memperhitungkan informasi film selain kluster pengguna.

#### Deep Learning
Penjelasan Model:

- Model ini menggunakan jaringan saraf tiruan untuk memprediksi rating film yang belum ditonton oleh pengguna.
- Pada model ini dilakukan _hyperparameter tuning_ menggunakan _RandomSearch_ untuk mencari parameter terbaik.
- Fungsi "recommend_movies_dl" digunakan untuk merekomendasikan film berdasarkan prediksi rating.

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

Tabel 6. Rekomendasi film menggunakan teknik _deep learning_

Kelebihan:

- Mampu memperhitungkan pola yang kompleks dan _non-linear_ dalam preferensi pengguna.
- Dapat memanfaatkan informasi lebih lanjut seperti metadata film.
- Mampu memperbaiki rekomendasi seiring waktu dengan _training_ ulang.

Kekurangan:

- Membutuhkan komputasi yang lebih intensif untuk _training_ model.
- Bergantung pada kualitas dan kuantitas data yang digunakan untuk _training_ model.

## Evaluation

### Metrik

- _Mean Squared Error (MSE)_ :
_Mean Squared Error_ adalah metrik yang digunakan untuk mengukur seberapa dekat rata-rata kuadrat dari selisih antara nilai yang diprediksi dan nilai yang sebenarnya dari data sampel. Metrik ini digunakan pada model pertama dan kedua. Formula untuk _MSE_ adalah sebagai berikut :

  _MSE_ = $\frac{1}{n} \Sigma_{i=1}^n({y}-\hat{y})^2$

  Keterangan :

    n : jumlah sampel

    Y : nilai sebenarnya dari sampel ke-i

    Ŷ : nilai yang diprediksi untuk sampel ke-i

- _Root Mean Squared Error (RMSE)_ :
_Root Mean Squared Error_ adalah akar kuadrat dari _MSE_. Ini memberikan ukuran kesalahan rata-rata antara nilai yang diprediksi dan nilai yang sebenarnya dalam satuan yang sama dengan variabel target. Metrik ini digunakan pada model pertama saja. _RMSE_ dihitung dengan cara berikut :

  _RMSE_ = $\sqrt{MSE}$

- _Precision_ :
_Precision_ adalah metrik evaluasi yang mengukur seberapa baik model membuat prediksi yang benar untuk kelas positif dari total prediksi positif yang dilakukan.

### Model Evaluation

### Content-Based Filtering

- _Cosine Similarity_

  Pada model dengan menggunakan _Cosine Similarity_ menghasilkan nilai presisi 100% dari top 10 rekomendasi film.

  ![evaluasi cosine](https://github.com/maybeitsai/Movie-Recommendation-System/assets/130530985/ff1fc8de-c3f1-4976-9ac5-2dfd71c7a465)

  Gambar 4. Visualisasi nilai presisi dari model berbasis konten


### Collaborative Filtering

- _KMeans CLustering_
  
  Pada model dengan pendekatan _Clustering_ menghasilkan nilai kesalahan sebagai berikut :
    - _MSE_ :  0.04460389925200849
    - _RMSE_ : 0.21119635236435427

  Berikut ini merupakan visualisasi hasil evaluasi pada model _KMeans CLustering_.
  
  ![evaluasi clustering](https://github.com/maybeitsai/Movie-Recommendation-System/assets/130530985/d7867b91-e502-4a0a-a9f0-3b9c55736eb8)

  Gambar 5. Visualisasi kesalahan pada model _KMeans CLustering_

 
- _Deep Learning_

  Pada model dengan pendekatan _Deep Learning_ menghasilkan nilai kesalahan sebagai berikut :
    - _MSE_ : 0.0101
    - _Validation MSE_ : 0.0384
    - _RMSE_ : 0.1006
    - _Validation RMSE_ : 0.1958
  
  Berikut ini merupakan visualisasi hasil evaluasi pada model _Deep Learning_.

  ![mse deep learning](https://github.com/maybeitsai/Movie-Recommendation-System/assets/130530985/c8e52f2d-c08e-4381-94c7-db000bbc0d05)
  
  Gambar 6. _Mean Squared Error (MSE)_ pada model _Deep Learning_

  ![rmse deep learning](https://github.com/maybeitsai/Movie-Recommendation-System/assets/130530985/1c0fd3c5-2f3f-410a-9d86-88ae85d709ec)
  
  Gambar 7. _Root Mean Squared Error (RMSE)_ pada model _Deep Learning_

### Kesimpulan
#### Goals Achievement
- Menghasilkan Rekomendasi Film yang Relevan: Kesimpulan ini mencakup pencapaian utama dari proyek, yaitu pengembangan sistem rekomendasi film yang dapat menganalisis preferensi pengguna dengan mendalam dan memberikan rekomendasi film yang sesuai dengan tingkat kesalahan yang rendah.
- Meningkatkan Kepuasan Pengguna: Proyek ini juga berhasil meningkatkan kepuasan pengguna dengan menyediakan pengalaman pencarian film yang lebih efisien dan memuaskan, sehingga mengurangi kebingungan dan meningkatkan retensi pengguna.

#### Solusi Efektif
- _Content-Based Filtering_ dengan _Cosine Similarity_: Pendekatan ini terbukti efektif dalam merekomendasikan film berdasarkan kesamaan genre. Meskipun sederhana, model ini memberikan rekomendasi yang relevan berdasarkan informasi genre film.
- _Collaborative Filtering_ dengan Algoritma _KMeans Clustering_ dan _Deep Learning_: Kedua pendekatan ini juga berhasil dalam memberikan rekomendasi film. Pendekatan _KMeans Clustering_ mengelompokkan pengguna berdasarkan preferensi pengguna, sementara pendekatan _Deep Learning_ memanfaatkan jaringan saraf tiruan untuk memprediksi rating film yang belum ditonton.

#### Perluasan Penelitian
- Inklusi Informasi Tambahan: Untuk meningkatkan akurasi rekomendasi, penelitian selanjutnya dapat mempertimbangkan inklusi informasi tambahan seperti metadata film, ulasan pengguna, atau faktor-faktor lain yang dapat mempengaruhi preferensi pengguna.
- Eksplorasi Model Lain: Selain pendekatan yang telah digunakan, penelitian dapat mengeksplorasi model lain seperti _ensemble methods_, atau teknik _hybrid_ untuk meningkatkan kualitas rekomendasi.
- Optimisasi Komputasi: Mengingat _Deep Learning_ membutuhkan komputasi yang intensif, penelitian dapat fokus pada optimisasi komputasi untuk meningkatkan efisiensi dan kinerja model.

## References

[1] Zhang, S., Yao, L., Sun, A., &Tay, Y. (2018). Deep Learning based Recommender System: A Survey and New Perspectives. ACM Computing Surveys, 1-35.

[2] Bobadilla, J., Alonso, S., & Hernando, A. (2020). Deep Learning Architecture for Collaborative Filtering Recommender Systems. MDPI andACS Style, 1-14.

[3] Khoali, M., Tali, A., & Laaziz, Y. (2020). Advanced Recommendation Systems Through Deep Learning. Association for Computing Machinery, 1-8.

[4] Phorasim, P., & Yu, L. 2017. Movies Recommendation Using Collaborative Filtering and K-Means. In International Journal of Advanced Computer Research, 55-58.

[5] B. T. W. Utomo and A. W. Anggriawan, “Sistem Rekomendasi Paket Wisata Se-Malang Raya Menggunakan Metode Hybrid Content Based Dan Collaborative,” J. Ilm. Teknol. Inf. Asia, vol. 9, no. 1, pp. 6–13, 2015.

[6] A. Kurniawan, “Sistem Rekomendasi Produk Sepatu Dengan Menggunakan Menggunakan Metode Collaborative Filtering,” Semin. Nas. Teknol. Inf. dan Komun., vol. 2016, no. Sentika, pp. 610–614, 2016.

[7] I. M. A. W. Putra, G. Indrawan, and K. Y. E. Aryanto, “Sistem Rekomendasi Berdasarkan Data Transaksi Perpustakaan Daerah Tabanan dengan menggunakan K-Means Clustering,” J. Ilmu Komput. Indones., vol. 3, no. 1, pp. 18–22, 2018.

[8] R. Ahuja, A. Solanki and A. Nayyar, "Movie Recommender System Using K-Means," 2019.

[9]  J. Fadhil and W. F. Mahmudy, "Pembuatan Sistem Rekomendasi Menggunakan Decision Tree dan Clustering," vol. 3, no. 1, 2007.

[10]  A. Halim, H. Gohzali, D. M. Panjaitan and I. Maulana, "Sistem Rekomendasi Film menggunakan Bisecting K-Means d an Collaborative Filtering," CITISEE 2017, p. 37, 2017.

