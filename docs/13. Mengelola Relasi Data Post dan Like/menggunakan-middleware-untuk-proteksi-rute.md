---
sidebar_position: 3
---

# 13.3 Menggunakan middleware untuk proteksi rute


### Penjelasan
Untuk memastikan hanya user yang terautentikasi yang bisa membuat, menghapus post, atau memberi like, kita akan menggunakan middleware yang sudah kita buat sebelumnya (misalnya `authenticateJWT`).

**Langkah-Langkah:**

1.  **Middleware Otentikasi:**
    
    -   Pastikan semua route yang memerlukan proteksi menggunakan middleware `authenticateJWT`.
2.  **Contoh Penerapan Middleware:**
    
    -   Pada contoh sebelumnya, middleware `authenticateJWT` sudah diterapkan pada route yang melibatkan pembuatan, penghapusan post, dan pemberian like.

### Kesimpulan
Dengan menggunakan middleware, kamu memastikan bahwa hanya user yang memiliki token autentikasi yang dapat mengakses rute tertentu. Ini meningkatkan keamanan aplikasi dan melindungi data sensitif dari akses yang tidak sah.