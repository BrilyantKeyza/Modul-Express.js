---
sidebar_position: 2
---

# 1.2 Operasi dasar (aritmatika, logika)

### Penjelasan
Operasi dasar dalam JavaScript membantu kita melakukan perhitungan (seperti matematika) dan membuat keputusan berdasarkan kondisi tertentu.

**Operasi Aritmatika:**

-   **Penjumlahan (`+`)**: Menambah dua angka.
-   **Pengurangan (`-`)**: Mengurangi satu angka dari angka lainnya.
-   **Perkalian (`*`)**: Mengalikan dua angka.
-   **Pembagian (`/`)**: Membagi satu angka dengan angka lainnya.

**Contoh Kode:**
```
let a = 10;
let b = 5;

let hasilPenjumlahan = a + b; // 15
let hasilPengurangan = a - b; // 5
let hasilPerkalian = a * b;   // 50
let hasilPembagian = a / b;   // 2

console.log(hasilPenjumlahan, hasilPengurangan, hasilPerkalian, hasilPembagian);
``` 

**Operasi Logika:**

-   **Lebih Besar (`>`)**: Membandingkan apakah angka di sebelah kiri lebih besar.
-   **Lebih Kecil (`<`)**: Membandingkan apakah angka di sebelah kiri lebih kecil.
-   **Sama Dengan (`===`)**: Membandingkan apakah dua nilai sama persis.

**Contoh Kode:**

```
let x = 10;
let y = 5;

let lebihBesar = x > y;  // true, karena 10 lebih besar dari 5
let lebihKecil = x < y;  // false, karena 10 tidak lebih kecil dari 5
let samaDengan = x === y; // false, karena 10 tidak sama dengan 5

console.log(lebihBesar, lebihKecil, samaDengan);
``` 

**Penjelasan Contoh:**

-   `hasilPenjumlahan`, `hasilPengurangan`, `hasilPerkalian`, dan `hasilPembagian` adalah hasil dari operasi matematika pada variabel `a` dan `b`.
-   `lebihBesar` adalah `true` karena 10 lebih besar dari 5.
-   `samaDengan` adalah `false` karena 10 tidak sama dengan 5.


### Kesimpulan
Operasi aritmatika digunakan untuk melakukan perhitungan matematika, sementara operasi logika membantu membuat keputusan dengan membandingkan nilai-nilai. Kedua jenis operasi ini adalah dasar dalam pengolahan data di JavaScript dan sangat penting untuk memahami bagaimana program dapat berinteraksi dan mengambil keputusan.

