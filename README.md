# Dokumentasi Program Manajemen Toko Beras

## Deskripsi Umum

Program ini dirancang untuk membantu pemilik toko beras dalam mengelola stok barang, mencatat transaksi penjualan, dan menyediakan fitur pencarian untuk memudahkan pengelolaan data. Program ini menggunakan database Firebase untuk penyimpanan data yang aman dan terstruktur.

## Stack Teknologi

*   **Python:** Bahasa pemrograman utama yang digunakan untuk logika program dan interaksi dengan database.
*   **Firebase (Firestore):** Database NoSQL berbasis cloud yang digunakan untuk menyimpan data barang dan transaksi. Firestore memungkinkan penyimpanan data secara real-time dan terstruktur dalam bentuk koleksi dan dokumen.
*   **firebase-admin:** Library Python yang menyediakan akses administratif ke Firebase, termasuk operasi seperti otentikasi, membaca dan menulis data.
*   **pandas:** Library Python yang kuat untuk manipulasi dan analisis data. Pandas digunakan untuk mengelola data dalam bentuk DataFrame, memudahkan dalam menampilkan data dalam bentuk tabel, filtering, dan operasi lainnya.

## Bentuk Database (Firebase)

*   **Collection 'barang':**
    *   Setiap dokumen mewakili satu jenis beras.
    *   Fields:
        *   nama: Nama beras (string, primary key).
        *   ukuran: Ukuran beras dalam kilogram (integer).
        *   harga: Harga beras per kilogram (integer).
        *   stok: Jumlah stok beras yang tersedia (integer).
*   **Collection 'transaksi':**
    *   Setiap dokumen mewakili satu transaksi penjualan.
    *   Fields:
        *   nama_pelanggan: Nama pelanggan (string).
        *   tanggal: Tanggal transaksi (timestamp).
        *   nama_beras: Nama beras yang dibeli (string).
        *   ukuran: Ukuran beras yang dibeli (integer).
        *   jumlah: Jumlah beras yang dibeli (integer).
        *   keterangan: Informasi tambahan mengenai transaksi (string, opsional).
        *   total_harga: Total harga transaksi termasuk pajak (float).
        *   keterangan_pajak: Rincian perhitungan pajak (string).

## Flowchart Program

+-------------------+
| Mulai Program |
+-------------------+
|
v
+-------------------+
| Tampilkan Menu |
+-------------------+
|
v
+-------------------+
| Terima Input |
+-------------------+
|
v
|
+------------+ Pilihan 1: Tambah Barang
| |
| +-----------------+
| | Input Data |
| | Barang |
| +-----------------+
| |
| +-----------------+
| | Simpan ke |
| | Firebase |
| +-----------------+
| |
+------------+
|
+------------+ Pilihan 2: Tambah Transaksi
| |
| +-----------------+
| | Input Data |
| | Transaksi |
| +-----------------+
| |
| +-----------------+
| | Validasi Stok |
| +-----------------+
| |
| +-----------------+
| | Hitung Harga |
| +-----------------+
| |
| +-----------------+
| | Simpan ke |
| | Firebase |
| +-----------------+
| |
+------------+
|
+------------+ Pilihan 3: Tampilkan Barang
| |
| +-----------------+
| | Ambil Data |
| | dari Firebase |
| +-----------------+
| |
| +-----------------+
| | Tampilkan |
| | Daftar Barang |
| +-----------------+
| |
+------------+
|
+------------+ Pilihan 4: Tampilkan Transaksi
| |
| +-----------------+
| | Ambil Data |
| | dari Firebase |
| +-----------------+
| |
| +-----------------+
| | Tampilkan |
| | Daftar Transaksi|
| +-----------------+
| |
+------------+
|
+------------+ Pilihan 5: Cari Barang/Transaksi
| |
| +-----------------+
| | Input Kata Kunci|
| +-----------------+
| |
| +-----------------+
| | Cari di |
| | Firebase |
| +-----------------+
| |
| +-----------------+
| | Tampilkan |
| | Hasil |
| +-----------------+
| |
+------------+
|
v
+-------------------+
| Kembali ke Menu |
+-------------------+

