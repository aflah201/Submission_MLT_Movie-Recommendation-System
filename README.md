# Laporan Proyek Machine Learning - Moh. Aflah Azzaky

---
## Project Overview
Budaya menonton acara TV dan film sekarang ini dipermudah dengan adanya internet. Platform streaming seperti Netflix, HBO Max dan Disney+ memberikan lebih banyak fleksibilitas kepada pengguna untuk menonton acara TV dan film favorit mereka, kapan saja dan di perangkat apa pun. Jumlah acara TV atau film yang disediakan oleh masingmasing platform ini pun bisa dibilang cukup besar, dengan salah satu platform seperti netflix memiliki katalog berkisaran 6000 item acara TV dan film.
Dengan banyaknya jumlah item yang disediakan, sistem rekomendasi menjadi fitur penting untuk dibangun dan memiliki peran besar dalam membantu pengguna menemukan item relevan yang mungkin mereka sukai. Selain itu, dari sudut pandang bisnis, sistem rekomendasi dapat membantu meningkatkan waktu aktfitas pengguna di dalam suatu platform
dengan cara menampilkan item-item relevan kepada pengguna, yang mana nantinya seiring waktu dapat meningkatkan pendapatan untuk pelatform itu sendiri. Oleh karena itu, sistem rekomendasi merupakan salah satu fitur penting yang harus dimiliki oleh platform-platform seperti layanan streaming acara TV dan film. Sistem rekomendasi pada dasarnya merupakan sistem yang berguna untuk menyaring dan mengidentifikasi item berupa produk, layanan atau informasi yang memiliki potensi besar untuk dipilih, dibeli ataupun digunakan oleh pengguna. Terdapat beberapa metode yang dapat digunakan dalam membangun sistem rekomendasi, seperti collaborative filtering (CF) yang merekomendasikan item berdasar kemiripan pengguna dalam hal memilih atau memberi nilai kepada item dan content-based filtering (CBF) yang merekomendasikan item berdasarkan kemiripan item dalam hal isi atau konten item yang disukai oleh pengguna. Namun perlu diketahui, masing-masing metode ini memiliki kelemahan. Untuk menutupi kelemahan masing-masing metode ini, pendekatan hybrid dapat dilakukan dimana kedua metode ini digabungkan dengan harapan dapat mengurangi kelemahan dari satu metode melalui kelebihan dari satu metode lainnya dan menghasilkan sistem rekomendasi yang lebih baik.[[1](https://openlibrarypublications.telkomuniversity.ac.id/index.php/engineering/article/view/18066)]
Proyek sistem rekomendasi film penting untuk diselesaikan karena platform streaming seperti Netflix, HBO Max, dan Disney+ memiliki ribuan item dalam katalognya. Pengguna dapat merasa kewalahan dalam memilih acara TV atau film yang relevan dengan preferensi mereka. Sistem rekomendasi berperan besar dalam menyaring item-item tersebut agar pengguna lebih mudah menemukan konten yang mereka sukai, yang pada akhirnya meningkatkan kepuasan dan loyalitas mereka terhadap platform tersebut. Dari sudut pandang bisnis, sistem rekomendasi yang efektif juga dapat meningkatkan waktu yang dihabiskan pengguna pada platform, yang pada gilirannya dapat meningkatkan pendapatan platform melalui perpanjangan langganan atau iklan.

---
## Business Understanding
### Problem Statements
Berdasarkan latar belakang diatas, berikut ini rumusan masalah yang dapat diselesaikan pada proyek ini:
- Bagaimana cara membangun sistem rekomendasi film yang efektif dan akurat untuk meningkatkan pengalaman pengguna dan waktu aktivitas mereka di platform streaming?
- Metode apa yang dapat digunakan untuk mengoptimalkan rekomendasi film agar sesuai dengan preferensi pengguna?
- Bagaimana menggabungkan berbagai pendekatan, seperti *collaborative filtering* dan *content-based filtering*, untuk mengatasi kelemahan masing-masing metode dan menghasilkan sistem rekomendasi yang lebih baik?

### Goals Statements
Berdasarkan rumusan masalah diatas, berikut ini tujuan yang dapat diselesaikan pada proyek ini:
- Mengembangkan sistem rekomendasi film yang dapat membantu pengguna menemukan konten yang relevan dengan preferensi mereka secara lebih efisien.
- Menggabungkan pendekatan *collaborative filtering* dan *content-based filtering* untuk meningkatkan akurasi dan efektivitas sistem rekomendasi.
- Meningkatkan waktu aktivitas pengguna di platform dan pada akhirnya, membantu meningkatkan pendapatan melalui kepuasan dan keterlibatan pengguna yang lebih tinggi.

### Solution Statements
Berdasarkan tujuan diatas, berikut ini solusi yang dapat diselesaikan pada proyek ini:
- Membangun sistem rekomendasi film berbasis *collaborative filtering* untuk merekomendasikan film berdasarkan kemiripan pengguna lain dengan perilaku serupa.
- Menggunakan *content-based filtering* untuk merekomendasikan film berdasarkan atribut atau karakteristik film yang disukai oleh pengguna.
- Mengimplementasikan pendekatan hybrid yang menggabungkan kedua metode tersebut untuk memaksimalkan kelebihan dan meminimalkan kekurangan masing-masing metode, sehingga dapat memberikan rekomendasi yang lebih akurat dan personal kepada pengguna.

---
## Data Understanding
Data pada project ini menggunakan data yang bersumber pada sebuah situs kaggle, dimana fokus pada data tersebut sebagai data awal rekomendasi film.[[Kaggle Dataset - Movie Recommendation Data](https://www.kaggle.com/datasets/rohan4050/movie-recommendation-data)]

Informasi dataset dapat dilihat pada tabel dibawah ini :
Jenis | Keterangan
--- | ---
Sumber | [Kaggle Dataset - Movie Recommendation Data](https://www.kaggle.com/datasets/rohan4050/movie-recommendation-data)
Lisensi | Unknown
Kategori | Movies and TV Shows, Recommender Systems
Jenis dan Ukuran Berkas | ZIP (13.1M)

Pada berkas yang diunduh yakni movie-recommendation-data.zip berisi satu folder dengan isi data links.csv, movies.csv, ratings.csv, tags.csv untuk rincian variabel dapat dilihat pada gambar berikut:


Dalam mengembangkan proyek rekomendasi ini diperlukan beberapa cara dalam pemrosesan data, yaitu:
1. Menampilkan dataset untuk mengetahui variabel yang digunakan.
2. Melihat isi dataset dengan fungsi `head() ` setiap dataframe.
3. Menampikan data unik untuk `movieId` dan `userId`.
4. Mendeskripsikan nilai statisika pada dataset `ratings`.
5. Memvisualisasikan hasil evaluasi data train dan test.

---
## Data Preparation
Berikut adalah tahapan dalam melakukan data preparation:

1. Menggabungkan seluruh `movieId` pada kategori film.
2. Menggabungkan seluruh `userId` pada kategori film.
3. Menggabungkan file `links, movies, ratings, dan tags`.
4. Cek missing value dengan fungsi isnull(), untuk mengatasi data kosong.
5. Menghitung jumlah rating berdasarkan `movieId`.
6. Menggabungkan seluruh data film dengan rating.
7. Menggabungkan seluruh data film dengan data film berdasarkan `movieId`.
8. Menggabungkan seluruh data film dengan data tags berdasarkan `movieId`.
9. Mengatasi missing value pada movies_all_data_df.
10. Membersihkan missing value menggunakan fungsi dropna().
11. Mengurutkan film berdasarkan `movieId`.
12. Mengecek jumlah movies_fix_df.
13. Membuat variabel movies_preparation_df yang berisi movies_fix_df kemudian mengurutkan berdasarkan `movieId`.
14. Membuang data duplikat pada variabel movies_preparation_df.
15. Mengonversi data series menjadi dalam bentuk list.
16. Membuat dictionary, berfungsi untuk pembuatan model.

---
## Model Development
Setelah melakukan pra-pemrosesan pada data, langkah selanjutnya adalah *Model Development* terhadap data, dengan menggunakan beberapa metode, diantaranya sebagai berikut:

1. ***Content Based Filtering***
  **Kelebihan:**
  - **Tidak Mengalami *Cold Start* untuk Item Baru**: Karena CBF didasarkan pada atribut konten item (misalnya genre, aktor, sutradara untuk film), item baru dengan deskripsi konten yang lengkap dapat segera direkomendasikan kepada pengguna.
  - **Independen dari Data Pengguna Lain**: CBF berfokus pada preferensi individu, sehingga tidak bergantung pada perilaku pengguna lain. Hal ini memungkinkan privasi pengguna tetap terjaga dan menghindari masalah yang terkait dengan perilaku kolektif.
  - **Rekomendasi Lebih Terfokus**: Karena CBF memanfaatkan kesamaan antara konten item yang disukai pengguna, rekomendasi yang dihasilkan cenderung konsisten dan sesuai dengan preferensi konten yang sudah diketahui.

  **Kekurangan:**
  - **Keterbatasan dalam Mengeksplorasi Konten Baru**: CBF cenderung merekomendasikan item yang serupa dengan yang sudah pernah disukai pengguna. Akibatnya, sistem kurang mampu memperkenalkan item-item baru yang mungkin berbeda namun tetap menarik bagi pengguna.
  - **Memerlukan Deskripsi Konten yang Mendetail**: Untuk menghasilkan rekomendasi yang baik, item harus memiliki atribut konten yang rinci dan relevan. Jika informasi ini tidak lengkap, akurasi rekomendasi dapat menurun.
  - **Terlalu Bergantung pada Preferensi Pengguna yang Terbatas**: Jika seorang pengguna memiliki riwayat interaksi yang sangat terbatas, rekomendasi yang diberikan bisa sangat terbatas dan tidak bervariasi.

  **Tahapan dalam menggunakan Content Based Filtering:**
  - Cek data pada dictionary yang telah dibuat.
  - Inisialisasi TfidVectorizer, adalah alat yang hebat untuk mengubah data teks menjadi fitur numerik, yang membuatnya penting untuk banyak tugas Pemrosesan Bahasa Alami (NLP).
  - Melakukan fit transformation matrix.
  - Mengubah vector dengan fitur todense().
  - Membuat dataframe untuk tf-idf matrix.
  - Menghitung cosine similarity dan membuat variabel.
  - Membuat fungsi rekomendasi.
  - Mendapatkan rekomendasi yang telah dibuat.

2. ***Collaborative Filtering***
  **Kelebihan:**
  - **Personalized Recommendations**: CF dapat memberikan rekomendasi yang sangat personal berdasarkan preferensi dan perilaku pengguna serupa. Misalnya, jika pengguna lain dengan selera serupa menyukai film tertentu, sistem akan merekomendasikan film tersebut.
  - **Tidak Bergantung pada Konten**: CF tidak memerlukan data spesifik tentang karakteristik atau atribut dari item (seperti genre atau deskripsi film), sehingga cocok untuk berbagai jenis data, bahkan yang tidak memiliki deskripsi konten rinci.
  - **Dapat Mengungkap Preferensi yang Tidak Terduga**: Karena CF didasarkan pada perilaku kolektif pengguna, sistem dapat merekomendasikan item yang mungkin tidak akan ditemukan pengguna jika hanya mengandalkan atribut konten.

  **Kekurangan:**
  - **Masalah *Cold Start***: Jika ada pengguna baru atau item baru yang tidak memiliki riwayat interaksi, CF sulit memberikan rekomendasi yang akurat karena kurangnya data.
  - **Scalability Issue**: Pada skala besar, dengan jutaan pengguna dan item, algoritma CF bisa menjadi tidak efisien dan memerlukan sumber daya komputasi besar.
  - ***Sparsity Problem***: Dalam dataset besar, interaksi antara pengguna dan item cenderung jarang (*sparse*), sehingga sulit untuk menemukan pola yang cukup untuk menghasilkan rekomendasi yang akurat.

  **Tahapan dalam menggunakan Collaborative Filtering:**
  - Membaca dataset rating film.
  - Encode data user dan title.
  - Mempetakan `userId` dan `movieId`.
  - Cek mapping.
  - Mengacak data untuk train dan test.
  - Membagi data untuk train dan test.

3. ***Kesimpulan:***
  - ***Collaborative Filtering*** cocok untuk memberikan rekomendasi yang lebih personal, tetapi rentan terhadap masalah data yang minim dan skala besar.
  - ***Content-Based Filtering*** efektif untuk item-item baru dan lebih konsisten dalam hal konten serupa, tetapi cenderung kurang eksploratif dan bergantung pada ketersediaan deskripsi konten yang detail. 

Pendekatan hybrid yang menggabungkan kedua metode ini dapat mengurangi kekurangan dari masing-masing pendekatan dengan memanfaatkan kelebihannya secara bersamaan.

---
## Evaluation
Setelah melakukan model developmenet pada data, langkah selanjutnya adalah *Evaluation* terhadap data, diantaranya sebagai berikut:
1. Membuat class RecommenderNet adalah model yang dirancang untuk membangun sistem rekomendasi dengan memanfaatkan embedding. Model ini memetakan pengguna dan item (seperti film) ke dalam ruang vektor berdimensi rendah sehingga hubungan antara pengguna dan item dapat dianalisis. Embedding ini memungkinkan sistem untuk mengenali pola kesamaan atau preferensi antara pengguna dan item secara efisien.
2. Melakukan proses compile model.
3. Melakukan proses training model.
4. Menampilkan plot evaluasi.

  Plot di atas menunjukkan nilai root mean squared error (RMSE) dari data latih (train) dan data uji (test) seiring bertambahnya epoch. Awalnya, RMSE pada kedua data menurun, menunjukkan model belajar dengan baik. Namun, setelah epoch 10-20, RMSE pada data uji mulai stabil dan sedikit meningkat, sementara RMSE pada data latih terus menurun. Ini adalah tanda overfitting, di mana model hanya bekerja baik pada data latih, tetapi tidak pada data uji. Untuk mengatasi hal ini, metode seperti regularization, dropout, atau early stopping dapat diterapkan agar model lebih baik dalam menggeneralisasi data baru.
5. Mendapatkan rekomendasi film.

---
## Kesimpulan
Kesimpulan dari proyek sistem rekomendasi film adalah bahwa platform streaming memerlukan sistem rekomendasi yang efektif untuk membantu pengguna menemukan konten yang relevan di tengah banyaknya pilihan yang tersedia. Sistem rekomendasi ini tidak hanya penting untuk meningkatkan pengalaman pengguna, tetapi juga berperan dalam memperpanjang waktu aktivitas pengguna di platform, yang pada akhirnya dapat meningkatkan pendapatan platform.

Untuk mencapai hal tersebut, rumusan masalah berfokus pada bagaimana mengembangkan sistem yang akurat dan efisien dengan menggabungkan berbagai pendekatan seperti *collaborative filtering* dan *content-based filtering*. Tujuan proyek adalah menciptakan sistem yang dapat memberikan rekomendasi yang lebih personal dan relevan bagi pengguna.

Solusi yang diusulkan adalah mengimplementasikan pendekatan hybrid, yang menggabungkan kekuatan kedua metode untuk mengatasi kelemahan masing-masing. Dengan pendekatan ini, sistem rekomendasi diharapkan mampu memberikan rekomendasi yang lebih baik dan meningkatkan kepuasan serta keterlibatan pengguna di platform.

---
## Penutup
Demikian hasil dari laporan proyek machine learning tentang Sistem Rekomendasi Film. Bilamana didalam penyampaian serta penjelasan yang kurang berkenaan, saya memohon maaf. Atas waktu dan perhatiannya, saya ucapkan Terima kasih telah membaca laporan ini. Semoga dapat memberi manfaat bagi kita semuanya.