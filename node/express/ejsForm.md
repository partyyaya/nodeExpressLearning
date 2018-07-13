## Ejs-form使用

#### 建立與使用
- 建立 search.ejs 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <form action="/searchList" method="post" >
        <input type="text" name="content" id="content" value="">
        <input type="submit" id="send"  value="送出">
    </form>
</body>
</html>
```
- 在專案router js檔加入

```javascript
app.post('/searchList',function(req,res){
    console.log(req.body.title);
    var title = req.body.title;
    //轉址(網址為search=>無法傳值)
    //res.redirect('search');
    
    //轉址渲染(網址為search)   
    res.render('search',{
        'title':title
    });
})
```
- 說明 : 
    - 先用 form action 指向 路徑:searchList method使用post
    - 使用 app.post() 接收request
    - 用 res.render() 渲染 search.ejs 並傳值(title)
- 執行 : node 你的.js 並到127.0.0.1:3000/search 輸入任意字串 即可看到成果