## Penjelasan Flowchart

1.  **Mulai Program:** Program dimulai.
2.  **Tampilkan Menu:** Menu pilihan ditampilkan kepada pengguna.
3.  **Terima Input:** Program menunggu input pilihan dari pengguna.
4.  **Proses Input:**
    *   **Pilihan 1 (Tambah Barang):**
        *   Input data barang dari pengguna.
        *   Simpan data barang ke Firebase.
    *   **Pilihan 2 (Tambah Transaksi):**
        *   Input data transaksi dari pengguna.
        *   Validasi stok beras yang tersedia.
        *   Hitung total harga termasuk pajak.
        *   Simpan data transaksi ke Firebase.
    *   **Pilihan 3 (Tampilkan Barang):**
        *   Ambil data barang dari Firebase.
        *   Tampilkan daftar barang dalam bentuk tabel.
    *   **Pilihan 4 (Tampilkan Transaksi):**
        *   Ambil data transaksi dari Firebase.
        *   Tampilkan daftar transaksi dalam bentuk tabel.
    *   **Pilihan 5 (Cari Barang/Transaksi):**
        *   Input kata kunci dari pengguna.
        *   Cari barang dan transaksi yang sesuai di Firebase.
        *   Tampilkan hasil pencarian.
5.  **Kembali ke Menu:** Kembali ke tampilan menu utama.

## Panduan Penggunaan untuk Awam

1.  **Prasyarat:**
    *   **Akun Google Cloud Platform (GCP):** Anda perlu memiliki akun GCP untuk menggunakan Firebase. Jika belum punya, buat akun gratis di https://console.cloud.google.com/.
    *   **Project Firebase:** Buat project baru di Firebase console (https://console.firebase.google.com/).
    *   **Firestore Database:** Aktifkan Firestore Database dalam project Firebase Anda.
    *   **Kunci Layanan (Service Account Key):**
        *   Di Firebase console, masuk ke "Project settings".
        *   Pada tab "Service accounts", buat kunci layanan baru.
        *   Unduh kunci layanan ini dalam format JSON. Ini adalah private key Anda.
    *   **Google Colaboratory atau Jupyter Notebook:** Pastikan Anda memiliki akses ke lingkungan ini untuk menjalankan kode Python.
2.  **Instalasi Library:**
    *   Buka Google Colaboratory atau Jupyter Notebook.
    *   Pastikan library yang diperlukan sudah terinstall. Jika belum, jalankan perintah berikut di awal notebook:

    ```bash
    !pip install firebase-admin pandas
    ```

3.  **Unggah Private Key:**
    *   Unggah file JSON private key yang Anda unduh tadi ke direktori yang sama dengan notebook Anda.
    *   Di dalam kode Python, ganti `/content/latihanujikom-85ee2-firebaseadminsdk-400lb-7d5f95374f.json` dengan path lengkap ke file private key Anda.
4.  **Menjalankan Program:**
    *   Jalankan semua sel kode di notebook secara berurutan.
    *   Program akan menampilkan menu pilihan.
    *   Ikuti petunjuk di menu untuk menambahkan data barang, transaksi, menampilkan data, atau mencari data.

## Penjelasan Tambahan

*   **Private Key:** Kunci layanan ini adalah rahasia dan memberikan akses penuh ke database Firebase Anda. Jangan pernah membagikannya secara publik.
*   **Google Colaboratory:** Jika Anda menggunakan Google Colaboratory, Anda dapat mengunggah file JSON private key langsung ke lingkungan Colab.
*   **Koneksi Internet:** Pastikan Anda memiliki koneksi internet yang stabil saat menjalankan program, karena program ini berinteraksi dengan database Firebase yang berada di cloud.

**Penting:**

*   Kode ini ditujukan untuk tujuan pembelajaran dan demonstrasi. Dalam aplikasi nyata, penting untuk menambahkan penanganan error yang lebih baik dan fitur keamanan yang lebih ketat (misalnya, otentikasi pengguna) sebelum menggunakannya dalam produksi.