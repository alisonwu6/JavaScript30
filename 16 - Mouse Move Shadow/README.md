# 16 - Mouse Move Shadow

### 功能說明
* 滑鼠在網頁上滑動產生文字陰影的效果

### JavaScript
* 解構賦值語法：將陣列或物件中的資料取出成獨立變數
  ```
  const width = hero.offsetWidth;
  const height = hero.offsetHeight;
  ```
  等同：`const { offsetWidth: width, offsetHeight: height } = hero;`

* this 與 e.target
  * 以此範例**shadow**函式的this都會指向`<div class="hero">`
  * e.target：此屬性永遠指向觸發事件的 DOM 物件，如this下的子元件

* 針對e.target可能為`<h1 contenteditable>🔥WOAH!</h1>`，調整x與y軸
  ```
  if (this !== e.target) {
    x = x + e.target.offsetLeft;
    y = y + e.target.offsetTop;
  }
  ```
* Math.round()：回傳四捨五入後的近似值
  * 以下為坐標跑動的參考值
  ```
  const xWalk = Math.round((x / width * walk) - (walk / 2));
  const yWalk = Math.round((y / height * walk) - (walk / 2));
  ```