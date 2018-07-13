## Ejs-Layout使用

#### 建立與使用
- 在 views 資料夾 建立ejsLayout.ejs

```EJS
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body> 
    <%/*此為引入layout寫法*/ %>
    <%-body %>
</body>
</html>   
``` 
- 使用layout.ejs
- 在views資料夾再 建立一個ejs 並打它應用上去即可
- 記得要放在TOP,下面內容會全部包在body標籤裡
```EJS
<% layout('layout') %>
```