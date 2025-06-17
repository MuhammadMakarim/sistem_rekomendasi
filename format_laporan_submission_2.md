# Laporan Proyek Machine Learning - Muhammad Makarim
---
## Project Overview

Pada era digital saat ini, pertumbuhan konten digital, termasuk anime, sangat pesat. Pengguna seringkali kewalahan dalam menemukan konten yang relevan dan menarik di tengah banyaknya pilihan yang tersedia. Sistem rekomendasi menjadi solusi krusial untuk membantu pengguna menavigasi lautan konten ini dengan menyajikan daftar item (dalam hal ini, anime) yang diprediksi sesuai dengan selera atau preferensi mereka.

Proyek ini bertujuan untuk membangun sistem rekomendasi anime menggunakan dua pendekatan utama: Content-Based Filtering dan Collaborative Filtering.

**Mengapa dan Bagaimana Masalah Rekomendasi Anime Perlu Diselesaikan** 

Masalah utama yang dihadapi pengguna di tengah melimpahnya konten anime adalah overload informasi (information overload). Dengan ribuan judul anime tersedia, mulai dari seri televisi, film, hingga OVA, pengguna kesulitan menemukan anime yang benar-benar sesuai dengan preferensi pribadi mereka. Tanpa bantuan, proses pencarian bisa memakan waktu, membuat frustrasi, dan bahkan menyebabkan pengguna melewatkan judul-judul potensial yang sebenarnya akan sangat mereka nikmati. Ini bukan hanya merugikan pengguna secara individu, tetapi juga bagi kreator dan platform distribusi anime, karena konten mereka mungkin tidak mencapai audiens yang tepat.

Oleh karena itu, pembangunan sistem rekomendasi anime menjadi krusial karena alasan berikut:
1. Meningkatkan Pengalaman Pengguna: Sistem rekomendasi mempersonalisasi penemuan konten, menyajikan anime yang relevan dengan selera unik setiap pengguna, sehingga meningkatkan kepuasan dan keterlibatan mereka.
2. Meningkatkan Konsumsi Konten: Dengan memudahkan pengguna menemukan anime yang disukai, sistem rekomendasi mendorong pengguna untuk menonton lebih banyak judul dan menghabiskan lebih banyak waktu di platform.
3. Mendukung Kreator dan Industri: Sistem rekomendasi membantu mendistribusikan visibilitas judul-judul anime, termasuk yang kurang populer namun berkualitas, sehingga memberikan kesempatan bagi kreator untuk menjangkau audiens yang tepat.
4. Mengatasi Cold Start Problem: Untuk pengguna baru atau anime baru, sistem rekomendasi (terutama dengan pendekatan hybrid atau content-based) dapat memberikan rekomendasi awal meskipun data interaksi belum banyak tersedia.

Masalah ini dapat diselesaikan dengan membangun sistem rekomendasi menggunakan berbagai algoritma. Dalam proyek ini, dua pendekatan utama yang digunakan adalah:
1. Content-Based Filtering: Mengidentifikasi anime yang memiliki fitur serupa dengan anime yang disukai pengguna. Jika pengguna menyukai anime dengan genre "Action" dan "Sci-Fi" serta memiliki rating tinggi, sistem akan mencari anime lain dengan kombinasi genre dan karakteristik serupa.
2. Collaborative Filtering: Mengidentifikasi pengguna lain dengan pola rating yang serupa dengan pengguna target. Jika pengguna A dan pengguna B sama-sama menyukai anime X, Y, dan Z, dan pengguna A baru saja menonton dan menyukai anime W, maka sistem akan merekomendasikan anime W kepada pengguna B. Metode SVD digunakan untuk menemukan pola laten dalam matriks interaksi pengguna-item yang memungkinkan prediksi rating.

Kombinasi atau pemilihan pendekatan yang tepat (atau bahkan pendekatan hybrid yang menggabungkan keduanya) adalah kunci untuk membangun sistem rekomendasi yang efektif dan mengatasi tantangan seperti cold-start dan over-specialization.

**Hasil Riset Terkait atau Referensi** <br>
Pembangunan sistem rekomendasi telah menjadi area penelitian yang luas dalam ilmu komputer dan ilmu data. Banyak studi telah menunjukkan efektivitas berbagai algoritma dalam meningkatkan metrik seperti accuracy (misalnya, RMSE, MAE) dan coverage dalam domain yang beragam, termasuk film, musik, dan produk e-commerce.

Referensi kredibel yang mendukung konsep dan metode yang digunakan dalam proyek ini antara lain:
> [1] Aggarwal, C. C. (2016). Recommender Systems: The Textbook. Springer. <br>
> [2] Koren, Y., Bell, R., & Volinsky, C. (2009). Matrix Factorization Techniques for Recommender Systems. Computer, 42(8), 30–37. 

