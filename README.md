Project ini merupakan bagian dari tugas Data Science untuk memahami faktor gagal bayar nasabah.

# Analisis Risiko Gagal Bayar Nasabah

## 1. Problem Statement
Masalah utama yang diselesaikan adalah meminimalkan kerugian finansial perusahaan akibat kredit gagal bayar(default). Project ini bertujuan untuk membangun model prediktif yang dapat membedakan nasabah yang mampu membayar tepat waktu (Target 0) dan nasabah yang memiliki kesulitan pembayaran (Target 1).

## 2. Dataset
Dataset berasal dari Home Credit yang terdiri dari beberapa tabel relasional:
- `application_train`: Data profil nasabah.
- `previous_application`: Histori pengajuan pinjaman sebelumnya.
- `bureau`: Data histori kredit nasabah di institusi keuangan lain.
- `installments_payments`: Riwayat pembayaran cicilan nyata vs tagihan.

## 3. Key Insights & Actions
Insight 1: Pola Kedisiplinan Pembayaran
Temuan: Nasabah dengan nilai AVG_PAYMENT_DELAY positif (sering terlambat meski hanya 1-5 hari) memiliki korelasi kuat terhadap kegagalan bayar di akhir tenor.
Aksi: Mengubah strategi penagihan dengan notifikasi pengingat otomatis H-3 sebelum jatuh tempo bagi kelompok ini.

Insight 2: Kapasitas Finansial (Debt-to-Income)
Temuan: Rasio antara AMT_CREDIT terhadap AMT_INCOME_TOTAL yang terlalu tinggi menjadi faktor risiko utama.
Aksi: Melakukan optimasi plafon (Principal Optimization) agar cicilan bulanan tidak melebihi 30-35% dari pendapatan rata-rata nasabah.

## 4. Metodologi & Pemodelan
Feature Engineering: Melakukan agregasi data transaksi (Mean, Min, Max) untuk meringkas histori nasabah menjadi fitur yang dapat dipelajari model.

Preprocessing: Handling Missing Values: Menggunakan SimpleImputer dengan strategi mean/median.

Feature Selection: Memilih fitur krusial seperti AMT_INCOME_TOTAL, AMT_CREDIT, dan fitur agregasi histori.
Algoritma: Menggunakan pendekatan Hybrid:
Logistic Regression: Sebagai baseline model untuk transparansi.
Random Forest: Sebagai advanced model untuk menangkap pola non-linear.

Performance: Model dievaluasi menggunakan metrik AUC-ROC untuk mengukur kemampuan model membedakan kelas risiko secara efektif.

## 5. Cara Penggunaan Notebook
Pastikan semua dataset (.csv) berada dalam direktori yang sama dengan file .ipynb.
Instal pustaka yang diperlukan: pip install pandas, numpy, matplotlib, seaborn, dan scikit-learn.
Jalankan sel secara berurutan mulai dari Loading Data, Feature Engineering, hingga Modeling.
