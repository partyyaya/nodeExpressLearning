## 路由整理與使用

#### 使用方式
- 在原路由加上此程式片段

```javascript
//使用 routes 資料夾裡的 user.js
var user = require('./routes/user');
app.use('/user',user);
```
- 建立routes資料夾
- 並建立user.js

```javascript
var express = require('express');
var router =  express.Router();

router.get('/edit-profile',function(req,res){
    res.send('profile');
})

router.get('/photo',function(req,res){
    res.send('photo');
})

module.exports = router;
```
- 用意 : 將每個功能做成自己的路由以便利管裡
    - 如 user 使用者頁面有自己的一塊路由 /user/xxx
- 舉例 : 
    - 當源路由進入user裡的photo
    - 則路徑會自動變成 : localhost:port/user/photo