# Perbandingan Metode Imputasi Missing Value pada Dataset Diabetes

Repository ini berisi tugas besar mata kuliah Penambangan Data yang membahas perbandingan beberapa metode imputasi missing value pada dataset diabetes. Project ini dibuat menggunakan Jupyter Notebook dan bertujuan untuk melihat bagaimana perbedaan metode imputasi dapat memengaruhi hasil klasifikasi.

## 📋 Deskripsi Project

Missing value merupakan salah satu permasalahan yang sering ditemukan dalam proses pengolahan data. Pada dataset diabetes, beberapa nilai 0 pada fitur medis tertentu dapat dianggap tidak valid, seperti nilai 0 pada Glucose, BloodPressure, SkinThickness, Insulin, dan BMI. Oleh karena itu, nilai tersebut perlu ditangani sebelum data digunakan untuk proses klasifikasi.

Project ini membandingkan beberapa metode imputasi missing value, kemudian mengevaluasi pengaruhnya terhadap performa model klasifikasi Random Forest.

## 🎯 Tujuan Project

Tujuan dari project ini adalah:

1. Mengidentifikasi missing value tersembunyi pada dataset diabetes
2. Menerapkan beberapa metode imputasi untuk menangani missing value
3. Membandingkan hasil klasifikasi dari setiap metode imputasi
4. Menentukan metode imputasi yang memberikan performa terbaik berdasarkan metrik evaluasi

## 📊 Dataset

Dataset yang digunakan adalah **Pima Indians Diabetes Dataset**. Dataset ini berisi beberapa fitur medis yang digunakan untuk memprediksi apakah seseorang memiliki indikasi diabetes atau tidak.

### Fitur pada Dataset:

- **Pregnancies**: Jumlah kehamilan
- **Glucose**: Kadar glukosa darah (puasa)
- **BloodPressure**: Tekanan darah (diastolic)
- **SkinThickness**: Ketebalan lipatan kulit trisep
- **Insulin**: Kadar insulin serum 2 jam
- **BMI**: Indeks Massa Tubuh
- **DiabetesPedigreeFunction**: Fungsi riwayat diabetes keluarga
- **Age**: Usia
- **Outcome**: Target klasifikasi (0 = Tidak diabetes, 1 = Diabetes)

## 🔍 Missing Value pada Dataset

Pada dataset ini, beberapa nilai 0 pada fitur tertentu dianggap sebagai missing value karena tidak masuk akal secara konteks medis. Kolom yang dicek adalah:

- Glucose
- BloodPressure
- SkinThickness
- Insulin
- BMI

Nilai 0 pada kolom tersebut diubah menjadi NaN, lalu ditangani menggunakan beberapa metode imputasi.

## 🛠️ Metode Imputasi

Metode imputasi yang digunakan dalam project ini adalah:

### 1. **Mean Imputation**
Mean Imputation mengganti nilai yang hilang dengan nilai rata-rata dari setiap fitur. Metode ini paling sederhana tetapi dapat mengurangi variansi data.

### 2. **KNN Imputation**
KNN Imputation mengisi missing value berdasarkan kemiripan data dengan beberapa tetangga terdekat (k=5). Metode ini lebih kompleks dan mempertahankan struktur data.

### 3. **MICE / Iterative Imputation**
MICE atau Iterative Imputation mengisi missing value secara iteratif dengan memanfaatkan hubungan antar fitur. Metode ini menghasilkan data yang paling realistis.

## 🤖 Model Klasifikasi

Model klasifikasi yang digunakan adalah **Random Forest Classifier** dengan 100 trees. Model ini dipilih karena:
- Robust terhadap outlier
- Dapat menangani fitur numerik dan kategorik
- Tidak memerlukan scaling data
- Efisien untuk dataset medium-size

## 📈 Metrik Evaluasi

Metrik evaluasi yang digunakan dalam project ini antara lain:

- **Accuracy**: Proporsi prediksi yang benar dari total prediksi
- **Precision**: Proporsi prediksi positif yang benar
- **Recall (Sensitivity)**: Proporsi kasus positif yang terdeteksi
- **F1-Score**: Harmonic mean antara Precision dan Recall
- **Confusion Matrix**: Matriks yang menunjukkan True Positives, True Negatives, False Positives, False Negatives
- **Classification Report**: Detail laporan performa per kelas

## 📁 Struktur Folder