Referensi-referensi ini memberikan dasar teoritis yang kuat mengenai cara kerja, kelebihan, dan kekurangan dari pendekatan Content-Based Filtering dan Collaborative Filtering (terutama SVD) yang diimplementasikan dalam proyek ini.

## Business Understanding
### Problem Statements <br>
Berdasarkan konteks proyek dan data yang digunakan, masalah utama dapat dirumuskan sebagai berikut:
1. Overload Informasi Anime: Pengguna kesulitan menemukan anime yang relevan dan menarik bagi mereka di antara ribuan judul yang tersedia dalam database.
2. Inefisiensi Pencarian Manual: Proses pencarian dan pemilihan anime secara manual memakan waktu dan bisa membuat frustrasi pengguna, sehingga mengurangi pengalaman menonton secara keseluruhan.

### Goals <br>
Tujuan utama dari pembangunan sistem rekomendasi ini, selaras dengan masalah yang diidentifikasi, adalah:
1. Meningkatkan Kemudahan Penemuan Konten: Menyediakan mekanisme otomatis untuk menyajikan anime yang kemungkinan besar akan disukai oleh pengguna.
2. Meningkatkan Relevansi Rekomendasi: Memastikan bahwa anime yang direkomendasikan sesuai dengan preferensi dan selera pengguna individu.
3. Meningkatkan Pengalaman Pengguna: Membuat proses menemukan anime menjadi lebih efisien dan menyenangkan.

### Solution Statements <br>
Untuk mencapai tujuan tersebut dan mengatasi masalah yang ada, solusi yang diusulkan dalam proyek ini adalah:
1. Membangun Sistem Rekomendasi Berbasis Konten: Mengembangkan model yang merekomendasikan anime berdasarkan kemiripan fitur-fitur intrinsik anime itu sendiri (seperti genre, rating, members), menggunakan teknik seperti TF-IDF dan Cosine Similarity.
2. Membangun Sistem Rekomendasi Kolaboratif: Mengembangkan model yang merekomendasikan anime berdasarkan pola interaksi (rating) pengguna, menggunakan teknik Model-Based Collaborative Filtering seperti Singular Value Decomposition (SVD).
3. Mengevaluasi Performa Model: Menggunakan metrik yang sesuai (misalnya, RMSE untuk CF, analisis similarity untuk CBF) serta demonstrasi rekomendasi untuk menilai efektivitas kedua pendekatan dalam merekomendasikan anime.

Melalui implementasi dan evaluasi kedua pendekatan ini, proyek ini berupaya menyediakan solusi efektif untuk membantu pengguna menemukan anime yang mereka sukai, sekaligus memberikan dasar perbandingan antara Content-Based Filtering dan Collaborative Filtering dalam domain data anime.

## Data Understanding
Bagian ini bertujuan untuk memahami karakteristik data yang digunakan dalam proyek sistem rekomendasi anime, termasuk sumber data, jumlah record, kondisi awal data, dan deskripsi variabel yang ada.

Data yang digunakan dalam proyek ini adalah Anime Recommendations Database. Dataset ini tersedia di Kaggle Hub.
<br>
https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database
<br>

Dataset ini terdiri dari dua berkas CSV utama:
1. anime.csv: Berkas ini berisi informasi metadata tentang berbagai judul anime.
2. rating.csv: Berkas ini berisi rating yang diberikan oleh pengguna terhadap anime.

Pada awal analisis, melakukan sampling pada df_rating menjadi 1% dari data asli (df_rating = df_rating.sample(frac=0.01, random_state=42)).
- Jumlah record awal df_anime: 12.294 baris, 7 kolom
- Jumlah record awal df_rating: 7.813.737 baris, 3 kolom
- Jumlah record setelah sampling df_rating: 78.137 baris, 3 kolom

Kondisi awal data menunjukkan adanya missing values pada beberapa kolom di df_anime (genre, type, episodes, rating, members) dan df_rating (rating). Terdapat juga nilai rating 0 pada df_rating yang diinterpretasikan sebagai implicit clicks atau tayangan tanpa rating eksplisit. Tidak ditemukan data duplikat pada kedua DataFrame.

### **Variabel pada Data**
Pada anime.csv:
- anime_id: ID unik untuk setiap judul anime.
- name: Judul anime.
- genre: Genre anime (dapat berisi beberapa genre dipisahkan '|').
- type: Tipe tayangan anime (TV, Movie, OVA, dll.).
- episodes: Jumlah episode.
- rating: Rata-rata rating global untuk anime ini (skala 1-10).
- members: Jumlah anggota komunitas MyAnimeList yang menambahkan anime ini ke daftar mereka.

Pada rating.csv:
- user_id: ID unik pengguna.
- anime_id: ID unik anime yang diberi rating.
- rating: Rating yang diberikan oleh user_id untuk anime_id (skala -1 hingga 10, -1/0 adalah implicit).

