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
        **Penjelasan:**
        
        -   `Item` adalah model yang akan digunakan untuk berinteraksi dengan tabel `Items` di MySQL.
        -   `name` dan `price` adalah kolom dalam tabel.
4.   **Mengubah Operasi CRUD untuk MySQL:**
    
      -   **Contoh Operasi Create:**
          

          ```
          app.post('/items', async (req, res) => {
            try {
              const item = await Item.create(req.body);
              res.status(201).json(item);
            } catch (error) {
              res.status(400).send(error);
            }
          });
          ``` 
          
      -   **Contoh Operasi Read:**
          
          ```
          app.get('/items', async (req, res) => {
            try {
              const items = await Item.findAll();
              res.json(items);
            } catch (error) {
              res.status(500).send(error);
            }
          });
          ``` 
          
      -   **Contoh Operasi Update:**
          
  
          ```
          app.put('/items/:id', async (req, res) => {
            try {
              const [updated] = await Item.update(req.body, {
                where: { id: req.params.id }
              });
              if (updated) {
                const updatedItem = await Item.findByPk(req.params.id);
                res.json(updatedItem);
              } else {
                res.status(404).send('Item tidak ditemukan');
              }
            } catch (error) {
              res.status(400).send(error);
            }
          });
          ```
          
      -   **Contoh Operasi Delete:**
          
          ```
          app.delete('/items/:id', async (req, res) => {
            try {
              const deleted = await Item.destroy({
                where: { id: req.params.id }
              });
              if (deleted) {
                res.status(204).send();
              } else {
                res.status(404).send('Item tidak ditemukan');
              }
            } catch (error) {
              res.status(500).send(error);
            }
          });
          ```
  5. **Menjalankan Aplikasi**

      Jalankan perintah berikut di terminal untuk memulai aplikasi:

      ```
      node app.js
      ```

      Buka browser dan akses `http://localhost:3000` untuk melihat aplikasi berjalan.

### Kesimpulan
Dengan menghubungkan aplikasi Express.js ke database seperti MongoDB atau MySQL, kamu bisa menyimpan dan mengelola data secara permanen. Ini memungkinkan pengembangan aplikasi yang lebih kompleks dan dinamis.