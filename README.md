# Indonesian Clickbait Detection: IndoBERT vs. SVM

Repositori ini berisi proyek implementasi dan komparasi model NLP untuk mendeteksi judul berita *clickbait* berbahasa Indonesia. Proyek ini membandingkan pendekatan Klasifikasi Klasik (*Machine Learning*) menggunakan **TF-IDF + SVM** dengan pendekatan modern (*Deep Learning / State-of-the-Art*) berbasis *Transformers* menggunakan **IndoBERT fine-tuning** beserta teknik optimasinya. 

Dataset: CLICK-ID (https://www.kaggle.com/datasets/andikawilliam/clickid)

## 📌 Fitur Proyek
- **Exploratory Data Analysis (EDA):** Analisis visual distribusi kelas berita serta karakteristik panjang teks (karakter dan jumlah kata) berbasis Plotly.
- **Baseline Model:** Ekstraksi fitur N-Gram TF-IDF dipadukan dengan algoritma *Support Vector Machine* (SVM) Kernel Linear.
- **Advanced Model:** Eksperimen *fine-tuning* model Pre-trained `indobenchmark/indobert-base-p2`.
- **Hyperparameter Optimization:** Penerapan *Learning Rate Adjustment*, *Gradient Accumulation*, dan *Early Stopping* untuk mengatasi kendala *overfitting* pada Deep Learning.

## 📊 Hasil Eksperimen & Evaluasi

### 1. Analisis Distribusi Panjang Teks
Karakteristik panjang teks (karakter dan kata) dieksplorasi untuk melihat pola perbedaan antara judul berita *clickbait* (Label 1) dan *non-clickbait* (Label 0).

### 2. Kurva Performa Perbandingan Loss (IndoBERT)
Eksperimen dilakukan dalam dua tahap pelatihan untuk menguji stabilitas arsitektur model IndoBERT:
- **Model Awal (`learning_rate=2e-5`):** Mengalami gejala *overfitting* yang cukup ekstrem pada Epoch 3, di mana kurva *Validation Loss* melonjak naik hingga mencapai nilai `0.556`.
- **Model Optimasi (`learning_rate=1e-5` + *Gradient Accumulation*):** Berhasil menekan laju *loss* secara stabil. Kurva *Validation Loss* berhasil diredam melandai pada kisaran `0.39 - 0.42` dan dikunci otomatis pada kondisi terbaiknya di Epoch 2 menggunakan *Early Stopping*.
- 
<img width="287" height="244" alt="image" src="https://github.com/user-attachments/assets/2ea17621-446d-473d-a59a-8db7879dbb3a" />
<img width="299" height="247" alt="image" src="https://github.com/user-attachments/assets/97c88bdb-9947-4861-bec8-da5da767555a" />
<img width="608" height="245" alt="image" src="https://github.com/user-attachments/assets/3550719d-9c4d-45d4-954a-41fb04dc50de" />
<img width="713" height="295" alt="image" src="https://github.com/user-attachments/assets/2cda1541-0e10-4bdd-8f90-061d977a186f" />

## 🛠️ Langkah Instalasi & Penggunaan

1. **Clone Repositori**
   ```bash
   git clone [https://github.com/ethereins/NLP-Clickbait-Classification-IndoBERT-vs-SVM.git](https://github.com/ethereins/NLP-Clickbait-Classification-IndoBERT-vs-SVM.git)
   cd NLP-Clickbait-Classification-IndoBERT-vs-SVM
