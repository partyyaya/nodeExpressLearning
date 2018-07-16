## Ejs-Include使用

#### 建立與使用
- 在 views 資料夾 建立in.ejs

```EJS
<h1>12345</h1>
``` 
- 使用in.ejs
- 在views資料夾再 建立一個ejs 並應用上去即可
```EJS
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body> 
    <%- include('in'); %>
</body>
</html>   
```