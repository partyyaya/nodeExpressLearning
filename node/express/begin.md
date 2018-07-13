## Express 開始

#### 安裝與開始
- 安裝 Express ： npm install express --save
- 建立 app.js(router) ： 

```javascript
//引入express
var express = require('express');
var app = express();

//會先用500檢查是否程式裡面是否發生錯誤(若在錯誤前有res.send()則頁面部會出現500)
//若找不到路徑再發404(裡面只要沒有符合路徑都會到404)
var login = function(req,res,next){
    var _url = req.url;
    console.log('yeeeeeee')
    next();
}

//可以這樣使用：
//app.use(login);

//代表守門員,若使用 next() 才會使使用者通過,不論是哪個路徑都會執行裡面的內容
app.use(function(req,res,next){
    console.log('有人進來了');
    next();
})

//可以將middleware放在中間
app.get('/',login,function(req,res){
    //pp();
    res.send('<html><head></head><body><h1>12345</h1></body></html>');
})

//err為500出現時才使用否則依綠都會出現404的字樣
app.use(function(req,res,next){
    res.status(404).send('抱歉你的頁面找不到');
})

app.use(function(err,req,res,next){
    console.error(err.stack);
    res.status(500).send('請稍等片刻,網頁補眠中');
})

//監聽port
//process.env.PORT ： 電腦預設的port
var port = process.env.PORT || 3000;
app.listen(port);
```
- 說明 ： 
    - 方便引入使用 express ： 
        - var express = require('express');
        - var app = express();
    - app.use() ： 稱 middleware 可當作守門員,在進入網頁之前可先檢查是否符合條件並執行
        - err ： 當錯誤時可以使用 
            - console.error(err.stack) 查看錯誤
        - req ： 得到的封包或傳值
        - res ： 回傳文本 或 傳值 給頁面
            - res.status(狀態).send(字串) ： 當發生狀態時會直接顯示send的字串
        - next() ： 滿足條件時使程序通過
    - app.get() ： 當網頁傳送get請求時會透過此方式回傳畫面
    - app.post() ： 當網頁傳送post請求時會透過此方式回傳畫面
    - app.listen(port) ： 監聽port -> 本機端可用：127.0.0.1：3000開啟
        - process.env.PORT ： 電腦預設的port
- 執行 ： node app.js

#### 基本設計與流程
- 首先先引入
- 設計 middleware(條件篩選,404,500)
- 設計 get 與 post 與路徑
- 設計畫面
- 測試流程

