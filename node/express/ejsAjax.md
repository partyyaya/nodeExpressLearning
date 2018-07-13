## Ejs-ajax使用

#### 建立與使用
- 在專案router js檔加入
- ps : 記得加入 app.use(express.static('public'));

```javascript
app.post('/searchAJAX',function(req,res){
    console.log(req.body);
    console.log(req.body.list[2]);
    console.log('hello!!')
    // console.log(req.body);
    // //轉址
    res.redirect('search');
    // res.render('search');
})
```
- 在 public 資料夾加入 js 資料夾
- 建立all.js檔案

```javascript
var send = document.getElementById('send');
var content = document.getElementById('content');

send.addEventListener('click',function(e){
    //避免submit事件
    e.preventDefault();

    var str = content.value;
    var data =  JSON.stringify({"content":str,"list":[1,2,3]});

    //使用ajax傳送資料
    var xhr = new XMLHttpRequest();
    xhr.open('post','/searchAJAX');

    //回傳字串類型資料
    xhr.setRequestHeader("Content-type",
    "application/json");

    //欲傳送資料
    xhr.send(data);
    xhr.onload = function(){
        console.log(xhr.responseText);
    }
})
```
- 執行 : node 你的.js 並到127.0.0.1:3000/search 輸入任意字串 即可在終端機cmd看到成果