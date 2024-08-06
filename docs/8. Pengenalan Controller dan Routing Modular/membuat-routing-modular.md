---
sidebar_position: 2
---

# 8.2 Membuat routing modular

### Penjelasan
Routing modular adalah pendekatan untuk mengatur routes dalam file terpisah berdasarkan fungsionalitasnya. Ini membantu menjaga file `app.js` tetap bersih dan mempermudah manajemen rute.

**Langkah-Langkah:**

1.  **Setup Struktur Routing Modular:**
    
    -   Pisahkan rute berdasarkan fitur atau resource yang berbeda. Misalnya, buat file rute untuk `items`, `users`, dll.
    
    Struktur direktori:
    
    ```
    /project
      /routes
        itemRoutes.js
        userRoutes.js
      app.js
      ```
    
2.  **Membuat Route untuk Fitur Tertentu:**
    
    -   Di `itemRoutes.js` dan `userRoutes.js`, definisikan routes untuk fitur masing-masing.
    
    **Contoh `userRoutes.js`:**
    
    ```
    // routes/userRoutes.js
    const express = require('express');
    const router = express.Router();
    const userController = require('../controllers/userController');
    
    router.get('/users', userController.getAllUsers);
    router.post('/users', userController.createUser);
    
    module.exports = router;
    ``` 
    
3.  **Mengimpor dan Menggunakan Routes Modular di Aplikasi:**
    
    -   Di `app.js`, impor semua route dan gunakan sebagai middleware.
    
    **Contoh `app.js`:**
    
    ```
    const express = require('express');
    const app = express();
    const itemRoutes = require('./routes/itemRoutes');
    const userRoutes = require('./routes/userRoutes');
    
    app.use(express.json());
    
    app.use('/api/items', itemRoutes);
    app.use('/api/users', userRoutes);
    
    app.listen(3000, () => {
      console.log('Server berjalan di http://localhost:3000');
    });
    ``` 
    

### Kesimpulan
 Routing modular memudahkan pengelolaan rute dengan memisahkan definisi rute ke dalam file terpisah sesuai dengan fitur atau resource. Ini membuat kode lebih terstruktur dan lebih mudah untuk dikelola seiring berkembangnya aplikasi.