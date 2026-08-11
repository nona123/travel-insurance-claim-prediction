# Travel Insurance Claim Prediction

## Deskripsi Proyek

Proyek ini bertujuan untuk menganalisis karakteristik customer dan transaksi pada perusahaan Travel Insurance serta membangun model machine learning untuk memprediksi kemungkinan terjadinya klaim.

Analisis dilakukan menggunakan Exploratory Data Analysis (EDA) untuk mengidentifikasi pola dan faktor yang berkaitan dengan klaim. Selanjutnya, beberapa algoritma klasifikasi digunakan dan dibandingkan untuk menentukan model yang paling sesuai dengan tujuan bisnis.

---

## Business Understanding

### Latar Belakang

Perusahaan Travel Insurance perlu memahami karakteristik customer dan transaksi yang memiliki kemungkinan lebih tinggi untuk menghasilkan klaim. Kemampuan dalam memprediksi potensi klaim dapat membantu perusahaan dalam melakukan risk assessment serta meningkatkan perencanaan dan pengelolaan klaim.

### Problem Statement

Perusahaan membutuhkan kemampuan untuk memprediksi apakah seorang customer berpotensi melakukan klaim berdasarkan karakteristik customer dan informasi transaksi Travel Insurance.

Selain itu, perusahaan ingin mengetahui faktor-faktor yang berkaitan dengan terjadinya klaim sehingga dapat memperoleh insight yang mendukung proses risk assessment dan pengambilan keputusan bisnis.

### Goals

Berdasarkan permasalahan tersebut, perusahaan ingin memiliki kemampuan untuk memprediksi kemungkinan seorang customer melakukan klaim, sehingga perusahaan dapat mengidentifikasi customer yang memiliki potensi klaim dan melakukan perencanaan pengelolaan risiko dengan lebih baik.

Perusahaan juga ingin mengetahui faktor atau variabel yang berkaitan dengan terjadinya klaim, sehingga hasil analisis dapat digunakan sebagai dasar dalam melakukan evaluasi produk, risk assessment, dan strategi pengelolaan klaim.

---

## Analytic Approach

Analisis dilakukan menggunakan pendekatan **Supervised Learning – Classification** untuk memprediksi apakah seorang customer akan melakukan klaim atau tidak.

Tahapan analisis meliputi:

1. **Data Preparation**
   - Menangani missing values.
   - Melakukan pengecekan dan penanganan data yang tidak sesuai.
   - Memisahkan variabel independen dan target.

2. **Exploratory Data Analysis**
   - Menganalisis distribusi klaim.
   - Menganalisis karakteristik customer berdasarkan klaim.
   - Menganalisis hubungan antara klaim dengan produk asuransi, destinasi, agency, distribution channel, usia, durasi perjalanan, dan variabel lainnya.

3. **Data Preprocessing**
   - Menggunakan `OneHotEncoder` untuk variabel kategorikal.
   - Menggunakan `RobustScaler` untuk variabel numerik.
   - Membangun preprocessing pipeline untuk memastikan proses transformasi dilakukan secara konsisten.

4. **Model Development**
   
   Tiga algoritma classification digunakan dalam analisis:
   - Logistic Regression
   - Random Forest
   - XGBoost

5. **Model Evaluation**
   
   Model dievaluasi menggunakan:
   - Recall
   - Precision
   - Accuracy
   - F1-Score
   - F2-Score
   - ROC-AUC
   - Confusion Matrix

---

## Model yang Digunakan

### 1. Logistic Regression

Digunakan sebagai salah satu model klasifikasi untuk memprediksi probabilitas customer melakukan klaim berdasarkan karakteristik yang tersedia.

### 2. Random Forest

Merupakan ensemble learning berbasis decision tree yang digunakan untuk menangkap hubungan non-linear antar variabel dan menghasilkan prediksi klasifikasi.

### 3. XGBoost

Merupakan algoritma gradient boosting yang digunakan untuk menangkap pola yang lebih kompleks dalam data dan meningkatkan kemampuan prediksi.

---

## Metric Evaluation

Beberapa metric digunakan untuk mengevaluasi performa masing-masing model.

| Metric | Tujuan |
|---|---|
| Recall | Mengukur kemampuan model dalam mengidentifikasi customer yang melakukan klaim |
| Precision | Mengukur ketepatan prediksi customer yang dikategorikan melakukan klaim |
| Accuracy | Mengukur proporsi prediksi yang benar secara keseluruhan |
| F1-Score | Mengukur keseimbangan antara Precision dan Recall |
| **F2-Score** | Memberikan bobot lebih besar terhadap Recall |
| ROC-AUC | Mengukur kemampuan model dalam membedakan kelas klaim dan tidak klaim |
| Confusion Matrix | Menunjukkan True Positive, True Negative, False Positive, dan False Negative |

### Metric Utama

**F2-Score digunakan sebagai metric utama** karena perusahaan lebih memprioritaskan kemampuan model dalam mengidentifikasi customer yang berpotensi melakukan klaim.

Dengan memprioritaskan Recall, perusahaan dapat meminimalkan kemungkinan customer yang sebenarnya melakukan klaim tetapi diprediksi tidak melakukan klaim (**False Negative**).

---

## Perbandingan Model

Hasil evaluasi model:

| Model | Recall | Precision | Accuracy | F1-Score | F2-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|---:|
| **Logistic Regression** | **1.0000** | **0.9830** | **0.9830** | **0.9914** | **0.9965** | **0.8429** |
| XGBoost | 0.9997 | 0.9830 | 0.9827 | 0.9913 | 0.9963 | 0.8009 |
| Random Forest | 0.9967 | 0.9832 | 0.9800 | 0.9899 | 0.9939 | 0.7476 |

Berdasarkan hasil evaluasi, **Logistic Regression** menghasilkan F2-Score tertinggi sebesar **99.65%** dan Recall sebesar **100%**, sehingga dipilih sebagai model terbaik berdasarkan metric utama.

---

## Business Interpretation

Berdasarkan hasil evaluasi, **Logistic Regression** dipilih sebagai model terbaik karena menghasilkan F2-Score tertinggi dan Recall sebesar 100%. Model ini dapat membantu perusahaan mengidentifikasi customer yang berpotensi melakukan klaim sehingga mendukung proses risk assessment dan perencanaan pengelolaan klaim. Namun, hasil Confusion Matrix menunjukkan adanya kecenderungan model dalam memprediksi customer sebagai claim, sehingga hasil prediksi perlu dipertimbangkan bersama karakteristik bisnis dan kebutuhan perusahaan.

---

## Insight Utama

Hasil Exploratory Data Analysis menunjukkan bahwa terdapat perbedaan claim rate pada berbagai karakteristik customer dan transaksi, terutama berdasarkan **Product Name**.

Beberapa produk memiliki claim rate yang lebih tinggi dibandingkan produk lainnya. Hal ini menunjukkan bahwa jenis produk dapat menjadi salah satu variabel yang relevan dalam memprediksi kemungkinan terjadinya klaim.

Selain itu, variabel seperti **Destination, Agency, Distribution Channel, Duration, Age, Net Sales, dan Commision** juga dianalisis untuk memahami karakteristik yang berkaitan dengan claim.

---

## Teknologi dan Library

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Jupyter Notebook

---

## Struktur Repository

```text
travel-insurance-claim-prediction/
│
├── data/
│   └── travel_insurance.csv
│
├── notebook/
│   └── Travel_Insurance_Claim_Prediction.ipynb
│
├── README.md
└── requirements.txt
