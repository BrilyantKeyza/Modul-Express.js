---
sidebar_position: 3
---

# 14.3 Menggunakan middleware untuk proteksi rute

### Penjelasan
Error handling dan validasi data adalah bagian penting dari pengembangan API. Ini membantu mencegah input yang tidak valid dan memberikan umpan balik yang jelas kepada pengguna API.

**Langkah-Langkah:**

1.  **Menangani Error:**
    
    -   Buat middleware untuk menangani error yang tidak terduga.
    
    **Contoh Error Handling Middleware:**
    
    ```
    app.use((err, req, res, next) => {
      console.error(err.stack);
      res.status(500).json({ error: 'Terjadi kesalahan pada server' });
    });
    ```
    
2.  **Validasi Data Input:**
    
    -   Gunakan library seperti `express-validator` untuk memvalidasi data yang masuk.
    
    **Contoh Validasi Data:**
    
    ```
    const { check, validationResult } = require('express-validator');
    
    app.post('/register', [
      check('username').isLength({ min: 5 }),
      check('email').isEmail(),
      check('password').isLength({ min: 5 })
    ], (req, res) => {
      const errors = validationResult(req);
      if (!errors.isEmpty()) {
        return res.status(400).json({ errors: errors.array() });
      }
    
      // Lanjutkan dengan proses registrasi...
    });
    ```
    
3.  **Memberikan Pesan Error yang Jelas:**
    
    -   Pastikan setiap response error memberikan pesan yang jelas dan informatif.
    
    **Contoh Pesan Error:**
    
    ```
    res.status(400).json({ error: 'Email sudah terdaftar' });
    ```
    

### Kesimpulan
 Dengan menangani error dan validasi data, kamu memastikan bahwa API lebih aman dan lebih mudah digunakan. Ini juga meningkatkan pengalaman user dengan memberikan umpan balik yang tepat jika terjadi masalah.