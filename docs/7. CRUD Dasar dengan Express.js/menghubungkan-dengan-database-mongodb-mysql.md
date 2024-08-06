---
sidebar_position: 2
---

# 7.2 Menghubungkan dengan database (MongoDB/MySQL)

### Penjelasan
Untuk menyimpan data secara permanen, kamu perlu menghubungkan aplikasi dengan database. Dalam modul ini, kita akan membahas cara menghubungkan Express.js dengan MongoDB atau MySQL.

**A. Menggunakan MongoDB:**

1.  **Instalasi Mongoose:**
    
    -   Mongoose adalah ODM (Object Data Modeling) yang digunakan untuk bekerja dengan MongoDB dalam Node.js.
    
    ```
    npm install mongoose
    ```
    
2.  **Menghubungkan ke MongoDB:**
    
    -   Di `app.js`, tambahkan kode untuk menghubungkan ke database MongoDB:
        
        ```
        const mongoose = require('mongoose');
        
        mongoose.connect('mongodb://localhost:27017/mydatabase', {
          useNewUrlParser: true,
          useUnifiedTopology: true
        });
        
        const db = mongoose.connection;
        db.on('error', console.error.bind(console, 'connection error:'));
        db.once('open', () => {
          console.log('Terhubung ke MongoDB');
        });
        ```
        
3.  **Membuat Model untuk Data:**
    
    -   Definisikan schema dan model untuk data yang akan disimpan:
        
   
        ```
        const itemSchema = new mongoose.Schema({
          name: String,
          price: Number
        });
        
        const Item = mongoose.model('Item', itemSchema);
        ```
        
4.  **Mengubah Operasi CRUD untuk MongoDB:**
    
    -   Sesuaikan operasi CRUD sebelumnya untuk bekerja dengan MongoDB menggunakan Mongoose.

**B. Menggunakan MySQL:**

1.  **Instalasi Sequelize:**
    
    -   Sequelize adalah ORM (Object Relational Mapping) untuk bekerja dengan database SQL seperti MySQL.
    
    ```
    npm install sequelize mysql2
    ```
    
2.  **Menghubungkan ke MySQL:**
    
    -   Di `app.js`, tambahkan kode untuk menghubungkan ke database MySQL:
        

        ```
        const { Sequelize, DataTypes } = require('sequelize');
        const sequelize = new Sequelize('database', 'username', 'password', {
          host: 'localhost',
          dialect: 'mysql'
        });
        
        sequelize.authenticate()
          .then(() => console.log('Terhubung ke MySQL'))
          .catch(err => console.error('Gagal terhubung ke MySQL:', err));
          ```
        
3.  **Membuat Model untuk Data:**
    
    -   Definisikan model untuk data yang akan disimpan:
   
        ```
        const Item = sequelize.define('Item', {
          name: {
            type: DataTypes.STRING,
            allowNull: false
          },
          price: {
            type: DataTypes.INTEGER,
            allowNull: false
          }
        });
        ``` 
        
4.  **Mengubah Operasi CRUD untuk MySQL:**
    
    -   Sesuaikan operasi CRUD sebelumnya untuk bekerja dengan MySQL menggunakan Sequelize.

### Kesimpulan
Dengan menghubungkan aplikasi Express.js ke database seperti MongoDB atau MySQL, kamu bisa menyimpan dan mengelola data secara permanen. Ini memungkinkan pengembangan aplikasi yang lebih kompleks dan dinamis.