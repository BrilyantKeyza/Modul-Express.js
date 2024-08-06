---
sidebar_position: 1
---

# 1.1 Variabel dan tipe data


### Penjelasan
Variabel adalah seperti kotak yang menyimpan informasi yang kita butuhkan dalam program. Misalnya, kita ingin menyimpan nama seseorang atau usia mereka. Kita dapat menggunakan variabel untuk menyimpan data ini.

**Tipe Data:**

1.  **String**: Ini adalah teks, seperti nama atau kata-kata. Contohnya: `"Halo"`, `"Alice"`.
2.  **Number**: Ini adalah angka, bisa berupa angka bulat (integer) atau desimal. Contohnya: `25`, `3.14`.
3.  **Boolean**: Ini adalah nilai benar atau salah, hanya ada dua kemungkinan: `true` (benar) atau `false` (salah).
4.  **Undefined**: Jika kita membuat variabel tapi tidak memberi nilai apa pun, nilainya akan menjadi `undefined`, artinya "tidak terdefinisi".

**Contoh Kode:**

```
let nama = "Alice";    // String: Teks nama
let usia = 25;         // Number: Angka usia
let lulus = true;      // Boolean: Apakah lulus? Benar atau Salah
let pekerjaan;         // Undefined: Belum diisi

// Tampilkan jenis data ke konsol
console.log(typeof nama); // "string"
console.log(typeof usia);  // "number"
console.log(typeof lulus); // "boolean"
console.log(typeof pekerjaan); // "undefined"
```

**Penjelasan Contoh:**

-   `nama` adalah variabel yang menyimpan teks "Alice".
-   `usia` menyimpan angka 25.
-   `lulus` menyimpan nilai `true`, menunjukkan bahwa Alice lulus.
-   `pekerjaan` belum diberi nilai, jadi nilainya `undefined`.


### Kesimpulan
Variabel adalah alat yang digunakan untuk menyimpan data dalam program. Ada berbagai jenis data yang dapat disimpan, seperti teks (string), angka (number), nilai benar atau salah (boolean), dan lainnya. Memahami tipe data ini penting karena mempengaruhi bagaimana data tersebut dapat digunakan dan diproses dalam kode Anda.