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
