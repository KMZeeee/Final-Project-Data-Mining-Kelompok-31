# Final-Project-Data-Mining-Kelompok-31
Final Project Pemenuhan Tugas Akhir Mata Kuliah Data Mining

| Nama                              | NRP          |
|-----------------------------------|--------------|
| Davin Fisabilillah Reynard Putra  | 5025221137   |
| Fadhiil Hanif Rizqullah           | 5025221144   |
| Nyoman Satyawikrama Upadhana           | 5025221194   |

# **Prediksi Kualitas Wine Menggunakan Machine Learning dengan Analisis Explainable AI Berbasis SHAP**

## Abstrak 

Peningkatan penggunaan metode analitik dalam industri pangan dan minuman menegaskan perlunya sistem penilaian kualitas produk yang lebih akurat dan objektif, termasuk pada evaluasi kualitas wine. Penelitian ini bertujuan mengembangkan model prediksi kualitas wine menggunakan beberapa algoritma machine learning, yaitu KNN, SVM, Decision Tree, Random Forest, dan XGBoost berdasarkan fitur fisikokimia dari Wine Quality Dataset UCI. Penelitian dilakukan melalui tiga skenario, yaitu perbandingan performa model setelah hyperparameter tuning, evaluasi teknik sampling menggunakan SMOTE untuk menangani ketidakseimbangan kelas, serta interpretasi model menggunakan Explainable AI berbasis SHAP. Hasil menunjukkan bahwa Random Forest memberikan performa terbaik dengan akurasi 0,82 dan F1-score 0,68, melampaui algoritma lainnya. Penerapan SMOTE tidak meningkatkan performa dan justru menurunkan akurasi pada sebagian besar model, mengindikasikan bahwa sampel sintetis tidak sepenuhnya mencerminkan struktur alami data. Analisis SHAP mengungkap bahwa alkohol dan volatile acidity merupakan fitur yang paling berpengaruh dalam memprediksi kualitas wine. Temuan ini menunjukkan bahwa model ensemble memiliki keandalan prediktif yang lebih kuat, sementara SHAP memberikan wawasan interpretatif yang penting bagi proses penilaian kualitas dan pengambilan keputusan dalam produksi.

Kata Kunci - prediksi kualitas wine, machine learning, Random Forest, SMOTE, SHAP

## 📊 Dataset

Dataset yang digunakan bersumber dari **UCI Machine Learning Repository** (Wine Quality Dataset).
* **Sumber Data:** Gabungan dataset *Red Wine* dan *White Wine*.
* **Total Sampel:** 6.497 data.
* **Fitur Input (11 Fisikokimia):**
    * *Fixed acidity, Volatile acidity, Citric acid, Residual sugar, Chlorides, Free sulfur dioxide, Total sulfur dioxide, Density, pH, Sulphates, Alcohol*.
* **Target Variabel:** `quality` (Dikategorikan menjadi kelas kualitas *Low, Medium, High*).
  
### Model yang Digunakan
Beberapa algoritma diuji, yaitu:

- **K-Nearest Neighbors (KNN)**
- **Support Vector Machine (SVM)**
- **Decision Tree**
- **Random Forest**
- **XGBoost**

### Evaluasi Model
Evaluasi dilakukan menggunakan:

- Accuracy  
- Precision  
- Recall  
- F1-Score  
- Confusion Matrix
  
## ⚙️ Alur Kerja & Metodologi

Penelitian ini dilakukan dengan pendekatan sistematis yang terdiri dari tahapan berikut:

### 1. Preprocessing Data
Sebelum pemodelan, data mentah diproses melalui tahapan:
* **Data Merging:** Menggabungkan dataset *Red Wine* dan *White Wine* menjadi satu kesatuan.
* **Encoding:** Menambahkan atribut tipe wine dan melakukan *Ordinal Encoding* untuk fitur target dan *one-hot encoding* untuk fitur kategorikal lainnya.
* **Normalization:** Menggunakan `StandardScaler` untuk menstandarisasi fitur numerik agar memiliki skala yang sama.
* **Data Splitting:** Membagi data menjadi *Training Set* dan *Testing Set*.

