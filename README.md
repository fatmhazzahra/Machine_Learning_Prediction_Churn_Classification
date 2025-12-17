# Implementasi Machine Learning: Prediksi Churn pada Perusahaan Telekomunikasi

## Latar Belakang 

Sesuai dengan perkembangan zaman, bisnis semakin modern dan tingkat kompetitif pun semakin tinggi. Hal ini menyebabkan kemampuan perusahaan untuk mempertahankan pelanggan (*customer retention*) menjadi aset yang jauh lebih berharga dibandingkan sekadar mengakuisisi pelanggan baru. Seperti yang kita tahu bahwa biaya untuk mendapatkan pelanggan baru (*Customer Acquisition Cost* atau CAC) lebih mahal dibandingkan biaya untuk mempertahankan pelanggan yang sudah ada.

Saat ini, perusahaan menghadapi tantangan di mana pelanggan memiliki banyak pilihan alternatif. Fenomena *churn* di mana pelanggan berhenti menggunakan layanan atau produk dapat menurunkan profit perusahaan secara signifikan dan menurunkan *Customer Lifetime Value* (CLV). Oleh karena itu, memahami pola perilaku pelanggan dan mendeteksi sinyal ketidakpuasan sejak dini bukan lagi sekadar opsi, melainkan kebutuhan strategis untuk keberlanjutan bisnis jangka panjang.

## Rumusan Masalah Bisnis 
Meskipun perusahaan memiliki data pelanggan yang melimpah, tidak semua perusahaan dapat memanfaatkannya dengan baik. Tantangan utama perusahaan adalah ketidakmampuan untuk mengidentifikasi pelanggan yang berisiko pergi (*churn*) sebelum mereka benar-benar berhenti berlangganan.

Masalah spesifik yang dihadapi meliputi:
* **Identifikasi Reaktif :** Perusahaan baru menyadari kehilangan pelanggan setelah pemutusan layanan terjadi, sehingga terlambat untuk melakukan tindakan pencegahan.
* **Revenue Leakage :** Tingginya angka *churn* menyebabkan kebocoran pendapatan bulanan/tahunan yang menghambat pertumbuhan perusahaan.
* **Ketidakefektifan Strategi Retensi :** Tanpa wawasan berbasis data, tim pemasaran sering kali melakukan promosi retensi untuk mempertahankan pelanggan secara acak, yang mana hal tersebut tidak efisien dan membuang anggaran pada pelanggan yang sebenarnya setia atau sudah pasti akan pergi (*churn*).

## Tujuan
Proyek ini bertujuan untuk membangun solusi analitis untuk mengurangi angka *churn*. Tujuan dari analisis ini adalah:

1.  **Membangun Model Prediktif :** Mengembangkan model *Machine Learning* yang mampu memprediksi probabilitas seorang pelanggan akan melakukan *churn* di masa depan dengan tingkat akurasi dan *recall* yang optimal.
2.  **Mengidentifikasi Faktor Utama :** Menentukan variabel atau fitur apa saja yang paling berpengaruh terhadap keputusan pelanggan untuk berhenti.
3.  **Rekomendasi Strategis :** Memberikan rekomendasi bagi tim bisnis untuk merancang program retensi yang lebih tepat sasaran.

## Pendekatan Analitis
Metodologi *Data Science* yang digunakan dalam proyek untuk menjawab permasalahan bisnis sebagai berikut:

1.  **Data Understanding:**
    * *Data Cleaning*  → Data Dictionary, Cek duplikat data, dan Missing Value.
2.  **Exploratory Data Analysis (EDA):**
    * Data Numerik → Analisis data, Cek Outlier
    * Data Kategorik → Analisis data, Cek Outlier
    * Imbalanced Data.
3.  **Data Preparation :**
    * Data Splitting → menjelaskan X dan y, Splitting data
    * Feature Engineering → *encoding* pada data kategorikal dan *scaling* pada data numerik, membuat pipeline dan kolom transformer.
