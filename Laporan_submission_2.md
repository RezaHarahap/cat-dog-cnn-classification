# Laporan Proyek Machine Learning - Muhammad Reza Pahlevi Harahap

## Project Overview

Buku adalah kumpulan lembaran kertas atau bahan lain yang mengandung tulisan, gambar, atau tempelan, yang dijilid pada salah satu sisinya. Seiring dengan kemajuan teknologi, hadir pula buku elektronik (e-book) yang dapat diakses melalui berbagai perangkat elektronik seperti komputer, tablet, atau ponsel pintar. Sistem rekomendasi memegang peranan krusial dalam membantu pengguna menavigasi dan menemukan item, termasuk buku, yang paling sesuai dengan minat dan preferensi mereka di tengah lautan pilihan yang tersedia. Banyaknya judul buku yang ada seringkali membuat pembaca kesulitan dalam menentukan bacaan selanjutnya.

Masalah ini perlu diselesaikan karena kesulitan dalam menemukan buku yang relevan dapat mengurangi kepuasan pengguna terhadap platform penyedia buku. Jika pengguna merasa kewalahan atau tidak menemukan apa yang mereka cari, loyalitas mereka terhadap platform dapat menurun. Dengan mengembangkan sistem rekomendasi buku yang efektif, kita dapat membantu pengguna menemukan buku-buku baru yang menarik dan sesuai dengan selera mereka. Hal ini tidak hanya meningkatkan pengalaman pengguna tetapi juga dapat mendorong mereka untuk lebih sering menggunakan platform dan bahkan berlangganan layanan yang ditawarkan. Proyek ini bertujuan membangun sebuah sistem rekomendasi buku untuk mengatasi tantangan tersebut.

## Business Understanding

Proses klarifikasi masalah dalam proyek ini adalah sebagai berikut:

### Problem Statements

Menjelaskan pernyataan masalah:
- Pengguna sering menghadapi kesulitan dalam menemukan buku baru yang sesuai dengan preferensi bacaan mereka di antara banyaknya pilihan judul yang tersedia.
- Preferensi pembaca dalam memilih buku sangat beragam, dipengaruhi oleh faktor seperti popularitas buku, kesamaan dengan riwayat bacaan sebelumnya (genre, penulis), atau berdasarkan rating dan ulasan dari pembaca lain.
- Tanpa sistem rekomendasi yang efektif, pengguna dapat merasa kewalahan atau tidak puas dengan pengalaman mereka dalam mencari buku, yang berpotensi mengurangi keterlibatan dan loyalitas mereka terhadap platform.

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Mengembangkan sistem yang mampu merekomendasikan buku-buku yang relevan dan menarik secara personal kepada setiap pengguna, mempermudah proses penemuan buku baru.
- Menyediakan rekomendasi yang dapat mengakomodasi berbagai preferensi pengguna dengan mempelajari pola dari interaksi pengguna-buku.
- Meningkatkan kepuasan pengguna dengan platform buku melalui fitur rekomendasi yang dipersonalisasi, sehingga mendorong penggunaan yang berkelanjutan dan loyalitas terhadap layanan.
 
### Solution statements
- Ada beberapa jenis sistem rekomendasi secara umum, yaitu Content Based Filtering, Collaborative Filtering, dan Hybrid Filtering.
- Solution Approach 1 (Fokus Proyek): Collaborative Filtering dengan Deep Learning. Proyek ini secara spesifik mengembangkan dan mengimplementasikan model sistem rekomendasi buku menggunakan teknik Collaborative Filtering dengan pendekatan Deep Learning. Pendekatan ini mempelajari pola dari data historis interaksi pengguna (rating buku) untuk menemukan kesamaan antar pengguna dan antar buku, kemudian merekomendasikan buku yang kemungkinan besar akan disukai pengguna berdasarkan preferensi pengguna lain yang serupa atau buku lain yang serupa. Model deep learning digunakan untuk menangkap pola yang kompleks dalam data interaksi tersebut.
- Solution Approach 2 (Alternatif Umum): Content-Based Filtering. Meskipun tidak diimplementasikan dalam notebook ini, Content-Based Filtering adalah pendekatan umum lainnya. Pendekatan ini merekomendasikan item berdasarkan perbandingan antara konten item (misalnya genre buku, kata kunci deskripsi, penulis) dengan profil preferensi pengguna yang dibangun dari item yang pernah disukai pengguna di masa lalu.

