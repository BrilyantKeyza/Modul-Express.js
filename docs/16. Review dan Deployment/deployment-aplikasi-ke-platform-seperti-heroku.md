---
sidebar_position: 2
---

# 16.2 Deployment aplikasi ke platform seperti Heroku

### Penjelasan
Heroku adalah platform cloud yang memungkinkan kamu untuk melakukan deployment aplikasi web dengan mudah. Kamu akan belajar cara mempersiapkan aplikasi untuk deployment dan bagaimana mengatur aplikasi di Heroku.

**Langkah-Langkah:**

1.  **Menyiapkan Aplikasi untuk Deployment:**
    
    -   **Environment Variables:** Pastikan variabel lingkungan seperti `DATABASE_URL`, `JWT_SECRET`, dan `NODE_ENV` diatur dengan benar di Heroku.
    -   **Procfile:** Buat file `Procfile` di root proyek untuk menentukan perintah yang dijalankan Heroku.
    
    **Contoh `Procfile`:**
    
    ```
    web: node app.js
    ```
    
    -   **Dependencies:** Pastikan semua dependensi terdaftar di `package.json`.
2.  **Membuat dan Menghubungkan ke Heroku:**
    
    -   Buat akun di [Heroku](https://www.heroku.com) dan instal Heroku CLI.
    -   Buat aplikasi baru di Heroku melalui CLI.
    
    **Contoh Perintah:**
    
    ```
    heroku create nama-aplikasi-kamu
    ```
    
3.  **Deploy Aplikasi:**
    
    -   **Push Aplikasi ke Heroku:**
        
        -   Pastikan semua perubahan sudah di-commit ke Git.
        -   Deploy aplikasi ke Heroku dengan perintah:
        

        ```
        git push heroku main
        ```
        
    -   **Mengatur Environment Variables di Heroku:**
        
        -   Gunakan perintah berikut untuk mengatur variabel lingkungan:
        

        ```
        heroku config:set NAMA_VARIABLE=nilai_variable
        ``` 
        
4.  **Mengecek Aplikasi:**
    
    -   Setelah deployment, buka aplikasi di browser menggunakan URL yang diberikan oleh Heroku.
    -   Cek apakah semua fitur berjalan dengan baik di lingkungan produksi.

### Kesimpulan
 Deployment ke Heroku memastikan bahwa aplikasi kamu dapat diakses oleh pengguna di seluruh dunia. Ini juga memperkenalkan kamu pada proses deployment di dunia nyata.