### 2. Skenario Eksperimen
Kami merancang tiga skenario untuk menguji performa dan interpretabilitas model:

* **Skenario 1: Hyperparameter Tuning (Baseline)**
    * Melatih 5 model: *K-Nearest Neighbors (KNN), Support Vector Machine (SVM), Decision Tree, Random Forest,* dan *XGBoost*.
    * Menggunakan `GridSearchCV` untuk mencari kombinasi parameter optimal pada data asli.

* **Skenario 2: Handling Imbalanced Data (SMOTE)**
    * Menerapkan *Synthetic Minority Over-sampling Technique* (SMOTE) pada data latih.
    * Tujuannya adalah menyeimbangkan jumlah sampel antar kelas kualitas wine untuk melihat dampaknya terhadap performa model.

* **Skenario 3: Model Interpretation (SHAP)**
    * Menggunakan *SHAP Values* pada model terbaik (Random Forest).
    * Menganalisis fitur mana yang paling berkontribusi terhadap keputusan model (Global & Local Interpretability).

## 📈 Hasil Eksperimen

Berikut adalah ringkasan hasil evaluasi model berdasarkan tiga skenario yang diuji.

### Hasil Skenario 1: Hyperparameter Tuning (Tanpa SMOTE)
*Model dilatih menggunakan data asli (imbalanced).*

| Model | Accuracy | Precision | Recall | F1-Score | Keterangan |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Random Forest** | **0.82** | **0.88** | **0.63** | **0.68** | 🏆 **Model Terbaik** |
| XGBoost | 0.81 | 0.87 | 0.62 | 0.67 | - |
| KNN | 0.81 | 0.87 | 0.63 | 0.68 | - |
| SVM | 0.76 | 0.84 | 0.51 | 0.52 | - |
| Decision Tree | 0.72 | 0.59 | 0.61 | 0.60 | - |

### Hasil Skenario 2: Evaluasi Sampling (Dengan SMOTE)
*Model dilatih menggunakan data yang telah diseimbangkan (oversampling).*

| Model | Accuracy | F1-Score | Perubahan (vs Skenario 1) |
| :--- | :---: | :---: | :--- |
| **Random Forest** | **0.81** | **0.68** | **Stabil (Sedikit Turun)** |
| XGBoost | 0.80 | 0.67 | Turun |
| KNN | 0.73 | 0.61 | 🔻 Turun Signifikan |
| SVM | 0.68 | 0.56 | 🔻 Turun Signifikan |

> **Analisis:** Teknik SMOTE terbukti **tidak efektif** meningkatkan performa. Akurasi model berbasis jarak (KNN, SVM) justru turun drastis karena adanya *noise* dari data sintetis yang tidak merepresentasikan karakteristik wine yang kompleks.

### Hasil Skenario 3: Interpretasi Model (SHAP)
*Fitur fisikokimia yang paling mempengaruhi kualitas wine.*

Fitur paling berpengaruh dalam prediksi:

| Rank | Fitur | Pengaruh |
|------|--------|-----------|
|  **1** | alcohol | semakin tinggi → kualitas meningkat |
|  **2** | volatile acidity | tinggi → kualitas menurun |
| 3 | density | berpengaruh pada kelas buruk & sedang |
| 4 | sulphates | meningkatkan kualitas dalam jumlah tertentu |

Analisis per kelas:
- **Kelas 0 (Buruk):** sangat dipengaruhi alcohol rendah + volatile acidity tinggi  
- **Kelas 1 (Sedang):** dipengaruhi alcohol dan density  
- **Kelas 2 (Baik):** dipengaruhi alcohol & residual sugar (lebih kecil efeknya)

## 📝 Kesimpulan

1.  **Random Forest** adalah algoritma terbaik untuk prediksi kualitas wine dengan akurasi **82%**.
2.  **Oversampling (SMOTE)** tidak direkomendasikan untuk dataset ini karena menurunkan kemampuan generalisasi model.
3.  Untuk meningkatkan kualitas wine, produsen disarankan fokus menjaga kadar **Alkohol** tetap optimal dan meminimalkan **Volatile Acidity**.

---
