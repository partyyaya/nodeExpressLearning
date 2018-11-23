## http 模組知識

#### 創建檔案
- 於根目錄創建 http.js
- http.js : 

```javascript
var http = require("http");
http.createServer(function(require,response){
    response.writeHead(200,{"Content-Type":"text/plain"});
    response.write("hello world");
    response.end();
}).listen(8080);
```
- 說明 :
    - 使用 require("http") 引入http 模塊
    - 使用 http.createServer() 可製作出server來傳遞資料
    - 利用 .listen(8080) 監聽 port 8080
    - 使用 response.writeHead() 設定傳送資料格式與表頭設定
        - 200 : 傳送正確
        - 404 : 傳送失敗(路徑錯誤)
        - 500 : 程式內部錯誤
        - text/plain : 文字訊息
        - text/html : 網頁文本
    - 使用 response.write("hello world") 設定在網頁上想顯示的資料
    - 使用 console.log(content.title) 得到想要的資料
- 執行 node http.js即可在終端機看到成果


