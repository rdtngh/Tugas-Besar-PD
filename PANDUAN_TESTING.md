# Panduan Pengujian dan Cara Menjalankan Project

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

## 🧪 Testing: Jalankan Notebook

### Opsi A: Melalui Jupyter UI

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

Jika berhasil tanpa error, berarti notebook dapat dijalankan.

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

Ketika notebook berhasil dijalankan, output nya adalah:

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
