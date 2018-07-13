## 載入靜態檔案(image,css,js)

#### 執行
- 在專案資料夾創建 放靜態文件 檔案資料夾
- 建立 images 資料夾,並在裡面放入圖片
- 在專案 router js檔案加上

```javascript
//增加靜態檔案的路徑
app.use(express.static('public'));

app.get('/',function(req,res){
    res.send('<html><head></head><body><image src="/images/123.jpg"></body></html>');
})
```
- 說明 : 
    - express.static('public') : 代表靜態檔案放在 public 資料夾內
- 執行 node 你的.js