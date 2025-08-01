# 📊 Data Mining Project - Sales Prediction

Halo! Ini project data mining buat prediksi penjualan toko. Project ini pake dataset dari Rossmann Store Sales yang lumayan gede nih datanya.

## 🎯 Apa sih project ini?

Project ini buat ngeprediksi penjualan toko Rossmann berdasarkan berbagai faktor kayak:
- Hari dalam seminggu
- Promo yang lagi jalan
- Liburan sekolah
- Jarak ke kompetitor
- Dan masih banyak lagi!

## 📁 Struktur Project

```
Data mining/
├── data/                    # Folder buat nyimpen dataset
│   ├── train.csv           # Data training (1M+ rows)
│   ├── test.csv            # Data testing
│   ├── store.csv           # Info toko
│   └── sample_submission.csv # Format submission
├── Load_dataset.ipynb      # Notebook buat load & explore data
└── README.md              # File ini
```

## 🚀 Cara Pake

1. **Install dependencies dulu:**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn xgboost
   ```

2. **Buka notebook:**
   - Buka `Load_dataset.ipynb` di Jupyter atau Google Colab
   - Run cell pertama buat install packages
   - Run cell kedua buat load data

3. **Explore data:**
   - Data udah digabung antara sales dan info toko
   - Ada 1M+ rows data training
   - 18 kolom features

## 📈 Dataset Info

**Train Data:**
- Store: ID toko
- DayOfWeek: Hari dalam seminggu (1-7)
- Date: Tanggal
- Sales: Penjualan (target variable)
- Customers: Jumlah customer
- Open: Toko buka/tutup
- Promo: Ada promo atau nggak
- StateHoliday: Liburan nasional
- SchoolHoliday: Liburan sekolah

**Store Data:**
- StoreType: Tipe toko (a,b,c,d)
- Assortment: Jenis produk
- CompetitionDistance: Jarak ke kompetitor
- Promo2: Info promo tambahan

## 🛠️ Tech Stack

- **Python** - Bahasa pemrograman utama
- **Pandas** - Buat manipulasi data
- **NumPy** - Buat komputasi numerik
- **Matplotlib & Seaborn** - Buat visualisasi
- **Scikit-learn** - Machine learning
- **XGBoost** - Gradient boosting

## 📝 TODO

- [x] Exploratory Data Analysis (EDA)
- [x] Feature Engineering
- [x] Model Selection
- [x] Hyperparameter Tuning
- [x] Model Evaluation
- [x] Submission
