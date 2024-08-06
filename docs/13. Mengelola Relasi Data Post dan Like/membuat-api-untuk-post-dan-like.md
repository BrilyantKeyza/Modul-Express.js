---
sidebar_position: 2
---

# 13.2 Membuat API untuk post dan like


### Penjelasan
Setelah model dan relasi didefinisikan, kita akan membuat API untuk memungkinkan user membuat post, memberi like pada post, dan menghapus like.

**Langkah-Langkah:**

1.  **Membuat API untuk Post:**
    
    -   Tambahkan route untuk membuat, membaca, mengupdate, dan menghapus post.
    
    **Contoh Route CRUD untuk Post:**
    

    ```
    const Post = require('./models/Post');
    
    // Membuat Post baru
    app.post('/posts', authenticateJWT, async (req, res) => {
      const { title, content } = req.body;
      const userId = req.user.id;
    
      try {
        const post = await Post.create({ title, content, userId });
        res.status(201).json(post);
      } catch (err) {
        res.status(400).json({ error: err.message });
      }
    });
    
    // Mendapatkan semua Post
    app.get('/posts', async (req, res) => {
      try {
        const posts = await Post.findAll();
        res.json(posts);
      } catch (err) {
        res.status(500).json({ error: err.message });
      }
    });
    
    // Menghapus Post
    app.delete('/posts/:id', authenticateJWT, async (req, res) => {
      const postId = req.params.id;
      const userId = req.user.id;
    
      try {
        const post = await Post.findOne({ where: { id: postId, userId } });
        if (!post) {
          return res.status(404).json({ error: 'Post tidak ditemukan atau kamu tidak memiliki izin untuk menghapusnya' });
        }
        await post.destroy();
        res.status(204).send();
      } catch (err) {
        res.status(500).json({ error: err.message });
      }
    });
    ``` 
    
2.  **Membuat API untuk Like:**
    
    -   Tambahkan route untuk memberi dan menghapus like dari post.
    
    **Contoh Route untuk Like:**
    
    ```
    const Like = require('./models/Like');
    
    // Memberi Like pada Post
    app.post('/posts/:postId/like', authenticateJWT, async (req, res) => {
      const postId = req.params.postId;
      const userId = req.user.id;
    
      try {
        const like = await Like.create({ postId, userId });
        res.status(201).json(like);
      } catch (err) {
        res.status(400).json({ error: err.message });
      }
    });
    
    // Menghapus Like dari Post
    app.delete('/posts/:postId/like', authenticateJWT, async (req, res) => {
      const postId = req.params.postId;
      const userId = req.user.id;
    
      try {
        const like = await Like.findOne({ where: { postId, userId } });
        if (!like) {
          return res.status(404).json({ error: 'Like tidak ditemukan' });
        }
        await like.destroy();
        res.status(204).send();
      } catch (err) {
        res.status(500).json({ error: err.message });
      }
    });
    ```
    

### Kesimpulan
 API ini memungkinkan user untuk membuat post, memberi like pada post, dan menghapus like yang sudah diberikan. Ini adalah dasar interaksi sosial dalam aplikasi yang melibatkan user-generated content.