---
sidebar_position: 2
---

# 14.2 Menggunakan middleware untuk proteksi rute

### Penjelasan
Postman adalah alat yang sangat berguna untuk menguji API yang kamu buat. Kamu dapat mengirim berbagai jenis request (GET, POST, PUT, DELETE) dan memverifikasi apakah API bekerja sesuai dengan yang diharapkan.

**Langkah-Langkah:**

1.  **Menyiapkan Postman:**
    
    -   Buka Postman dan buat Collection baru untuk menyimpan semua request API.
2.  **Mengirim Request Registrasi dan Login:**
    
    -   Buat request `POST /api/register` untuk mendaftarkan user baru.
    -   Buat request `POST /api/login` untuk mendapatkan token autentikasi.
3.  **Mengirim Request CRUD Post dan Like:**
    
    -   Buat request `POST /api/posts` untuk membuat post baru (jangan lupa sertakan token di header).
    -   Buat request `POST /api/posts/{postId}/like` untuk memberi like pada post.
    -   Gunakan request `GET /api/posts` untuk melihat semua post.
    -   Gunakan request `DELETE /api/posts/{id}` untuk menghapus post yang telah dibuat.
4.  **Mengecek Response:**
    
    -   Pastikan setiap request menghasilkan response yang sesuai, seperti status code 200 untuk success, 201 untuk created, dan 400 atau 404 untuk error.

### Kesimpulan
 Testing dengan Postman memungkinkan kamu untuk memverifikasi bahwa API bekerja sesuai dengan harapan. Dengan menguji semua endpoint, kamu bisa memastikan aplikasi media sosial berjalan dengan baik.