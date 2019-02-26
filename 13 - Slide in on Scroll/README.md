# 13 - Slide in on Scroll

### 功能說明
* 當捲軸滑動時，圖片會做出移入與移出的效果。

### JavaScript
* 利用**debounce**方法將scroll的監聽事件減少成**20毫秒**監聽一次，減少瀏覽器監聽太多scroll事件
  ```
  window.addEventListener('scroll', debounce(checkSlide));
  ```
* window屬性
  * window.scrollY：視窗範圍外Y軸已經滾動的量
  * window.innerHeight：網頁viewport的高度

### 功能開發邏輯說明
  * 所需值
    * 取得圖片1/2高度的定位點
      ```
      const slideInAt = (window.scrollY + window.innerHeight) - sliderImage.height / 2;
      ```
    * 取得圖片底部定位點
      ```
      const imageBottom = sliderImage.offsetTop + sliderImage.height;
      ```
    * 判斷視窗是否已經超過圖片高度一半
      ```
      const isHalfShown = slideInAt > sliderImage.offsetTop;
      ```
    * 判斷滾動範圍是否已經超過圖片底部（卷軸垂直位移量）
      ```
      const isNotScrolledPast = window.scrollY < imageBottom;
      ```
  * 當 `isHalfShown && isNotScrolledPast` 兩個皆成立，增加active類別。
    ```
    if (isHalfShown && isNotScrolledPast) {
      sliderImage.classList.add('active');
    } else {
      sliderImage.classList.remove('active');
    }
    ```