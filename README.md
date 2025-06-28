# UAS-Penalaran-Komputer
Sistem Case-Based Reasoning untuk Analisis Putusan Pengadilan
##Deskripsi Proyek

Proyek ini mengimplementasikan sistem Case-Based Reasoning (CBR) sederhana untuk mendukung analisis putusan pengadilan. Sistem ini memanfaatkan data putusan yang di-scrape dari Direktori Putusan Mahkamah Agung Republik Indonesia. Tujuan utama adalah untuk menemukan putusan lama yang paling mirip dengan kasus baru (query) dan memprediksi solusi berdasarkan pengalaman masa lalu.

Proyek ini dibagi menjadi 5 tahapan utama sesuai siklus CBR: Pembangunan Basis Kasus, Representasi Kasus, Pencarian Kasus (Retrieval), Penggunaan Kembali Solusi (Reuse), dan Evaluasi Model.

## Instalasi

Untuk menjalankan proyek ini, Anda perlu menginstal dependensi Python berikut.
Direkomendasikan untuk menggunakan lingkungan virtual (misalnya venv atau conda) untuk mengelola dependensi.

1.  *Kloning Repositori ini:*

    bash
    git clone https://github.com/natasyadelviraa/UAS-PK.git
    cd UAS-PK
    

2.  *Buat dan Aktifkan Lingkungan Virtual (Opsional, Direkomendasikan):*

    bash
    python -m venv venv
    # Di Windows:
    .\venv\Scripts\activate
    # Di macOS/Linux:
    source venv/bin/activate
    

3.  *Instal Dependensi:*
    Anda dapat menginstal semua dependensi menggunakan pip dari file requirements.txt. (Anda perlu membuat file requirements.txt ini dari lingkungan Colab Anda dengan perintah !pip freeze > requirements.txt).

    bash
    pip install -r requirements.txt
    

    Atau secara manual (jika requirements.txt tidak dibuat, berdasarkan tools yang digunakan):

    bash
    pip install pandas requests beautifulsoup4 pdfminer.six scikit-learn transformers sentence-transformers numpy joblib
    

## Struktur Proyek

Repositori ini memiliki struktur folder sebagai berikut:

  * notebooks/: Berisi Jupyter Notebook (.ipynb) untuk setiap tahapan proyek (Tahap 1 hingga Tahap 5).
  * data/:
      * data/raw/: Berisi file teks putusan yang sudah dibersihkan (.txt).
      * data/processed/: Berisi data putusan terstruktur dalam format CSV (misalnya cases.csv dan CSV metadata awal dari Tahap 1).
      * data/eval/: Berisi file terkait evaluasi (misalnya queries.json, retrieval_metrics.csv, prediction_metrics.csv).
      * data/results/: Berisi hasil prediksi (misalnya predictions.csv).
  * models/: Berisi model terlatih dan vektor representasi (misalnya bert_case_vectors.npy, tfidf_vectorizer.joblib, vectorizer_type.txt). (Ini adalah hasil penyimpanan Tahap 3)
  * README.md: File ini.

## Cara Menjalankan Proyek (Pipeline End-to-End)

Proyek ini dirancang untuk dijalankan dalam Google Colaboratory, yang memungkinkan eksekusi selangkah demi selangkah dan integrasi dengan Google Drive.

1.  *Buka Notebooks di Google Colab:*

      * Unggah atau buka setiap file .ipynb dari folder notebooks/ di Google Colab.

2.  *Mount Google Drive:*

      * Pastikan Anda menjalankan sel koneksi Google Drive di awal setiap notebook untuk menyimpan dan mengakses data secara persisten.

    <!-- end list -->

    python
    from google.colab import drive
    drive.mount('/content/drive')
    

3.  *Jalankan Setiap Tahap Secara Berurutan:*

      * Setiap notebook (Tahap_1.ipynb hingga Tahap_5.ipynb) harus dijalankan secara berurutan.
      * Pastikan setiap sel dalam notebook dijalankan tanpa error sebelum melanjutkan ke sel berikutnya atau ke notebook tahap selanjutnya.
      * *Penting: Pastikan *output dari tahap sebelumnya (misalnya cases.csv dari Tahap 2, model dari Tahap 3) berhasil tersimpan di Google Drive sebelum memulai tahap berikutnya.

    *Urutan Eksekusi:*

      * Buka Tahap_1.ipynb, jalankan semua sel. (Membangun Case Base)
      * Buka Tahap_2.ipynb, jalankan semua sel. (Case Representation)
      * Buka Tahap_3.ipynb, jalankan semua sel. (Case Retrieval)
      * Buka Tahap_4.ipynb, jalankan semua sel. (Case/Solution Reuse)
      * Buka Tahap_5.ipynb, jalankan semua sel. (Model Evaluation)

## Kontributor

  * Natasya Delvira Maharani - 202210370311355

-----