## Data Understanding

Dataset yang digunakan dalam proyek ini adalah "Book Recommendation Dataset" di platform Kaggle. Dataset ini dapat diunduh melalui tautan: https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset. 

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- Users.csv:
    Jumlah data: 278.858 baris dan 3 kolom.
    Kondisi data: Kolom Age memiliki 110.762 nilai kosong.
    Variabel:
    User-ID: ID unik untuk setiap pengguna.
    Location: Lokasi pengguna. 
    Age: Usia pengguna. 
- Books.csv:
    Jumlah data: 271.360 baris dan 8 kolom.
    Kondisi data: Terdapat 2 nilai kosong pada kolom Book-Author, 2 pada Publisher, dan 3 pada Image-URL-L. Beberapa nilai pada Year-Of-Publication tidak valid (contoh: nama penerbit).
    Variabel:
    ISBN: Nomor Standar Buku Internasional, ID unik untuk buku. 
    Book-Title: Judul buku.
    Book-Author: Penulis buku.
    Year-Of-Publication: Tahun publikasi buku. 
    Publisher: Penerbit buku. 
    Image-URL-S: URL gambar sampul buku ukuran kecil. 
    Image-URL-M: URL gambar sampul buku ukuran sedang.
    Image-URL-L: URL gambar sampul buku ukuran besar. 
- Ratings.csv:
    Jumlah data: 1.149.780 baris dan 3 kolom.
    Kondisi data: Tidak ada nilai kosong. Rating berkisar dari 0 hingga 10.
    Variabel:
    User-ID: ID pengguna yang memberikan rating. 
    ISBN: ISBN buku yang diberi rating. 
    Book-Rating: Rating yang diberikan oleh pengguna untuk buku tersebut. 

Karena jumlah data yang sangat besar, proyek ini menggunakan sampel data sebanyak 12.000 baris pertama dari masing-masing dataset (Users.csv, Books.csv, dan Ratings.csv) untuk proses pembuatan model guna efisiensi komputasi.

### Exploratory Data Analysis (EDA)
Exploratory Data Analysis (EDA) dilakukan pada sampel data ini untuk memahami karakteristiknya lebih dalam. Beberapa insight dari EDA:
- Visualisasi 10 tahun dengan publikasi buku terbanyak menunjukkan bahwa tahun 2002 memiliki jumlah publikasi tertinggi dalam sampel data.
- Distribusi rating buku menunjukkan bahwa rating 0 merupakan rating yang paling banyak diberikan oleh pengguna, diikuti oleh rating 8 dan 7. Ini bisa mengindikasikan rating implisit (buku yang dilihat tetapi tidak benar-benar dirating) atau ketidakpuasan.
- Stephen King adalah penulis paling populer berdasarkan jumlah buku dalam sampel data.
- Lokasi "london, england, united kingdom" muncul sebagai lokasi yang paling sering terdata untuk pengguna dalam sampel.
- Di antara buku-buku yang paling banyak dibaca (memiliki jumlah rating terbanyak), "The Lovely Bones: A Novel" memiliki rata-rata rating tertinggi.

## Data Preparation
Tahapan persiapan data yang dilakukan secara berurutan adalah sebagai berikut:
- Pengambilan Sampel Data: Mengambil 12.000 baris pertama dari masing-masing file CSV (Users.csv, Books.csv, Ratings.csv). Alasan: Untuk mengurangi beban komputasi dan mempercepat proses pelatihan model dengan dataset yang lebih manageable.
- Modifikasi data_books (Dataset Buku):
    * Menghapus kolom Image-URL-S, Image-URL-M, dan Image-URL-L. Alasan: URL gambar sampul tidak digunakan sebagai fitur dalam model collaborative filtering ini.
    * Mengganti nama kolom: Book-Title menjadi Book_Title, Book-Author menjadi Book_Author, Year-Of-Publication menjadi Year_Publication. Alasan: Untuk konsistensi penamaan dan kemudahan akses.
    * Mengubah tipe data Year_Publication menjadi numerik (int64), menangani nilai yang tidak valid. Alasan: Untuk memungkinkan analisis berbasis tahun jika diperlukan, meskipun tidak secara langsung digunakan sebagai fitur embedding.
