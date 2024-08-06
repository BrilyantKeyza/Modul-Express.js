---
sidebar_position: 1
---

# 11.1 Instalasi dan konfigurasi Sequelize

### Penjelasan
Sequelize adalah ORM yang mendukung berbagai jenis database, seperti PostgreSQL, MySQL, SQLite, dan lainnya. Dengan Sequelize, kamu bisa mengelola database menggunakan model JavaScript yang merepresentasikan tabel di database.

**Langkah-Langkah:**

1.  **Instalasi Sequelize dan Driver Database:**
    
    -   Instal Sequelize dan driver untuk database yang akan kamu gunakan (misalnya MySQL):
        
        ```
        npm install sequelize
        npm install mysql2
        ``` 
        
2.  **Konfigurasi Sequelize:**
    
    -   Buat file konfigurasi `sequelize.js` untuk mengatur koneksi ke database:
        
        ```
        const { Sequelize } = require('sequelize');
        
        const sequelize = new Sequelize('nama_database', 'username', 'password', {
          host: 'localhost',
          dialect: 'mysql' // atau 'postgres', 'sqlite', dll.
        });
        
        sequelize.authenticate()
          .then(() => {
            console.log('Koneksi berhasil.');
          })
          .catch(err => {
            console.error('Koneksi gagal:', err);
          });
        
        module.exports = sequelize;
        ```
        
3.  **Menghubungkan Sequelize dengan Express:**
    
    -   Impor dan gunakan `sequelize.js` dalam `app.js`:
        
        ```
        const express = require('express');
        const sequelize = require('./config/sequelize');
        const app = express();
        
        app.use(express.json());
        
        // Routes dan logika lainnya
        
        app.listen(3000, () => {
          console.log('Server berjalan di http://localhost:3000');
        });
        ```
        

### Kesimpulan
 Instalasi dan konfigurasi Sequelize memberikan dasar untuk mengelola database dalam aplikasi Express.js. Dengan setup ini, kamu siap untuk mulai mendefinisikan model dan melakukan operasi database.