---
sidebar_position: 3
---

# 11.3 Querying database dengan Sequelize

### Penjelasan
Setelah model dibuat, kamu bisa mulai melakukan operasi database seperti CRUD (Create, Read, Update, Delete) menggunakan Sequelize. Operasi-operasi ini dilakukan dengan menggunakan method-method yang disediakan oleh Sequelize.

**Langkah-Langkah:**

1.  **Menambahkan Data ke Database:**
    
    -   Gunakan method `create` untuk menambahkan data baru:
        
        ```
        const User = require('./models/User');
        
        app.post('/users', async (req, res) => {
          try {
            const user = await User.create(req.body);
            res.status(201).json(user);
          } catch (err) {
            res.status(400).json({ error: err.message });
          }
        });
        ``` 
        
2.  **Membaca Data dari Database:**
    
    -   Gunakan method `findAll` atau `findOne` untuk mengambil data:
        
        ```
        app.get('/users', async (req, res) => {
          try {
            const users = await User.findAll();
            res.json(users);
          } catch (err) {
            res.status(500).json({ error: err.message });
          }
        });
        ```
        
3.  **Memperbarui Data di Database:**
    
    -   Gunakan method `update` untuk memperbarui data:
        
        ```
        app.put('/users/:id', async (req, res) => {
          try {
            const [updated] = await User.update(req.body, { where: { id: req.params.id } });
            if (updated) {
              const updatedUser = await User.findOne({ where: { id: req.params.id } });
              res.json(updatedUser);
            } else {
              res.status(404).json({ error: 'User tidak ditemukan' });
            }
          } catch (err) {
            res.status(500).json({ error: err.message });
          }
        });
        ```
        
4.  **Menghapus Data dari Database:**
    
    -   Gunakan method `destroy` untuk menghapus data:
        
        ```
        app.delete('/users/:id', async (req, res) => {
          try {
            const deleted = await User.destroy({ where: { id: req.params.id } });
            if (deleted) {
              res.status(204).send();
            } else {
              res.status(404).json({ error: 'User tidak ditemukan' });
            }
          } catch (err) {
            res.status(500).json({ error: err.message });
          }
        });
        ```
        

### Kesimpulan
 Dengan Sequelize, kamu bisa melakukan berbagai operasi database dengan cara yang lebih intuitif dan terstruktur. Sequelize menyediakan berbagai method untuk melakukan querying database tanpa perlu menulis SQL secara langsung, sehingga mempercepat dan mempermudah pengembangan aplikasi.