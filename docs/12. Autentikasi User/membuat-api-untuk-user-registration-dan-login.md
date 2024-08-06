---
sidebar_position: 1
---

# 12.1 Membuat API untuk user registration dan login 

### Penjelasan
Pada tahap ini, kamu akan membuat API yang memungkinkan user untuk mendaftar (registration) dan login ke dalam aplikasi. Proses registrasi melibatkan penyimpanan data user (seperti username dan password) ke dalam database. Proses login melibatkan verifikasi data user dan menghasilkan token jika verifikasi berhasil.

**Langkah-Langkah:**

1.  **Setup Model User:**
    
    -   Buat model `User` yang mencakup `username`, `email`, dan `password`.
    -   Pastikan `password` di-hash sebelum disimpan (ini akan dijelaskan lebih lanjut pada bagian bcrypt).
    
    **Contoh Model User:**

    ```
    const { DataTypes } = require('sequelize');
    const sequelize = require('../config/sequelize');
    
    const User = sequelize.define('User', {
      username: {
        type: DataTypes.STRING,
        allowNull: false,
        unique: true
      },
      email: {
        type: DataTypes.STRING,
        allowNull: false,
        unique: true
      },
      password: {
        type: DataTypes.STRING,
        allowNull: false
      }
    });
    
    module.exports = User;
    ```
    
2.  **Membuat Route untuk Registrasi:**
    
    -   Buat route `POST /register` untuk menerima data registrasi dan menyimpan user baru di database.
    
    **Contoh Route Registrasi:**
    
    ```
    const bcrypt = require('bcrypt');
    const User = require('./models/User');
    
    app.post('/register', async (req, res) => {
      const { username, email, password } = req.body;
    
      try {
        const hashedPassword = await bcrypt.hash(password, 10);
        const user = await User.create({ username, email, password: hashedPassword });
        res.status(201).json(user);
      } catch (err) {
        res.status(400).json({ error: err.message });
      }
    });
    ```
    
3.  **Membuat Route untuk Login:**
    
    -   Buat route `POST /login` untuk memverifikasi user dan mengirimkan token jika login berhasil.
    
    **Contoh Route Login:**
    
    ```
    const jwt = require('jsonwebtoken');
    
    app.post('/login', async (req, res) => {
      const { username, password } = req.body;
    
      try {
        const user = await User.findOne({ where: { username } });
        if (!user) {
          return res.status(404).json({ error: 'User tidak ditemukan' });
        }
    
        const validPassword = await bcrypt.compare(password, user.password);
        if (!validPassword) {
          return res.status(401).json({ error: 'Password salah' });
        }
    
        const token = jwt.sign({ id: user.id }, 'secret_key', { expiresIn: '1h' });
        res.json({ token });
      } catch (err) {
        res.status(500).json({ error: err.message });
      }
    });
    ```
    

### Kesimpulan
Membuat API untuk registrasi dan login adalah langkah pertama dalam implementasi autentikasi user. Dengan route ini, user bisa mendaftar dan login ke dalam aplikasi.