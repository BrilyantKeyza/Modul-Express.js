---
sidebar_position: 1
---

# 14.1 Menggunakan middleware untuk proteksi rute

### Penjelasan
Pada tahap ini, kita akan menggabungkan semua endpoint yang telah dibuat sebelumnya—seperti registrasi user, login, pembuatan post, pemberian like, dan lainnya—ke dalam satu aplikasi Express.js. Ini akan menciptakan API yang lengkap untuk aplikasi media sosial.

**Langkah-Langkah:**

1.  **Struktur Dasar Aplikasi:**
    
    -   Pastikan semua model (`User`, `Post`, `Like`) dan relasi antar model sudah diatur.
    -   Buat file `routes.js` yang mengatur semua route.
    
    **Contoh Struktur Folder:**
    ```
    /models
     - User.js
     - Post.js
     - Like.js
    /routes
     - index.js
    /middleware
     - authenticateJWT.js
    app.js
    ```
    
2.  **Mengatur Routes di `routes/index.js`:**
    
    -   Gabungkan semua endpoint ke dalam satu file routes.
    
    **Contoh Routes:**
    
    ```
    const express = require('express');
    const router = express.Router();
    const authenticateJWT = require('../middleware/authenticateJWT');
    const { register, login, createPost, likePost, deletePost, getPosts } = require('../controllers');
    
    // User Routes
    router.post('/register', register);
    router.post('/login', login);
    
    // Post Routes
    router.post('/posts', authenticateJWT, createPost);
    router.get('/posts', getPosts);
    router.delete('/posts/:id', authenticateJWT, deletePost);
    
    // Like Routes
    router.post('/posts/:postId/like', authenticateJWT, likePost);
    
    module.exports = router;
    ```
    
3.  **Menggabungkan Routes ke `app.js`:**
    
    -   Pastikan semua routes terintegrasi di `app.js`.
    
    **Contoh Integrasi di `app.js`:**

    ```
    const express = require('express');
    const app = express();
    const routes = require('./routes');
    
    app.use(express.json());
    app.use('/api', routes);
    
    const PORT = process.env.PORT || 3000;
    app.listen(PORT, () => {
      console.log(`Server berjalan di port ${PORT}`);
    });
    ```
    

### Kesimpulan
 Pada tahap ini, kamu telah menggabungkan semua endpoint ke dalam satu aplikasi Express.js yang berfungsi penuh, yang memungkinkan user untuk mendaftar, login, membuat post, dan memberi like.