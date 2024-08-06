---
sidebar_position: 1
---

# 6.1 Instalasi dan penggunaan Nodemon

### Penjelasan
Nodemon adalah alat yang memantau perubahan file di proyek Node.js kamu dan secara otomatis me-restart server saat ada perubahan. Ini sangat membantu dalam pengembangan karena kamu tidak perlu secara manual menghentikan dan memulai ulang server setiap kali melakukan perubahan.

**Langkah-Langkah Instalasi dan Penggunaan:**

1.  **Instal Nodemon:**
    
    -   Instal Nodemon secara global atau sebagai dependensi pengembangan di proyek kamu.
    
    **Instalasi Global:**
    
    ```
    npm install -g nodemon
    ```
    
    **Instalasi Lokal (di dalam proyek):**
    
    ```
    npm install nodemon --save-dev
    ```
    
2.  **Menjalankan Aplikasi dengan Nodemon:**
    
    -   Alih-alih menggunakan perintah `node app.js` untuk menjalankan aplikasi, kamu bisa menggunakan perintah berikut:
    
    
    ```
    nodemon app.js
    ```
    
    -   Nodemon akan secara otomatis memantau perubahan dalam file `app.js` atau file lain yang terkait, dan me-restart server jika ada perubahan.
3.  **Konfigurasi Nodemon (Opsional):**
    
    -   Kamu bisa membuat file konfigurasi untuk Nodemon bernama `nodemon.json` untuk mengatur berbagai opsi seperti extensi file yang dipantau, delay sebelum restart, dan lainnya.
    -   Contoh `nodemon.json`:
    
    ```
    {
      "watch": ["app.js", "routes/"],
      "ext": "js json"
    }
    ```
    

### Kesimpulan
 Nodemon adalah alat yang sangat berguna selama pengembangan, yang menghemat waktu dengan me-restart server secara otomatis setiap kali kamu membuat perubahan pada kode.