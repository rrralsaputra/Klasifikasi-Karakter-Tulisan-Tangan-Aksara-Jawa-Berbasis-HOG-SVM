# 📝 Klasifikasi Tulisan Tangan Aksara Jawa Menggunakan HOG+SVM dan CNN

## 📖 Deskripsi Proyek

Proyek ini merupakan implementasi sistem klasifikasi karakter tulisan tangan **Aksara Jawa (Hanacaraka)** berbasis **Pengolahan Citra Digital (PCD)** dan **Machine Learning**. Penelitian ini membandingkan dua pendekatan klasifikasi:

1. **Histogram of Oriented Gradients (HOG) + Support Vector Machine (SVM)**
2. **Convolutional Neural Network (CNN)**

Tujuan utama penelitian adalah mengidentifikasi model yang paling efektif dalam mengenali karakter tulisan tangan Aksara Jawa berdasarkan metrik evaluasi seperti Accuracy, Precision, Recall, dan F1-Score.

---

## 🎯 Tujuan Penelitian

* Mengembangkan sistem klasifikasi karakter tulisan tangan Aksara Jawa.
* Menerapkan metode ekstraksi fitur HOG dan klasifikasi SVM.
* Membangun model CNN sebagai metode pembanding.
* Membandingkan performa HOG+SVM dan CNN untuk menentukan model terbaik.

---

## 📂 Dataset

Dataset terdiri dari citra tulisan tangan karakter Aksara Jawa.

### Statistik Dataset

| Keterangan      | Jumlah |
| --------------- | ------ |
| Jumlah Kelas    | 20     |
| Total Citra     | 1580   |
| Data per Kelas  | 79     |
| Data Training   | 1093   |
| Data Validation | 234    |
| Data Testing    | 235    |

### Kelas Karakter

```text
ha  na  ca  ra  ka
da  ta  sa  wa  la
pa  dha ja  ya  nya
ma  ga  ba  tha nga
```

---

## 🔄 Alur Penelitian

```text
Dataset
   │
   ▼
Preprocessing
   │
   ▼
Data Splitting
   │
   ▼
Data Augmentation
   │
   ├─────────────┐
   ▼             ▼
 HOG          CNN
   │             │
   ▼             ▼
 SVM       Deep Learning
   │             │
   └──────┬──────┘
          ▼
      Evaluation
```

---

## 🖼️ Preprocessing

Tahapan preprocessing yang digunakan:

1. Grayscale Conversion
2. Gaussian Blur
3. Otsu Thresholding
4. Cropping
5. Padding
6. Resize (64 × 64)
7. Normalization

Tujuan preprocessing adalah menyeragamkan citra sehingga model dapat mempelajari pola karakter dengan lebih baik.

---

## 🔁 Data Augmentation

Augmentasi diterapkan **hanya pada data training** untuk meningkatkan variasi data dan mengurangi overfitting.

Metode augmentasi yang digunakan:

* Rotasi
* Translasi
* Pergeseran posisi

Jumlah data training meningkat secara signifikan setelah proses augmentasi.

---

## 📊 Ekstraksi Fitur HOG

Parameter HOG:

```python
orientations = 9
pixels_per_cell = (8,8)
cells_per_block = (2,2)
block_norm = 'L2-Hys'
```

Hasil ekstraksi menghasilkan feature vector yang digunakan sebagai input model SVM.

---

## 🤖 Model HOG + SVM

### Konfigurasi

```python
SVC(
    kernel='rbf',
    C=10,
    gamma='scale'
)
```

### Hasil Evaluasi

| Metrik              | Nilai  |
| ------------------- | ------ |
| Train Accuracy      | 98.96% |
| Validation Accuracy | 83.33% |
| Test Accuracy       | 86.81% |
| Macro Precision     | 0.88   |
| Macro Recall        | 0.87   |
| Macro F1-Score      | 0.87   |

---

## 🧠 Model CNN

CNN digunakan sebagai metode pembanding dengan kemampuan ekstraksi fitur otomatis.

### Arsitektur CNN

```text
Input Image
      │
      ▼
Conv2D
      │
      ▼
MaxPooling
      │
      ▼
Conv2D
      │
      ▼
MaxPooling
      │
      ▼
Flatten
      │
      ▼
Dense
      │
      ▼
Softmax
```

### Hasil Evaluasi

| Metrik              | Nilai  |
| ------------------- | ------ |
| Train Accuracy      | 99.69% |
| Validation Accuracy | 90.60% |
| Test Accuracy       | 90.21% |
| Macro Precision     | 0.91   |
| Macro Recall        | 0.90   |
| Macro F1-Score      | 0.90   |

---

## 📈 Perbandingan Model

| Metrik    | HOG+SVM |      CNN |
| --------- | ------: | -------: |
| Accuracy  |    0.87 | **0.90** |
| Precision |    0.88 | **0.91** |
| Recall    |    0.87 | **0.90** |
| F1-Score  |    0.87 | **0.90** |

### Kesimpulan Perbandingan

CNN memberikan performa yang lebih baik dibandingkan HOG+SVM pada seluruh metrik evaluasi. Selain memperoleh akurasi yang lebih tinggi, CNN juga memiliki kemampuan generalisasi yang lebih baik dengan gap train-validation yang lebih kecil.

---

## 🛠️ Tech Stack

* Python
* OpenCV
* NumPy
* Pandas
* Scikit-Learn
* Scikit-Image
* TensorFlow / Keras
* Matplotlib
* Seaborn





---

## 📚 Referensi

* Dalal, N., & Triggs, B. (2005). Histograms of Oriented Gradients for Human Detection.
* Cortes, C., & Vapnik, V. (1995). Support Vector Machines.
* LeCun, Y., Bengio, Y., & Hinton, G. (2015). Deep Learning.

---

## 👨‍🎓 Author
**Kelompok 2 Kelas 24B**  
  Najmu Tsaqib Arsalan (24031554026)  
  Muhammad Geralldo Agatha Saputra (24031554091)
  Moh. Rasya Al Khalifi (24031554132)  
  
**Program Studi Sains Data**
**Universitas Negri Surabaya**

**2025/2026**
