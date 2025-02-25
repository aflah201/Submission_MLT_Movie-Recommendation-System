# Laporan Proyek Machine Learning - Moh. Aflah Azzaky

---
## Project Overview
Budaya menonton acara TV dan film sekarang ini dipermudah dengan adanya internet. Platform streaming seperti Netflix, HBO Max dan Disney+ memberikan lebih banyak fleksibilitas kepada pengguna untuk menonton acara TV dan film favorit mereka, kapan saja dan di perangkat apa pun. Jumlah acara TV atau film yang disediakan oleh masingmasing platform ini pun bisa dibilang cukup besar, dengan salah satu platform seperti netflix memiliki katalog berkisaran 6000 item acara TV dan film.
Dengan banyaknya jumlah item yang disediakan, sistem rekomendasi menjadi fitur penting untuk dibangun dan memiliki peran besar dalam membantu pengguna menemukan item relevan yang mungkin mereka sukai. Selain itu, dari sudut pandang bisnis, sistem rekomendasi dapat membantu meningkatkan waktu aktfitas pengguna di dalam suatu platform
dengan cara menampilkan item-item relevan kepada pengguna, yang mana nantinya seiring waktu dapat meningkatkan pendapatan untuk pelatform itu sendiri. Oleh karena itu, sistem rekomendasi merupakan salah satu fitur penting yang harus dimiliki oleh platform-platform seperti layanan streaming acara TV dan film. Sistem rekomendasi pada dasarnya merupakan sistem yang berguna untuk menyaring dan mengidentifikasi item berupa produk, layanan atau informasi yang memiliki potensi besar untuk dipilih, dibeli ataupun digunakan oleh pengguna. Terdapat beberapa metode yang dapat digunakan dalam membangun sistem rekomendasi, seperti collaborative filtering (CF) yang merekomendasikan item berdasar kemiripan pengguna dalam hal memilih atau memberi nilai kepada item dan content-based filtering (CBF) yang merekomendasikan item berdasarkan kemiripan item dalam hal isi atau konten item yang disukai oleh pengguna.[[1](https://openlibrarypublications.telkomuniversity.ac.id/index.php/engineering/article/view/18066)]

Proyek sistem rekomendasi film penting untuk diselesaikan karena platform streaming seperti Netflix, HBO Max, dan Disney+ memiliki ribuan item dalam katalognya. Pengguna dapat merasa kewalahan dalam memilih acara TV atau film yang relevan dengan preferensi mereka. Sistem rekomendasi berperan besar dalam menyaring item-item tersebut agar pengguna lebih mudah menemukan konten yang mereka sukai, yang pada akhirnya meningkatkan kepuasan dan loyalitas mereka terhadap platform tersebut. Dari sudut pandang bisnis, sistem rekomendasi yang efektif juga dapat meningkatkan waktu yang dihabiskan pengguna pada platform, yang pada gilirannya dapat meningkatkan pendapatan platform melalui perpanjangan langganan atau iklan.

---
## Business Understanding
### Problem Statements
Berdasarkan latar belakang diatas, berikut ini rumusan masalah yang dapat diselesaikan pada proyek ini:
- Bagaimana cara membangun sistem rekomendasi film yang efektif dan akurat untuk meningkatkan pengalaman pengguna dan waktu aktivitas mereka di platform streaming?
- Metode apa yang dapat digunakan untuk mengoptimalkan rekomendasi film agar sesuai dengan preferensi pengguna?

### Goals Statements
Berdasarkan rumusan masalah diatas, berikut ini tujuan yang dapat diselesaikan pada proyek ini:
- Mengembangkan sistem rekomendasi film yang dapat membantu pengguna menemukan konten yang relevan dengan preferensi mereka secara lebih efisien.
- Menggabungkan pendekatan *collaborative filtering* dan *content-based filtering* untuk meningkatkan akurasi dan efektivitas sistem rekomendasi.

### Solution Statements
Berdasarkan tujuan diatas, berikut ini solusi yang dapat diselesaikan pada proyek ini:
- Membangun sistem rekomendasi film berbasis *collaborative filtering* untuk merekomendasikan film berdasarkan kemiripan pengguna lain dengan perilaku serupa.
- Menggunakan *content-based filtering* untuk merekomendasikan film berdasarkan atribut atau karakteristik film yang disukai oleh pengguna.

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

Berikut informasi mengenai jumlah data, tipe data, data statisika, dan informasi data hilang (missing value) yang terdapat pada dataset ini:

![Screenshot 2024-10-21 010141](https://github.com/user-attachments/assets/8008f841-6817-4412-bf3d-0d54318870fd)

Pada berkas links.csv berisi 9734 baris x 3 kolom. Kolom-kolom tersebut berisi diantaranya 1 kolom berisi tipe data `float64`, dan 2 kolom berisi tipe data `int64`.
Untuk penjelasan mengenai variabel dapat dilihat sebagai berikut:
Variabel | Keterangan | Tipe Data
--- | --- | ---
movieId | Merupakan id film. | `int64`
imdbId | Merupakan id basis data daring yang berisi informasi mengenai film, acara TV, video rumahan, permainan video, dan acara internet. | `int64`
tmdbId | Merupakan id basis data film dan TV yang dapat diakses secara gratis dan diedit oleh pengguna. | `float64`

![Screenshot 2024-10-21 010155](https://github.com/user-attachments/assets/2f7af2b3-cc6c-47fb-91c4-b4c18900c151)

Pada berkas movies.csv berisi 9742 baris x 3 kolom. Kolom-kolom tersebut berisi diantaranya 1 kolom berisi tipe data `int64`, dan 2 kolom berisi tipe data `object`.
Untuk penjelasan mengenai variabel dapat dilihat sebagai berikut:
Variabel | Keterangan | Tipe Data
--- | --- | ---
movieId | Merupakan id film. | `int64`
title | Merupakan judul film. | `object`
genres | merupakan kategori film. | `object`

![Screenshot 2024-10-21 133954](https://github.com/user-attachments/assets/8672e229-2c27-4031-abb6-ad1f1fa6e660)

Pada berkas ratings.csv berisi 100.836 baris x 6 kolom. Kolom-kolom tersebut berisi diantaranya 1 kolom berisi tipe data `float64`, dan 5 kolom berisi tipe data `int64`.
Untuk penjelasan mengenai variabel dapat dilihat sebagai berikut:
Variabel | Keterangan | Tipe Data
--- | --- | ---
userId | Merupakan id pengguna. | `int64`
movieId | Merupakan id film. | `int64`
rating | Merupakan penilaian film. | `float64`
timestamp | Merupakan tanda waktu atau nilai numerik yang mewakili waktu tertentu dalam bentuk yang dapat dimengerti komputer. | `int64`

![Screenshot 2024-10-21 010226](https://github.com/user-attachments/assets/90a18231-a03a-48d7-8b86-ff1b13fcf9ce)

Pada berkas tags.csv berisi 3683 baris x 4 kolom. Kolom-kolom tersebut berisi diantaranya 1 kolom berisi tipe data `object`, dan 3 kolom berisi tipe data `int64`.
Untuk penjelasan mengenai variabel dapat dilihat sebagai berikut:
Variabel | Keterangan | Tipe Data
--- | --- | ---
userId | Merupakan id pengguna. | `int64`
movieId | Merupakan id film. | `int64`
tag | Merupakan kategori. | `object`
timestamp | Merupakan tanda waktu atau nilai numerik yang mewakili waktu tertentu dalam bentuk yang dapat dimengerti komputer. | `int64`

Dalam mengembangkan proyek rekomendasi ini diperlukan beberapa cara dalam pemrosesan data, yaitu:
1. Menampilkan dataset untuk mengetahui variabel yang digunakan.
2. Melihat isi dataset dengan fungsi `head()` setiap dataframe.
3. Menampikan data unik untuk `movieId` dan `userId`.
4. Mendeskripsikan nilai statisika pada dataset `ratings` menggunakan `describe()`.
5. Cek missing value dengan fungsi `isnull()`, untuk mengatasi data kosong.

   ![Screenshot 2024-10-21 093610](https://github.com/user-attachments/assets/19cdcf40-1bda-49a1-b7ef-c2e1d4c0e6e8)

   Dari hasil diatas terdapat data kosong pada variabel `tmdbId` berjumlah 8 data.
6. Melakukan pembatasan nilai outliers pada `rating`, yang menghasilkan data bersih sejumlah 96.655 data.
7. Melakukan pengecekan data duplikat setiap dataset, ternyata tidak terdeteksi data duplikat.

---
## Data Preparation
Berikut adalah tahapan dalam melakukan data preparation:

1. Menggabungkan seluruh `movieId` pada kategori film.
2. Menggabungkan seluruh `userId` pada kategori film.
3. Menggabungkan file `links`, `movies`, `ratings`, dan `tags`.
4. Menghitung jumlah rating berdasarkan `movieId`.
5. Menggabungkan seluruh data film dengan rating.
6. Menggabungkan seluruh data film dengan data film berdasarkan `movieId`.
7. Menggabungkan seluruh data film dengan data tags berdasarkan `movieId`.
8. Mengatasi missing value pada movies_all_data_df.
9. Mengurutkan film berdasarkan `movieId`.
10. Mengecek jumlah movies_fix_df.
11. Membuat variabel movies_preparation_df yang berisi movies_fix_df kemudian mengurutkan berdasarkan `movieId`.
12. Membuang data duplikat pada variabel movies_preparation_df.
13. Mengonversi data series menjadi dalam bentuk list.
14. Membuat dictionary, berfungsi untuk pembuatan model.
15. Inisialisasi TfidVectorizer adalah alat yang hebat untuk mengubah data teks menjadi fitur numerik, yang membuatnya penting untuk banyak tugas Pemrosesan Bahasa Alami (NLP).
16. Encode data penting untuk mengubah data kategorikal (userId) menjadi numerik dan sebaliknya, yang biasa digunakan dalam pembelajaran mesin untuk merepresentasikan data.
17. Pemetaan data kolom user dan movie dalam dataframe ratings berisi representasi terkode dari userId dan movieId, yang biasanya lebih efisien untuk digunakan dalam algoritma machine learning seperti model rekomendasi.
18. Membuat data untuk train dan test.

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
        - Berikut ini adalah hasil film yang disukai pengguna:

            movieId | title | genres
            --- | --- | ---
            31903 | Zelary (2003) | Drama\|Romance

            Dari hasil diatas dapat dilihat bahwa pengguna menyukai film yang berjudul Zelary (2003) dengan kategori film Drama|Romance.
        - Berikut ini hasil dari top-5 rekomendasi berdasarkan algoritma Content Based Filtering adalah sebagai berikut:
        
            title | genres
            --- | ---
            M. Butterfly (1993) | Drama\|Romance
            Nicholas Nickleby (2002) | Drama\|Romance
            Far from Heaven (2002) | Drama\|Romance
            Talk to Her (Hable con Ella) (2002) | Drama\|Romance
            Before Sunrise (1995) | Drama\|Romance

            Dari hasil diatas dapat dilihat bahwa film yang berkategori Drama|Romance menjadi yang direkomendasikan oleh sistem. Hal ini berdasarkan dari film yang disukai oleh pengguna. Dari 5 item yang direkomendasikan, 5 item memiliki genre Drama|Romance. (similar). Artinya, precision sistem kita sebesar 5/5 atau 100%.
            Teknik Evaluasi di atas adalah dengan menggunakan precission, rumus dari teknik ini adalah :

            ![Screenshot 2024-10-21 141327](https://github.com/user-attachments/assets/3e8d46b2-98bb-44ba-a3d6-bd43ed72d462)


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
    - Berikut ini adalah hasil Top Rekomendasi
      Menampilkan rekomendasi untuk pengguna: 462
   
      Film dengan rating tertinggi dari pengguna:
      Titles | Genres
      --- | ---
      Taxi Driver (1976) | Crime\|Drama\|Thriller
      Heavenly Creatures (1994) | Crime\|Drama
      Godfather, The (1972) | Crime\|Drama
      Monty Python's Life of Brian (1979) | Comedy
      Raging Bull (1980) | Drama
   
      10 film teratas yang direkomendasikan:
      Titles | Genres
      --- | ---
      Place in the Sun, A (1951) | Drama\|Romance
      My Life (1993) | Drama
      Crossing Delancey (1988) | Comedy\|Romance
      Woman Under the Influence, A (1974) | Drama
      Adam's Rib (1949) | Comedy\|Romance
      Into the Woods (1991) | Adventure\|Comedy\|Fantasy\|Musical
      Match Factory Girl, The (Tulitikkutehtaan tyttö) (1990) | Comedy\|Drama
      It's Such a Beautiful Day (2012) | Animation\|Comedy\|Drama\|Fantasy\|Sci-Fi
      Frank (2014) | Comedy\|Drama\|Mystery
      Black Mirror: White Christmas (2014) | Drama\|Horror\|Mystery\|Sci-Fi\|Thriller

3. ***Kesimpulan:***
    - ***Collaborative Filtering*** cocok untuk memberikan rekomendasi yang lebih personal, tetapi rentan terhadap masalah data yang minim dan skala besar.
    - ***Content-Based Filtering*** efektif untuk item-item baru dan lebih konsisten dalam hal konten serupa, tetapi cenderung kurang eksploratif dan bergantung pada ketersediaan deskripsi konten yang detail. 

4. Membuat class **Cosine Similarity**, merupakan metode untuk mengukur kemiripan antara dua vektor dalam ruang multidimensi. Biasanya digunakan dalam analisis teks, data produk, atau pengguna untuk menghitung sejauh mana dua entitas memiliki kesamaan. Nilai kemiripan yang dihasilkan berkisar antara -1 hingga 1, di mana 1 menunjukkan vektor sepenuhnya sama (kemiripan maksimum). 0 menunjukkan vektor ortogonal atau tidak ada kemiripan. -1 menunjukkan vektor berlawanan arah.
   - Rumus Cosine Similarity
     
     ![Screenshot 2024-10-21 202530](https://github.com/user-attachments/assets/e17a2a69-ef13-4796-b0ab-d5e1f7f6f894)

     - A dan B dua vektor (misalnya, title atau genre).
     - A ⋅ B adalah hasil perkalian dot product (perkalian elemen-elemen dari kedua vektor dan penjumlahan hasilnya).
     - ∥A∥ dan ∥B∥ adalah panjang (magnitude) dari masing-masing vektor.

   - Langkah kerja untuk sistem rekomendasi
     - Representasi data sebagai vektor berdasarkan fitur tertentu.
     - Menghitung similarity Setiap pasangan dihitung dengan rumus cosine similarity untuk menemukan kemiripan.
     - Pilih similarity terbesar untuk membuat rekomendasi.

   - Parameter yang harus diperhatikan
     - Input Matrix: Biasanya matriks user-item atau item-item.
     - Sparsity: Pastikan tidak terlalu banyak data kosong dalam vektor rating.
     - Normalisasi: Vektor dapat dinormalisasi sebelum perhitungan, terutama jika nilai rating berbeda-beda.

6. Membuat class **RecommenderNet**, merupakan model yang dirancang untuk membangun sistem rekomendasi dengan memanfaatkan embedding. Model ini memetakan pengguna dan item (seperti film) ke dalam ruang vektor berdimensi rendah sehingga hubungan antara pengguna dan item dapat dianalisis. Embedding ini memungkinkan sistem untuk mengenali pola kesamaan atau preferensi antara pengguna dan item secara efisien.
   - Langkah kerja
     - Input layer berupa pasangan user ID dan item ID. Setiap entitas ini direpresentasikan sebagai vektor embedding.
     - Embedding Layer dihasilkan untuk merepresentasikan fitur terlatih dari pengguna dan item.
     - Dot Product Layer Hasil embedding dihubungkan melalui operasi dot product untuk memprediksi rating atau skor relevansi.
     - Output Layer memberikan rating yang diprediksi atau probabilitas kesukaan untuk sebuah item.
     - Loss Function Mean Squared Error (MSE) atau Binary Crossentropy digunakan sebagai fungsi loss, tergantung pada jenis rekomendasi.

   - Parameter yang harus diperhatikan
     - Jumlah Users dan Items.
     - Embedding Size.
     - Optimizer biasanya menggunakan ADAM atau SGD.
     - Loss Function menggunakan **MSE** Cocok untuk memprediksi rating, menggunakan **Binary Crossentropy** Cocok untuk prediksi biner (misalnya, like/dislike).
     - Epoch menentukan berapa kali seluruh dataset diproses.
     - Batch Size adalah jumlah sampel yang digunakan dalam sekali iterasi.

---
## Evaluation
Setelah melakukan model developmenet pada data, langkah selanjutnya adalah *Evaluation* terhadap data, diantaranya sebagai berikut:

1. Model RecommenderNet dikompilasi menggunakan dua elemen penting: loss function (fungsi kerugian) dan metric (metrik evaluasi). Berikut adalah penjelasan mengenai hasil proyek berdasarkan metrik evaluasi yang digunakan:
    - **Loss Function (Binary Crossentropy)**
        - **BinaryCrossentropy** digunakan untuk menghitung seberapa besar kesalahan yang dihasilkan model dalam memprediksi keluaran biner (dalam hal ini mungkin rating seperti "suka" atau "tidak suka" terhadap suatu item).
        - Fungsi kerugian ini akan mengukur perbedaan antara nilai prediksi model dan nilai sebenarnya. Nilai kerugian yang lebih rendah menunjukkan bahwa model lebih baik dalam membuat prediksi yang benar.
   
    - **Metrik Evaluasi (Root Mean Squared Error - RMSE)**
        - **Root Mean Squared Error (RMSE)** adalah metrik yang digunakan untuk mengevaluasi kualitas prediksi model. Ini mengukur seberapa jauh prediksi model dari nilai aktual dalam satuan asli dari target (misalnya, rating film atau produk).
        - **Cara Menghitung RMSE**:
            - RMSE adalah akar kuadrat dari rata-rata nilai kuadrat dari kesalahan prediksi. Semakin kecil nilai RMSE, semakin akurat model dalam memprediksi.
            - Jika nilai RMSE mendekati nol, ini berarti model berhasil memprediksi nilai yang sangat mendekati nilai sebenarnya.
   
    - **Rumus RMSE**:
      
      ![Screenshot 2024-10-21 092611](https://github.com/user-attachments/assets/6c9f4934-dfc7-4e8b-aec4-82b93d311a8d)

      dimana:
      - N adalah jumlah sampel
      - 𝑦𝑖 adalah nilai aktual
      - 𝑦𝑖^ adalah nilai prediksi

    - **Interpretasi Hasil**
        - **Binary Crossentropy**: Setelah model dilatih, nilai *loss* (kerugian) akan memberikan indikasi seberapa jauh model dari hasil ideal. Jika *loss* sangat rendah, ini menunjukkan model memiliki prediksi yang baik dalam hal klasifikasi biner (misalnya, apakah seorang pengguna menyukai sebuah item atau tidak).
        - **RMSE**: Metrik RMSE akan menunjukkan akurasi prediksi model. Nilai RMSE yang kecil menunjukkan bahwa prediksi rating atau preferensi dari model mendekati nilai rating yang sesungguhnya. Sebaliknya, nilai RMSE yang tinggi menunjukkan bahwa prediksi model masih jauh dari hasil sebenarnya.

        Secara umum, setelah proses pelatihan model selesai:
        - **Jika loss rendah dan RMSE kecil**: Ini berarti model berhasil memberikan rekomendasi yang akurat.
        - **Jika loss atau RMSE tinggi**: Model mungkin memerlukan penyesuaian, seperti perubahan arsitektur, *hyperparameter tuning*, atau penambahan lebih banyak data untuk pelatihan.

        Hasil akhir proyek akan sangat dipengaruhi oleh nilai dari kedua metrik ini, yang memberi wawasan tentang seberapa efektif model dalam memberikan rekomendasi yang relevan.

2. Menampilkan plot evaluasi.

    ![plot rekomendasi](https://github.com/user-attachments/assets/beaa9fde-d82e-454b-9be0-4ff018a9b311)

    Plot di atas menunjukkan nilai root mean squared error (RMSE) dari data latih (train) dan data uji (test) seiring bertambahnya epoch. Awalnya, RMSE pada kedua data menurun, menunjukkan model belajar dengan baik. Namun, setelah epoch 10-20, RMSE pada data uji mulai stabil dan sedikit meningkat, sementara RMSE pada data latih terus menurun. Ini adalah tanda overfitting, di mana model hanya bekerja baik pada data latih, tetapi tidak pada data uji. Untuk mengatasi hal ini, metode seperti regularization, dropout, atau early stopping dapat diterapkan agar model lebih baik dalam menggeneralisasi data baru.

   Dari plot RMSE yang diberikan, nilai RMSE untuk pendekatan *Collaborative Filtering* dapat diestimasi dengan melihat nilai terendah (minimum) pada kurva data latih (train) dan data uji (test).
   - **RMSE Data Latih (Train)**: Di akhir epoch (sekitar epoch 100), RMSE untuk training mendekati 0.211.
   - **RMSE Data Uji (Test)**: Untuk data testing, nilai RMSE terlihat sedikit lebih tinggi dan berfluktuasi, tetapi cenderung stabil di sekitar 0.225 hingga 0.230 pada akhir epoch.

3. Mendapatkan top-5 rekomendasi
   title | genres
   --- | ---
   M. Butterfly (1993) | Drama\|Romance
   Nicholas Nickleby (2002) | Drama\|Romance
   Far from Heaven (2002) | Drama\|Romance
   Talk to Her (Hable con Ella) (2002) | Drama\|Romance
   Before Sunrise (1995) | Drama\|Romance

   Dari hasil diatas dapat dilihat bahwa film yang berkategori Drama|Romance menjadi yang direkomendasikan oleh sistem. Hal ini berdasarkan dari film yang disukai oleh pengguna. Dari 5 item yang direkomendasikan, 5 item memiliki genre Drama|Romance. (similar). Artinya, precision sistem kita sebesar 5/5 atau 100%.
   Teknik Evaluasi di atas adalah dengan menggunakan precission, rumus dari teknik ini adalah :

   ![Screenshot 2024-10-21 141327](https://github.com/user-attachments/assets/3e8d46b2-98bb-44ba-a3d6-bd43ed72d462)
4. Mendapatkan rekomendasi film.

   ![Screenshot 2024-10-21 170933](https://github.com/user-attachments/assets/02c980e1-d5b2-426f-bbec-4bb2331e18a1)
   
   Menampilkan rekomendasi untuk pengguna: 462
   
   Film dengan rating tertinggi dari pengguna:
   Titles | Genres
   --- | ---
   Taxi Driver (1976) | Crime\|Drama\|Thriller
   Heavenly Creatures (1994) | Crime\|Drama
   Godfather, The (1972) | Crime\|Drama
   Monty Python's Life of Brian (1979) | Comedy
   Raging Bull (1980) | Drama

   10 film teratas yang direkomendasikan:
   Titles | Genres
   --- | ---
   Place in the Sun, A (1951) | Drama\|Romance
   My Life (1993) | Drama
   Crossing Delancey (1988) | Comedy\|Romance
   Woman Under the Influence, A (1974) | Drama
   Adam's Rib (1949) | Comedy\|Romance
   Into the Woods (1991) | Adventure\|Comedy\|Fantasy\|Musical
   Match Factory Girl, The (Tulitikkutehtaan tyttö) (1990) | Comedy\|Drama
   It's Such a Beautiful Day (2012) | Animation\|Comedy\|Drama\|Fantasy\|Sci-Fi
   Frank (2014) | Comedy\|Drama\|Mystery
   Black Mirror: White Christmas (2014) | Drama\|Horror\|Mystery\|Sci-Fi\|Thriller
   
   Dari hasil rekomendasi film diatas adalah Film dengan rating tinggi memberikan saran umum berdasarkan popularitas dan kualitas film. Rekomendasi personal lebih spesifik berdasarkan preferensi atau perilaku pengguna 462, bertujuan memberikan pengalaman lebih relevan dan menarik.
---
## Kesimpulan
Proyek sistem rekomendasi film sangat relevan dalam konteks platform streaming seperti Netflix, HBO Max, dan Disney+ yang menyediakan ribuan item dalam katalognya. Dengan jumlah konten yang begitu besar, pengguna sering merasa kesulitan memilih acara TV atau film yang sesuai dengan preferensi mereka. Sistem rekomendasi menjadi kunci untuk meningkatkan pengalaman pengguna dengan mempermudah mereka menemukan konten yang relevan dan menarik.

Dari sudut pandang bisnis, sistem rekomendasi yang efektif tidak hanya meningkatkan kepuasan pengguna, tetapi juga berpotensi memperpanjang waktu aktivitas pengguna di platform. Hal ini, pada akhirnya, dapat meningkatkan pendapatan melalui langganan atau iklan.

Dalam rangka mencapai tujuan tersebut, proyek ini akan mengembangkan sistem rekomendasi dengan memanfaatkan kombinasi metode *collaborative filtering* dan *content-based filtering*. Pendekatan ini diharapkan dapat meningkatkan akurasi dan efektivitas rekomendasi, dengan:
1. *Collaborative filtering*: Merekomendasikan film berdasarkan kesamaan preferensi atau perilaku pengguna lain.  
2. *Content-based filtering*: Merekomendasikan film berdasarkan karakteristik konten yang sudah disukai oleh pengguna.

Dengan penerapan solusi ini, diharapkan sistem rekomendasi yang dibangun dapat memberikan pengalaman yang lebih personal bagi pengguna sekaligus membantu platform streaming mencapai tujuan bisnis mereka.

---
## Penutup
Demikian hasil dari laporan proyek machine learning tentang Sistem Rekomendasi Film. Bilamana didalam penyampaian serta penjelasan yang kurang berkenaan, saya memohon maaf. Atas waktu dan perhatiannya, saya ucapkan Terima kasih telah membaca laporan ini. Semoga dapat memberi manfaat bagi kita semuanya.
