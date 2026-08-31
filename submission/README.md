# Laporan Proyek Machine Learning - Muhammad Reza Pahlevi Harahap

## Domain Proyek

Pada proyek ini, saya membangun model klasifikasi gambar untuk membedakan antara kucing dan anjing menggunakan Convolutional Neural Network (CNN).  
Masalah ini penting karena model seperti ini banyak digunakan dalam berbagai aplikasi nyata, seperti sistem pengenalan hewan otomatis atau pemantauan hewan peliharaan.

Referensi: [Deep Learning for Image Classification](https://scholar.google.com/)

## Business Understanding

### Problem Statements

- Bagaimana membangun model yang mampu mengklasifikasikan gambar sebagai kucing atau anjing?
- Bagaimana memastikan akurasi model tinggi dengan dataset terbatas?

### Goals

- Membuat model CNN yang mampu membedakan gambar kucing dan anjing.
- Mencapai akurasi setinggi mungkin dengan preprocessing dan tuning sederhana.

### Solution Statements

- Membuat CNN sederhana dengan beberapa layer convolution dan pooling.
- Melakukan augmentasi data untuk meningkatkan variasi dataset.
- Menggunakan dropout untuk menghindari overfitting.

## Data Understanding

Dataset yang digunakan adalah kumpulan gambar kucing dan anjing, tersedia dari sumber publik.  
Contoh dataset: [Kaggle Dogs vs. Cats Dataset](https://www.kaggle.com/c/dogs-vs-cats/data).

Fitur dari dataset:
- Gambar berformat JPG.
- Setiap gambar memiliki label 'cat' atau 'dog' berdasarkan nama file.

## Data Preparation

Tahapan data preparation yang dilakukan:
- Mengubah ukuran semua gambar menjadi 150x150 piksel.
- Menskalakan pixel gambar ke rentang 0-1.
- Membagi dataset menjadi train, validation, dan test set.
- Menggunakan `ImageDataGenerator` untuk augmentasi sederhana (rescale, horizontal flip, dll).

## Modeling

Model yang dibangun menggunakan CNN bertingkat:

- Layer Conv2D diikuti MaxPooling2D untuk ekstraksi fitur.
- Layer Flatten untuk meratakan output dari convolutional layers.
- Dense layer untuk klasifikasi.
- Dropout layer digunakan untuk mengurangi overfitting.
- Output layer dengan aktivasi sigmoid karena klasifikasi binary.

Model dikompilasi menggunakan optimizer Adam dan loss function binary crossentropy.

## Evaluation

Metrik evaluasi yang digunakan:
- **Akurasi**: Persentase gambar yang diklasifikasikan dengan benar.

Hasil proyek:
- Model mencapai akurasi yang cukup baik pada data validasi.
- Dropout berhasil membantu mencegah overfitting selama training.
