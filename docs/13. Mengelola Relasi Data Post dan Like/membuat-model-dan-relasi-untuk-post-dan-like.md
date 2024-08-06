---
sidebar_position: 1
---

# 13.1 Membuat model dan relasi untuk post dan like


### Penjelasan
Relasi antara `Post` dan `Like` biasanya adalah relasi one-to-many, di mana satu post bisa memiliki banyak like. Di Sequelize, kita bisa merepresentasikan relasi ini dengan mendefinisikan model `Post` dan `Like`, serta mendefinisikan asosiasi antar keduanya.

**Langkah-Langkah:**

1.  **Membuat Model Post:**
    
    -   Buat model `Post` yang memiliki field seperti `title`, `content`, dan `userId` (foreign key yang merujuk ke user yang membuat post).
    
    **Contoh Model Post:**
    
    ```
    const { DataTypes } = require('sequelize');
    const sequelize = require('../config/sequelize');
    
    const Post = sequelize.define('Post', {
      title: {
        type: DataTypes.STRING,
        allowNull: false
      },
      content: {
        type: DataTypes.TEXT,
        allowNull: false
      },
      userId: {
        type: DataTypes.INTEGER,
        allowNull: false
      }
    });
    
    module.exports = Post;
    ```
    
2.  **Membuat Model Like:**
    
    -   Buat model `Like` yang memiliki field `userId` (foreign key ke user yang memberi like) dan `postId` (foreign key ke post yang di-like).
    
    **Contoh Model Like:**
    

    ```
    const { DataTypes } = require('sequelize');
    const sequelize = require('../config/sequelize');
    
    const Like = sequelize.define('Like', {
      userId: {
        type: DataTypes.INTEGER,
        allowNull: false
      },
      postId: {
        type: DataTypes.INTEGER,
        allowNull: false
      }
    });
    
    module.exports = Like;
    ``` 
    
3.  **Mendefinisikan Relasi antara Post dan Like:**
    
    -   Hubungkan model `Post` dan `Like` menggunakan `hasMany` dan `belongsTo` untuk merepresentasikan relasi one-to-many.
    
    **Contoh Relasi:**

    ```
    const User = require('./User');
    const Post = require('./Post');
    const Like = require('./Like');
    
    // Relasi antara User dan Post
    User.hasMany(Post, { foreignKey: 'userId' });
    Post.belongsTo(User, { foreignKey: 'userId' });
    
    // Relasi antara Post dan Like
    Post.hasMany(Like, { foreignKey: 'postId' });
    Like.belongsTo(Post, { foreignKey: 'postId' });
    
    // Relasi antara User dan Like
    User.hasMany(Like, { foreignKey: 'userId' });
    Like.belongsTo(User, { foreignKey: 'userId' });
    ```
    

### Kesimpulan
Dengan mendefinisikan model dan relasi ini, kamu telah mengatur struktur database yang memungkinkan setiap post memiliki banyak like, dan setiap like terkait dengan user yang memberikannya. Relasi ini adalah dasar untuk operasi CRUD pada post dan like.