# MBG Tweet Classification - Ensemble IndoBERT dan IndoBERTweet

Repositori ini berisi source code dan dokumentasi untuk penyelesaian **Case 1 Big Data Challenge (BDC) Satria Data 2026**. Tujuan utama dari proyek ini adalah membangun model Deep Learning yang mampu mengklasifikasikan wacana publik mengenai program Makan Bergizi Gratis (MBG) di platform X (Twitter) ke dalam 8 kelas substantif.

## Deskripsi Proyek dan Metodologi
Karena karakteristik User Generated Content (UGC) yang kotor dan ambigu, proyek ini tidak mengandalkan model tunggal. Solusi ini dibangun menggunakan pendekatan Heterogeneous Ensemble Learning.

Fitur utama dari arsitektur pemodelan ini meliputi:
1. Dual Backbone: Menggabungkan indobenchmark/indobert-base-p2 (unggul di bahasa formal) dan indolem/indobertweet-base-uncased (unggul di bahasa slang Twitter).
2. Stratified K-Fold Cross-Validation: Pelatihan menggunakan skema 5-fold dan variasi learning rate (2e-5 dan 3e-5) untuk menghasilkan 4 base learners yang tangguh dan tahan terhadap overfitting.
3. Threshold Optimization: Menggunakan algoritma Nelder-Mead untuk mencari batas keputusan (threshold) terbaik pada probabilitas Out-of-Fold (OOF) guna memaksimalkan metrik Balanced Accuracy.
4. Ensemble Strategy: Menggunakan kombinasi prediksi Soft Voting dan Stacking untuk menentukan kelas akhir.

Model mengklasifikasikan tweet ke dalam 8 kategori substantif:
1. Anggaran
2. Kualitas Pangan
3. Distribusi
4. Ekonomi
5. Tata Kelola
6. Sasaran Penerima
7. Politik
8. Lainnya

## Requirements (Kebutuhan Pustaka)
Pastikan Anda telah menginstal pustaka berikut sebelum menjalankan kode:
1. pandas dan numpy
2. scikit-learn
3. scipy (Untuk optimasi Nelder-Mead)
4. torch
5. transformers
6. datasets

## Cara Menjalankan Kode
Untuk mereproduksi hasil prediksi, silakan ikuti langkah-langkah berikut:
1. Pastikan dataset case 1 labeled data.xlsx dan case 1 text to predict.xlsx tersedia di direktori lokal atau workspace Anda.
2. Jalankan notebook final (indobertensemble.ipynb) secara berurutan.
3. Notebook akan mengeksekusi prapemrosesan, augmentasi data minoritas (seperti kelas Ekonomi), pelatihan multi-model, ekstraksi probabilitas OOF, hingga proses Ensemble.
4. Hasil prediksi akhir diekspor dalam format .xlsx (berada di folder output/) sesuai format submisi panitia.

---
Dibuat untuk keperluan submission kompetisi **Case 1 Big Data Challenge (BDC) Satria Data 2026**.
