---
sidebar_position: 1
---

# 15.1 Membuat view untuk halaman utama, login, dan registrasi

### Penjelasan
EJS adalah template engine untuk Node.js yang memungkinkan kamu untuk menyisipkan JavaScript ke dalam HTML. Dengan EJS, kamu bisa membuat halaman web dinamis yang menampilkan data dari server.

**Langkah-Langkah:**

1.  **Setup EJS di Express:**
    
    -   Instal EJS dan atur sebagai view engine di aplikasi Express.js.
    
    **Contoh Instalasi dan Setup:**
    
    ```
    npm install ejs
    ```
    
    ```
    const express = require('express');
    const app = express();
    
    app.set('view engine', 'ejs');
    app.set('views', './views'); // Set folder untuk menyimpan file EJS
    
    app.use(express.urlencoded({ extended: true })); // Untuk menangani form data
    ```
    
2.  **Membuat View untuk Halaman Registrasi:**
    
    -   Buat file `register.ejs` di folder `views`.
    
    **Contoh `register.ejs`:**
    
    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Registrasi</title>
    </head>
    <body>
        <h1>Registrasi</h1>
        <form action="/register" method="POST">
            <label for="username">Username:</label>
            <input type="text" name="username" required><br>
    
            <label for="email">Email:</label>
            <input type="email" name="email" required><br>
    
            <label for="password">Password:</label>
            <input type="password" name="password" required><br>
    
            <button type="submit">Daftar</button>
        </form>
        <p>Sudah punya akun? <a href="/login">Login</a></p>
    </body>
    </html>
    ```
    
3.  **Membuat View untuk Halaman Login:**
    
    -   Buat file `login.ejs` di folder `views`.
    
    **Contoh `login.ejs`:**
    
    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Login</title>
    </head>
    <body>
        <h1>Login</h1>
        <form action="/login" method="POST">
            <label for="email">Email:</label>
            <input type="email" name="email" required><br>
    
            <label for="password">Password:</label>
            <input type="password" name="password" required><br>
    
            <button type="submit">Login</button>
        </form>
        <p>Belum punya akun? <a href="/register">Daftar</a></p>
    </body>
    </html>
    ```
    
4.  **Membuat View untuk Halaman Utama:**
    
    -   Buat file `index.ejs` di folder `views`.
    
    **Contoh `index.ejs`:**
    
    ```
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Halaman Utama</title>
    </head>
    <body>
        <h1>Selamat Datang, <%= user.username %>!</h1>
        <a href="/logout">Logout</a>
    
        <h2>Post Baru</h2>
        <form action="/posts" method="POST">
            <label for="title">Judul:</label>
            <input type="text" name="title" required><br>
    
            <label for="content">Konten:</label>
            <textarea name="content" required></textarea><br>
    
            <button type="submit">Buat Post</button>
        </form>
    
        <h2>Semua Post</h2>
        <ul>
            <% posts.forEach(post => { %>
                <li>
                    <h3><%= post.title %></h3>
                    <p><%= post.content %></p>
                    <p>Oleh: <%= post.User.username %></p>
                </li>
            <% }) %>
        </ul>
    </body>
    </html>
    ```
    

### Kesimpulan
 Dengan membuat view ini, kamu telah menciptakan halaman dasar yang memungkinkan user untuk mendaftar, login, dan melihat/membuat post. Ini adalah dasar dari aplikasi media sosial berbasis web.