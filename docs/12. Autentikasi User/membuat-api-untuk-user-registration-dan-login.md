---
sidebar_position: 1
---

# 12.1 Membuat API untuk user registration dan login 

### Penjelasan
Pada tahap ini, kamu akan membuat API yang memungkinkan user untuk mendaftar (registration) dan login ke dalam aplikasi. Proses registrasi melibatkan penyimpanan data user (seperti username dan password) ke dalam database. Proses login melibatkan verifikasi data user dan menghasilkan token jika verifikasi berhasil.


#### **A. User Registration (Registrasi Pengguna)**

Registrasi pengguna adalah proses di mana pengguna baru membuat akun di aplikasi. Proses ini melibatkan pengumpulan data seperti nama pengguna (username), email, dan password, serta validasi data, hashing password untuk keamanan, dan penyimpanan data ke database.

**Langkah-langkah dan Kode:**

1.  **Rute untuk Registrasi:**
    
    -   Buat rute POST yang menerima data registrasi dari pengguna.
    -   Letak kode: Di dalam file `routes/auth.js`.
    
    ```
    // routes/auth.js
    const express = require('express');
    const bcrypt = require('bcrypt');
    const { User } = require('../models'); // Model User dihubungkan ke database
    const router = express.Router();
    
    router.post('/register', async (req, res) => {
        const { username, email, password } = req.body;
    
        // Validasi data input
        if (!username || !email || !password) {
            return res.status(400).send('Semua field harus diisi');
        }
    
        // Hashing password
        const hashedPassword = await bcrypt.hash(password, 10);
    
        try {
            // Simpan user ke database
            const newUser = await User.create({
                username,
                email,
                password: hashedPassword
            });
    
            res.status(201).json({ message: 'User berhasil terdaftar', user: newUser });
        } catch (error) {
            res.status(500).json({ message: 'Terjadi kesalahan', error });
        }
    });
    
    module.exports = router;
    ```
    
2.  **Validasi Data:**
    
    -   Validasi dilakukan di dalam rute POST untuk memastikan semua data yang diperlukan telah diisi.
    -   Letak kode: Bagian `if (!username || !email || !password)` di dalam rute registrasi.
3.  **Hashing Password:**
    
    -   Gunakan bcrypt untuk hashing password sebelum menyimpannya ke database.
    -   Letak kode: `const hashedPassword = await bcrypt.hash(password, 10);`
4.  **Simpan ke Database:**
    
    -   Data pengguna yang sudah di-hash disimpan ke dalam database menggunakan model `User`.
    -   Letak kode: `const newUser = await User.create({ ... })`.

#### **B. User Login**

Login adalah proses di mana pengguna masuk ke aplikasi menggunakan email dan password yang mereka buat saat registrasi.

**Langkah-langkah dan Kode:**

1.  **Rute untuk Login:**
    
    -   Buat rute POST yang menerima data login dari pengguna.
    -   Letak kode: Di dalam file `routes/auth.js`.
    
    ```
    // routes/auth.js
    const jwt = require('jsonwebtoken');
    const secretKey = 'your_secret_key'; // Ganti dengan kunci rahasia kamu
    
    router.post('/login', async (req, res) => {
        const { email, password } = req.body;
    
        // Cari user berdasarkan email
        const user = await User.findOne({ where: { email } });
    
        if (!user) {
            return res.status(404).json({ message: 'Email tidak ditemukan' });
        }
    
        // Cek password
        const isMatch = await bcrypt.compare(password, user.password);
        
        if (!isMatch) {
            return res.status(401).json({ message: 'Password salah' });
        }
    
        // Buat token JWT
        const token = jwt.sign({ id: user.id, email: user.email }, secretKey, { expiresIn: '1h' });
    
        res.json({ message: 'Login berhasil', token });
    });
    ```
    
2.  **Cek Email dan Password:**
    
    -   Verifikasi bahwa email dan password cocok dengan yang ada di database menggunakan bcrypt.
    -   Letak kode: `const isMatch = await bcrypt.compare(password, user.password);`
3.  **Generasi JWT:**
    
    -   Jika email dan password cocok, buat JWT yang akan digunakan untuk otentikasi pada rute-rute lain.
    -   Letak kode: `const token = jwt.sign({ id: user.id, email: user.email }, secretKey, { expiresIn: '1h' });`
    

### Kesimpulan
Membuat API untuk registrasi dan login adalah langkah pertama dalam implementasi autentikasi user. Dengan route ini, user bisa mendaftar dan login ke dalam aplikasi.