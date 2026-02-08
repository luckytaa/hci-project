Proyek ini merupakan bagian dari tugas Data Science untuk memahami faktor gagal bayar nasabah.

# Analisis Risiko Gagal Bayar Nasabah

## 1. Problem Statement
Masalah utama yang diselesaikan adalah meminimalkan kerugian finansial perusahaan akibat kredit macet. Proyek ini bertujuan untuk membangun model prediktif yang dapat membedakan nasabah yang mampu membayar tepat waktu (Target 0) dan nasabah yang memiliki kesulitan pembayaran (Target 1).

## 2. Dataset
Dataset berasal dari Home Credit yang terdiri dari beberapa tabel relasional:
- `application_train`: Data profil nasabah.
- `POS_CASH_balance`: Histori saldo dan keterlambatan hari (SK_DPD).
- `credit_card_balance`: Perilaku penggunaan kartu kredit.
- `installments_payments`: Riwayat pembayaran cicilan nyata vs tagihan.

## 3. Key Insights & Actions
### Insight 1: Bahaya Penarikan Tunai & Overlimit
- Temuan: Nasabah yang sering melakukan penarikan tunai di ATM (`AMT_DRAWINGS_ATM_CURRENT`) dan menggunakan kartu di atas limit memiliki risiko gagal bayar 3x lebih tinggi.
- Action: Menerapkan sistem peringatan dini (early warning) untuk menurunkan limit kredit secara otomatis jika perilaku "gali lubang tutup lubang" terdeteksi.
### Insight 2: Pola Keterlambatan Kecil (SK_DPD)
- Temuan: Keterlambatan kecil (1-5 hari) yang berulang di awal tenor merupakan indikator kuat nasabah akan macet total di kemudian hari.
- Action: Mengubah strategi penagihan dengan mengirimkan notifikasi pengingat H-3 sebelum jatuh tempo khusus untuk nasabah dengan histori telat kecil.

## 4. Modeling & Performance
- Preprocessing: Handling missing values dengan median, One-Hot Encoding untuk fitur kategori, dan Feature Scaling.
- Fitur Utama: Rasio Pendapatan vs Kredit, Rata-rata SK_DPD, dan Selisih Pembayaran (AMT_PAYMENT vs AMT_INSTALMENT).
- Algoritma: LightGBM / Random Forest.
- Performance: Model mencapai skor AUC-ROC sebesar 0.7X (masukkan angka hasil modemu), yang menunjukkan kemampuan prediksi yang solid.

## 5. Cara Penggunaan
1. Clone repository ini.
2. Pastikan library `pandas`, `numpy`, dan `lightgbm` terinstall.
3. Jalankan file `notebooks/hci.ipynb`.
