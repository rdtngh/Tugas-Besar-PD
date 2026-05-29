# Panduan Pengujian dan Cara Menjalankan Project

## ✅ Verifikasi Struktur Project

Project Anda sekarang memiliki struktur berikut:

```
Tugas-Besar-PD/
├── .git/                          # Repository Git
├── .gitignore                     # File konfigurasi Git
├── .venv/                         # Virtual environment
├── dataset/
│   └── diabetes.csv              # Dataset Pima Indians Diabetes
├── notebook/
│   └── Perbandingan_Metode_Imputasi_Missing_Value_Dataset_Diabetes.ipynb
├── README.md                      # Dokumentasi project
└── requirements.txt               # Daftar library yang diperlukan
```

## 🚀 Langkah-Langkah Menjalankan Project Secara Lokal

### Step 1: Setup Virtual Environment

```powershell
# Buat virtual environment
python -m venv .venv

# Aktifkan virtual environment (PowerShell)
.\.venv\Scripts\Activate.ps1

# Jika ada error execution policy:
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
.\.venv\Scripts\Activate.ps1
```

### Step 2: Install Library

```bash
pip install -r requirements.txt
```

### Step 3: Jalankan Jupyter Notebook

```bash
jupyter notebook
```

### Step 4: Buka dan Jalankan Notebook

1. Di Jupyter, navigasi ke folder `notebook/`
2. Buka file: `Perbandingan_Metode_Imputasi_Missing_Value_Dataset_Diabetes.ipynb`
3. Jalankan semua cell dengan: **Kernel → Restart & Run All**

## 🔍 Perbaikan yang Dilakukan

### 1. **Perbaikan Notebook** ✓

#### Masalah Lama:
- Cell menggunakan variabel `df` sebelum variabel tersebut didefinisikan
- Error: `NameError: name 'df' is not defined`
- Urutan cell tidak logis
- Duplikasi import library di multiple cell
- Mixed data loading (URL dan file lokal)

#### Solusi yang Diterapkan:
- **Urutan cell diperbaiki menjadi:**
  1. Judul & identitas kelompok
  2. Pendahuluan
  3. Import library (HANYA SEKALI)
  4. Load dataset dari file lokal (`../dataset/diabetes.csv`)
  5. Inspeksi data awal
  6. Identifikasi missing value tersembunyi (ubah 0 → NaN)
  7. Eksplorasi data
  8. Visualisasi missing value
  9. Split feature dan target (`X`, `y`)
  10. Split train-test set
  11. Implementasi 3 metode imputasi
  12. Training model
  13. Evaluasi dan perbandingan
  14. Visualisasi hasil
  15. Kesimpulan

- **Duplikasi import dihilangkan:** Semua import dilakukan SEKALI di awal notebook
- **Path diubah ke relative path:** `../dataset/diabetes.csv` (bekerja karena notebook berada di folder `notebook/`)
- **Dataset dibaca dengan benar:** Karena dataset sudah memiliki header, tidak perlu parameter `names=`

### 2. **Perbaikan requirements.txt** ✓

#### Sebelum:
- File terlalu besar (hasil `pip freeze`)
- Banyak library yang tidak dipakai

#### Sesudah:
```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=0.24.0
jupyter>=1.0.0
openpyxl>=3.6.0
```

### 3. **Pembuatan .gitignore** ✓

File `.gitignore` yang dibuat mengecualikan:
- Virtual environment (`.venv/`)
- Cache Python (`__pycache__/`, `.pyc`)
- Jupyter checkpoints (`.ipynb_checkpoints/`)
- Konfigurasi lokal (`.env`, `.vscode/`, `.idea/`)
- File testing (`.log`, `hasil_test.ipynb`)

### 4. **Pembuatan README.md** ✓

README yang komprehensif berisi:
- Deskripsi project
- Tujuan project
- Penjelasan dataset dan fitur
- Penjelasan missing value
- 3 metode imputasi yang digunakan
- Model klasifikasi (Random Forest)
- Metrik evaluasi
- Struktur folder
- Cara menjalankan project lengkap
- Cara mengecek notebook berjalan
- Library yang digunakan
- Kesimpulan
- Identitas kelompok

## 📋 Checklist Verifikasi

- [x] Notebook bisa dibuka tanpa error di Jupyter
- [x] Semua import library hanya di satu tempat (cell 3)
- [x] Dataset dibaca dari file lokal (`../dataset/diabetes.csv`)
- [x] Variabel `df` dibuat SEBELUM digunakan
- [x] Semua missing value (nilai 0) diubah menjadi NaN
- [x] Split feature/target dilakukan setelah data siap
- [x] Ketiga metode imputasi diimplementasikan dengan benar
- [x] Model training dilakukan untuk setiap metode
- [x] Evaluasi dan visualisasi hasil lengkap
- [x] Notebook bisa dijalankan dari awal sampai akhir dengan "Restart & Run All"
- [x] requirements.txt berisi library minimal yang diperlukan
- [x] .gitignore mengecualikan file yang tidak perlu
- [x] README.md lengkap dengan instruksi

## 🧪 Testing: Jalankan Notebook

### Opsi A: Melalui Jupyter UI (Rekomendasi untuk Awal)

```
1. Terminal: jupyter notebook
2. Browser: Buka notebook di folder notebook/
3. Menu: Kernel → Restart & Run All
4. Tunggu hingga semua cell selesai dijalankan
5. Pastikan tidak ada error (output terakhir harus "Project selesai")
```

### Opsi B: Melalui Terminal Command

```powershell
jupyter nbconvert --to notebook --execute ".\notebook\Perbandingan_Metode_Imputasi_Missing_Value_Dataset_Diabetes.ipynb" --output "hasil_test.ipynb"
```

Jika berhasil tanpa error, berarti notebook dapat dijalankan sempurna.

File `hasil_test.ipynb` akan otomatis diabaikan oleh Git (sudah di `.gitignore`).

## 📤 Persiapan untuk GitHub

Setelah memastikan notebook berjalan sempurna, gunakan perintah berikut:

```bash
# Cek status
git status

# Tambah semua file
git add .

# Commit dengan pesan yang jelas
git commit -m "Memperbaiki notebook dan menambahkan dokumentasi project"

# Push ke GitHub
git push
```

## 📞 Troubleshooting

### Error: `NameError: name 'df' is not defined`
**Solusi:** Pastikan Anda telah menjalankan semua cell dari awal sampai akhir dengan **Kernel → Restart & Run All**

### Error: `FileNotFoundError: ../dataset/diabetes.csv`
**Solusi:** 
- Pastikan file dataset berada di folder `dataset/`
- Jalankan notebook dari folder `notebook/` (bukan copy ke tempat lain)

### Error: `No module named 'sklearn'`
**Solusi:** 
```bash
pip install -r requirements.txt
```

### Jupyter tidak ditemukan
**Solusi:** 
```bash
pip install jupyter
```

## 📊 Output yang Diharapkan

Ketika notebook berhasil dijalankan, Anda akan melihat:

1. **Tabel Perbandingan Performa Model**
   - Perbandingan Accuracy, Precision, Recall, F1-Score untuk 3 metode

2. **Visualisasi:**
   - Bar chart perbandingan metrik
   - ROC curves untuk setiap metode
   - Confusion matrix untuk setiap metode
   - Distribusi fitur
   - Pola missing value

3. **Classification Report:**
   - Detail laporan untuk setiap metode imputasi

4. **Kesimpulan:**
   - Metode imputasi mana yang paling efektif

---

**Project siap untuk diunggah ke GitHub!** 🎉
