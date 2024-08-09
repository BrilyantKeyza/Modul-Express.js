---
sidebar_position: 3
---

# 12.3 Implementasi JWT untuk otentikasi

### Penjelasan
JWT (JSON Web Token) adalah standar yang digunakan untuk membuat token yang dapat dikirimkan ke client setelah proses login. Token ini digunakan untuk memverifikasi identitas user pada request berikutnya.

**Langkah-Langkah:**

1.  **Instal JWT:**
    
    -   Instal `jsonwebtoken` melalui npm:
        
        ```
        npm install jsonwebtoken
        ```
        

2.  **Buat JWT saat Login:**
    
    -   Setelah pengguna berhasil login, buat JWT yang berisi informasi tentang pengguna.
    -   Letak kode: Di dalam rute login di file `routes/auth.js`.
    
        ```
        const token = jwt.sign({ id: user.id, email: user.email }, secretKey, { expiresIn: '1h' });
        ```
    
3.   **Middleware untuk Verifikasi JWT:**
    
      -   Buat middleware yang memverifikasi token JWT pada setiap rute yang memerlukan otentikasi.
      -   Letak kode: Buat file baru `middleware/auth.js`.
      

      ```
      // middleware/auth.js
      const jwt = require('jsonwebtoken');
      const secretKey = 'your_secret_key'; // Ganti dengan kunci rahasia kamu
      
      function authenticateToken(req, res, next) {
          const token = req.header('Authorization').split(' ')[1];
          
          if (!token) return res.status(401).json({ message: 'Akses ditolak' });
      
          try {
              const verified = jwt.verify(token, secretKey);
              req.user = verified;
              next();
          } catch (error) {
              res.status(400).json({ message: 'Token tidak valid' });
          }
      }
      
      module.exports = authenticateToken;
      ```
    
4.    **Gunakan Middleware di Rute Terproteksi:**
    
      -   Terapkan middleware ini pada rute yang ingin dilindungi agar hanya pengguna yang terotentikasi yang dapat mengakses.
      -   Letak kode: Di dalam file `routes/protected.js`.
        
        ```
        // routes/protected.js
        const express = require('express');
        const authenticateToken = require('../middleware/auth');
        const router = express.Router();
        
        router.get('/protected', authenticateToken, (req, res) => {
            res.json({ message: 'Ini adalah rute terproteksi', user: req.user });
        });
        
        module.exports = router;
        ```
    

### Kesimpulan
 JWT memberikan cara yang aman untuk melakukan otentikasi user dalam aplikasi. Dengan JWT, kamu bisa memastikan bahwa hanya user yang memiliki token yang valid yang dapat mengakses rute atau data tertentu.