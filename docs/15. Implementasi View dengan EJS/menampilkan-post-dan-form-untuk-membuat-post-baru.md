---
sidebar_position: 2
---

# 15.2 Menampilkan post dan form untuk membuat post baru

### Penjelasan
Halaman utama aplikasi akan menampilkan semua post yang ada, serta menyediakan form bagi user untuk membuat post baru.

**Langkah-Langkah:**

1.  **Mengirim Data ke View dari Controller:**
    
    -   Pastikan controller untuk halaman utama mengirim data post yang dibutuhkan oleh view.
    
    **Contoh Controller:**
    
    ```
    const Post = require('../models/Post');
    const User = require('../models/User');
    
    // Controller untuk halaman utama
    exports.getHomePage = async (req, res) => {
        try {
            const posts = await Post.findAll({ include: User });
            res.render('index', { user: req.user, posts });
        } catch (error) {
            res.status(500).send('Terjadi kesalahan pada server');
        }
    };
    ```
    
2.  **Menampilkan Data di View:**
    
    -   Di file `index.ejs`, kita sudah menyiapkan kode untuk menampilkan semua post yang dikirim dari controller.
3.  **Menangani Form untuk Membuat Post Baru:**
    
    -   Form yang ada di `index.ejs` mengirim data ke route `POST /posts`. Pastikan route tersebut sudah diatur untuk menerima data dan membuat post baru.
    
    **Contoh Route:**
    
    ```
    const express = require('express');
    const router = express.Router();
    const { getHomePage, createPost } = require('../controllers/homeController');
    const authenticateJWT = require('../middleware/authenticateJWT');
    
    router.get('/', authenticateJWT, getHomePage);
    router.post('/posts', authenticateJWT, createPost);
    
    module.exports = router;
    ```
    

### Kesimpulan
 Dengan menampilkan post dan form untuk membuat post baru di halaman utama, kamu menyediakan cara bagi user untuk berinteraksi dengan konten dalam aplikasi. Hal ini penting untuk aplikasi media sosial di mana user-generated content adalah inti dari aplikasi tersebut.