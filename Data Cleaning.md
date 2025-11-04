# Data Cleaning dengan Pandas

## 1. Apa Itu Data Cleaning?

Data Cleaning (pembersihan data) adalah proses memperbaiki, menghapus, atau menyesuaikan data yang salah, tidak lengkap, atau ganda agar hasil analisis menjadi akurat dan dapat dipercaya.

Dalam dunia nyata, data sering datang dalam kondisi “kotor”:
- Ada data yang hilang atau kosong.
- Ada data ganda (duplikat).
- Ada kesalahan pengetikan.
- Ada format yang tidak konsisten (misalnya tanggal ditulis beda-beda).

Tanpa data cleaning, hasil analisis bisa menyesatkan — seperti membuat kesimpulan salah karena data dasarnya tidak rapi.

### Mengapa Data Cleaning Penting?
1. **Meningkatkan Kualitas Data**: hasil analisis jadi lebih akurat dan bisa dipercaya.  
2. **Mendukung Keputusan yang Lebih Baik**: data yang bersih membantu organisasi mengambil keputusan yang tepat.  
3. **Efisiensi Waktu**: data yang rapi lebih cepat diolah, tanpa perlu perbaikan berulang.  
4. **Memenuhi Standar Kualitas**: banyak industri dan lembaga memiliki aturan tentang keakuratan data.

---

## Masalah Umum pada Data

| Jenis Masalah | Contoh | Dampak |
|----------------|--------|--------|
| Nilai Hilang (*Missing Value*) | Kolom harga kosong | Analisis rata-rata jadi salah |
| Data Duplikat | Baris pelanggan sama dua kali | Hasil total penjualan berlipat |
| Format Tidak Konsisten | Tanggal ditulis “1/1/2024” dan “2024-01-01” | Gagal diolah sistem |
| Salah Ketik | “Surabya” bukan “Surabaya” | Data wilayah jadi tidak valid |
| Outlier (*nilai ekstrem*) | Harga 1.000.000.000 | Mengganggu perhitungan statistik |

---

## Langkah-langkah Umum Data Cleaning

1. Menilai kualitas data — melihat tipe data dan jumlah nilai kosong.  
2. Menghapus data yang tidak relevan — misalnya kolom yang tidak digunakan.  
3. Menangani nilai kosong (*NaN*) — bisa dihapus atau diisi.  
4. Menghapus data duplikat — agar data tidak dihitung dua kali.  
5. Menstandarkan format — misalnya semua huruf jadi kapital.  
6. Menangani outlier — nilai yang terlalu jauh dari normal.

---

## 2. Praktik di Google Colab

Google Colab adalah alat berbasis web untuk menulis dan menjalankan kode Python tanpa instalasi tambahan.

### a. Buka Google Colab
1. Buka [https://colab.research.google.com](https://colab.research.google.com)  
2. Klik **File → Upload Notebook** atau **New Notebook**

---

### b. Instalasi dan Import Library
```python
# Biasanya pandas sudah tersedia di Colab, tapi jika belum:
!pip install pandas

import pandas as pd
```
---

### c. Membaca Data CSV
Upload file Data Ritel.csv ke Colab

```python
# Baca dataset
df = pd.read_csv("Data Ritel.csv")

# Tampilkan 5 baris pertama
df.head()
```

---

### d. Menampilkan Informasi Data
```python
# Melihat ukuran data
print("Jumlah baris dan kolom:", df.shape)

# Melihat tipe data dan jumlah nilai kosong
df.info()

# Melihat ringkasan statistik
df.describe()
```

---

### e. Menangani Nilai Kosong (NaN)
```python
# Cek ada berapa nilai kosong di setiap kolom
print(df.isna().sum())

# Isi nilai kosong dengan teks "Tidak Ada"
df = df.fillna("Tidak Ada")

# Atau hapus baris yang kosong semua (opsional)
df = df.dropna(how='all')

# Lihat hasilnya
df.head()
```

---

### f. Menghapus Data Duplikat
```python
# Cek apakah ada duplikat
print("Jumlah data duplikat sebelum dihapus:", df.duplicated().sum())

# Hapus duplikat
df = df.drop_duplicates()

# Lihat hasilnya
print("Jumlah data duplikat setelah dihapus:", df.duplicated().sum())
df.head()
```

---

### g. Menyimpan Hasil Cleaning
```python
# Simpan dataset hasil cleaning ke file baru
df.to_csv("Data Ritel Clean.csv", index=False)

# Download hasilnya
from google.colab import files
files.download("Data Ritel CLean.csv")
```







