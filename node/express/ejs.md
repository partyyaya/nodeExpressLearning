## Ejs 使用

#### 安裝 與 使用
- 安裝 ejs-locals 與 body-parser
- npm install ejs-locals body-parser --save
- 在專案router js檔加入

```javascript
var express = require('express');
var app = express();
var engine = require('ejs-locals');
var bodyParser = require('body-parser');

app.engine('ejs',engine);

//統一將樣板放入views資料夾
app.set('views','./views');

//用ejs template方式呈現
app.set('view engine','ejs');

//增加body解析
app.use(bodyParser.json());//可解析json資料
app.use(bodyParser.urlencoded({extended:false}))

app.get('/',function(req,res){
    res.render('index',{
        'isShow':true,
        'title':'就學習',
        'me':'<h1>chin</h1>',
        'array':['aaa','bbb','ccc','ddddd']
    });
})
```
- 說明 : 
    - app.engine('ejs',engine) : 表示使用ejs當渲染引擎
    - app.set('views','./views') : 統一將樣板放入views資料夾
    - app.set('view engine','ejs') :　用ejs template方式呈現
    - res.render('index',{'title':"12378"}) : 對 index.ejs 渲染,並提交數據(title)
    - 常見的四種content-type
        - application/x-www-form-urlencoded 常见的form提交
        - multipart/form-data 文件提交
        - application/json 提交json格式的資料
        - text/xml 提交xml格式的資料
    - app.use(bodyParser.json()) :　解析json資料(req.body)
        - 也就是header中包含：Content-Type: application/json
    - app.use(bodyParser.urlencoded({extended:false})):用来解析form表单提交的資料
        - 也就是header中包含：Content-Type: application/x-www-form-urlencoded
        - 屬性: extended -> extended選項允許使用querystring(false)或qs(true)來解析，默認值是true
            - querystring 用來字符串化對像或解析字符串 : 
                - querystring.parse("name=henry&age=30") => { name: 'henry', age: '30' }
            - qs是一個querystring的庫，在qs的功能基礎上，支持更多的功能優化了一些安全性
            
```
// 內建對象 querystring
querystring.parse("info[name]=henry&info[age]=30&hobby[1]=sport&hobby[2]=coding") => 
{ 
    'info[name]': 'henry',
    'info[age]': '30',
    'hobby[1]': 'sport',
    'hobby[2]': 'coding'
}

// 第三方插件 qs
qs.parse("info[name]=henry&info[age]=30&hobby[1]=sport&hobby[2]=coding") => 
{
    info: {
    name: 'henry',
    age: '30'
    },
    hobby: [ 'sport', 'coding' ]
}
```
- 建立 views資料夾
- 在資料夾裡 建立 index.ejs :

```EJS
<% if(isShow){ %>
        <span>友秀出來</span>
<%}%>
<%=title%>
<%-me%>

<ul>
    <% for(var i=0;i<array.length;i++){ %>
        <li><%= array[i]%></li>
    <% } %>
</ul>
```
- 說明 : 
    -  %= % => 輸出字串
    -  %- % => 輸出網頁文本
    -  %  % => 進行邏輯與其他運算
- 執行 : node 你的.js 並到127.0.0.1:3000即可看到成果
