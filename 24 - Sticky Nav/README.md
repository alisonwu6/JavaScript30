# 24 - Sticky Nav

### 功能說明
* 當nav上緣與網站viewport上邊界碰到時，就將nav固定在viewport上方。


### JavaScript
* window.scrollY：視窗垂直滑動量
* element.offsetTop：元素上邊界與視覺窗口上邊界的距離
* nav一旦fixed於上邊界，高度就會消失，此時為了避免`.site-wrap`上移，須增加paddingTop給body
* offsetHeight：元素的高度，包含padding和border
```
const nav = document.querySelector('#main');
let topOfNav = nav.offsetTop;

  function fixNav() {
    if (window.scrollY >= topOfNav) {
      document.body.style.paddingTop = nav.offsetHeight + 'px';
      document.body.classList.add('fixed-nav');
    } else {
      document.body.classList.remove('fixed-nav');
      document.body.style.paddingTop = 0;
    }
  }
window.addEventListener('scroll', fixNav);
```

### CSS
* 將fixed-nav設定在body上，方便設定其他fixed-nav狀態下其他元件的樣式
```
body.fixed-nav nav {
  position: fixed;
  box-shadow: 0 5px 0 rgba(0, 0, 0, 0.1);
}
```
* fixed-nav狀態下其他元件的樣式，此部分從max-width: 0px 變成 500px
```
.fixed-nav li.logo {
  max-width: 500px;
}
```