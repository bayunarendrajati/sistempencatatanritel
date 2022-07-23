# SISTEM PENCATATAN

Sistem ini berbasis web yang dikembangkan dengan platform Google Apps Script
Untuk melakukan implementasi, ikuti langkah berikut:

## 1. Buat project Apps Script baru
Buka https://script.google.com/home kemudian klik **Project baru**.

Salin file ```Code.gs```, ```main.html```, ```stylesheet.html```, ```dan script.html```.

## 2. Buat file spreadsheet baru untuk dataset
Buka https://docs.google.com/spreadsheets/u/0/ dan buat spreadsheet dengan klik tombol ```+```.

Kemudian klik **File** > **Impor** dan unggah file ```Evaluasi Penjualan dan Pembelian Toko.xlsx``` pada folder ```Sample dataset toko```

## 3. Hubungkan spreadsheet dengan sistem pencatatan
Klik **Bagikan** pada file spreadsheet, atur hak akses sesuai keperluan dan dapatkan url.

Buka project Apps Script yang telah dibuat, buka file ```Code.gs```.

Salin url kedalam variabel url pada file ```Code.gs``` (Deklarasi variabel terdapat pada baris nomor 1).

Selanjutnya simpan perubahan.

## 4. Menerapkan sistem pencatatan

Pada project Apps Script, pilih **Deployment** dan pilih **New Deployment**

Berikan deskripsi, dan atur hak akses sesuai keperluan. Klik **Terapkan**

Sistem sudah dapat diakses dengan membuka url yang disediakan oleh Apps Script.

Sistem juga dapat disematkan dengan menggunakan ```HTML iFrame``` atau **Google Sites**


## Catatan

Repository sistem pencatatan dapat diakses pada 
