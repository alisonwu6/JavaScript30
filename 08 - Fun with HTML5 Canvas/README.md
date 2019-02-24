# 08 - Fun with HTML5 Canvas

### 功能說明
* 在Canvas上跟著滑鼠畫線，繪製過程能變更顏色與改變線的寬度

### JavaScript - Canvas
* Canvas主要是透過方法來繪製圖型
* 繪圖情境設定：
  1. Canvas的API定義在`getContext()`方法回傳的「繪圖情境」
    * `getContext(2d)`來獲取一個”CanvasRenderingContext2D物件“
  2. 繪製直線使用方法：
    * .beginPath()：開始一個新路徑
    * .moveTo(lastX, lastY)：在(lastX, lastY)開始一個新的子路徑
    * .lineTo(e.offsetX, e.offsetY)： 新增一個線段，從(lastX, lastY)連至(e.offsetX, e.offsetY)
    * .stroke()：畫出線段需呼叫stroke方法
  3. 圖型屬性：
    * .strokeStyle：線條的顏色、間曾或圖樣
    * .lineJoin：頂點要如何描繪
    * .lineCap：線條的端點要如何描繪
    * .lineWidth：畫出來的線條寬度