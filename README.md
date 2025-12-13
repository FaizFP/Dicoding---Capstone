# Analisis Segmentasi Pelanggan Toko Ritel Online 🛒📊

![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![Libraries](https://img.shields.io/badge/Library-Pandas%20%7C%20Scikit--Learn%20%7C%20Seaborn-green)
![Project](https://img.shields.io/badge/Project-Dicoding%20Capstone-orange)

## 📌 Ringkasan Proyek
Proyek ini merupakan bagian dari **Dicoding Capstone**, yang bertujuan untuk mengoptimalkan strategi pemasaran ritel online melalui segmentasi pelanggan. Dengan menganalisis data transaksi historis, kami mengelompokkan pelanggan ke dalam segmen perilaku yang berbeda menggunakan teknik **RFM Analysis** dan **Machine Learning**.

Hasil analisis ini memberikan wawasan bagi bisnis untuk menargetkan pelanggan dengan promosi yang lebih personal, meningkatkan retensi, dan memaksimalkan pendapatan.

## 📂 Dataset
* **Sumber Data:** Online Retail Dataset (via Kaggle).
* **Deskripsi:** Data transaksi transnasional yang berisi semua transaksi yang terjadi antara 01/12/2010 dan 09/12/2011 untuk ritel online non-toko yang berbasis di Inggris.
* **Volume Data:** 541,909 baris data transaksi awal.
* **Atribut Penting:** `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID`, `Country`.

## ⚙️ Metodologi & Alur Kerja

Analisis dilakukan menggunakan Python dengan langkah-langkah sebagai berikut:

### 1. Data Cleaning & Preprocessing
* **Pembersihan Data:** Menghapus baris tanpa `CustomerID` dan menangani nilai yang hilang.
* **Filtering:** Mengeliminasi transaksi pembatalan (Invoice diawali 'C'), kode stok non-produk (seperti 'POST', 'BANK CHARGES'), dan nilai kuantitas/harga negatif.
* **Tipe Data:** Konversi `InvoiceDate` ke format datetime dan `CustomerID` ke integer.
* **Feature Engineering:** Membuat kolom `TotalAmount` (Quantity × UnitPrice).

### 2. Analisis RFM (Recency, Frequency, Monetary)
Pelanggan dievaluasi berdasarkan tiga pilar utama perilaku belanja:
* **Recency (R):** Jumlah hari sejak pembelian terakhir.
* **Frequency (F):** Jumlah total transaksi unik.
* **Monetary (M):** Total uang yang dibelanjakan.

*Teknis: Data RFM dibersihkan dari outlier (Capping method) dan dinormalisasi menggunakan Log Transformation dan StandardScaler.*

### 3. Machine Learning: Clustering
* **Algoritma:** K-Means Clustering.
* **Optimasi K:** Menggunakan **Elbow Method** dan **Silhouette Score** untuk menentukan jumlah klaster optimal.
    * *Hasil:* K=4 dipilih sebagai jumlah klaster paling optimal secara bisnis dan statistik.
* **Model Alternatif:** DBSCAN juga diuji untuk mendeteksi noise, namun K-Means memberikan segmentasi yang lebih dapat ditindaklanjuti.

## 📊 Hasil Analisis: 4 Profil Pelanggan

Berdasarkan pemodelan, pelanggan dikelompokkan menjadi 4 segmen unik:

| Segmen Pelanggan | Karakteristik Perilaku | Rekomendasi Strategi |
| :--- | :--- | :--- |
| **VIP (Sultan)** 💎 | **Rata-rata Belanja: ~7,800+**<br>Baru saja berbelanja, frekuensi sangat tinggi, pengeluaran besar. | Berikan layanan prioritas, akses eksklusif ke produk baru, dan *personal shopper*. |
| **Loyal Customers** 🥇 | **Rata-rata Belanja: ~1,700+**<br>Berbelanja secara rutin dengan nilai transaksi yang sehat. | Tawarkan program loyalitas (poin), *upselling* produk premium, dan rekomendasi berbasis riwayat. |
| **Potential / New** 🌱 | **Rata-rata Belanja: ~500+**<br>Pelanggan baru atau yang sesekali belanja dengan potensi tumbuh. | Berikan diskon sambutan, edukasi produk melalui email, dan insentif pembelian kedua. |
| **Low Value / Risk** ⚠️ | **Rata-rata Belanja: ~300+**<br>Jarang berbelanja, nilai kecil, dan sudah lama tidak kembali (Recency tinggi). | Lakukan kampanye *win-back* dengan diskon agresif atau survei untuk mengetahui kendala. |

## 💡 Temuan Menarik (Produk Favorit)
Analisis produk terlaris per segmen menunjukkan preferensi yang berbeda:
* **Segmen VIP** cenderung membeli barang kerajinan unik (*Paper Craft Little Birdie*) dalam jumlah besar.
* **Segmen Loyal** menyukai barang kebutuhan rumah tangga estetis (*Storage Jar*).
* **Segmen Potential & Low Value** lebih responsif terhadap barang-barang dekorasi kecil yang murah.

## 🛠️ Instalasi & Penggunaan

## ⚙️ Petunjuk Setup Environment

1. Buka terminal atau command prompt.
2. Buat virtual environment (opsional tapi disarankan):
   ```bash
   python -m venv venv
   ```
3. Aktifkan virtual environment:
   - Windows: `venv\Scripts\activate`
   - Mac/Linux: `source venv/bin/activate`
4. Install dependensi:
   ```bash
   pip install -r requirements.txt
   ```

Proyek ini dikembangkan menggunakan **Jupyter Notebook**.

1.  **Clone repositori ini:**
    ```bash
    git clone [https://github.com/faizfp/dicoding---capstone.git](https://github.com/faizfp/dicoding---capstone.git)
    ```

2.  **Jalankan Notebook:**
    Buka file `Capstone_SegmentationMarketing.ipynb` di Jupyter Notebook atau Google Colab untuk melihat analisis langkah demi langkah.
