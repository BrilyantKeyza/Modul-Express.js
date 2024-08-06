---
sidebar_position: 1
---

# 9.1 Konsep Middleware

### Penjelasan
Middleware adalah fungsi yang memiliki akses ke objek request (`req`), objek response (`res`), dan fungsi `next` dalam siklus request-response di aplikasi Express.js. Middleware dapat melakukan tugas-tugas seperti:

-   Menjalankan kode apa pun.
-   Mengubah objek request dan response.
-   Mengakhiri siklus request-response.
-   Memanggil middleware berikutnya dalam stack.

**Urutan eksekusi middleware:** Middleware dieksekusi secara berurutan sesuai dengan urutan mereka didefinisikan dalam kode. Jika middleware tidak memanggil `next()`, maka request tidak akan dilanjutkan ke middleware berikutnya atau rute handler.

**Contoh Sederhana Middleware:**

```
const express = require('express');
const app = express();

// Middleware sederhana yang mencatat waktu request
app.use((req, res, next) => {
  console.log('Waktu:', Date.now());
  next(); // Lanjutkan ke middleware berikutnya atau route handler
});

app.get('/', (req, res) => {
  res.send('Hello World');
});

app.listen(3000, () => {
  console.log('Server berjalan di http://localhost:3000');
});
``` 

### Kesimpulan
 Middleware adalah fungsi yang berperan di antara request yang masuk dan respon yang dikirimkan oleh server. Middleware memberikan fleksibilitas untuk mengelola request secara teratur dan modular.
