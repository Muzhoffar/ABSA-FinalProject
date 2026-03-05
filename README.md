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

## 🧰 Tech Stack

| Tahap | Library |
|---|---|
| Scraping | `google-play-scraper` |
| Preprocessing | `PySastrawi`, `NLTK` |
| Topic Modeling | `Gensim` (LDA, Coherence Score, pyLDAvis) |
| Klasifikasi | `scikit-learn` (SVM, TF-IDF, GridSearchCV) |
| Imbalanced Data | `imbalanced-learn` (SMOTE) |
| Visualisasi | `matplotlib`, `seaborn`, `WordCloud`, `pyLDAvis` |

---

## 📊 Hasil

### Aspek yang Teridentifikasi (LDA)
Dari proses topic modeling, teridentifikasi **3 aspek utama**:
- 🖥️ **Aspek Aplikasi** — performa, bug, update
- 📶 **Aspek Jaringan** — sinyal, koneksi, kecepatan
- 🛒 **Aspek Pembelian** — paket, harga, kuota

---

### Optimasi Hyperparameter (Grid Search)

| Aspek | Kernel Terbaik | Nilai C | F1-Score Macro |
|---|---|---|---|
| Aplikasi | Linear | 0.1 | 0.8889 |
| Jaringan | Linear | 0.1 | 0.8682 |
| Pembelian | RBF | 10 | 0.9124 |

Aspek Aplikasi dan Jaringan optimal dengan kernel **Linear**, menandakan data cenderung dapat dipisahkan secara linear. Aspek Pembelian membutuhkan kernel **RBF**, mengindikasikan pola yang lebih kompleks.

---

### Evaluasi Akhir Model (Rata-rata 5-Fold Cross Validation)

| Aspek | Kelas | Precision | Recall | F1-Score | Accuracy |
|---|---|---|---|---|---|
| 🖥️ Aplikasi | Negatif | 0.9728 | 0.9720 | 0.9724 | **0.9516** |
| | Positif | 0.8058 | 0.8076 | 0.8055 | |
| 📶 Jaringan | Negatif | 0.9624 | 0.9573 | 0.9598 | **0.9319** |
| | Positif | 0.7670 | 0.7885 | 0.7767 | |
| 🛒 Pembelian | Negatif | 0.9317 | 0.9810 | 0.9557 | **0.9338** |
| | Positif | 0.9413 | 0.8077 | 0.8691 | |

Model secara konsisten lebih kuat mendeteksi ulasan **negatif** di semua aspek. Aspek **Pembelian** mencatatkan keseimbangan terbaik antara kelas negatif dan positif, sedangkan aspek **Aplikasi** mencapai akurasi tertinggi.

---

## 👤 Author

**Rifqi Sirojul Muzhoffar**  
📧 rmuzhoffar@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/rifqi-sm) | [GitHub](https://github.com/Muzhoffar)
📧 [rmuzhoffar@gmail.com]  
🔗 [LinkedIn](https://linkedin.com/in/rifqi-sm) | [GitHub](https://github.com/Muzhoffar)
