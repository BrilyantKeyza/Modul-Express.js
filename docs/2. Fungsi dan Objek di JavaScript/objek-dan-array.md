---
sidebar_position: 2
---

# 2.2 Objek dan array


### Penjelasan

1.  **Objek:** Objek adalah koleksi data yang terkait, yang disimpan dalam bentuk pasangan `key: value`. Objek memungkinkan kamu menyimpan informasi kompleks dengan cara yang lebih terstruktur.
    
    **Contoh Kode:**
    
    ```
    let orang = {
      nama: "Alice",
      usia: 25,
      pekerjaan: "Programmer"
    };
    
    console.log(orang.nama); // Output: "Alice"
    console.log(orang.usia);  // Output: 25
    ```
    
    **Penjelasan:**
    
    -   `orang` adalah objek dengan tiga properti: `nama`, `usia`, dan `pekerjaan`.
    -   Anda bisa mengakses setiap properti menggunakan tanda titik (`.`).
2.  **Array:** Array adalah kumpulan data yang disimpan dalam satu variabel, dan data ini bisa berupa apa saja: angka, string, objek, atau bahkan fungsi.
    
    **Contoh Kode:**
    
    ```
    let buah = ["Apel", "Mangga", "Pisang"];
    
    console.log(buah[0]); // Output: "Apel"
    console.log(buah[2]); // Output: "Pisang"
    ``` 
    
    **Penjelasan:**
    
    -   `buah` adalah array dengan tiga elemen: "Apel", "Mangga", dan "Pisang".
    -   Anda dapat mengakses elemen array menggunakan indeks, yang dimulai dari 0.

### Kesimpulan
Objek dan array adalah cara penting untuk menyimpan dan mengatur data dalam JavaScript. Objek digunakan untuk mengelompokkan data yang memiliki hubungan, sementara array digunakan untuk mengelompokkan data dalam urutan tertentu.