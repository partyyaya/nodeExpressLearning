## exports 的應用

#### 創建檔案
- 於根目錄創建 called.js 與 call.js
- called.js : 

```javascript
/*
exports.content=1;
exports.title=2222;
等於以下                */
module.exports={
    content:1,
    title:2222
}
```
- call.js : 

```javascript
//引入called.js
var content = require('./called');

console.log("hello");

//輸出引入內容
console.log(content);
console.log(content.title);
```
- 說明 :
    - 使用 exports 或 module.exports 傳輸資料
    - 使用 require('./檔案名稱') 去引入檔案
    - 使用 console.log(content.title) 得到想要的資料
- 執行 node call.js即可在終端機看到成果


