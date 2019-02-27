# 22 - Follow Along Link Highlighter

### 功能說明
* 頁面上所有的連結標籤<a>hover時都會都會有滑入白色底的特效。


### CSS
* 版面有點跑掉，所以調整了一點，並附上註解'Modified'

### JavaScript
1. 
  * createElement：建立HTML元素
  * element.classList.add('className')：為元素加入class
  * document.body.append(element)：將element加入到HTML body內
  ```
  const highlight = document.createElement('span');
  highlight.classList.add('highlight');
  document.body.append(highlight);
  ```
2. 為lighlight元素的特效出現位置定位
  * getBoundingClientRect()：回傳元素本身的尺寸與其相對位置
  * 使用transform需要顧慮到網頁下滑時scrollY的距離，所以這邊透過coords來算出寬、高、滑動Y軸後的位置高度
```
function highlightLink() {
  const linkCoords = this.getBoundingClientRect();
  // console.log(linkCoords);
  const coords = {
    width: linkCoords.width,
    height: linkCoords.height,
    top: linkCoords.top + window.scrollY,
    left: linkCoords.left + window.scrollX
  }
  highlight.style.width = `${coords.width}px`;
  highlight.style.height = `${coords.height}px`;
  highlight.style.transform = `translate(${coords.left}px,${coords.top}px)`;
}
```
