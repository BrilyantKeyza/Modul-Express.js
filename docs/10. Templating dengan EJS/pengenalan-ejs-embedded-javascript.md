---
sidebar_position: 1
---

# 10.1 Pengenalan EJS (Embedded JavaScript)

### Penjelasan
EJS adalah sebuah templating engine yang memungkinkan kamu untuk menyisipkan logika JavaScript ke dalam file HTML. Dengan EJS, kamu bisa membuat halaman web yang dinamis dengan cara yang lebih terstruktur dan mudah dikelola.

**Fitur Utama EJS:**

-   **Sintaks Familiar:** Menggunakan sintaks yang mirip dengan HTML dan JavaScript, sehingga mudah dipelajari.
-   **Integrasi yang Baik dengan Express:** EJS terintegrasi dengan baik dengan Express.js, memudahkan proses rendering halaman.
-   **Kemampuan Loop dan Kondisional:** Kamu bisa menggunakan loop (`<% for %>`) dan kondisi (`<% if %>`) langsung dalam file template.

**Contoh Sintaks EJS:**

```
<!DOCTYPE html>
<html>
<head>
    <title>Halaman EJS</title>
</head>
<body>
    <h1>Selamat Datang, <%= name %>!</h1>

    <% if (items.length > 0) { %>
        <ul>
            <% items.forEach(item => { %>
                <li><%= item %></li>
            <% }) %>
        </ul>
    <% } else { %>
        <p>Tidak ada item yang tersedia.</p>
    <% } %>
</body>
</html>
```

### Kesimpulan
EJS memungkinkan kamu untuk membuat halaman web yang lebih dinamis dan interaktif dengan cara yang mudah. Dengan EJS, kamu bisa menyisipkan data dari backend ke dalam halaman HTML dan menggunakan logika JavaScript di dalam template.