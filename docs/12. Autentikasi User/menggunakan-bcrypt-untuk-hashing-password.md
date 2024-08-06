---
sidebar_position: 2
---

# 12.2 Menggunakan bcrypt untuk hashing password

### Penjelasan
bcrypt adalah library yang digunakan untuk melakukan hashing pada password sebelum disimpan di database. Hashing adalah proses mengubah password menjadi representasi string acak, sehingga lebih aman dan tidak dapat dibalikkan dengan mudah.

**Langkah-Langkah:**

1.  **Instal bcrypt:**
    
    -   Instal bcrypt melalui npm:
        
        ```
        npm install bcrypt
        ```
        
2.  **Menggunakan bcrypt untuk Hashing:**
    
    -   Hash password saat user mendaftar:
    
    **Contoh Hashing Password:**

    ```
    const hashedPassword = await bcrypt.hash(password, 10);
    ``` 
    
    -   Saat login, gunakan bcrypt untuk membandingkan password yang diinput dengan hash yang tersimpan:
    
    **Contoh Verifikasi Password:**
    
    ```
    const validPassword = await bcrypt.compare(password, user.password);
    ```
    

### Kesimpulan
 bcrypt meningkatkan keamanan dengan memastikan password yang disimpan di database tidak dapat dibaca jika database diakses oleh pihak yang tidak berwenang. Dengan bcrypt, kamu bisa melindungi data user dari potensi serangan.