# Klasifikasi Tipe Laptop Menggunakan Algoritma K-Nearest Neighbors (KNN)

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.2%2B-orange.svg)](https://scikit-learn.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-F37626.svg)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Repositori ini berisi proyek machine learning untuk mengklasifikasikan tipe laptop (misalnya, *Notebook, Ultrabook, Gaming*) berdasarkan spesifikasi teknisnya. Proyek ini mencakup seluruh alur kerja ilmu data, mulai dari analisis data eksplorasi (EDA), prapemrosesan, pelatihan model K-Nearest Neighbors (KNN), hingga evaluasi dan penyimpanan model.

---

## 🎯 Latar Belakang & Pernyataan Masalah

Pasar laptop sangat beragam dengan berbagai kategori seperti *Notebook, Ultrabook, Gaming, 2 in 1 Convertible*, dan lain-lain. Bagi konsumen, membedakan tipe laptop hanya dari spesifikasi teknis bisa menjadi hal yang membingungkan. Proyek ini bertujuan untuk membangun sebuah model klasifikasi yang dapat secara otomatis memprediksi tipe sebuah laptop berdasarkan atribut-atribut teknisnya, membantu sistem e-commerce dalam mengkategorikan produk atau konsumen dalam mengidentifikasi jenis laptop yang sesuai.

---

## 💿 Dataset

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
    F --> G[6. Evaluasi Model <br><i>(Accuracy, Confusion Matrix, etc.)</i>];
    G --> H[7. Penyimpanan Model <br><i>(knn_model.joblib)</i>];
    H --> I[ Selesai ];
```

**Penjelasan Detail:**
1.  **Analisis Data Eksplorasi (EDA)**: Memahami distribusi, korelasi, dan hubungan antar fitur menggunakan visualisasi data.
2.  **Prapemrosesan Data**:
    -   **One-Hot Encoding**: Mengubah fitur-fitur kategorikal menjadi format numerik.
    -   **Standard Scaling**: Menyamakan skala semua fitur numerik agar tidak ada fitur yang mendominasi proses pelatihan.
3.  **Pelatihan & Evaluasi Model**: Model K-Nearest Neighbors (KNN) dilatih menggunakan data latih dan dievaluasi kinerjanya menggunakan data uji.

---

## 📈 Hasil & Evaluasi

Berdasarkan hasil evaluasi pada data uji, model klasifikasi KNN yang telah dilatih berhasil mencapai:

-   **Akurasi: 76.5%**

Hasil ini menunjukkan bahwa model mampu memprediksi tipe laptop dengan cukup baik. Model yang telah dilatih kemudian disimpan dalam file `knn_model.joblib` untuk penggunaan di masa depan.

---

## 💡 Cara Menggunakan Model yang Sudah Dilatih

File `knn_model.joblib` berisi model yang siap pakai. Anda dapat memuatnya untuk membuat prediksi pada data baru tanpa perlu melatih ulang. Berikut adalah contoh penggunaannya:

```python
import joblib
import pandas as pd
import numpy as np

# Muat model yang sudah dilatih
model = joblib.load('knn_model.joblib')

# CATATAN PENTING:
# Untuk membuat prediksi, data baru HARUS diproses (encode dan scale)
# dengan cara yang SAMA PERSIS seperti data latih.
# Anda perlu menyimpan objek OneHotEncoder dan StandardScaler dari notebook
# untuk digunakan pada data baru.

# Kode di bawah ini hanya ilustrasi prediksi setelah data diproses.
# Silakan merujuk ke notebook untuk alur preprocessing yang lengkap.

print("Model berhasil dimuat. Siap untuk prediksi setelah data diproses.")

# Contoh data baru (sebelum diproses):
# new_laptop = pd.DataFrame({ ... })
# preprocessed_new_laptop = preprocess(new_laptop)
# prediction = model.predict(preprocessed_new_laptop)
# print(f"Prediksi Tipe Laptop: {prediction[0]}")
```
> Bagian ini menunjukkan bagaimana proyek Anda bisa digunakan dalam aplikasi nyata.

---

## 🚀 Cara Menjalankan Proyek Secara Lokal

Untuk mereproduksi hasil atau melakukan eksperimen lebih lanjut, ikuti langkah-langkah berikut:

### Prasyarat
-   Python 3.8 atau yang lebih baru
-   Git

### Langkah-langkah Instalasi

1.  **Clone Repositori**
    ```bash
    git clone [https://github.com/NAMA_USER_ANDA/NAMA_REPOSITORI_ANDA.git](https://github.com/NAMA_USER_ANDA/NAMA_REPOSITORI_ANDA.git)
    cd NAMA_REPOSITORI_ANDA
    ```

2.  **Buat dan Aktifkan Virtual Environment**
    ```bash
    # Membuat venv
    python -m venv venv
    # Aktivasi di Windows
    .\venv\Scripts\activate
    # Aktivasi di macOS/Linux
    source venv/bin/activate
    ```

3.  **Instal Dependensi**
    Pastikan Anda memiliki file `requirements.txt` dengan isi berikut:
    ```txt
    pandas
    numpy
    scikit-learn
    matplotlib
    seaborn
    jupyterlab
    joblib
    ```
    Lalu, jalankan perintah instalasi:
    ```bash
    pip install -r requirements.txt
    ```

4.  **Jalankan Jupyter Notebook**
    ```bash
    jupyter lab KNN_prediksi_Type_Laptop.ipynb
    ```
    Ini akan membuka notebook di browser Anda, di mana Anda dapat menjalankan semua sel kode.

---

## 📂 Struktur Repositori

```
├── 📜 K-Nearest Neighbors Approach to Laptop Type Classification.pdf   # Laporan penelitian proyek
├── 📜 KNN_prediksi_Type_Laptop.ipynb                                # Kode utama proyek dalam Jupyter Notebook
├── 📜 laptop_data_cleaned.csv                                       # Dataset yang digunakan
├── 📦 knn_model.joblib                                              # Model machine learning yang sudah dilatih
└── 📜 README.md                                                     # Dokumentasi proyek (file ini)
```

---

## 🚧 Keterbatasan dan Pengembangan di Masa Depan

**Keterbatasan:**
-   **Kinerja KNN**: Algoritma KNN bisa menjadi lambat pada dataset yang sangat besar.
-   **Akurasi**: Akurasi 76.5% cukup baik, namun masih ada ruang untuk perbaikan.
-   **Dataset**: Cakupan dataset mungkin belum mewakili semua varian laptop di pasar.

**Pengembangan di Masa Depapan:**
-   **Eksperimen Algoritma**: Mencoba model lain seperti *Random Forest* atau *XGBoost* untuk perbandingan performa.
-   **Hyperparameter Tuning**: Mencari parameter optimal untuk model menggunakan *GridSearchCV*.
-   **Deployment**: Menerapkan model sebagai API menggunakan **Flask** atau **FastAPI**.

---

## ✍️ Author & Kontak

-   **Nama**: [David Mario Yohanes Samosir]
-   **LinkedIn**: [David Mario](https://www.linkedin.com/in/david-mario-yohanes-samosir/)

---

## 📄 Lisensi

Proyek ini dilisensikan di bawah Lisensi MIT.
