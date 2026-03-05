# 📱 Analisis Sentimen Berbasis Aspek (ABSA) pada Ulasan Aplikasi by.U

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-green.svg)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Proyek skripsi ini mengimplementasikan **Aspect-Based Sentiment Analysis (ABSA)** pada ulasan pengguna aplikasi **by.U** di Google Play Store menggunakan metode **LDA** (Latent Dirichlet Allocation) untuk ekstraksi aspek dan **SVM** (Support Vector Machine) untuk klasifikasi sentimen.

---

## 📌 Deskripsi Proyek

Tujuan penelitian ini adalah mengidentifikasi aspek-aspek yang dibicarakan pengguna dalam ulasan aplikasi by.U, kemudian mengklasifikasikan sentimen (positif, negatif, netral) untuk setiap aspek secara otomatis.

**Pipeline utama:**
1. **Pengambilan Data** — Scraping 10.000 ulasan dari Google Play Store
2. **Preprocessing** — Pembersihan teks berbahasa Indonesia (case folding, cleaning, tokenisasi, normalisasi, konversi negasi, stopword removal, stemming)
3. **Pemodelan Topik (LDA)** — Ekstraksi aspek menggunakan Coherence Score untuk menentukan jumlah topik optimal
4. **Klasifikasi Sentimen (SVM)** — Klasifikasi per aspek dengan GridSearchCV, SMOTE, dan Stratified K-Fold Cross-Validation

---

## 🗂️ Struktur Repository

```
absa-byu-reviews/
│
├── ABSA.ipynb              # Notebook utama (end-to-end pipeline)
├── requirements.txt        # Daftar dependensi Python
├── README.md
│
├── data/
│   ├── data_raw.csv        # Data mentah hasil scraping (tidak di-push ke GitHub)
│   ├── data_preprocessed.csv
│   └── data_labeled.csv    # Data berlabel untuk training SVM
│
└── models/
    └── *.joblib            # Model SVM tersimpan per aspek
```

> ⚠️ File `data/data_raw.csv` dan `models/*.joblib` tidak disertakan di repo ini karena ukuran file. Jalankan notebook dari awal untuk meregenerasinya.

---

## 🔧 Metode & Tools

| Tahap | Metode / Library |
|---|---|
| Scraping | `google-play-scraper` |
| Preprocessing | `Sastrawi`, `NLTK`, `re` |
| Pemodelan Topik | `Gensim` (LDA, Coherence Score, pyLDAvis) |
| Klasifikasi | `scikit-learn` (SVM, TF-IDF) |
| Imbalanced Data | `imbalanced-learn` (SMOTE, SMOTEENN) |
| Visualisasi | `matplotlib`, `seaborn`, `WordCloud`, `pyLDAvis` |

---

## 🚀 Cara Menjalankan

### 1. Clone repository
```bash
git clone https://github.com/<username>/absa-byu-reviews.git
cd absa-byu-reviews
```

### 2. Install dependensi
```bash
pip install -r requirements.txt
```

### 3. Jalankan notebook
```bash
jupyter notebook ABSA.ipynb
```

> Pastikan folder `data/` tersedia dan berisi `data_raw.csv`. Jika belum ada, uncomment bagian scraping di **Section 2.1** pada notebook untuk mengambil data langsung dari Google Play Store.

---

## 📊 Hasil

- **Aspek yang teridentifikasi (LDA):**
  - Aspek 1: Aplikasi
  - Aspek 2: Jaringan
  - Aspek 3: Layanan/Paket

- **Evaluasi model SVM** dilakukan menggunakan Stratified K-Fold Cross-Validation dengan metrik akurasi, precision, recall, dan F1-score per aspek.

---

## 📦 Requirements

Lihat [`requirements.txt`](requirements.txt) untuk daftar lengkap dependensi.

---

## 📄 Lisensi

Proyek ini menggunakan lisensi [MIT](LICENSE). Bebas digunakan untuk keperluan belajar dan referensi akademis.

---

## 👤 Author

**Rifqi Sirojul Muzhoffar**  
📧 [rmuzhoffar@gmail.com]  
🔗 [LinkedIn](https://linkedin.com/in/rifqi-sm) | [GitHub](https://github.com/Muzhoffar)
