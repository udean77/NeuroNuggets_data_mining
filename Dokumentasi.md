# 🎯 Prediksi Penjualan Rossmann (XGBoost & Linear Regression)

## 🔍 Ringkasan Proyek

Proyek ini nyoba buat prediksi penjualan harian di toko-toko Rossmann. Saya pakai data waktu dan info spesifik toko, lalu coba 2 model: Linear Regression sama XGBoost (pakai GPU). Hasilnya dibandingin buat lihat mana yang paling oke.

---

## 📦 Dataset
-  source : https://www.kaggle.com/competitions/rossmann-store-sales/data
- `train.csv`: data penjualan harian tiap toko
- `store.csv`: info tambahan tiap toko

➡️ Digabungin lewat kolom `Store` biar semua fitur lengkap.

---

## ⚙️ Feature Engineering

- **Fitur waktu**: Tahun, Bulan, Tanggal, Hari (0–6), Weekend/Enggak
- **Fitur kategori** (disandikan ke angka): Tipe toko, jenis barang, hari libur
- **Fitur kombinasi**:
  - `Promo_StoreType` = Promo × TipeToko
  - `Competition_Promo` = Jarak Kompetitor × Promo

---

## 📊 EDA Singkat

- **Distribusi Sales**: Condong ke kiri, banyak hari dengan sales kecil
- **Tren waktu**: Ada penurunan pelan-pelan
- **Efek promo**: Jelas naik saat promo
- **Hari dalam minggu**: Weekend beda banget
- **Data hilang**: Udah diberesin sebelum modeling

---

## 📉 Model Dasar - Linear Regression

- Pakai 14 fitur hasil engineering
- Hasil awal:
  ```bash
  RMSPE: ~0.47
  ```

---

## ⚡ XGBoost + GPU

- Pakai `tree_method='hist'`, `device='cuda'`
- Hyperparameter tuning pakai `RandomizedSearchCV`
- Param terbaik:
  ```json
  {
    'n_estimators': 500,
    'max_depth': 8,
    'learning_rate': 0.05,
    'gamma': 0.2,
    'subsample': 0.8,
    'colsample_bytree': 0.9,
    'reg_alpha': 1,
    'reg_lambda': 1.5
  }
  ```

---

## 🏁 Model Final & Evaluasi

- Dilatih di semua data training
- Dicek pakai validation set

```bash
Final XGBoost RMSPE: 0.3958
Contoh prediksi: [9948.72, 8003.03, 7287.34, 6837.28, 5816.98]
```

➡️ RMSPE 0.3958 artinya rata-rata prediksi meleset \~39.6% dari nilai aslinya.

---

## ⚔️ Perbandingan Model

| Model             | RMSPE        |
| ----------------- | ------------ |
| Linear Regression | \~0.47       |
| XGBoost (Tuned)   | **0.3958** ✅ |

---

## 📤 Submission

- Format CSV:
  - Kolom: `Id`, `Sales`
- Output disiapin buat dikirim ke platform lomba atau deploy model

---

## 🧠 Catatan

- Butuh GPU biar XGBoost-nya ngebut
- Bisa ditingkatin lagi pakai fitur baru kayak moving average, rolling window, dll
- Buat ngurangin overfitting bisa pakai early stopping atau cross-validation

---