### **Exploratory Data Analysis - EDA**
Beberapa tahapan eksplorasi data telah dilakukan untuk mendapatkan insight awal mengenai karakteristik data:
1. Jumlah Record & Contoh Data: Melihat jumlah total baris dan menampilkan 5 baris pertama dari setiap tabel memberikan gambaran sekilas mengenai struktur dan isi data.
2. Daftar Fitur & Tipe Data: Memeriksa nama kolom dan tipe datanya membantu mengidentifikasi fitur yang tersedia dan potensi kebutuhan akan preprocessing (misalnya, mengubah 'episodes' menjadi numerik).
3. Cek Missing Values: Mengidentifikasi jumlah nilai yang hilang di setiap kolom menunjukkan sejauh mana data perlu dibersihkan atau diimputasi sebelum digunakan dalam model.
4. Cek Duplikasi Data: Memastikan tidak adanya baris duplikat yang dapat mempengaruhi analisis atau pelatihan model.
5. Statistik Deskriptif Dasar: Melihat ringkasan statistik (count, mean, std, min, max, dll.) untuk kolom numerik seperti rating dan members memberikan pemahaman awal tentang distribusi nilai.
6. Insight Awal: Menghitung jumlah pengguna unik, anime unik, dan implicit clicks memberikan gambaran skala data interaksi dan karakteristik perilakunya.

**Visualisasi Data & Insight**

Exploratory Data Analysis juga melibatkan visualisasi data untuk mengungkap pola dan distribusi:
1. Distribusi Rating Pengguna:
    - Visualisasi: Count plot dari nilai rating (0-10).
    - Insight: Terlihat bahwa nilai rating 0 (implicit click) memiliki frekuensi yang sangat tinggi dibandingkan dengan rating eksplisit (1-10). Di antara rating eksplisit, distribusi cenderung condong ke rating yang lebih tinggi.
