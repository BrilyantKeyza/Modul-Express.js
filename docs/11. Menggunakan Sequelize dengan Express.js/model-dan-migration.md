---
sidebar_position: 2
---

# 11.2 Model dan migration

### Penjelasan
Model di Sequelize merepresentasikan tabel di database. Setiap model berkorespondensi dengan sebuah tabel dan setiap instance dari model berkorespondensi dengan sebuah baris dalam tabel. Migration adalah skrip yang memungkinkan kamu untuk melacak perubahan struktur database secara versioned.

**Langkah-Langkah:**

1.  **Membuat Model:**
    
    -   Definisikan model untuk tabel. Misalnya, model `User`:
        

        ```
        const { DataTypes } = require('sequelize');
        const sequelize = require('../config/sequelize');
        
        const User = sequelize.define('User', {
          username: {
            type: DataTypes.STRING,
            allowNull: false,
            unique: true
          },
          email: {
            type: DataTypes.STRING,
            allowNull: false,
            unique: true
          },
          password: {
            type: DataTypes.STRING,
            allowNull: false
          }
        });
        
        module.exports = User;
        ```
        
2.  **Menggunakan Migration:**
    
    -   Sequelize memiliki CLI untuk membuat migration. Instal CLI terlebih dahulu:
        
        ```
        npm install --save-dev sequelize-cli
        ```
        
    -   Inisialisasi Sequelize di proyek:
        
        ```
        npx sequelize-cli init
        ``` 
        
    -   Buat migration untuk model `User`:
        
        ```
        npx sequelize-cli model:generate --name User --attributes username:string,email:string,password:string
        ```
        
    -   Jalankan migration untuk memperbarui database:
        
        ```
        npx sequelize-cli db:migrate
        ```
        

### Kesimpulan
Model di Sequelize memungkinkan kamu untuk mengelola tabel di database dengan kode JavaScript. Migration membantu melacak perubahan pada struktur database dan menjaga konsistensi database selama pengembangan.