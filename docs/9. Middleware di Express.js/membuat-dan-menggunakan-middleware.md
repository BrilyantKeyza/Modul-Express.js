---
sidebar_position: 2
---

# 9.2 Membuat dan menggunakan middleware

### Penjelasan
Di Express.js, kamu bisa membuat middleware sendiri untuk berbagai keperluan seperti validasi, autentikasi, logging, atau bahkan menangani error.

**Langkah-Langkah:**

1.  **Membuat Middleware Sederhana:**
    
    -   Middleware dasar hanya memerlukan tiga parameter: `req`, `res`, dan `next`.
    
    **Contoh Middleware untuk Logging:**
    

    ```
    const requestLogger = (req, res, next) => {
      console.log(`${req.method} ${req.url}`);
      next();
    };
    ``` 
    
2.  **Menggunakan Middleware Secara Global:**
    
    -   Kamu bisa menggunakan middleware di seluruh aplikasi dengan `app.use()`.
    
    **Contoh:**

    ```
    app.use(requestLogger);
    ```
    
    -   Ini akan menjalankan middleware `requestLogger` untuk setiap request yang masuk.
3.  **Menggunakan Middleware untuk Rute Tertentu:**
    
    -   Kamu juga bisa menerapkan middleware pada rute tertentu saja.
    
    **Contoh:**
    
    ```
    app.get('/protected', requestLogger, (req, res) => {
      res.send('Ini halaman yang dilindungi.');
    });
    ```
    
    -   Middleware `requestLogger` hanya akan berjalan saat rute `/protected` diakses.
4.  **Middleware untuk Penanganan Error:**
    
    -   Express.js menyediakan mekanisme untuk menangani error menggunakan middleware dengan empat parameter (termasuk `err`).
    
    **Contoh Middleware Error Handling:**
    
    ```
    const errorHandler = (err, req, res, next) => {
      console.error(err.stack);
      res.status(500).send('Ada sesuatu yang salah!');
    };
    
    app.use(errorHandler);
	```
    
    -   Middleware ini akan menangani error yang terjadi di dalam aplikasi dan mengirimkan respons dengan status `500`.

### Kesimpulan
 Membuat dan menggunakan middleware memberikan kamu kontrol penuh atas bagaimana request diproses di aplikasi Express.js. Dengan middleware, kamu dapat menambahkan fitur seperti logging, autentikasi, validasi, dan penanganan error dengan cara yang modular dan terstruktur.