# Klasifikasi Tipe Laptop Menggunakan Algoritma K-Nearest Neighbors (KNN)

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.2%2B-orange.svg)](https://scikit-learn.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-F37626.svg)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Repositori ini berisi proyek machine learning untuk mengklasifikasikan tipe laptop (misalnya, *Notebook, Ultrabook, Gaming*) berdasarkan spesifikasi teknisnya menggunakan algoritma K-Nearest Neighbors (KNN). Proyek ini mencakup seluruh alur kerja ilmu data, mulai dari pembersihan data, analisis data eksplorasi (EDA), prapemrosesan, pelatihan model, hingga evaluasi.

---

## 📖 Latar Belakang & Pernyataan Masalah

Pasar laptop sangat beragam dengan berbagai kategori seperti *Notebook, Ultrabook, Gaming, 2 in 1 Convertible*, dan lain-lain. Bagi konsumen, membedakan tipe laptop hanya dari spesifikasi teknis bisa menjadi hal yang membingungkan.

Proyek ini bertujuan untuk membangun sebuah model klasifikasi yang dapat secara otomatis memprediksi tipe sebuah laptop berdasarkan atribut-atribut teknisnya seperti RAM, berat, harga, ukuran layar, dan fitur lainnya. Model ini dapat membantu sistem e-commerce dalam mengkategorikan produk atau membantu konsumen dalam mengidentifikasi jenis laptop yang sesuai dengan kebutuhan mereka.

---

## 📊 Dataset

Dataset yang digunakan dalam proyek ini adalah `laptop_data_cleaned.csv`, yang berisi informasi detail tentang berbagai laptop. Fitur-fitur utama yang digunakan untuk prediksi meliputi:

-   **Fitur Numerik**: `Ram`, `Weight`, `Price`, `ppi` (pixels per inch)
-   **Fitur Kategorikal**: `Company`, `OpSys`, `Cpu brand`
-   **Fitur Biner**: `Touchscreen`, `IPS`
-   **Target Variabel**: `TypeName` (tipe laptop yang akan diprediksi)

---

## ⚙️ Metodologi Alur Kerja

Proyek ini mengikuti alur kerja machine learning yang terstruktur, divisualisasikan dalam diagram berikut:

```mermaid
graph TD
    A[ Mulai ] --> B[1. Pemuatan Data <br><i>(laptop_data_cleaned.csv)</i>];
    B --> C[2. Analisis Data Eksplorasi (EDA) <br><i>(Visualisasi dengan Seaborn & Matplotlib)</i>];
    C --> D[3. Prapemrosesan Data <br><i>(One-Hot Encoding & Scaling)</i>];
    D --> E[4. Pembagian Data <br><i>(Data Latih & Data Uji)</i>];
    E --> F[5. Pelatihan Model <br><i>(Algoritma K-Nearest Neighbors)</i>];
    F --> G[6. Evaluasi Model <br><i>(Accuracy, Confusion Matrix, Classification Report)</i>];
    G --> H[7. Penyimpanan Model <br><i>(knn_model.joblib)</i>];
    H --> I[ Selesai ];
```

**Penjelasan Detail:**
1.  **Analisis Data Eksplorasi (EDA)**: Menggunakan visualisasi data untuk memahami distribusi, korelasi antar fitur, dan hubungan antara fitur dengan variabel target.
2.  **Prapemrosesan Data**:
    -   **One-Hot Encoding**: Mengubah fitur-fitur kategorikal (seperti `Company`, `OpSys`) menjadi format numerik yang dapat diproses oleh model.
    -   **Standard Scaling**: Menyamakan skala semua fitur numerik agar tidak ada fitur yang mendominasi proses pelatihan model karena perbedaan rentang nilai.
3.  **Pelatihan Model**: Model K-Nearest Neighbors (KNN) dilatih menggunakan data latih yang sudah diproses.
4.  **Evaluasi Model**: Kinerja model diukur pada data uji menggunakan metrik evaluasi standar untuk masalah klasifikasi.

---

## 📈 Hasil & Evaluasi

Berdasarkan hasil evaluasi pada data uji, model klasifikasi KNN yang telah dilatih berhasil mencapai:

-   **Akurasi: 76.5%**

Ini menunjukkan bahwa model mampu memprediksi tipe laptop dengan benar pada sekitar 76.5% dari kasus yang belum pernah dilihat sebelumnya. Analisis lebih lanjut menggunakan *Classification Report* menunjukkan kinerja presisi dan *recall* untuk setiap kelas tipe laptop, sementara *Confusion Matrix* memberikan gambaran visual tentang di mana model sering melakukan kesalahan klasifikasi.

Model yang telah dilatih disimpan dalam file `knn_model.joblib` untuk penggunaan di masa depan, seperti untuk deployment ke dalam aplikasi atau API.

---

## 💻 Teknologi yang Digunakan

-   **Bahasa Pemrograman**: Python 3
-   **Library Utama**:
    -   Pandas: Untuk manipulasi dan analisis data.
    -   NumPy: Untuk komputasi numerik.
    -   Scikit-learn: Untuk implementasi model machine learning (KNN, Scaler, Encoder) dan evaluasi.
    -   Matplotlib & Seaborn: Untuk visualisasi data.
-   **Lingkungan Kerja**: Jupyter Notebook

---

## 🚀 Cara Menjalankan Proyek Secara Lokal

Untuk mereproduksi hasil dari proyek ini, ikuti langkah-langkah berikut:

### Prasyarat
-   Python 3.8 atau yang lebih baru.
-   `pip` (Python package installer).
-   Git.

### Langkah-langkah Instalasi

1.  **Clone Repositori**
    ```bash
    git clone [https://github.com/NAMA_USER_ANDA/NAMA_REPOSITORI_ANDA.git](https://github.com/NAMA_USER_ANDA/NAMA_REPOSITORI_ANDA.git)
    cd NAMA_REPOSITORI_ANDA
    ```

2.  **Buat dan Aktifkan Virtual Environment**
    ```bash
    # Membuat virtual environment
    python -m venv venv

    # Mengaktifkan di Windows
    .\venv\Scripts\activate

    # Mengaktifkan di macOS/Linux
    source venv/bin/activate
    ```

3.  **Instal Dependensi**
    Buat file bernama `requirements.txt` dengan isi berikut, lalu instal:
    ```txt
    pandas
    numpy
    scikit-learn
    matplotlib
    seaborn
    jupyterlab
    joblib
    ```
    Jalankan perintah instalasi:
    ```bash
    pip install -r requirements.txt
    ```

4.  **Jalankan Jupyter Notebook**
    ```bash
    jupyter lab KNN_prediksi_Type_Laptop.ipynb
    ```
    Ini akan membuka Jupyter Lab di browser Anda, di mana Anda dapat menjalankan semua sel kode di dalam notebook untuk melihat prosesnya secara langsung.

---

## 📂 Struktur Repositori

```
├── 📜 K-Nearest Neighbors Approach to Laptop Type Classification.pdf   # Laporan/Paper penelitian proyek
├── 📜 KNN_prediksi_Type_Laptop.ipynb                                # Kode utama proyek dalam Jupyter Notebook
├── 📜 laptop_data_cleaned.csv                                       # Dataset yang digunakan
├── 📦 knn_model.joblib                                              # Model machine learning yang sudah dilatih
└── 📜 README.md                                                     # Dokumentasi proyek (file ini)
```
