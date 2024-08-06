---
sidebar_position: 2
---

# 4.2 Membuat aplikasi "Hello World"

### Penjelasan
Langkah pertama dalam memahami Express.js adalah dengan membuat aplikasi sederhana yang menampilkan pesan "Hello World" ketika diakses melalui browser.

**Langkah-Langkah:**

1.  **Inisialisasi Proyek:**
    
    -   Buat direktori baru untuk proyek kamu, lalu masuk ke direktori tersebut melalui terminal.
    -   Inisialisasi proyek Node.js dengan perintah berikut:
        
	     ```
        npm init -y
        ```
        
2.  **Instal Express.js:**
    
    -   Instal Express.js sebagai dependensi proyek dengan perintah:
        
        ```
        npm install express
        ``` 
        
3.  **Buat File Utama:**
    
    -   Buat file bernama `app.js` dalam direktori proyek. Ini akan menjadi file utama aplikasi kamu.
    
    **Contoh Kode:**
    

    ```
    const express = require('express');
    const app = express();
    const port = 3000;
    
    app.get('/', (req, res) => {
      res.send('Hello World!');
    });
    
    app.listen(port, () => {
      console.log(`Aplikasi berjalan di http://localhost:${port}`);
    });
    ``` 
    
    **Penjelasan:**
    
    -   `express` diimpor dan digunakan untuk membuat aplikasi Express.
    -   Aplikasi mendengarkan permintaan GET ke rute utama `'/'` dan mengirimkan respons dengan teks "Hello World!".
    -   Server kemudian dijalankan pada port 3000.
4.  **Jalankan Aplikasi:**
    
    -   Jalankan aplikasi dengan perintah berikut di terminal:
        
		```
        node app.js
        ```
        
    -   Buka browser dan pergi ke `http://localhost:3000` untuk melihat pesan "Hello World!".
        

### Kesimpulan
Membuat aplikasi "Hello World" adalah langkah pertama untuk memahami bagaimana Express.js bekerja, memberikan kamu gambaran dasar tentang bagaimana server dibuat dan bagaimana merespon permintaan dari klien.