![Grafik Distribusi Rating Pengguna](https://raw.githubusercontent.com/MuhammadMakarim/sistem_rekomendasi/8cc0023b3fbfa61f7d9fb60b5419335b174f7b41/Gambar/Distribusi%20seluruh%20nilai%20rating.png)

2. Rating Korelasi:
    - Visualisasi: Heatmap korelasi antara fitur numerik episodes, members, dan rating di df_anime (setelah mengonversi episodes menjadi numerik dan menghapus nilai non-valid/0).
    - Insight: Terdapat korelasi positif antara members dan rating, menunjukkan bahwa anime yang memiliki komunitas besar cenderung memiliki rating rata-rata yang lebih tinggi. Korelasi antara episodes dengan members dan rating cenderung lemah.
![Grafik Korelasi Fitur Numerik](https://raw.githubusercontent.com/MuhammadMakarim/sistem_rekomendasi/8cc0023b3fbfa61f7d9fb60b5419335b174f7b41/Gambar/correlation%20matrix.png)

3. Top-N Anime:
    - Visualisasi: Bar plot Top 3 anime berdasarkan jumlah rating (count) dan Top 10 anime berdasarkan rata-rata rating (mean), dengan filter minimum jumlah rating > 0 dan threshold count >= 250 untuk rata-rata rating.
    - Insight: Anime dengan jumlah rating terbanyak mencerminkan popularitas atau jangkauan yang luas, sementara anime dengan rata-rata rating tertinggi (dengan threshold count) cenderung dianggap berkualitas oleh sebagian besar penonton yang sudah menontonnya.
![Top Anime by Avarage Rating](https://raw.githubusercontent.com/MuhammadMakarim/sistem_rekomendasi/53da6adc730231d8e8f339a1e0a9cb6d8d200c16/Gambar/top_anime_bycount.png)
![Top Anime by Rating](https://raw.githubusercontent.com/MuhammadMakarim/sistem_rekomendasi/53da6adc730231d8e8f339a1e0a9cb6d8d200c16/Gambar/top10_animebyratings.png)

4. Genre Explosion & Top Genres:
    - Visualisasi: Menghitung genre unik dan menampilkan bar plot 20 genre teratas berdasarkan frekuensinya di dataset.
    - Insight: Mengungkap genre-genre yang paling dominan dalam dataset, memberikan pemahaman tentang jenis konten yang paling banyak tersedia (misalnya, Comedy, Action, Sci-Fi seringkali muncul di daftar teratas).
![Top 20 Genres](https://raw.githubusercontent.com/MuhammadMakarim/sistem_rekomendasi/53da6adc730231d8e8f339a1e0a9cb6d8d200c16/Gambar/top20_genres.png)

5. Tipe Anime:
    - Visualisasi: Count plot distribusi tipe anime.
    - Insight: Menunjukkan tipe anime apa yang paling umum dalam dataset (misalnya, TV Series seringkali mendominasi jumlah).

![Distribusi Tipe Anime](https://raw.githubusercontent.com/MuhammadMakarim/sistem_rekomendasi/53da6adc730231d8e8f339a1e0a9cb6d8d200c16/Gambar/dsitribusi_tipe_anime.png)

## Data Preparation
Tahap Data Preparation merupakan langkah krusial untuk membersihkan, mengubah, dan menyusun data mentah menjadi format yang siap digunakan untuk pelatihan model. Teknik-teknik yang diterapkan pada tahap ini bertujuan untuk menangani masalah yang teridentifikasi saat Data Understanding, seperti missing values dan format data yang tidak sesuai.

Proses Data Preparation dilakukan secara berurutan sebagai berikut:
1. Penanganan Missing Values (Cleaning Data):
    - Proses: Nilai yang hilang pada DataFrame df_anime diisi dengan nilai yang relevan: kolom genre diisi string kosong (''), type diisi 'Unknown', episodes diubah ke numerik dan diisi 0 jika tidak valid/hilang, members diisi 0 jika hilang, dan rating diisi dengan nilai rata-rata (mean_score) dari kolom rating yang ada. Pada DataFrame df_rating, baris dengan missing value pada kolom rating dihapus.
    - Alasan: Missing values dapat menyebabkan error saat pemrosesan data atau pelatihan model, dan imputasi (pengisian nilai) atau penghapusan baris adalah cara untuk menangani masalah ini. Strategi pengisian nilai dipilih berdasarkan tipe data dan konteks kolom (misalnya, mengisi rating dengan rata-rata global, atau mengisi genre kosong agar tidak hilang saat TF-IDF).
  
2. Pemisahan Data Rating (Explicit vs Implicit):
    - Proses: DataFrame df_rating dipisah menjadi dua: df_rating_cf berisi rating eksplisit (> 0), dan df_rating_imp berisi implicit clicks (rating = 0).
    - Alasan: Model Collaborative Filtering yang berbasis prediksi rating eksplisit memerlukan data rating yang sebenarnya diberikan oleh pengguna. Memisahkan implicit clicks memungkinkan kita fokus pada data rating eksplisit yang lebih akurat merefleksikan preferensi kuat pengguna. Data implicit clicks mungkin relevan untuk tipe model CF lain atau analisis terpisah, tetapi untuk model SVD berbasis prediksi rating, rating > 0 lebih sesuai.

3. Filtering Data Rating (Berdasarkan Minimum Interaksi):
    - Proses: DataFrame df_rating_cf (rating eksplisit) difilter untuk hanya menyertakan pengguna (user_id) dan anime (anime_id) yang memiliki jumlah interaksi (rating > 0) minimal 20.
    - Alasan: Pengguna atau item dengan interaksi yang sangat sedikit (sparsity) cenderung tidak memberikan informasi yang cukup bagi model Collaborative Filtering berbasis matriks seperti SVD untuk menemukan pola yang kuat. Menghapus pengguna dan item yang "tidak aktif" membantu mengurangi sparsity dan meningkatkan kualitas data pelatihan untuk model CF, memastikan bahwa model dilatih pada interaksi yang lebih andal.
  
4. Feature Engineering untuk Content-Based Filtering:
    - Proses:
        - TF-IDF untuk Genre: Kolom genre pada df_anime diproses menggunakan TfidfVectorizer untuk mengubah representasi teks genre menjadi matriks numerik (TF-IDF matrix). Pola token r"(?u)\b\w+\b" digunakan untuk memastikan genre yang dipisahkan | diperlakukan sebagai token terpisah.
        - Scaling Fitur Numerik: Fitur numerik rating (rata-rata global anime) dan members pada df_anime dinormalisasi menggunakan MinMaxScaler untuk membawa nilai-nilai ini ke dalam skala yang serupa (biasanya 0-1).
        - Penggabungan Fitur: Matriks TF-IDF (fitur teks) dan matriks fitur numerik yang sudah di-scaling digabungkan secara horizontal (hstack) untuk membentuk feature_matrix tunggal yang merepresentasikan setiap anime.
    - Alasan:
        - Model berbasis konten memerlukan representasi numerik dari fitur item. TF-IDF adalah teknik standar untuk mengukur pentingnya kata (dalam hal ini, genre) dalam dokumen (anime) relatif terhadap korpus (seluruh dataset anime).
        - Scaling fitur numerik penting agar fitur dengan skala nilai yang berbeda (misalnya, jumlah members bisa jutaan, rating hanya 0-10) tidak mendominasi perhitungan kemiripan berbasis jarak (seperti Cosine Similarity). MinMaxScaler membawa semua fitur ke rentang yang seragam.
        - Menggabungkan fitur teks dan numerik memungkinkan model Content-Based mempertimbangkan berbagai aspek anime (genre dan popularitas/kualitas global) saat menghitung kemiripan.

5. Feature Engineering (Collaborative)
   Tahap ini secara spesifik menyiapkan data dalam format yang dibutuhkan oleh model Collaborative Filtering.
   - Proses: Matriks interaksi pengguna-item (user_matrix_train) dibuat menggunakan pivot table dari DataFrame df_rating (setelah proses sampling, pembersihan, dan filtering). Indeks matriks adalah user_id, kolomnya adalah anime_id, dan nilainya adalah rating. Nilai yang kosong (pengguna belum merating anime tertentu) diisi dengan 0 menggunakan fillna(0). Selain itu, user ID dan item ID diekstrak ke dalam list terpisah untuk memudahkan indexing.
   - Alasan: Collaborative Filtering berbasis model, khususnya SVD, memerlukan data interaksi dalam bentuk matriks pengguna-item. Matriks ini merepresentasikan hubungan antara pengguna dan item berdasarkan rating yang diberikan. Pembuatan pivot table adalah cara standar untuk mencapai format ini. Mengisi nilai kosong (sparsity) memungkinkan matriks ini diproses oleh algoritma dekomposisi matriks seperti SVD. Menyimpan user ID dan item ID dalam list terpisah memudahkan pemetaan kembali hasil komputasi SVD (yang berupa matriks numerik) ke ID pengguna dan anime yang sebenarnya, yang penting saat membuat rekomendasi akhir.

Dengan selesainya tahap Feature Engineering ini, data dalam format yang sesuai (baik representasi fitur untuk Content-Based maupun matriks interaksi untuk Collaborative Filtering) telah siap untuk digunakan dalam tahap pengembangan model.

## Modeling
Tahap Modeling ini adalah inti dari proyek, di mana dua pendekatan sistem rekomendasi yang berbeda dibangun dan diimplementasikan untuk memprediksi anime yang relevan bagi pengguna. Dua solusi rekomendasi disajikan: Content-Based Filtering dan Collaborative Filtering menggunakan SVD.

**1. Model Development dengan Content Based Filtering**
Dalam pendekatan ini, rekomendasi dibuat berdasarkan kemiripan antara fitur-fitur anime.
- Representasi Fitur:
    - Menggunakan feature_matrix yang telah disiapkan di tahap Data Preparation, yang merupakan gabungan dari matriks TF-IDF genre dan fitur numerik rating serta members yang sudah di-scaling. Matriks ini merepresentasikan setiap anime sebagai vektor fitur multidimensional.
    - Dibuat mapping antara anime_id dan indeks baris dalam feature_matrix untuk memudahkan pencarian.
- Hitung Similarity:
    - Menggunakan cosine_similarity untuk menghitung tingkat kemiripan (dalam rentang 0 hingga 1) antara setiap pasangan anime berdasarkan feature_matrix mereka. Hasilnya adalah matriks similiaritas cosine_sim.
- Fungsi Rekomendasi (recommend_content_verbose):
    - Fungsi ini menerima anime_id target dan jumlah rekomendasi yang diinginkan (top_n).
    - Mencari indeks matriks untuk anime_id target.
    - Mengambil baris similiaritas dari cosine_sim yang sesuai dengan indeks target.
    - Mengurutkan anime berdasarkan skor similiaritas dalam urutan menurun (mengabaikan anime target itu sendiri).
    - Mengambil top_n anime teratas berdasarkan skor similiaritas.
    - Menampilkan detail anime target dan tabel berisi detail anime yang direkomendasikan beserta skor similiaritasnya.
    - Menyertakan visualisasi bar plot yang menampilkan skor similiaritas anime yang direkomendasikan terhadap anime target.
- Output Top-N Recommendation (Contoh Percobaan):
    - Percobaan 1 (Target anime_id=1 - Cowbay Bebop): Fungsi recommend_content_verbose(anime_id=1, top_n=10) dipanggil. Output akan menampilkan tabel detail untuk anime ID 1 (Cowboy Bebop) dan tabel berisi 10 anime yang direkomendasikan beserta atributnya dan skor similiaritas. Bar plot akan memvisualisasikan skor similiaritas tersebut. Anime yang direkomendasikan diharapkan memiliki genre atau karakteristik lain yang serupa dengan Cowboy Bebop.
    - Percobaan 2 (Target anime_id Random): Fungsi recommend_content_verbose dipanggil dengan anime_id yang dipilih secara acak dari dataset. Output akan menampilkan detail anime acak tersebut dan 10 rekomendasi yang serupa secara konten. Visualisasi similiaritas juga ditampilkan. <br>
![Percobaan 1](https://raw.githubusercontent.com/MuhammadMakarim/sistem_rekomendasi/ec7a596380f9b5819220f35fff971f742ecd08f8/Gambar/percobaan1_cbf.png)
![Percobaan 2](https://raw.githubusercontent.com/MuhammadMakarim/sistem_rekomendasi/ec7a596380f9b5819220f35fff971f742ecd08f8/Gambar/percobaan2_cbf.png)

**Kelebihan & Kekurangan Content-Based Filtering:**
- Kelebihan:
    - Tidak Membutuhkan Data Pengguna Lain: Rekomendasi hanya bergantung pada profil pengguna target dan fitur item. Baik untuk menangani cold-start pengguna baru.
    - Mampu Merekomendasikan Item Baru: Dapat merekomendasikan item yang belum pernah diberi rating asalkan fitur itemnya mirip dengan yang disukai pengguna.
    - Penjelasan Mudah: Rekomendasi dapat dijelaskan berdasarkan fitur-fitur item yang disukai pengguna (misalnya, "direkomendasikan karena Anda menyukai anime bergenre Sci-Fi dan Action").
- Kekurangan:
    - Over-specialization: Cenderung merekomendasikan item yang sangat mirip, membatasi penemuan konten yang beragam (filter bubble).
    - Keterbatasan Fitur: Kualitas rekomendasi sangat bergantung pada kekayaan dan deskriptifnya fitur-fitur item.
    - Membutuhkan Analisis Konten: Membutuhkan preprocessing dan rekayasa fitur yang mendalam untuk item (misalnya, NLP untuk teks).

**2. Model Development dengan Collaborative Filtering**
Pendekatan ini merekomendasikan item berdasarkan pola interaksi (rating) dari sekelompok pengguna. Metode yang digunakan adalah Model-Based CF dengan Singular Value Decomposition (SVD).
- Definisi & Pelatihan Model (SVD):
    - Menggunakan matriks pengguna-item user_matrix_train yang telah disiapkan di tahap Data Preparation.
    - Menerapkan Singular Value Decomposition (SVD) pada matriks ini menggunakan svds dari scipy.sparse.linalg. svds cocok untuk matriks yang jarang (sparse). Matriks diuraikan menjadi tiga matriks: U (faktor laten pengguna), sigma_vals (nilai singular), dan Vt (faktor laten item). Jumlah faktor laten (k) dipilih 50.
    - Nilai singular (sigma_vals) diubah menjadi matriks diagonal sigma.
    - Matriks prediksi rating (pred_df_svd) direkonstruksi dengan mengalikan ketiga matriks hasil dekomposisi (np.dot(np.dot(U, sigma), Vt)). Matriks prediksi ini memiliki dimensi yang sama dengan user_matrix_train dan berisi rating prediksi untuk semua pasangan pengguna-item (termasuk yang belum dirating asli). Hasilnya disimpan dalam DataFrame dengan indeks user_ids dan kolom item_ids.
- Fungsi Top-N Recommendation (get_top_n & recommend_cf_verbose):
    - Fungsi get_top_n menerima DataFrame prediksi (pred_df_svd), user_id target, dan jumlah rekomendasi (n).
    - Mengambil baris prediksi rating untuk user_id target.
    - Mengidentifikasi item yang sudah dirating oleh pengguna target dari user_matrix_train asli.
    - Memfilter prediksi rating untuk hanya item yang belum dirating asli oleh pengguna target.
    - Mengurutkan prediksi rating yang tersisa dalam urutan menurun dan memilih top N item.
    - Mengembalikan list anime_id dan list skor prediksi rating untuk item yang direkomendasikan.
    - Fungsi recommend_cf_verbose memanggil get_top_n, mengambil detail anime yang direkomendasikan dari df_anime, menampilkan detail anime yang sudah dirating pengguna (untuk konteks) dan detail anime yang direkomendasikan (termasuk rating aktual dan prediksi rating), serta memvisualisasikan prediksi rating menggunakan bar plot.
- Output Top-N Recommendation (Contoh Percobaan):
    - Percobaan 1 (user_id Random): Fungsi recommend_cf_verbose dipanggil dengan user_id yang dipilih secara acak dari daftar user aktif di df_rating_cf. Output akan menampilkan (jika ada) anime yang sudah dirating oleh user tersebut, diikuti oleh tabel berisi 5 anime yang direkomendasikan oleh model SVD (yang belum dirating user target) beserta detailnya, rating aktualnya (dari dataset), dan prediksi rating dari model SVD. Bar plot akan menampilkan prediksi rating dari 5 anime tersebut.
    - Percobaan 2 (user_id Random Lain): Fungsi recommend_cf_verbose dipanggil dengan user_id acak lainnya. Output serupa dengan percobaan 1, menampilkan rekomendasi yang dipersonalisasi berdasarkan pola rating user acak kedua. <br>
![Percobaan 1](https://raw.githubusercontent.com/MuhammadMakarim/sistem_rekomendasi/ec7a596380f9b5819220f35fff971f742ecd08f8/Gambar/percobaan1_cf.png)
![Percobaan 2](https://raw.githubusercontent.com/MuhammadMakarim/sistem_rekomendasi/ec7a596380f9b5819220f35fff971f742ecd08f8/Gambar/percobaan2_cf.png)

**Kelebihan & Kekurangan Collaborative Filtering (SVD):**
- Kelebihan:
    - Menemukan Pola Kompleks: Mampu mengidentifikasi hubungan tersembunyi antara pengguna dan item berdasarkan pola rating, merekomendasikan item yang mungkin tidak mirip secara konten tetapi disukai oleh pengguna serupa.
    - Tidak Membutuhkan Fitur Item Detail: Hanya memerlukan data interaksi pengguna-item, berguna ketika fitur item sulit didapatkan.
    - Efektif untuk Item Populer: Cenderung berhasil merekomendasikan item yang sudah sering diinteraksikan oleh banyak pengguna.

- Kekurangan:
    - Cold Start Problem (Pengguna & Item): Sulit memberikan rekomendasi untuk pengguna baru (tidak ada data rating) atau item baru (belum banyak dirating).
    - Sparsity: Kinerja dapat menurun pada dataset di mana sebagian besar pengguna hanya merating sedikit item, membuat matriks interaksi sangat jarang.
    - Sulit Dijelaskan: Hasil rekomendasi berbasis faktor laten seringkali sulit diberikan penjelasan intuitif mengapa item tertentu direkomendasikan.
    - Skalabilitas (pada Matriks Sangat Besar): Meskipun svds dirancang untuk matriks sparse, melatih pada matriks pengguna-item yang masif masih membutuhkan sumber daya komputasi signifikan.

Dengan selesainya tahap Modeling ini, kedua model rekomendasi (Content-Based dan Collaborative Filtering) telah berhasil dibangun dan didemonstrasikan kemampuannya dalam menyajikan Top-N rekomendasi berdasarkan kriteria masing-masing. Tahap selanjutnya adalah evaluasi formal terhadap performa kedua model.

## Evaluation
Tahap Evaluation ini mengukur seberapa baik model rekomendasi yang telah dibangun dalam mencapai tujuan yang ditetapkan. Metrik evaluasi yang dipilih disesuaikan dengan jenis model dan data yang digunakan.

### **Metrik Evaluasi**
**1. Content-Based Filtering:**
- **Precision@k:** Mengukur seberapa banyak item yang relevan dari k item teratas yang direkomendasikan.
- **Recall@k:** Mengukur seberapa banyak item relevan yang berhasil ditemukan oleh sistem dalam k item teratas.

**2. Collaborative Filtering (SVD):**
Menggunakan metrik Root Mean Squared Error (RMSE) untuk mengevaluasi performa model. RMSE umumnya digunakan dalam sistem rekomendasi, terutama pada pendekatan Collaborative Filtering berbasis prediksi rating, untuk mengukur akurasi prediksi model dibandingkan dengan rating aktual pengguna.
- **Formula RMSE:**

  $RMSE = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (\hat{y}_i - y_i)^2}$

  Di mana:
  - $N$ adalah jumlah pasangan prediksi-aktual yang dievaluasi.
  - $\hat{y}_i$ adalah rating yang diprediksi oleh model untuk interaksi ke-i.
  - $y_i$ adalah rating aktual yang diberikan oleh pengguna untuk interaksi ke-i.
- Cara Kerja Metrik: RMSE menghitung rata-rata dari akar kuadrat perbedaan antara nilai prediksi dan nilai aktual. Ini memberikan nilai tunggal yang merepresentasikan "kesalahan" rata-rata model dalam memprediksi rating. Nilai RMSE yang lebih rendah menunjukkan bahwa prediksi model secara rata-rata lebih dekat dengan nilai aktual, sehingga model dianggap memiliki akurasi prediksi yang lebih baik. Karena perbedaan dikuadratkan, RMSE memberikan bobot lebih besar pada kesalahan prediksi yang besar.
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

### **Hasil Proyek Berdasarkan Metrik Evaluasi**
**Evaluasi Content-Based Filtering** <br>
Evaluasi model (Content-Based Filtering) menggunakan metrik Precision dan Recall memberikan gambaran tentang seberapa akurat dan komprehensif rekomendasi yang dihasilkan. Pada percobaan, evaluasi dilakukan dengan mengambil 30 anime secara acak, kemudian model menghasilkan 10 rekomendasi teratas untuk setiap anime berdasarkan kemiripan kontennya, terutama genre.
Hasil evaluasi menunjukkan angka sebagai berikut:
- Average Precision: 0.6167
- Average Recall: 0.3327

Interpretasi Hasil:
1. Average Precision (0.6167): Nilai Precision rata-rata 0.6167 berarti bahwa, secara rata-rata untuk 30 anime yang diuji, sekitar 61.67% dari 10 anime yang direkomendasikan oleh model Content-Based memiliki genre yang sama atau relevan dengan anime target yang menjadi dasar rekomendasi. Ini mengindikasikan bahwa ketika model memberikan rekomendasi, sebagian besar (lebih dari setengah) dari item tersebut memang sesuai dengan preferensi genre yang diidentifikasi dari anime target. Model ini cenderung cukup baik dalam memberikan rekomendasi yang relevan dalam daftar pendek yang disajikan kepada pengguna.
2. Average Recall (0.3327): Nilai Recall rata-rata 0.3327 berarti bahwa, secara rata-rata, model Content-Based berhasil merekomendasikan sekitar 33.27% dari total anime di dataset yang seharusnya relevan (memiliki genre yang sama dengan anime target). Nilai Recall ini menunjukkan kemampuan model untuk menemukan semua item relevan yang ada. Dalam konteks sistem rekomendasi Top-N (yang hanya memberikan daftar pendek), nilai Recall yang tidak terlalu tinggi ini adalah hal yang umum dan dapat diterima. Model berfokus untuk memberikan item yang paling mungkin disukai (Precision) daripada menemukan semua kemungkinan item yang relevan (Recall).

Berdasarkan nilai Precision (0.6167), model Content-Based Filtering cukup efektif dalam memastikan bahwa mayoritas rekomendasi yang diberikan dalam daftar pendek 10 item memang relevan dari segi genre. Meskipun nilai Recall (0.3327) menunjukkan bahwa model tidak menangkap semua anime relevan yang ada di dataset, ini merupakan trade-off yang umum dalam sistem rekomendasi Top-N di mana prioritas diberikan pada akurasi dalam daftar rekomendasi yang ditampilkan kepada pengguna (Precision). Hasil ini menunjukkan bahwa model berhasil memberikan rekomendasi yang sebagian besar sesuai dengan atribut konten anime target.

**Evaluasi Collaborative Filtering (SVD Model)** <br>
Untuk Collaborative Filtering, RMSE dihitung dengan membandingkan rating yang diprediksi oleh model SVD dengan rating aktual yang ada di data pelatihan (rating > 0).
- Proses Evaluasi:
    - Mengekstrak semua rating aktual (> 0) dari matriks pelatihan (user_matrix_train) menjadi daftar pasangan (pengguna, anime, rating aktual).
    - Untuk setiap pasangan (pengguna, anime) dari daftar rating aktual, mencari rating yang diprediksi oleh model SVD dari matriks pred_df_svd.
    -  Mengumpulkan semua pasangan rating aktual dan rating prediksi yang sesuai.
    -   Menghitung RMSE antara vektor rating aktual dan vektor rating prediksi.
- Hasil:
    - Evaluasi Collaborative Filtering (SVD Model): RMSE = 7.2628
- Penjelasan Hasil: Nilai RMSE sebesar 7.2628 untuk model Collaborative Filtering berbasis SVD mengindikasikan tingkat kesalahan prediksi rating yang relatif tinggi pada skala rating 0-10. Ini berarti, rata-rata, prediksi rating model SVD menyimpang sekitar 7.26 poin dari rating aktual yang diberikan pengguna di data pelatihan. Hasil ini menyarankan bahwa model SVD dengan konfigurasi saat ini mungkin tidak terlalu akurat dalam memprediksi rating eksplisit pengguna.
Ada beberapa kemungkinan alasan untuk nilai RMSE yang tinggi ini:
    - Sparsity Data: Meskipun sudah difilter, matriks pengguna-item masih sangat jarang. SVD dapat kesulitan menemukan pola yang kuat dari data yang sedikit.
    - Keterbatasan Model SVD: SVD menangkap pola linier, tetapi mungkin ada pola non-linier dalam preferensi pengguna yang tidak tertangkap.
    - Parameter Model: Jumlah faktor laten (k=50) mungkin tidak optimal.
    - Variasi Rating Pengguna: Pengguna memiliki skala dan kriteria rating yang sangat bervariasi, membuat prediksi rating numerik yang akurat menjadi sulit.

Meskipun nilai RMSE untuk CF SVD tampak tinggi, perlu diingat bahwa tujuan utama sistem rekomendasi seringkali adalah menyediakan daftar Top-N item yang relevan, bukan memprediksi rating numerik secara sempurna. Model SVD yang tidak terlalu akurat dalam prediksi rating individu masih bisa menghasilkan daftar rekomendasi Top-N yang cukup baik, terutama jika item dengan prediksi rating tertinggi cenderung relevan.

Secara keseluruhan, tahap evaluasi ini memberikan gambaran kuantitatif tentang performa kedua model. Content-Based Filtering dievaluasi secara terbatas pada dispersi rating dalam set rekomendasi, sementara Collaborative Filtering dievaluasi akurasi prediksi ratingnya menggunakan RMSE. Hasil ini menunjukkan area potensial untuk peningkatan di masa depan, seperti penyesuaian parameter model atau mencoba algoritma rekomendasi lainnya.

**---Ini adalah bagian akhir laporan---**
