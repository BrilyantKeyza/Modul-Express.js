---
sidebar_position: 3
---

# 1.3 Struktur kontrol (if, for, while)

### Penjelasan
Struktur kontrol adalah cara untuk mengarahkan jalannya program. Kita bisa membuat keputusan (`if`), mengulangi kode (`for`, `while`), atau keduanya.

**If Statement:** Gunakan `if` untuk membuat keputusan berdasarkan suatu kondisi. Jika kondisi benar (`true`), maka blok kode tertentu akan dijalankan.

**Contoh Kode:**

```
let nilai = 85;

if (nilai >= 90) {
  console.log("Nilai A");
} else if (nilai >= 80) {
  console.log("Nilai B");
} else {
  console.log("Nilai C");
}
```

**Penjelasan:**

-   Jika `nilai` 90 atau lebih, maka tampilkan "Nilai A".
-   Jika `nilai` antara 80 dan 89, maka tampilkan "Nilai B".
-   Jika `nilai` kurang dari 80, tampilkan "Nilai C".

**For Loop:** Digunakan untuk mengulangi suatu blok kode beberapa kali.

**Contoh Kode:**

```
for (let i = 1; i <= 5; i++) {
  console.log("Perulangan ke-" + i);
}
```

**Penjelasan:**

-   Mulai dari `i = 1` dan terus bertambah hingga `i` mencapai 5.
-   Setiap kali, program akan menampilkan "Perulangan ke-1", "Perulangan ke-2", dan seterusnya.

**While Loop:** Serupa dengan `for`, tapi lebih fleksibel dalam kondisi.

**Contoh Kode:**

```
let count = 1;

while (count <= 5) {
  console.log("Hitungan ke-" + count);
  count++;
}
```

**Penjelasan:**

-   Selama `count` kurang dari atau sama dengan 5, blok kode di dalam `while` akan terus dijalankan.
-   Setiap iterasi, `count` bertambah 1.

### Kesimpulan
Struktur kontrol memungkinkan program untuk membuat keputusan (dengan `if`) dan melakukan tugas berulang (dengan `for` dan `while`). Ini adalah alat penting dalam pemrograman yang memungkinkan kode menjadi dinamis dan responsif terhadap berbagai kondisi yang terjadi selama program berjalan.