4.  **Modeling:**
    * Melatih beberapa algoritma model klasifikasi sebagai pembanding
    * Melakukan *Resampling* untuk mendapatkan performa model yang optimal.
    * Melakukan *Hyperparameter Tuning* untuk mendapatkan performa model yang optimal.

5.  **Model Interpretation:**
    * Menggunakan teknik seperti SHAP untuk menjelaskan alasan atau faktor yang memengaruhi *churn* kepada tim bisnis.
  
## Stakeholder
Pemangku kebijakan yang berpengaruh terhadap hasil dari prediksi *churn* diantaranya sebagai berikut:
1. **Customer Retention Team** → berhubungan dengan pelanggan yang *churn*
2. **Customer Relationship Team** → berhubungan dengan pelanggan yang tidak *churn*
3. **Marketing Team** → berhubungan dengan strategi pemberian campaign yang tepat sasaran
4. **Chief Marketing Officer** → berhubungan dengan profit dan loss yang didapatkan perusahaan
5. **Investor / Pemilik perusahaan** → berhubungan dengan arah perusahaan kedepannya.

## Metrics
* **False Negative (FN):** Model memprediksi pelanggan "Setia", padahal aslinya "Churn".
    * Perusahaan kehilangan pelanggan berharga tanpa sempat melakukan pencegahan. Ini adalah kerugian finansial terbesar (*High Cost*) berupa hilangnya *Customer Lifetime Value* (CLV).
* **False Positive (FP):** Model memprediksi pelanggan "Churn", padahal aslinya "Setia".
    * Perusahaan memberikan promosi retensi kepada pelanggan yang sebenarnya tidak berniat pergi. Biayanya relatif kecil, hanya sebatas biaya promosi/diskon (*Low Cost*).

Berdasarkan pertimbangan biaya di atas, prioritas Stakeholder adalah meminimalisir kehilangan pelanggan (FN). Maka, metrik utama yang digunakan adalah:
1. **PR AUC (Precision–Recall Area Under Curve) :** Digunakan sebagai metrik utama karena mampu mengevaluasi trade-off antara precision dan recall secara menyeluruh pada berbagai nilai threshold, serta lebih representatif untuk imbalanced data
2. **Recall (Sensitivity):** Fokus utama untuk menangkap sebanyak mungkin pelanggan yang berpotensi *churn*. Semakin tinggi *Recall*, semakin sedikit pelanggan *churn* yang lolos dari deteksi.
3.  **Precision:** Untuk mengontrol tingkat kesalahan False Positive agar biaya promosi tetap efisien.

## 5 Point Business ML Goals
1.  **Problem :**
    Tingginya tingkat *churn* yang tidak terdeteksi secara dini menyebabkan hilangnya pendapatan berulang (*recurring revenue*) dan inefisiensi biaya akuisisi.
2.  **Data :**
    Menggunakan data historis perusahaan yang mencakup demografi pelanggan dan riwayat transaksi.
3.  **ML Objective :**
    Membangun model klasifikasi biner untuk memprediksi probabilitas seorang pelanggan akan berhenti berlangganan (*churn probability*) di bulan berikutnya.
4.  **Action :**
    Mengintegrasikan hasil prediksi kepada tim bisnis/marketing, di mana pelanggan berisiko tinggi untuk *churn* akan diberikan treatment khusus berupa insentif personal, diskon, atau pendekatan *customer service* proaktif.
5.  **Value :**
    Menurunkan *Churn Rate*, menyelamatkan pendapatan potensial (*Saved Revenue*), dan meningkatkan efisiensi biaya pemasaran dengan menargetkan retensi hanya pada pelanggan yang benar-benar berisiko.

---
## Modul yang dibutuhkan untuk menjalankan program:
lightgbm >= 4.6.0
imbalanced-learn >= 0.14.0
pandas >= 2.2.2
numpy >= 2.0.2
scikit-learn >= 1.6.1
xgboost >= 3.1.2
shap >= 0.50.0

---
Author : *Fatimah Azzahra*
---
seaborn >= 0.13.2

