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

1. Menilai kualitas data: melihat tipe data dan jumlah nilai kosong.  
2. Menghapus data yang tidak relevan: misalnya kolom yang tidak digunakan.  
3. Menangani nilai kosong (*NaN*): bisa dihapus atau diisi.  
4. Menghapus data duplikat: agar data tidak dihitung dua kali.  
5. Menstandarkan format: misalnya semua huruf jadi kapital.  
6. Menangani outlier: nilai yang terlalu jauh dari normal.

---

## 2. Praktik di Google Colab

Google Colab adalah alat berbasis web untuk menulis dan menjalankan kode Python tanpa instalasi tambahan. Pada praktik ini akan digunakan Google Colab untuk menjalankan seluruh proses data cleaning menggunakan pandas. Apabila menggunakan lingkungan kerja lain, pastikan platform tersebut mendukung format .ipynb atau lingkungan Jupyter Notebook agar kode dapat dijalankan dengan benar.

### a. Buka Google Colab
1. Buka [https://colab.research.google.com](https://colab.research.google.com)  
2. Klik **File → New Notebook**

---

### b. Instalasi dan Import Library
Biasanya pandas sudah tersedia di Colab, tapi jika belum:
```python
!pip install pandas
```
Import library
```python
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

Cek ada berapa nilai kosong di data tersebut
```python
df.isnull().sum()
```
Jika ada, lakukan penanganan nilai kosong. Dalam kasus ini, baris dan kolom yang berisi NaN akan dihapus agar bisa diproses lebih lanjut.

Hapus kolom
```python
df = df.drop(columns=["Empty1", "Empty2"])
```
Hapus baris yang berisi NaN dan lihat hasilnya
```python
df = df.dropna()
df
```
Cek lagi apakah masih ada missing value?

---

### f. Menghapus Data Duplikat

Cek apakah ada duplikat
```python
df.duplicated().sum()
```
Hapus duplikat
```python
df = df.drop_duplicates()
```
Cek lagi apakah masih ada data duplikat?

---

### g. Menyimpan Hasil Cleaning
```python
# Simpan dataset hasil cleaning ke file baru
df.to_csv("Data Ritel Clean.csv", index=False)
```