- Modifikasi data_rating (Dataset Rating): Mengganti nama kolom: User-ID menjadi UserID, Book-Rating menjadi Book_Rating. Alasan: Konsistensi penamaan.
- Modifikasi data_users (Dataset Pengguna):
    * Menghapus kolom Age. Alasan: Banyaknya nilai kosong (lebih dari sepertiga pada sampel) dan kolom ini tidak akan digunakan dalam model collaborative filtering yang fokus pada interaksi.
    * Mengganti nama kolom User-ID menjadi UserID. Alasan: Konsistensi penamaan.
- Penggabungan Data:
    * Menggabungkan data_rating dengan data_books (yang sudah dimodifikasi) berdasarkan ISBN menjadi data_train. Alasan: Untuk mendapatkan informasi detail buku (judul, penulis) untuk setiap rating.
    * Menggabungkan data_rating dengan data_users (yang sudah dimodifikasi) berdasarkan UserID menjadi data_using. Alasan: Untuk mendapatkan informasi pengguna (lokasi) untuk setiap rating, meskipun lokasi akhirnya tidak digunakan dalam model.
- Penghapusan Duplikat:
    * Menghapus baris duplikat dari data_train berdasarkan ISBN, hasilnya disimpan sebagai data_prep. Alasan: Untuk memastikan setiap buku unik dalam daftar buku yang akan digunakan.
    * Menghapus baris duplikat dari data_using berdasarkan UserID, hasilnya disimpan sebagai data_prus. Alasan: Untuk memastikan setiap pengguna unik.
- Pembuatan DataFrame Buku yang Disederhanakan (books_new): Membuat DataFrame baru yang hanya berisi id (dari ISBN), title (dari Book_Title), dan author (dari Book_Author) dari data_prep. Alasan: Untuk mempermudah pencarian informasi buku saat menampilkan rekomendasi.
- Encoding Fitur Pengguna dan Buku:
    * Memetakan setiap UserID unik ke integer berurutan (user_encoded).
    * Memetakan setiap ISBN unik (dari data_rating) ke integer berurutan (book_encoded).
    * Menyimpan pemetaan ini dalam dictionary (user_to_user_encoded, user_encoded_to_user, book_to_book_encoded, book_encoded_to_book).
    * Menambahkan kolom user (hasil encoding UserID) dan book (hasil encoding ISBN) ke DataFrame data_rating (disimpan sebagai data). Alasan: Model deep learning memerlukan input numerik.
- Normalisasi Rating: Mengubah tipe data Book_Rating menjadi float32 dan menormalisasi nilainya ke rentang [0, 1] dengan membagi semua rating dengan nilai rating maksimum (yaitu 10). Alasan: Untuk menstabilkan proses pelatihan dan agar output model (dengan aktivasi sigmoid) berada dalam rentang yang sama.
- Pembagian Data: Mengacak dataset data dan membaginya menjadi data latih (90%) dan data validasi (10%). x terdiri dari pasangan user (encoded) dan book (encoded), sedangkan y adalah Book_Rating yang telah dinormalisasi. Alasan: Untuk melatih model dan mengevaluasi kinerjanya pada data yang tidak terlihat selama pelatihan.

## Modeling
Sistem rekomendasi yang dibuat menggunakan pendekatan Collaborative Filtering berbasis Deep Learning. Model ini bertujuan untuk mempelajari representasi laten (embedding) dari pengguna dan buku berdasarkan histori rating.

Solusi 1: Collaborative Filtering dengan Deep Learning (RecommenderNet)
Model RecommenderNet didefinisikan sebagai kelas Keras dengan arsitektur sebagai berikut:

