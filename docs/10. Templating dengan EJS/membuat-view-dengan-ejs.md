---
sidebar_position: 2
---

# 10.2 Membuat view dengan EJS

### Penjelasan
Dalam Express.js, kamu bisa menggunakan EJS untuk merender view yang dihasilkan dari data yang dikirimkan oleh controller. View adalah bagian dari aplikasi yang bertanggung jawab untuk menampilkan data kepada pengguna.

**Langkah-Langkah:**

1.  **Setup Express.js untuk Menggunakan EJS:**
    
    -   Instal EJS melalui npm:
        
        ```
        npm install ejs
        ```
        
    -   Di `app.js`, atur view engine menjadi EJS:
        
        ```
        const express = require('express');
        const app = express();
        
        app.set('view engine', 'ejs');
        
        app.listen(3000, () => {
          console.log('Server berjalan di http://localhost:3000');
        });
        ```
        
2.  **Membuat File Template EJS:**
    
    -   Buat direktori `views` di dalam proyek, dan di dalamnya buat file `index.ejs`.
    -   Contoh `index.ejs`:
        
        ```
        <!DOCTYPE html>
        <html>
        <head>
            <title>Halaman Utama</title>
        </head>
        <body>
            <h1>Selamat Datang di Halaman Utama!</h1>
            <p>Nama: <%= name %></p>
            <ul>
              <% items.forEach(item => { %>
                <li><%= item %></li>
              <% }) %>
            </ul>
        </body>
        </html>
        ```
        
3.  **Mengirim Data dari Route ke View:**
    
    -   Di `app.js`, buat rute yang merender view dengan data:

        ```
        app.get('/', (req, res) => {
          const name = 'ChatGPT';
          const items = ['Apel', 'Jeruk', 'Mangga'];
          res.render('index', { name, items });
        });
        ```
        
    
    **Penjelasan:**
    
    -   `res.render()` digunakan untuk merender file EJS dan mengirimkan data yang akan disisipkan ke dalam template.
4.  **Menjalankan Aplikasi:**
    
    -   Jalankan server dengan perintah:
        
        ```
        node app.js
        ```
        
    -   Akses `http://localhost:3000` di browser untuk melihat hasilnya.

### Kesimpulan
Dengan EJS, kamu bisa membuat halaman web yang dinamis dan interaktif. EJS memudahkan proses integrasi data dari backend dengan template HTML, sehingga kamu bisa menghasilkan tampilan yang lebih kaya dan fungsional.