```
Tugas-Besar-PD/
├── dataset/
│   └── diabetes.csv
├── notebook/
│   └── Perbandingan_Metode_Imputasi_Missing_Value_Dataset_Diabetes.ipynb
├── README.md
├── requirements.txt
├── .gitignore
└── .git/
```

## 🚀 Cara Menjalankan Project

### 1. Clone Repository
```bash
git clone https://github.com/rdtngh/Tugas-Besar-PD.git
cd Tugas-Besar-PD
```

### 2. Buat Virtual Environment
```bash
python -m venv .venv
```

### 3. Aktifkan Virtual Environment

**Untuk PowerShell:**
```powershell
.\.venv\Scripts\Activate.ps1
```

Jika muncul error execution policy, jalankan:
```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
```

Lalu aktifkan kembali:
```powershell
.\.venv\Scripts\Activate.ps1
```

**Untuk Command Prompt:**
```cmd
.venv\Scripts\activate.bat
```

**Untuk Linux/Mac:**
```bash
source .venv/bin/activate
```

### 4. Install Library
```bash
pip install -r requirements.txt
```

### 5. Jalankan Jupyter Notebook
```bash
jupyter notebook
```

### 6. Buka Notebook
- Buka file notebook pada folder `notebook/`
- Jalankan semua cell dari awal sampai akhir

## ✅ Cara Mengecek Notebook Berjalan

Untuk memastikan notebook dapat berjalan tanpa error, gunakan salah satu cara berikut:

### Opsi 1: Melalui Jupyter
1. Buka notebook di Jupyter
2. Klik menu **Kernel** → **Restart & Run All**
3. Pastikan semua cell berhasil dijalankan tanpa error

### Opsi 2: Melalui Terminal
```bash
jupyter nbconvert --to notebook --execute ".\notebook\Perbandingan_Metode_Imputasi_Missing_Value_Dataset_Diabetes.ipynb" --output "hasil_test.ipynb"
```

Jika perintah selesai tanpa error, berarti notebook dapat dijalankan dari awal sampai akhir. File `hasil_test.ipynb` akan dihapus secara otomatis (sudah masuk `.gitignore`).

## 📚 Library yang Digunakan

| Library | Versi | Penggunaan |
|---------|-------|-----------|
| pandas | ≥1.3.0 | Manipulasi data |
| numpy | ≥1.21.0 | Operasi numerik |
| matplotlib | ≥3.4.0 | Visualisasi (plot statis) |
| seaborn | ≥0.11.0 | Visualisasi (statistical graphics) |
| scikit-learn | ≥0.24.0 | Machine learning |
| jupyter | ≥1.0.0 | Notebook environment |
| openpyxl | ≥3.6.0 | Export ke Excel |

## 📊 Hasil Singkat

Project menghasilkan perbandingan performa ketiga metode imputasi melalui:
- Tabel perbandingan metrik (Accuracy, Precision, Recall, F1-Score)
- Visualisasi bar chart perbandingan metrik
- ROC curves untuk setiap metode
- Confusion matrix untuk setiap metode
- Classification report detail

## 🎓 Kesimpulan

Penanganan missing value merupakan tahap penting dalam proses data mining. Pada dataset diabetes, nilai 0 pada beberapa fitur medis perlu diperlakukan sebagai missing value agar proses analisis menjadi lebih valid. 

Dengan membandingkan beberapa metode imputasi, project ini menunjukkan bagaimana pilihan metode imputasi dapat memengaruhi performa model klasifikasi. Setiap metode memiliki kelebihan dan kekurangan:

- **Mean Imputation**: Cepat dan sederhana, tapi mengurangi variansi
- **KNN Imputation**: Lebih baik mempertahankan struktur data
- **MICE Imputation**: Menghasilkan data paling realistis dengan memanfaatkan hubungan antar fitur

Pemilihan metode imputasi perlu disesuaikan dengan karakteristik data dan tujuan analisis.

## 👥 Author / Identitas Kelompok

**Kelompok**: 05  
**Mata Kuliah**: Penambangan Data  
**Topik**: Perbandingan Metode Imputasi Missing Value pada Dataset Diabetes  
**Periode**: Semester Genap 2025/2026

### Anggota:
1. Najlatika (123140078)
2. Bening Apni Prameswari (123140089)
3. Falent Antonius Panjaitan (123140124)
4. Raditya Alrasyid Nugroho (123140125)
5. Raisya Syifa Saleh (123140169)
6. Muhamad Arif Ardani (123140186)

---
