# 02 - JS and CSS Clock

### 功能說明
* 使用JavaScript與CSS實作時鐘

### JavaScript
1. **setInterval(setDate, 1000);**
  * 以指定的毫秒數值為間隔，持續執行函式。
  * new Date()取得當下時間
    * Date.getSeconds()
    * Date.getMinutes()
    * Date.getHours()
  
  * 旋轉角度因指針(.hand)使用transform: rotate(90deg)，所以需要加回90。


