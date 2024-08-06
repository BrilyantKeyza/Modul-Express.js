---
sidebar_position: 1
---

# 7.1  Membuat operasi CRUD (Create, Read, Update, Delete)

### Penjelasan
CRUD adalah singkatan dari Create, Read, Update, Delete, yang merupakan operasi dasar yang dilakukan pada data dalam aplikasi web. Dalam konteks Express.js, CRUD memungkinkan kita untuk mengelola data melalui API endpoints.

**Langkah-Langkah CRUD dengan Express.js:**

1.  **Setup Proyek:**
    
    -   Buat direktori baru untuk proyek kamu.
    -   Inisialisasi proyek dengan `npm init -y`.
    -   Instal Express.js:
        
        ```
        npm install express
        ```
        
2.  **Membuat Server Dasar:**
    
    -   Buat file `app.js` dan setup server dasar:
        
        ```
        const express = require('express');
        const app = express();
        const port = 3000;
        
        app.use(express.json());
        
        app.listen(port, () => {
          console.log(`Server berjalan di http://localhost:${port}`);
        });
        ``` 
        
3.  **Operasi Create (POST):**
    
    -   Tambahkan endpoint untuk membuat data baru:
        
     
        ```
        let items = [];
        
        app.post('/items', (req, res) => {
          const item = req.body;
          items.push(item);
          res.status(201).json(item);
        });
        ```
        
    
    **Penjelasan:**
    
    -   `req.body` berisi data yang dikirim oleh klien, yang kemudian ditambahkan ke array `items`.
    -   `res.status(201)` mengirimkan status `201 Created` sebagai tanda data berhasil disimpan.
4.  **Operasi Read (GET):**
    
    -   Tambahkan endpoint untuk membaca semua data:
        
   
        ```
        app.get('/items', (req, res) => {
          res.json(items);
        });
		```
        
    
    **Penjelasan:**
    
    -   `res.json(items)` mengembalikan semua data yang ada dalam array `items`.
5.  **Operasi Update (PUT):**
    
    -   Tambahkan endpoint untuk memperbarui data berdasarkan ID:
       
        ```
        app.put('/items/:id', (req, res) => {
          const id = parseInt(req.params.id);
          const updatedItem = req.body;
          items[id] = updatedItem;
          res.json(updatedItem);
        });
        ```
        
    
    **Penjelasan:**
    
    -   `req.params.id` digunakan untuk mendapatkan ID dari URL.
    -   Data di array `items` diperbarui dengan data baru yang dikirim oleh klien.
6.  **Operasi Delete (DELETE):**
    
    -   Tambahkan endpoint untuk menghapus data berdasarkan ID:
        
        ```
        app.delete('/items/:id', (req, res) => {
          const id = parseInt(req.params.id);
          items.splice(id, 1);
          res.status(204).send();
        });
        ```
        
    
    **Penjelasan:**
    
    -   Data dihapus dari array `items` berdasarkan ID yang dikirim dalam URL.
    -   Status `204 No Content` dikirim sebagai respons tanpa konten.

### Kesimpulan
 Dengan operasi CRUD dasar ini, kamu bisa mengelola data dalam aplikasi Express.js. Ini adalah pondasi dari aplikasi web atau API yang dinamis.