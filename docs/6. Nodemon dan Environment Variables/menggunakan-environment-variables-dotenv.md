---
sidebar_position: 2
---

# 6.2 Menggunakan environment variables (dotenv)

### Penjelasan
Environment variables adalah variabel yang digunakan untuk menyimpan konfigurasi yang dapat berubah-ubah tergantung pada lingkungan (development, testing, production). Misalnya, kamu bisa menyimpan URL database, API keys, atau port server dalam environment variables sehingga tidak perlu mengubah kode saat berpindah lingkungan.

**Mengapa Menggunakan Environment Variables?**

-   **Keamanan**: Informasi sensitif seperti API keys atau database credentials dapat disimpan dalam environment variables dan tidak langsung dalam kode sumber.
-   **Fleksibilitas**: Kamu bisa dengan mudah mengubah konfigurasi tanpa mengubah kode.

**Langkah-Langkah Menggunakan dotenv:**

1.  **Instal dotenv:**
    
    -   Instal dotenv sebagai dependensi proyek:
    
    ```
    npm install dotenv
    ```
    
2.  **Buat File `.env`:**
    
    -   Buat file `.env` di root direktori proyek kamu. Di dalam file ini, kamu bisa mendefinisikan environment variables.
    -   Contoh isi `.env`:
    
    ```
    PORT=3000
    DATABASE_URL=mongodb://localhost:27017/mydatabase
    ```
    
3.  **Menggunakan Environment Variables di Kode:**
    
    -   Di file utama proyek kamu (misalnya, `app.js`), import dan konfigurasikan dotenv:
    
    
    ```
    require('dotenv').config();
    
    const port = process.env.PORT || 3000;
    const dbUrl = process.env.DATABASE_URL;
    
    app.listen(port, () => {
      console.log(`Server berjalan di port ${port}`);
    });
    ```
    
    -   Dengan ini, kamu bisa mengakses nilai dari environment variables menggunakan `process.env.VARIABLE_NAME`.

### Kesimpulan 
Menggunakan environment variables dengan bantuan dotenv membuat aplikasi kamu lebih aman dan mudah dikonfigurasi untuk berbagai lingkungan. Ini juga memungkinkan kamu untuk menyimpan informasi sensitif di luar kode sumber dan menyesuaikan konfigurasi dengan mudah.