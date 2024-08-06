---
sidebar_position: 1
---

# 8.1 Memisahkan logika ke dalam controller

### Penjelasan
Controller adalah komponen dalam arsitektur aplikasi yang menangani logika bisnis. Dengan memisahkan logika ke dalam controller, kamu dapat menjaga kode lebih terstruktur dan mudah dikelola, serta memudahkan pemeliharaan dan pengujian.

**Langkah-Langkah:**

1.  **Setup Struktur Proyek:**
    
    -   Buat struktur direktori untuk memisahkan file controller dan routes.
    
    ```
    /project
      /controllers
        itemController.js
      /routes
        itemRoutes.js
      app.js
      ```
    
2.  **Membuat Controller:**
    
    -   Buat file `itemController.js` di direktori `controllers`.
    -   Definisikan fungsi untuk menangani logika bisnis.
    
    **Contoh `itemController.js`:**
    
    ```
    // controllers/itemController.js
    const Item = require('../models/itemModel'); // Import model
    
    // Fungsi untuk mendapatkan semua item
    exports.getAllItems = async (req, res) => {
      try {
        const items = await Item.find();
        res.json(items);
      } catch (error) {
        res.status(500).json({ message: error.message });
      }
    };
    
    // Fungsi untuk membuat item baru
    exports.createItem = async (req, res) => {
      const item = new Item(req.body);
      try {
        const newItem = await item.save();
        res.status(201).json(newItem);
      } catch (error) {
        res.status(400).json({ message: error.message });
      }
    };
    
    // Fungsi untuk memperbarui item
    exports.updateItem = async (req, res) => {
      try {
        const item = await Item.findByIdAndUpdate(req.params.id, req.body, { new: true });
        if (!item) return res.status(404).json({ message: 'Item tidak ditemukan' });
        res.json(item);
      } catch (error) {
        res.status(400).json({ message: error.message });
      }
    };
    
    // Fungsi untuk menghapus item
    exports.deleteItem = async (req, res) => {
      try {
        const item = await Item.findByIdAndDelete(req.params.id);
        if (!item) return res.status(404).json({ message: 'Item tidak ditemukan' });
        res.status(204).send();
      } catch (error) {
        res.status(500).json({ message: error.message });
      }
    };
    ``` 
    
3.  **Menghubungkan Controller dengan Route:**
    
    -   Di file route (`itemRoutes.js`), gunakan controller untuk menangani request.
    
    **Contoh `itemRoutes.js`:**
    
    ```
    // routes/itemRoutes.js
    const express = require('express');
    const router = express.Router();
    const itemController = require('../controllers/itemController');
    
    router.get('/items', itemController.getAllItems);
    router.post('/items', itemController.createItem);
    router.put('/items/:id', itemController.updateItem);
    router.delete('/items/:id', itemController.deleteItem);
    
    module.exports = router;
    ```
    
4.  **Menghubungkan Routes dengan Aplikasi:**
    
    -   Di `app.js`, impor dan gunakan routes yang telah dibuat.
    
    **Contoh `app.js`:**
    
    ```
    const express = require('express');
    const app = express();
    const itemRoutes = require('./routes/itemRoutes');
    
    app.use(express.json());
    
    app.use('/api', itemRoutes);
    
    app.listen(3000, () => {
      console.log('Server berjalan di http://localhost:3000');
    });
    ```
    

### Kesimpulan
 Memisahkan logika ke dalam controller membuat aplikasi lebih terstruktur dan memudahkan pemeliharaan. Controller menangani logika bisnis, sementara route mengatur endpoint dan menghubungkan controller