- Input: Pasangan ID pengguna (telah di-encode) dan ID buku (telah di-encode).
- Embedding Layers:
    * user_embedding: Membuat vektor embedding untuk setiap pengguna. Dimensi: (jumlah_pengguna_unik, embedding_size).
    * user_bias: Membuat vektor bias untuk setiap pengguna. Dimensi: (jumlah_pengguna_unik, 1).
    * book_embedding: Membuat vektor embedding untuk setiap buku. Dimensi: (jumlah_buku_unik, embedding_size).
    * book_bias: Membuat vektor bias untuk setiap buku. Dimensi: (jumlah_buku_unik, 1).
    * Ukuran embedding (embedding_size) yang digunakan adalah 50. Inisialisasi he_normal dan regularisasi L2 (1e-6) digunakan pada layer embedding.
- Interaksi: Dot product antara embedding pengguna dan embedding buku.
- Output: Hasil dot product dijumlahkan dengan bias pengguna dan bias buku, kemudian dilewatkan melalui fungsi aktivasi sigmoid untuk menghasilkan prediksi  rating antara 0 dan 1.
- Model ini dikompilasi menggunakan:    
    * Optimizer: Adam dengan learning_rate=0.001.
    * Loss Function: BinaryCrossentropy (karena output sigmoid dan target ternormalisasi).
    * Metric: RootMeanSquaredError.
- Model dilatih selama 100 epoch dengan batch_size 64.
- Kelebihan RecommenderNet (Collaborative Filtering - Deep Learning):
    * Mampu menangkap pola dan hubungan yang kompleks antara pengguna dan item melalui embedding.
    * Tidak memerlukan fitur eksplisit dari item (seperti genre buku), hanya data interaksi.
    * Dapat menghasilkan rekomendasi yang mengejutkan (serendipitous) karena didasarkan pada kesamaan perilaku pengguna.
- Kekurangan RecommenderNet:
    * Cold Start Problem: Sulit memberikan rekomendasi untuk pengguna baru atau item baru yang belum memiliki data interaksi.
    * Data Sparsity: Kinerja dapat menurun jika matriks interaksi pengguna-item sangat jarang (banyak pengguna hanya memberi rating pada sedikit item).

Solusi 2: Content-Based Filtering (Sebagai Alternatif Umum)
Seperti yang disebutkan di bagian Solution Approach, notebook mengidentifikasi Content-Based Filtering sebagai salah satu jenis sistem rekomendasi. Meskipun tidak diimplementasikan, pendekatan ini akan merekomendasikan buku berdasarkan atribut buku (misalnya, genre, penulis, kata kunci) dan preferensi pengguna terhadap atribut tersebut yang dipelajari dari buku yang telah mereka sukai sebelumnya.
- Kelebihan Content-Based Filtering:
    * Tidak mengalami cold start problem untuk item baru selama fitur item tersedia.
    * Dapat merekomendasikan item yang spesifik dan sesuai dengan minat pengguna.
    * Rekomendasi lebih mudah dijelaskan.
- Kekurangan Content-Based Filtering:
    * Membutuhkan data fitur item yang baik dan terstruktur.
    * Cenderung menghasilkan rekomendasi yang kurang beragam (over-specialization), sulit menemukan item di luar profil minat awal pengguna.
    * Tidak efektif jika data interaksi pengguna sedikit untuk membangun profil.
- Proyek ini berfokus pada implementasi Solusi 1.
- Top-N Recommendation Output:
Model memberikan daftar rekomendasi buku. Prosesnya melibatkan:
    * Mengidentifikasi buku yang belum pernah diberi rating oleh pengguna tersebut.
    * Memprediksi rating untuk buku-buku tersebut menggunakan model RecommenderNet yang telah dilatih.
    * Mengurutkan buku berdasarkan prediksi rating tertinggi.
    * Menampilkan N buku teratas.
Setelah model dilatih, dapat digunakan untuk menghasilkan rekomendasi buku untuk pengguna tertentu. Untuk seorang pengguna dengan user_id contoh 278418, sistem merekomendasikan 10 buku teratas sebagai berikut:

