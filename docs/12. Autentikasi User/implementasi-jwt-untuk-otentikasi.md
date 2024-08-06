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
        
2.  **Membuat Token JWT saat Login:**
    
    -   Saat user berhasil login, buat token JWT dan kirimkan ke client:
    
    **Contoh Membuat JWT:**
    
    ```
    const token = jwt.sign({ id: user.id }, 'secret_key', { expiresIn: '1h' });
    ```
    
3.  **Menggunakan JWT untuk Melindungi Rute:**
    
    -   Buat middleware untuk memverifikasi token pada rute yang memerlukan autentikasi:
    
    **Contoh Middleware JWT:**
    
    ```
    const authenticateJWT = (req, res, next) => {
      const token = req.header('Authorization').split(' ')[1];
    
      if (!token) {
        return res.status(403).json({ error: 'Token tidak tersedia' });
      }
    
      jwt.verify(token, 'secret_key', (err, user) => {
        if (err) {
          return res.status(403).json({ error: 'Token tidak valid' });
        }
        req.user = user;
        next();
      });
    };
    ```
    
    -   Terapkan middleware ini pada rute yang ingin dilindungi:
    
    **Contoh Penerapan Middleware:**
    
    ```
    app.get('/protected', authenticateJWT, (req, res) => {
      res.json({ message: 'Ini adalah data rahasia.' });
    });
    ```
    

### Kesimpulan
 JWT memberikan cara yang aman untuk melakukan otentikasi user dalam aplikasi. Dengan JWT, kamu bisa memastikan bahwa hanya user yang memiliki token yang valid yang dapat mengakses rute atau data tertentu.