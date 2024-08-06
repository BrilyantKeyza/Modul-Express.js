---
sidebar_position: 3
---

# 4.3 Konsep routing dasar

### Penjelasan
Routing adalah konsep penting dalam pengembangan web yang mengacu pada cara aplikasi web menangani permintaan (request) yang datang dari klien ke berbagai endpoint (rute). Dalam Express.js, kamu dapat mendefinisikan rute untuk menangani permintaan HTTP yang berbeda seperti GET, POST, PUT, dan DELETE.

**Contoh Kode:**

```
app.get('/', (req, res) => {
  res.send('Ini adalah halaman utama');
});

app.get('/about', (req, res) => {
  res.send('Ini adalah halaman About');
});

app.get('/contact', (req, res) => {
  res.send('Ini adalah halaman Contact');
});
```

**Penjelasan:**

-   Rute `'/'` mengarahkan ke halaman utama.
-   Rute `'/about'` mengarahkan ke halaman "About".
-   Rute `'/contact'` mengarahkan ke halaman "Contact".

Kamu juga bisa menangani metode HTTP lain, misalnya POST, dengan cara yang serupa:

```
app.post('/submit-form', (req, res) => {
  res.send('Formulir berhasil dikirim');
});
```

### Kesimpulan
 Routing dalam Express.js memungkinkan kamu untuk menentukan bagaimana aplikasi merespon permintaan ke endpoint yang berbeda. Ini adalah bagian fundamental dari aplikasi web, memungkinkan kamu untuk mengarahkan pengguna ke halaman atau bagian yang tepat berdasarkan permintaan mereka.