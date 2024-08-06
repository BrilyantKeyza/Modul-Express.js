---
sidebar_position: 1
---

# 2.1 Deklarasi dan pemanggilan fungsi

### Penjelasan
Fungsi adalah blok kode yang dapat digunakan kembali di berbagai tempat dalam program. Fungsi memungkinkan kamu untuk mengorganisir kode, menghindari pengulangan, dan membuat kode lebih mudah dipelihara.

**Cara Deklarasi Fungsi:**

1.  **Fungsi dengan Nama:** Fungsi ini diberi nama sehingga dapat dipanggil kembali di mana saja dalam program.
    
    **Contoh Kode:**
    
    ```
    function sapa(nama) {
      console.log("Halo, " + nama + "!");
    }
    ```
    
    **Penjelasan:**
    
    -  Fungsi `sapa` menerima satu parameter `nama`.
    -  Fungsi ini mencetak pesan "Halo, [nama]!" ketika dipanggil.
2.  **Pemanggilan Fungsi:** Untuk menjalankan fungsi yang telah dideklarasikan, kita perlu memanggilnya dengan nama fungsi tersebut, dan memberikan nilai jika diperlukan.
    
    **Contoh Kode:**
    
    ```
    sapa("Alice"); // Output: "Halo, Alice!"
    sapa("Bob");   // Output: "Halo, Bob!"
    ```
    

### Kesimpulan
 Fungsi membantu dalam mengorganisir kode dan membuatnya lebih modular, yang berarti kamu dapat menulis sekali dan menggunakan kembali berkali-kali.