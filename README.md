# Student Performance Classification using Stacking Ensemble Learning

Bu proje, **Düzce Üniversitesi** CE469 Machine Learning dersi kapsamında hazırlanmıştır. Projenin amacı, öğrencilerin demografik ve eğitim geçmişlerine dayanarak sınav başarı durumlarını (Pass/Fail) tahmin etmektir.

## 📊 Proje Özeti
Projede, Kaggle'dan alınan "Students Performance in Exams" veri seti kullanılmıştır. 1,000 örneklemden oluşan veri setinde öğrencilerin matematik, okuma ve yazma skorlarının ortalaması alınarak bir hedef değişken oluşturulmuştur.

* **Target Variable:** Ortalama skor $\geq 60$ ise "Pass" (1), aksi takdirde "Fail" (0).
* **Feature Engineering:** Veri sızıntısını (Data Leakage) önlemek için sınav skorları (math, reading, writing) modelden çıkarılmış; sadece cinsiyet, etnik köken, ebeveyn eğitim düzeyi, öğle yemeği tipi ve hazırlık kursu durumu gibi demografik veriler kullanılmıştır.

## 🛠️ Kullanılan Teknolojiler
* **Dil:** Python
* **Platform:** Google Colab
* **Kütüphaneler:** Scikit-learn, Pandas, NumPy, Matplotlib, Seaborn

## 🧠 Modeller ve Metodoloji
Projede 5 farklı temel sınıflandırıcı ve bunların kombinasyonundan oluşan bir **Stacking Ensemble** mimarisi kullanılmıştır:

1. **Logistic Regression** (Baseline model) 
2. **K-Nearest Neighbors (KNN)** (StandardScaler ile optimize edildi) 
3. **Support Vector Machines (SVM)** 
4. **Decision Tree** (Aşırı öğrenmeyi önlemek için budandı) 
5. **Random Forest** 

### Stacking Architecture
* **Level-0 (Base Learners):** Tuned KNN ve Tuned Random Forest.
* **Level-1 (Meta Learner):** Logistic Regression.

## 📈 Performans Sonuçları (Test Seti)
Stacking Ensemble modeli, özellikle **Recall** ve **F1-Score** değerlerinde en istikrarlı sonuçları vermiştir.

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Logistic Regression | 0.66 | 0.717 | 0.859 | 0.782 | 0.644 |
| KNN | 0.70 | 0.741 | 0.887 | 0.807 | 0.682 |
| Random Forest | 0.68 | 0.719 | 0.901 | 0.800 | 0.611 |
| **Stacking Ensemble** | **0.70** | **0.725** | **0.929** | **0.814** | **0.619** |

*Veriler projenin final raporundan alınmıştır.*
