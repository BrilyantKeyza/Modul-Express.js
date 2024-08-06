---
sidebar_position: 3
---

# 5.3 Menangani response dan status code

### Penjelasan
Setelah mengirim request, server akan mengirimkan response yang berisi data atau pesan tertentu, serta status code yang menunjukkan hasil dari permintaan tersebut.

**Status Code Umum:**

-   **200 OK**: Permintaan berhasil, dan server mengembalikan data yang diminta.
-   **201 Created**: Data berhasil dibuat (biasanya untuk POST request).
-   **204 No Content**: Permintaan berhasil, tetapi tidak ada data yang dikembalikan (biasanya untuk DELETE request).
-   **400 Bad Request**: Permintaan yang dikirim klien salah atau tidak valid.
-   **404 Not Found**: Server tidak menemukan apa yang diminta (misalnya, endpoint atau ID yang tidak ada).
-   **500 Internal Server Error**: Terjadi kesalahan di server.

**Melihat Response di Postman:**

-   Setelah mengirim request, kamu dapat melihat response dari server di bagian bawah Postman.
-   Bagian ini akan menunjukkan body dari response (jika ada), status code, dan waktu respon.
-   Kamu juga bisa melihat header dari response, yang memberikan informasi tambahan tentang data yang dikirim server.

### Kesimpulan
Memahami dan menangani response serta status code sangat penting dalam API testing, karena ini memberi tahu kamu apakah permintaan berhasil atau ada yang salah, dan bagaimana menanganinya.