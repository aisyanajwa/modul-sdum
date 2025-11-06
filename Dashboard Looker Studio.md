# Modul Praktik: Membuat Dashboard Penjualan dengan Google Looker Studio
________________________________________

## 1. Pendahuluan
Google Looker Studio (sebelumnya bernama *Google Data Studio*) adalah alat berbasis web untuk membuat dashboard interaktif dan laporan visual dari data.  
Melalui Looker Studio, data dari file seperti CSV, Excel, atau Google Sheets dapat divisualisasikan menjadi grafik yang mudah dibaca dan membantu pengambilan keputusan.

> ⚠️ Catatan Penting:  
> Looker Studio hanya dapat digunakan oleh akun Google berusia 18 tahun ke atas.  
> Jika akun belum memenuhi batas usia:
> - Gunakan akun sekolah atau kampus (institutional account) yang sudah diverifikasi.  
> - Gunakan akun Google lain atau buat akun baru dengan tanggal lahir di atas 18 tahun.

---

## 2. Persiapan Data
1. Siapkan file hasil data cleaning bernama **Data Ritel.csv**.  
2. Pastikan file sudah tersimpan di Google Drive atau Google Sheets.  
3. Kolom minimal yang diperlukan:
   - `Order Date`  
   - `Region`  
   - `Category`  
   - `Sub-Category`  
   - `City`  
   - `Sales`  
   - `Profit`  
   - `Quantity`

---

## 3. Membuka Looker Studio
1. Buka [https://lookerstudio.google.com](https://lookerstudio.google.com).  
2. Klik **Blank Report (Laporan Kosong)** untuk membuat dashboard baru.  
3. Pilih **Add Data (Tambahkan Data)** → pilih **Google Sheets** atau upload file **CSV**.  
4. Tambahkan file **Data Ritel.csv** dan klik **Add to Report (Tambahkan ke Laporan)**.

---

## 4. Membuat Visualisasi Data

Setiap bagian di bawah ini akan membuat satu grafik yang berbeda.  
Gunakan menu **Insert** pada toolbar untuk menambahkan grafik ke kanvas dashboard.

---

### A. Kartu Skor
**Tujuan:** Menampilkan data utama seperti total penjualan, jumlah pesanan, dan total pelanggan.

**Langkah-langkah:**
1. Pilih **Insert → Scorecard**.  
2. Letakkan tiga kartu di bagian atas dashboard.  
3. Atur setiap kartu dengan:
   - **Total Sales:** `SUM(Sales)`  
   - **Total Orders:** `COUNT_DISTINCT(Order ID)`  
   - **Total Customers:** `COUNT_DISTINCT(Customer ID)`  
4. Gunakan warna kontras agar mudah dibaca (misalnya teks terang di latar gelap).

---

### B. Order by Region
**Tujuan:** Menunjukkan jumlah pesanan di setiap wilayah.

**Langkah-langkah:**
1. Pilih **Insert → Donut Chart**.  
2. Atur:
   - Dimensi: `Region`  
   - Metrik: `COUNT_DISTINCT(Order ID)`  
3. Atur warna, label dan legenda.   
4. Beri judul **Order by Region**.

---

### C. Order by Category
**Tujuan:** Membandingkan jumlah pesanan berdasarkan kategori produk.

**Langkah-langkah:**
1. Tambahkan **Donut Chart** kedua.  
2. Atur:
   - Dimensi: `Category`  
   - Metrik: `COUNT_DISTINCT(Order ID)`  
3. Atur warna, label dan legenda.  

---

### D. Order by City
**Tujuan:** Menampilkan jumlah pesanan berdasarkan kota.

**Langkah-langkah:**
1. Pilih **Insert → Bar Chart**.  
2. Atur:
   - Dimensi: `City`  
   - Metrik: `COUNT_DISTINCT(Order ID)`  
3. Aktifkan opsi urutkan menurun berdasarkan jumlah pesanan.  

---

### E. Order by Sub-Category
**Tujuan:** Menampilkan sub-kategori produk dengan jumlah pesanan tertinggi.

**Langkah-langkah:**
1. Pilih **Insert → Bar Chart (Horizontal)**.  
2. Atur:
   - Dimensi: `Sub-Category`  
   - Metrik: `COUNT_DISTINCT(Order ID)`  
3. Aktifkan opsi urutkan menurun untuk melihat urutan pesanan tertinggi.  

---

### F. Sales Trend
**Tujuan:** Menampilkan perkembangan penjualan dari waktu ke waktu.

**Langkah-langkah:**
1. Pilih **Insert → Line Chart**.  
2. Atur:
   - Dimensi: `Order Date`  
   - Metrik: `SUM(Sales)`  
3. Pada bagian rentang tanggal, pilih `Order Date`.  
4. Buat dua versi:
   - **Sales Trend (Yearly)** – tampilan per tahun  
   - **Sales Trend (Monthly)** – tampilan per bulan  
5. Beri warna garis yang jelas dan tambahkan label angka.

---

### G. Filter dan Kontrol Data
**Tujuan:** Memberi pengguna kemampuan untuk memilih data yang ingin ditampilkan.

**Langkah-langkah:**
1. Pilih **Add a Control → Dropdown List**.  
2. Tambahkan tiga kontrol utama:
   - `Year` berdasarkan `Order Date`  
   - `Category`  
   - `City`  
3. Letakkan kontrol di bagian atas dashboard agar mudah digunakan.

---

## 5. Menyimpan dan Berbagi Dashboard
1. Klik **File → Save (Simpan)** untuk menyimpan proyek.  
2. Untuk membagikan hasilnya:
   - Klik **Share → Copy Link (Bagikan → Salin Tautan)**, atau  
   - **Share with others (Bagikan dengan orang lain)** dan ubah izin menjadi *Viewer*.  
3. Pastikan dashboard sudah menampilkan seluruh grafik tanpa error.

---

## 6. Hasil Akhir
Dashboard *Superstore Sales Performance* akan menampilkan:
- Kartu skor total penjualan, pesanan, dan pelanggan.  
- Diagram donat per wilayah dan kategori.  
- Grafik batang per kota dan sub-kategori.  
- Grafik garis tren penjualan tahunan dan bulanan.  
- Filter interaktif untuk tahun, kategori, dan kota.

---

## 7. Catatan Jika Terjadi Error
Jika muncul pesan “Terjadi error sistem pada Looker Studio”, periksa hal berikut:
- Pastikan koneksi internet stabil.  
- Cek sumber data di menu **Resource → Manage Added Data Sources (Kelola Sumber Data Tambahan)**.  
- Pastikan tidak ada kolom dihapus atau diubah namanya di Google Sheets.

________________________________________
