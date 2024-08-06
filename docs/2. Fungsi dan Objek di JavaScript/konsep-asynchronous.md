---
sidebar_position: 3
---

# 2.2 Konsep Asynchronous (callback, promise)

### Penjelasan
Asynchronous adalah cara menangani operasi yang memakan waktu lama, seperti mengambil data dari server, tanpa menghentikan eksekusi kode lainnya.

1.  **Callback:** Callback adalah fungsi yang dikirim sebagai argumen ke fungsi lain dan dipanggil setelah tugas selesai.
    
    **Contoh Kode:**
    
    ```
    function panggilSetelahDuaDetik(callback) {
      setTimeout(callback, 2000); // Menunggu 2 detik
    }
    
    panggilSetelahDuaDetik(function() {
      console.log("Dua detik telah berlalu");
    });
    ``` 
    
    **Penjelasan:**
    
    -   `setTimeout` adalah fungsi bawaan JavaScript yang menunggu selama waktu yang ditentukan (dalam milidetik) sebelum memanggil fungsi callback.
    -   Dalam contoh ini, pesan akan muncul setelah 2 detik.
2.  **Promise:** Promise adalah objek yang mewakili penyelesaian (atau kegagalan) dari operasi asynchronous, dan hasilnya yang terkait.
    
    **Contoh Kode:**
    
	```
    let janji = new Promise(function(resolve, reject) {
      let sukses = true; // Ubah menjadi false untuk melihat efek reject
    
      if (sukses) {
        resolve("Operasi berhasil!");
      } else {
        reject("Operasi gagal.");
      }
    });
    
    janji.then(function(pesan) {
      console.log(pesan); // Jika sukses: "Operasi berhasil!"
    }).catch(function(error) {
      console.log(error); // Jika gagal: "Operasi gagal."
    });
    ```
    
    **Penjelasan:**
    
    -   `Promise` adalah cara menangani operasi asynchronous yang lebih modern dan terstruktur dibandingkan callback.
    -   `resolve` digunakan ketika operasi berhasil, dan `reject` digunakan ketika operasi gagal.
    -   `.then()` menangani hasil sukses, dan `.catch()` menangani error.

### Kesimpulan
Konsep asynchronous memungkinkan JavaScript untuk menangani operasi yang membutuhkan waktu tanpa menghentikan sisa program. Callback dan promise adalah dua cara umum untuk bekerja dengan kode asynchronous, dengan promise menawarkan cara yang lebih rapi dan terstruktur.