Menampilkan Rekomendasi Untuk Pengguna: 278418
===========================
10 Rekomendasi Buku Teratas
--------------------------------
1 Little Altars Everywhere : Rebecca Wells
2 The Watsons Go to Birmingham - 1963 (Yearling Newbery) : CHRISTOPHER PAUL CURTIS
3 Politically Correct Bedtime Stories: Modern Tales for Our Life and Times : James Finn Garner
4 Les Fourmis : Bernard Werber
5 Night over Water : Ken Follett
6 She's Come Undone (Oprah's Book Club) : Wally Lamb
7 Rebecca : Daphne Du Maurier
8 Chasing the Dime : Michael Connelly
9 The Bonesetter's Daughter : Amy Tan
10 Life's Little Instruction Book (Life's Little Instruction Books (Paperback)) : H. Jackson Brown
Model memprediksi rating untuk buku-buku yang belum pernah dikunjungi oleh pengguna, dan kemudian mengurutkannya untuk mendapatkan 10 rekomendasi teratas.

- Kelebihan:
    * Personalisasi Tinggi: Model dapat belajar preferensi individual pengguna dan merekomendasikan item yang sangat relevan, bahkan jika item tersebut belum populer secara keseluruhan.
    * Menemukan Pola Tersembunyi: Deep Learning mampu menemukan pola-pola kompleks dalam data yang mungkin tidak terlihat dengan metode tradisional.
    * Skalabilitas: Model ini dapat diskalakan untuk menangani dataset yang besar, meskipun pada proyek ini digunakan subset data.
- Kekurangan:
    * Cold Start Problem: Sulit memberikan rekomendasi akurat untuk pengguna baru (karena tidak ada riwayat rating) atau buku baru (karena belum ada rating dari pengguna lain).
    * Kebutuhan Data: Membutuhkan banyak data interaksi (rating) untuk melatih model secara efektif.
    * Interpretability Rendah: Sulit untuk menjelaskan secara intuitif mengapa suatu rekomendasi diberikan, karena model deep learning seringkali dianggap sebagai "kotak hitam".

## Evaluation
Metrik evaluasi yang digunakan untuk menilai performa model sistem rekomendasi ini adalah:

- Root Mean Squared Error (RMSE):
RMSE mengukur akar kuadrat dari rata-rata selisih kuadrat antara nilai prediksi dan nilai aktual. Semakin kecil nilai RMSE, semakin baik performa model dalam memprediksi rating.
Formula:
RMSE= [Formula RMSE](RMSE.png)

Di mana:
    * N adalah jumlah data.
    * yi adalah nilai rating aktual (ternormalisasi).
    * y^i adalah nilai rating prediksi (output model).

- Cara Kerja: RMSE memberikan penalti yang lebih besar untuk kesalahan prediksi yang besar. Nilainya dapat diinterpretasikan dalam unit yang sama dengan variabel target.
- Hasil Proyek: Plot pelatihan menunjukkan nilai RMSE untuk data latih dan validasi menurun seiring bertambahnya epoch. Pada epoch terakhir (100):
    * RMSE data latih: sekitar 0.1496
    * RMSE data validasi: sekitar 0.2946
- Mean Squared Error (MSE):
MSE mengukur rata-rata dari selisih kuadrat antara nilai prediksi dan nilai aktual.
Formula:
MSE= [Formula MSE](MSE.png)

- Cara Kerja: Seperti RMSE, MSE memberikan bobot lebih pada kesalahan besar. Ini adalah loss function yang umum untuk masalah regresi.
- Hasil Proyek: Notebook melaporkan nilai MSE yang dibagi dengan 1e3 (kemungkinan untuk scaling atau kesalahan ketik, perlu dikonfirmasi maksud pembagian ini):
    * MSE data latih (setelah dibagi 1e3): 2.1095x10^-5
    * MSE data validasi (setelah dibagi 1e3): 8.6761x10^-5 Jika nilai MSE aktualnya tanpa pembagian 1e3 adalah (RMSE)^2 maka:
    * MSE data latih aktual: (0.1496)^2 ≈ 0.02238
    * MSE data validasi aktual: (0.2946)^2 ≈ 0.08679

Nilai RMSE validasi sekitar 0.2946 pada skala rating ternormalisasi (0-1) menunjukkan bahwa model memiliki kemampuan prediksi yang cukup baik. Adanya perbedaan antara RMSE latih dan validasi (0.1496 vs 0.2946) menunjukkan adanya gap generalisasi, yang umum terjadi, namun model tidak tampak overfitting secara ekstrem karena kurva validasi masih menunjukkan penurunan dan stabil.
