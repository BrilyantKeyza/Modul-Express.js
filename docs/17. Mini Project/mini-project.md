---
sidebar_position: 1
---

# Mini Project CRUD Mahasiswa 

#### **Fitur Utama:**

1.  **Tambah Data Mahasiswa (Create)**
2.  **Lihat Daftar Mahasiswa (Read)**
3.  **Edit Data Mahasiswa (Update)**
4.  **Hapus Data Mahasiswa (Delete)**

#### **Langkah-Langkah Pembangunan:**

1.  **Setup Proyek:**
    
    -   Inisialisasi proyek Node.js:
        
        ```
        npm init -y
        npm install express sequelize sqlite3 ejs body-parser
        ```
        
    -   Struktur folder:
        
        
        `/project-folder
        |-- /controllers
        |-- /models
        |-- /routes
        |-- /views
        |-- app.js`


    -   Membuat Folder Satu per Satu 
        Jalankan perintah berikut satu per satu untuk membuat setiap folder:
        ```
        mkdir controllers
        mkdir models
        mkdir routes
        mkdir views
        ```
        ```
        touch app.js
        ```
        
2.  **Membuat Model Mahasiswa:**
    
    -   Buat model menggunakan Sequelize.
    -   Database yang digunakan bisa SQLite untuk kemudahan.
    
    **models/mahasiswa.js:**

    ```
    const { Sequelize, DataTypes } = require('sequelize');
    const sequelize = new Sequelize({
        dialect: 'sqlite',
        storage: 'database.sqlite'
    });
    
    const Mahasiswa = sequelize.define('Mahasiswa', {
        nama: {
            type: DataTypes.STRING,
            allowNull: false
        },
        nis: {
            type: DataTypes.STRING,
            allowNull: false,
            unique: true
        },
        kelas: {
            type: DataTypes.STRING,
            allowNull: false
        }
    });
    
    module.exports = Mahasiswa;
    ``` 
    
3.  **Membuat Controller untuk CRUD:**
    
    -   Buat controller yang menangani operasi CRUD.
    
    **controllers/mahasiswaController.js:**
    
    ```
    const Mahasiswa = require('../models/mahasiswa');
    
    exports.getAllMahasiswa = async (req, res) => {
        const mahasiswa = await Mahasiswa.findAll();
        res.render('index', { mahasiswa });
    };
    
    exports.createMahasiswa = async (req, res) => {
        const { nama, nis, kelas } = req.body;
        await Mahasiswa.create({ nama, nis, kelas });
        res.redirect('/');
    };
    
    exports.getMahasiswaById = async (req, res) => {
        const mahasiswa = await Mahasiswa.findByPk(req.params.id);
        res.render('edit', { mahasiswa });
    };
    
    exports.updateMahasiswa = async (req, res) => {
        const { nama, nis, kelas } = req.body;
        await Mahasiswa.update({ nama, nis, kelas }, {
            where: { id: req.params.id }
        });
        res.redirect('/');
    };
    
    exports.deleteMahasiswa = async (req, res) => {
        await Mahasiswa.destroy({ where: { id: req.params.id } });
        res.redirect('/');
    };
    ``` 
    
4.  **Membuat Routing:**
    
    -   Buat rute yang memetakan setiap operasi CRUD.
    
    **routes/mahasiswaRoutes.js:**
    
    ```
    const express = require('express');
    const router = express.Router();
    const mahasiswaController = require('../controllers/mahasiswaController');
    
    router.get('/', mahasiswaController.getAllMahasiswa);
    router.get('/add', (req, res) => res.render('add'));
    router.post('/add', mahasiswaController.createMahasiswa);
    router.get('/edit/:id', mahasiswaController.getMahasiswaById);
    router.post('/edit/:id', mahasiswaController.updateMahasiswa);
    router.post('/delete/:id', mahasiswaController.deleteMahasiswa);
    
    module.exports = router;
    ```
    
5.  **Membuat View dengan EJS:**
    
    -   Buat halaman EJS untuk menampilkan, menambah, mengedit, dan menghapus data mahasiswa.
    
    **views/index.ejs:**
    ```
    <h1>Daftar Mahasiswa</h1>
    <a href="/add">Tambah Mahasiswa</a>
    <ul>
        <% mahasiswa.forEach(mhs => { %>
            <li>
                <%= mhs.nama %> - <%= mhs.nis %> - <%= mhs.kelas %>
                <a href="/edit/<%= mhs.id %>">Edit</a>
                <form action="/delete/<%= mhs.id %>" method="post" style="display:inline;">
                    <button type="submit">Delete</button>
                </form>
            </li>
        <% }) %>
    </ul>
    ``` 
    
    **views/add.ejs:**
    
    ```
    <h1>Tambah Mahasiswa</h1>
    <form action="/add" method="post">
        <input type="text" name="nama" placeholder="Nama" required>
        <input type="text" name="nis" placeholder="NIS" required>
        <input type="text" name="kelas" placeholder="Kelas" required>
        <button type="submit">Tambah</button>
    </form>
    ```
    
    **views/edit.ejs:**
    
    ```
    <h1>Edit Mahasiswa</h1>
    <form action="/edit/<%= mahasiswa.id %>" method="post">
        <input type="text" name="nama" value="<%= mahasiswa.nama %>" required>
        <input type="text" name="nis" value="<%= mahasiswa.nis %>" required>
        <input type="text" name="kelas" value="<%= mahasiswa.kelas %>" required>
        <button type="submit">Simpan</button>
    </form>
    ```
    
6.  **Menjalankan Aplikasi:**
    
    -   Tambahkan kode untuk menjalankan server Express.js.
    
    **app.js:**
    
    ```
    const express = require('express');
    const bodyParser = require('body-parser');
    const sequelize = require('./models/mahasiswa').sequelize;
    const mahasiswaRoutes = require('./routes/mahasiswaRoutes');
    
    const app = express();
    
    app.set('view engine', 'ejs');
    app.use(bodyParser.urlencoded({ extended: true }));
    app.use('/', mahasiswaRoutes);
    
    sequelize.sync().then(() => {
        app.listen(3000, () => console.log('Server running on port 3000'));
    });
    ```
    

### **Kesimpulan:**

Dengan mengikuti langkah-langkah di atas, kamu akan belajar bagaimana membuat aplikasi CRUD sederhana menggunakan Express.js. Aplikasi ini memungkinkan pengguna untuk menambah, melihat, mengedit, dan menghapus data mahasiswa. Mini project ini tidak hanya membantu memahami konsep CRUD, tetapi juga memberikan pengalaman langsung dalam pengembangan aplikasi web.