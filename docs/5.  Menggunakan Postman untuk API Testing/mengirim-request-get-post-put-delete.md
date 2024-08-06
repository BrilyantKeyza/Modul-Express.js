---
sidebar_position: 2
---

# 5.2 Mengirim request GET, POST, PUT, DELETE

### Penjelasan
Request dalam HTTP adalah permintaan yang dikirimkan klien ke server. Ada beberapa jenis request yang sering digunakan saat bekerja dengan API:

1.  **GET Request:**
    
    -   Digunakan untuk mengambil data dari server.
    
    **Contoh di Postman:**
    
    -   Masukkan URL endpoint API (misalnya, `http://localhost:3000/api/items`) di bidang URL.
    -   Pilih metode `GET` dari dropdown di sebelah kiri.
    -   Klik tombol "Send".
    -   Kamu akan melihat respons dari server di bagian bawah.
2.  **POST Request:**
    
    -   Digunakan untuk mengirim data baru ke server.
    
    **Contoh di Postman:**
    
    -   Pilih metode `POST`.
    -   Masukkan URL endpoint.
    -   Di bawah tab "Body", pilih `raw` dan `JSON`.
    -   Masukkan data JSON yang ingin kamu kirim, misalnya:
        
        ```
        {
          "name": "Item Baru",
          "price": 10000
        }
        ```
        
    -   Klik "Send" untuk mengirim request.
3.  **PUT Request:**
    
    -   Digunakan untuk memperbarui data yang sudah ada di server.
    
    **Contoh di Postman:**
    
    -   Pilih metode `PUT`.
    -   Masukkan URL endpoint dengan ID dari data yang ingin diupdate (misalnya, `http://localhost:3000/api/items/1`).
    -   Di bawah tab "Body", pilih `raw` dan `JSON`.
    -   Masukkan data JSON yang diperbarui, misalnya:
        
        ```
        {
          "name": "Item Diperbarui",
          "price": 15000
        }
        ```
        
    -   Klik "Send".
4.  **DELETE Request:**
    
    -   Digunakan untuk menghapus data dari server.
    
    **Contoh di Postman:**
    
    -   Pilih metode `DELETE`.
    -   Masukkan URL endpoint dengan ID dari data yang ingin dihapus (misalnya, `http://localhost:3000/api/items/1`).
    -   Klik "Send".

### Kesimpulan
 Postman memungkinkan kamu untuk dengan mudah mengirim berbagai jenis request ke server, yang sangat membantu dalam pengembangan dan pengujian API.
